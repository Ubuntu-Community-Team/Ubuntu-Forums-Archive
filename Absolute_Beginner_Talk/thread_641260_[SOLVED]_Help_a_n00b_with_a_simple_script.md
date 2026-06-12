---
title: "[SOLVED] Help a n00b with a simple script"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by FokkerCharlie on 2007-12-15
Hi  all

I hope someone can help me with getting this to work...

I have made a little script for myself, to re-start my wireless network.  It needs doing occasionally, as WLAN support in Ubuntu isn't all that it might be.  I also need to give my gf an easy way to kick-start the internet, as she isn't convinced (yet) by Linux, and doesn't like fiddling around.

Anyway, here's the script, which is on my desktop:

```
#!/bin/bash
echo "Restarting wireless network"
sudo /etc/init.d/networking restart
```

At the moment, if I double-click the icon, I see a dialog asking whether I'd like to run the file or view it.  I always want to run it, so I have been into Nautilus, Edit>Prefs>Behaviour>Run executable text files when they are opened.

Unfortunately, after selecting this, when I double-click the icon, nothing happens.  The script does not run, there's no dialog, nothing.  Can anyone point me in the right direction here?

When this is (hopefully) solved, the script will ask me for my password.  I'd like to circumvent this, so I went to the terminal:

```
export EDITOR=gedit && sudo visudo
```

And added the last line to sudoers:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
ca ALL=NOPASSWD: /home/ca/Desktop/wireless-restart.sh
```

to no good effect!

So if you can help with either problem, please do let me know!

Thanks in advance
Charlie

---

### Post by cmnorton on 2007-12-15
Are the script's protections marked executable at least for user?

chmod 755

---

### Post by Nano Geek on 2007-12-15
Use **gksudo** instead of **sudo**. gksudo will pop-up a box asking for the password instead of doing it in the terminal which you can't see.

---

### Post by FokkerCharlie on 2007-12-15
Cool!

That seems to work now... to be honest, it could be that it was working all along, I just couldn't see it.

Thanks!

---

### Post by Nano Geek on 2007-12-15
I'm glad you fixed it. :)

---

