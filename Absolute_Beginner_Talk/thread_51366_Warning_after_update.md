---
title: "Warning after update"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by Dutch on 2005-07-23
After updating Ubuntu 5.04 I get this warning.
I don't know what it means, do I have to take action ?

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

---

### Post by Xian on 2005-07-23
The nerim.net repos are not affliated with Ubuntu.
Any apt errors that you receive using them can not be resolved locally.

---

### Post by poofyhairguy on 2005-07-23
Please. Please. Please. Please take action.

Follow these instructions:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Even if you already did at one time....do it again now. Apt-get is telling me you are using a server that might cause some nasty breakage. Thanks for bringing this up.

---

### Post by Xian on 2005-07-23
Where would an absolute beginner even get this repo? I generally tend to believe if someone is using outside repos that they are fully aware of the limitations and risks this implies, but this certainly wouldn't be the case with a brand new Linux user. Yet this also isn't the first time I've seen such a question posed in this forum section. Is someone going around advocating this to be included in the source list?

Maybe I just give too much rope.... :)

---

### Post by aysiu on 2005-07-23
Maybe new users take it from Mepis?

---

### Post by poofyhairguy on 2005-07-24
[QUOTE=Xian]Where would an absolute beginner even get this repo? I generally tend to believe if someone is using outside repos that they are fully aware of the limitations and risks this implies, but this certainly wouldn't be the case with a brand new Linux user. Yet this also isn't the first time I've seen such a question posed in this forum section. Is someone going around advocating this to be included in the source list?
[/QUOTE]

A: Maybe BassMan's add on CD? It uses that repo.

B: An old version of the Ubuntu Guide.

C: A Debian friend

D: Satan himself

---

### Post by Dutch on 2005-07-24
[QUOTE=poofyhairguy]Please. Please. Please. Please take action.

Follow these instructions:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Even if you already did at one time....do it again now. Apt-get is telling me you are using a server that might cause some nasty breakage. Thanks for bringing this up.[/QUOTE]

Could some body explain in simple English what is so rear ?
In the beginning of Linux ( some weeks ago) I got the tip to download this file(has this something to do with it all ?)
==========================================
# Sources list by Tim Raats aka Vectrox ([www.ubuntu-linux.nl](www.ubuntu-linux.nl))

deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main
=============================================

W'll I'm bussy now with your link poofyhairguy, so thanks for your tip, but I would like to know wjat was hapening.

Thanks,

Dutch.

---

### Post by Dutch on 2005-07-24
oke, with following the link from poofyhairguy the warning is gone with the 686 vrsion.
Are there now files on my PC after using the wrong download site that I need to delete ?
But with the old 386 version I get the same problem with updating, even when I changed the file twice, it didn't change.
WAARSCHUWING: De volgende pakketten kunnen niet geauthenticeerd worden:
  firestarter
The next program could not be autenthicated : firestarter.
and
How to turn on Num Lock on GNOME startup?
(gedit:8416): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
==========================================
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH=/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH

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
  unset IFS
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
=========================================


Thanks,Dutch.

---

### Post by poofyhairguy on 2005-07-25
[QUOTE=Dutch]oke, with following the link from poofyhairguy the warning is gone with the 686 vrsion.
Are there now files on my PC after using the wrong download site that I need to delete ?
But with the old 386 version I get the same problem with updating, even when I changed the file twice, it didn't change.[/QUOTE]

hmm..you need the 

> sudo apt-get update

command

As far as bad files...you are safe, its just good we got that out of there for now.

---

