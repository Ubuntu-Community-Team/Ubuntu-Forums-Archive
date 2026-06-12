---
title: "Problems with Feisty Fawn/G4 Mac Mini"
date: 2007-05-07
forum: Apple PPC Users
---

### Post by mahesh.nanjunda on 2007-05-07
Hi all,

I just installed the Power PC version of Feisty Fawn on my G4 Mac Mini.
I have a few problems, would be greatful if anyone could help me:

1) I tried to install swfdec for Flash, but it gives some error, is there any website which has an easy install process? (I'm new to Linux). Is gnash easier to install?
2) When I plugin my USB external hard disk it mounts, however when I tried to eject it it fails, saying unable to eject disk (I have a LaCie USB 80GB external hard disk)
3) I am unable to enter 'Suspend' mode. (In Mac OS X, I always select 'sleep')

Any help would be appreciated.

Thanks and regards,
Mahesh.

---

### Post by stmiller on 2007-05-07
Hey sleep (suspend) should be possible, if this machine uses an ATI video chip. What happens when you try to suspend?
If there is a USB hard drive plugged in, that may be preventing the computer from going to sleep.

Check out the PPCFAQs at the link below for flash tips.

For the mounting problem, see if this is installed (if you are using gnome)

sudo apt-get install gnome-mount

or for Xfce install:

xfce4-mount-plugin

---

### Post by mahesh.nanjunda on 2007-05-08
Hello, thanks for your reply.

I typed sudo apt-get install gnome-mount in Terminal and it says:
'gnome-mount is already the latest version'

When I typed xfce4-mount-plugin it says:
command not found

When I click on the Suspend icon, it actually locks the screen.
And when I re-enter my password, this message appears at the bottom-right:
'Your computer failed to suspend. Check the help file for common problems.'

Any ideas?

Thanks,
Mahesh.

---

### Post by Alterax on 2007-05-08
sounds as if the XFCE plugin is not installed.

Try this:

sudo apt-get install xfce4-mount-plugin

That should help with the mounting/unmounting issue.

Alterax

---

### Post by Auria on 2007-05-08
> **Alterax said:**
> sounds as if the XFCE plugin is not installed.

Try this:

sudo apt-get install xfce4-mount-plugin

That should help with the mounting/unmounting issue.

Alterax

But, he doesnt seem to use XUbuntu... installing XFCE stuff may not be the solution

---

