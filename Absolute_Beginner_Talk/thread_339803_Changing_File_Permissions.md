---
title: "Changing File Permissions"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Catsworth on 2007-01-16
Hi Guys,

Just a quickie.

I still, to my shame, have a Windoze partition on my laptop.  When I boot Ubuntu it automatically mounts the Windows partition and makes it available on the desktop and within 'Places'.  This is fine for me because I still need access to some of the stuff on that partition.....however.....

How do I stop this drive from appearing when my GF logs in?  I'm guessing that I either need to change the permissions on the drive (greyed out in the file explorer, is there a graphical way of doing this or do I need to use the terminal?) or that I need to set it to unmount if it's her that logs in, but I'm not really sure if I'm right or even how to do those things.

Any advice would be greatly appreciated.

Thanks.

---

### Post by bodhi.zazen on 2007-01-16
> **Catsworth said:**
> Hi Guys,

Just a quickie.

I still, to my shame, have a Windoze partition on my laptop.  When I boot Ubuntu it automatically mounts the Windows partition and makes it available on the desktop and within 'Places'.  This is fine for me because I still need access to some of the stuff on that partition.....however.....

How do I stop this drive from appearing when my GF logs in?  I'm guessing that I either need to change the permissions on the drive (greyed out in the file explorer, is there a graphical way of doing this or do I need to use the terminal?) or that I need to set it to unmount if it's her that logs in, but I'm not really sure if I'm right or even how to do those things.

Any advice would be greatly appreciated.

Thanks.

Not sure, but try editing /etc/fstab

On the line for your windows partition change defaults to 

uid=xxx,gid=yyy,umask=007

where xxx and yyy are your user name

---

### Post by ljpm on 2007-01-16
> **Catsworth said:**
> Hi Guys,

Just a quickie.

I still, to my shame, have a Windoze partition on my laptop.  When I boot Ubuntu it automatically mounts the Windows partition and makes it available on the desktop and within 'Places'.  This is fine for me because I still need access to some of the stuff on that partition.....however.....

How do I stop this drive from appearing when my GF logs in?  I'm guessing that I either need to change the permissions on the drive (greyed out in the file explorer, is there a graphical way of doing this or do I need to use the terminal?) or that I need to set it to unmount if it's her that logs in, but I'm not really sure if I'm right or even how to do those things.

Any advice would be greatly appreciated.

Thanks.

You can do that when you set up the user account. I am not at my Linux computer at the moment but I think you unselect access to external drives. I will check when I get home and update. 

This will disable access to the drive but the icon will still appear on the desktop. 

If any one has a better solution, like complete removal of icon, with or without disabling of all external drives, this would be appreciated. My 5 year old daughter uses my computer and she keeps amazing me with the things she gets into or does on the computer. I would prefer not to have the icons on the screen tempting her. :D

---

### Post by Catsworth on 2007-01-16
> **bodhi.zazen said:**
> Not sure, but try editing /etc/fstab

On the line for your windows partition change defaults to 

uid=xxx,gid=yyy,umask=007

where xxx and yyy are your user name

Would that restrict that volume so that only I could view it (I'm assuming that's what putting my user name in there does).

---

### Post by bodhi.zazen on 2007-01-16
> **Catsworth said:**
> Would that restrict that volume so that only I could view it (I'm assuming that's what putting my user name in there does).

Yes.

The you can remove the icon as directed by ljpm (under system settings)

---

