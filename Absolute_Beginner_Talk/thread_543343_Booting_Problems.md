---
title: "\Booting Problems"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Spacedementia87 on 2007-09-05
Right i did a few edits to the xorg.conf and then on restart it wouldn't boot into the GUI so i had to fix the xorg.conf file in the command prompt (i had missed the S off one of the Sections)

Once that was done i booted in and could not log in.  After entering my name and password it told me that I was being immediately logged out and gave this as the details

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:20.Xservers" -h "" -l ":20" "bob"
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 20: [[: not found
Warning: Only changing the first 7 of 11 buttons.
```

Currently logged in as a failsafe to make this post.

---

### Post by sumguy231 on 2007-09-05
I can't think of any reason for your /etc/profile to be broken, but have mine:
```

# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

```
I doubt that will really help though, since it looks like you have far worse problems than that. /etc/profile doesn't seem to do much more than set the prompt.

---

### Post by Spacedementia87 on 2007-09-05
I'll give it a go.

The files I edited were the /etc/X11/xorg.conf w whci i think i got back to how it was

I created a file called ~/.xsession and put a few lines of code in that

I edited /etc/X11/imwheel/inwheelrc which I have now put back to normal.

---

### Post by Spacedementia87 on 2007-09-05
My profile fil is exactly the same as that just with this lin on the bottom:

```
[[ -f "/etc/autopackage/paths-bash" ]] && . "/etc/autopackage/paths-bash"
```

---

