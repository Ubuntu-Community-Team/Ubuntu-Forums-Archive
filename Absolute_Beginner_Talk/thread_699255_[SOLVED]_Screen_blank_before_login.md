---
title: "[SOLVED] Screen blank before login"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by filligree on 2008-02-17
I've been using Ubuntu for a few weeks, and had this problem initially, which I solved by reinstalling (this was an accidental solution - I had other problems, and decided reinstalling was easier than trying to work out what I needed to fix).  I don't particulalrly want to reinstall again, since I've got everything set up and working.

The problem is this - when I switch the computer on my monitor goes to sleep until the login screen loads.  I previously had grub and the orange bar screen running, but now they've vanished, which means I can't boot into Windows (and I need to, sadly, since my printer isn't supported in Ubuntu).  I also get the message "Input Out of Range" when shutting down rather than the orange bar again.

This has only started since we had a power cut a couple of days ago.  Anything else you need to know, please ask - I'm a noob, and so don't know what things are important yet.

Cheers.

---

### Post by aashay on 2008-02-17
This happens because the combination of resolution and refresh rate used by usplash is too low for your system. Try adding vga=794 (or 795)  to your kernel parameters while booting. To do this while ubuntu is highlited, press e and go to the second line. press e again and append vga=794 to the line. Press enter and then b to boot.
EDIT: I am assuming you run a resolution on 1280x1024. Please correct me if i am wrong

---

### Post by filligree on 2008-02-17
I'd love to, but I don't see anything before the login screen, just a blank screen.  No grub, szo no way of adding to the kernel parameters.

---

### Post by aashay on 2008-02-17
The screen blanks out before grub loads up? Or is grub not installed at all?? Do you have a /boot/grub/menu.lst ? If so please post it here

---

### Post by filligree on 2008-02-17
The screen blanks before grub loads.  in fact, I no longer even see the Compaq screen that my monitor loads before grub, just the ubuntu login screen, which is fine.  Do I find /boot./grub/menu.lst via terminal?  Sorry, I'm still learning.

---

### Post by filligree on 2008-02-17
Ok, I have boot/grub/menu.lst in the filesystem.

---

### Post by filligree on 2008-02-17
> **filligree said:**
> Ok, I have boot/grub/menu.lst in the filesystem.

And this is what it contains

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-51-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-51-386 root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-51-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-51-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-51-386 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.15-51-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by isparkes on 2008-02-17
could it be that your master boot record is broken, and is no longer finding Grub? What happens if you boot from a live CD? Do you still see all the other information on the drive?

---

### Post by filligree on 2008-02-17
I don't think that that is the problem, as I don't see ANYTHING at all before login, and my monitor goes to sleep - I don't see the COMPAQ screen I was seeing before, or the Ubuntu loading screen, which makes me think it's a screen resolution problem.  I'd like to try what aashay suggested, but the display doesn't show, so I can't, unless there's a way into it via terminal.

---

### Post by filligree on 2008-02-17
OK, thought I'd try running from the Live CD again, and my system won't run from it, will only (eventually) boot into Ubuntu, so now it appears I don't even have the reinstall option.  I also tried running a Live CD of Feisty, which wouldn't run either.  Is there a way to get into the kernal parameters and amend them via terminal or something similar.

---

### Post by filligree on 2008-02-17
Also, double checked screen resolution, is only 1024x780 with refresh rate 75Hz.

---

### Post by filligree on 2008-02-17
And again, I'll keep posting, in case something I do makes any difference to what someone can tell  me - I don't have the usplash.conf file.  It's just not there.  I tried adding vga=791 to /boot/grub/menu.lst, but it made no difference.

---

### Post by Tupy on 2008-02-17
I had a blank screen after i selected ubuntu from grub, to have a splash screen (ubuntu logo with load bar) i had to do the folowing:

edit /etc/usplash.conf and set resolution to a correct one for the screen. if you type
```
sudo gedit /etc/usplash.conf
```
 you can edit the file and save it. Mine looks like this:

```
# Usplash configuration file
xres=1024
yres=768
```

then you have to type in console
```
sudo update-usplash-theme usplash-theme-ubuntu
```

Hope it works!

---

### Post by Hobo Joe on 2008-02-17
I've had this exact same problem, and after months(literally, months) of trying to figure it out, I finally did last night.

You have to edit grub and disable the splash screen. Although this fixes the problem, you won't seen the loading bar, you'll just see the text version of the boot process.
So you'd make the appropriate section of grub look like this: 
```

title		Ubuntu, kernel 2.6.15-51-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-51-386 root=/dev/sdb1 ro quiet [COLOR="Red"]**nosplash**[/COLOR]
initrd		/boot/initrd.img-2.6.15-51-386
savedefault
boot

```

Hopefully this works for you like it did for me!

---

### Post by aashay on 2008-02-17
maybe you fiddled around with power saving features in the bios which causes your monitor to sleep. Because in any case , you care supposed to see the "compaq" screen and grub. Does entering BIOS setup cause the display to reappear?

---

### Post by erginemr on 2008-02-18
> **Tupy said:**
> I had a blank screen after i selected ubuntu from grub, to have a splash screen (ubuntu logo with load bar) i had to do the folowing:

edit /etc/usplash.conf and set resolution to a correct one for the screen. if you type
```
sudo gedit /etc/usplash.conf
```
 you can edit the file and save it. Mine looks like this:

```
# Usplash configuration file
xres=1024
yres=768
```

then you have to type in console
```
sudo update-usplash-theme usplash-theme-ubuntu
```

Hope it works!

This is the correct solution. I have come across this problem several times and editing usplash.cong file is the way to go, the only difference being we used 
```
sudo dpkg-reconfigure -phigh usplash
```
to reflect the change instead.

Please also refer to this reading:
[http://geekybits.blogspot.com/2007/11/fix-for-no-splash-in-ubuntu-710.html](http://geekybits.blogspot.com/2007/11/fix-for-no-splash-in-ubuntu-710.html)
and this one:
[http://www.livingubuntu.com/?p=72](http://www.livingubuntu.com/?p=72)

---

### Post by filligree on 2008-02-18
Right, I edited the screen resolutions in usplash.conf, but still have blank screen (no grub).  How do I access the BIOS settings?

Also, how do I thank people?  I really appreciate all the help... :-)

---

### Post by sabatron on 2008-02-18
It's different for other computers I think...but I can access mine if I press F2 as soon as the start up.  Some people press esc.  I think your computer manual will tell you.

---

### Post by Nick8692 on 2008-02-18
yes, this has happend to me before.  It is easy to fix.

boot into recovery mode and type;

**sudo dpkg-reconfigure --phigh xserver-xorg**

This will reset your x server by asking you a seris of questions.  Just select the defult for each question unless you know better :)
if there are any errors, or you finnish, just reboot and it should work perfectly fine.

---

### Post by filligree on 2008-02-18
OK, the problem still remains, and the biggest is that I don't see ANYTHING before the login screen - so I can't run recovery mode, BIOS or anything.  If I run "sudo dpkg-reconfigure --phigh xserver-xorg" in a terminal, will i get the same results whether I'm in recovery mode or not?

---

### Post by filligree on 2008-02-18
OK, running that code made no difference - xorg.conf is still the same.  I tried accessing the BIOS by pressing F10 during boot, but still no display, so no idea if anything worked.  Seemed to hang, so ended up hard-restarting.

---

### Post by aashay on 2008-02-18
Maybe your display (CRT?) is taking too long to power on. The login screen shows up some  time before it powers on so you think it powers on just when it appears. It seems so because you are supposed to have display in grub and BIOS no matter what. BIOS settings can be entered by pressing F2 or DEL when the computer is booting up. See if this owrks:
In the login window prefs -> Accessibility tab, Enable a sound to be played when the screen is ready. 
Next time you start the computer, check the lag between the sound and the display.

---

### Post by filligree on 2008-02-18
Well, it worked til we had a power cut a couple of days ago.  Anyway, tis a TFT flatscreen thingy, and it displays the resolution details when it powers up, then goes to sleep until the login window appears, the sound plays, then it runs fine.  At shut down I get "Input Video Out of Range".

---

### Post by filligree on 2008-02-18
Well, I fixed it, although I'm not sure I understand how.  In Ubuntu, through the System menu, I set the screen resolution to 600x480 or whatever the smallest is, which then gave me "input out of range".  I hard restarted, and since then, it's been fine.  weird.  Thanks for all your help and suggestions.  Just to be certain, I also added the vga=794 to the kernal line of the ubuntu boot in grub.

---

### Post by erginemr on 2008-02-18
> **filligree said:**
> Well, I fixed it, although I'm not sure I understand how.  In Ubuntu, through the System menu, I set the screen resolution to 600x480 or whatever the smallest is, which then gave me "input out of range".  I hard restarted, and since then, it's been fine.  weird.  Thanks for all your help and suggestions.  Just to be certain, I also added the vga=794 to the kernal line of the ubuntu boot in grub.

No problem. But make no mistake: Setting screen resolution from System menu and reconfiguring xorg.conf (or xserver-xorg) will only change the desktop resolution at and after the login window. It has nothing to do with the splash screen, which is taken care of by setting the usplash.conf file to a lower resolution. The change is then recorded to your system with:
```
sudo dpkg-reconfigure -phigh usplash
```

Anyway, if you have solved your problem somehow, the rule of thumb "if it ain't broken, don't fix it" applies again. Before closing this case, please check that your desktop resolution is OK, too.

**To close a thread** -> Select "mark this thread as solved" from the thread tools menu.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

**To thank someone** -> Click on the blue ribbon/badge on the bottom right part of the post(s), whose author(s), you believe, has helped you fix your problem.

---

### Post by timbounceback on 2008-02-18
i've had exactly this problem on a computer at school before - unfortunately i can't recall how i solved it :-(.

---

### Post by theonhighgod on 2008-02-19
> **Tupy said:**
> I had a blank screen after i selected ubuntu from grub, to have a splash screen (ubuntu logo with load bar) i had to do the folowing:

edit /etc/usplash.conf and set resolution to a correct one for the screen. if you type
```
sudo gedit /etc/usplash.conf
```
 you can edit the file and save it. Mine looks like this:

```
# Usplash configuration file
xres=1024
yres=768
```

then you have to type in console
```
sudo update-usplash-theme usplash-theme-ubuntu
```

Hope it works!

this worked on my acer aspire 5050 except i changed the usplash config file to read:

```
# Usplash configuration file
xres=1024
yres=800
```

to find the perfect resolution i looked up my current resolution by going settings->peripherals->monitor and display in the kmenu, not used gnome in a while so cant remember how, im sure its easy tho

thanks for the help

---

### Post by penjoseph on 2008-02-20
I used these settings for # Usplash configuration file
xres=800
yres=600

- it worked only for shutdown. The following command enables for startup


sudo update-initramfs -u

---

### Post by theonhighgod on 2008-02-22
i found i had to run

```
sudo dpkg-reconfigure usplash
```

after i changed the /etc/usplash.conf file, im not sure which is the best command but just incase someone had a problem with the other command,

---

### Post by SunnyRabbiera on 2008-02-22
Yeh had this issue myself, its something up with the way gutsy takes monitors and certain graphics cards.

---

