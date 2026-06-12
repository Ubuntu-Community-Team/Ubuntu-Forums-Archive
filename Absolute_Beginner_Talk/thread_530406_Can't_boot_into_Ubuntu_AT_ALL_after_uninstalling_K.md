---
title: "Can't boot into Ubuntu AT ALL after uninstalling KDE"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by mikecomua on 2007-08-20
Hello, I have originally installed Ubuntu Feisty on my computer but then decided to try KDE, so I typed in[PHP]sudo aptitude install kubuntu-desktop[/PHP]. Then I booted KDE OK, and worked with it for a few days. Afterwards, when I wanted to boot into Gnome Mac OS icons show up on the boot screen (I installed the theme) and I see taskbars with no icons.
Then I uninstalled and installed Gnome, but nothing worked. I posted my question on Ubuntu forums [http://ubuntuforums.org/showthread.php?t=529537]("http://ubuntuforums.org/showthread.php?t=529537") So I uninstalled KDE using Konsole and it said something about two packages not being uninstalled and it asked if it should continue and i said yes. So I entered Gnome from the  sessions menu, but there were the same empty taskbars.
By the way I downloaded a GRUB splash screen from KDE-look.org 
[http://kde-look.org/content/show.php/Ubuntu+7.04+Grub+Bootscreen?content=57961]("http://kde-look.org/content/show.php/Ubuntu+7.04+Grub+Bootscreen?content=57961")
Then I rebooted, Grub showed up, I selected Ubuntu, it loaded and then a black screen shows up with this[
[PHP]/etc/init.d/rc:2:usplash_write: permission denied
/etc/init.d/rc:2:/etc/rcS.d/S85 u random: Permission denied
/etc/init.d/rc:2:usplash_write: permission denied
init:Unable to execute "/bin/sh" for rc-default: Permission denied
init:rc-default main process 4221 terminated with status 255[/PHP]
;cry:
P.S. If my Ubuntu install is dead will I be able to safely format my Ubuntu partition and reinstall Ubuntu?
P.P.S. This was typed using a Ubuntu  LiveCD

---

### Post by yogo on 2007-08-20
Since you are able to connect to the Internet, just use Synaptic to reinstall Gnome, also another good light desktop manager is XFCE. add one of these and you should be good to go without reinstalling Ubuntu.

---

### Post by mikecomua on 2007-08-20
Did you read the message?

---

### Post by mikecomua on 2007-08-20
I can't even boot into Ubuntu!

---

### Post by nvteighen on 2007-08-20
First, using your Live CD, try to backup your data. (access the partition from Places --> Computer, mount the Ubuntu partition, locate your home folder and copy). That's the most important.

Second, have you tried using an older kernel? Surely you have **Ubuntu, kernel 2.6.20-15** in your GRUB menu.

---

### Post by irish_flu on 2007-08-20
After that error message, are you dumped to a command prompt, or is it just the error with no ability to enter commands?

---

### Post by mikecomua on 2007-08-20
1)I have tried kernel 2.6.20.15 and recovery mode.
2)I tried to enter sudo aptitude install kubuntu-desktop and sudo aptitude install gnome-desktop, but it didn't even ask for the password

---

### Post by nvteighen on 2007-08-20
> **mikecomua said:**
> 1)I have tried kernel 2.6.20.15 and recovery mode.
2)I tried to enter sudo aptitude install kubuntu-desktop and sudo aptitude install gnome-desktop, but it didn't even ask for the password

Well, sudo apt-get will try to install KDE **into your Live CD session** (that's why it doesn't ask for your password) and you'll run out of RAM memory trying to do that. Also, your problem wouldn't be solved by that, as your problem is at the kernel and the boot process.

Try to see what permissions are set to init.d. Be sure to look for the one at your hard disk (not the one loaded by the Live CD).

But first backup everything!

Possibly, KDE hijacked something... I'd a problem where KDE destroyed my fonts in GNOME and had to reinstall. For the future, don't have both installed at the same time.

---

### Post by mikecomua on 2007-08-20
how do I do that?

---

### Post by yogo on 2007-08-20
> **nvteighen said:**
> For the future, don't have both installed at the same time.


This point might be debatable? I have KDE, Gnome, and XFCE all installed at the same time, I think having at least one back up manager lets say if Gnome fails, then you can start a new session with KDE or XFCE.

---

### Post by nvteighen on 2007-08-20
> **mikecomua said:**
> how do I do that?

To backup:
1) After Live CD has booted and GNOME is ready, go to Places -> Computer.
2) You'll see your drives. One will be surely called "Filesystem", that is your Live CD's system.
3) Double click anything called "x GiB Volume"
4) Then, in that window, click the home folder and then the folder with your regular username.
5) You'll see all your data. Plug a Flash drive (it will appear in the Desktop) and drag-and-drop.

Maybe you'll need to drop your files into another computer if your Flash drive (or whatever) is too small.

That's the principal, actually: to rescue your data. Afterwards, you can simply reinstall...

---

### Post by mikecomua on 2007-08-20
I found init in /media/disk-1/etc/gdm/Init.
Here's what it says:
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH=/usr/X11R6/bin:$PATH
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}


sysmodmap=/etc/X11/Xmodmap

XMODMAP=`gdmwhich xmodmap`
if [ x$XMODMAP != x ] ; then
  if [ x$GDM_PARENT_DISPLAY = x ]; then
    if [ -f $sysmodmap ]; then
      $XMODMAP $sysmodmap
    fi
  else
    ( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $XMODMAP -pke ) | $XMODMAP -
  fi

  #
  # Switch Sun's Alt and Meta mod mappings
  #

  UNAME=`gdmwhich uname`
  PROCESSOR=`$UNAME -p`
  if [ x$PROCESSOR = xsparc ]; then
    if $XMODMAP | /usr/bin/grep mod4 | /usr/bin/grep Alt > /dev/null 2>/dev/null
    then
      $XMODMAP -e "clear Mod1" \
               -e "clear Mod4" \
               -e "add Mod1 = Alt_L" \
               -e "add Mod1 = Alt_R" \
               -e "add Mod4 = Meta_L" \
               -e "add Mod4 = Meta_R"
    fi
  fi
fi

SETXKBMAP=`gdmwhich setxkbmap`
if [ x$SETXKBMAP != x ] ; then
  # FIXME: is this all right?  Is this completely on crack?
  # What this does is move the xkb configuration from the GDM_PARENT_DISPLAY
  # FIXME: This should be done in code.  Or there must be an easier way ...
  if [ -n "$GDM_PARENT_DISPLAY" ]; then
    XKBSETUP=`( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $SETXKBMAP -v )`
    if [ -n "$XKBSETUP" ]; then
      XKBKEYMAP=`echo "$XKBSETUP" | grep '^keymap' | awk '{ print $2 }'`
      XKBTYPES=`echo "$XKBSETUP" | grep '^types' | awk '{ print $2 }'`
      XKBCOMPAT=`echo "$XKBSETUP" | grep '^compat' | awk '{ print $2 }'`
      XKBSYMBOLS=`echo "$XKBSETUP" | grep '^symbols' | awk '{ print $2 }'`
      XKBGEOMETRY=`echo "$XKBSETUP" | grep '^geometry' | awk '{ print $2 }'`
      if [ -n "$XKBKEYMAP" ]; then
        $SETXKBMAP -keymap "$XKBKEYMAP"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" -a -n "$XKBGEOMETRY" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS" -geometry "$XKBGEOMETRY"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS"
      elif [ -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -symbols "$XKBSYMBOLS"
      fi
    fi
  fi
fi

exit 0

I am VERY new to Ubuntu. Sorry to cause this trouble

---

### Post by nvteighen on 2007-08-21
No, you that's not related to boot, but to GNOME. Actually, I'm looking for a folder, not a file.

Please, with your hard drive mounted (go to Places --> Computer and double click your partition as you did before). Then open a terminal (Applications --> Accesories --> Terminal) and type:

```

ls -l /media/disk/boot

```

or, if it not works (because it is your USB stick what's mounted at /media/disk)

```

ls -l /media/disk-1/boot

```

Send me what you get (mark the text as it you were in Notepad, right-click and select "Copy").

Have you backed everything up successfully?

---

