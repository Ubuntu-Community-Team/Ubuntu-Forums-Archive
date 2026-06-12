---
title: "How to install Ubuntu over Mandrake 10.1"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by jacatone on 2005-09-09
Installing Mandrake was a snap, but when I trying install Ubuntu it has this very confusing text based interface. Is there a site that explains Ubuntu installation in easy to follow terms? Thanks.

---

### Post by X5-655 on 2005-09-09
[QUOTE=jacatone]Installing Mandrake was a snap, but when I trying install Ubuntu it has this very confusing text based interface. Is there a site that explains Ubuntu installation in easy to follow terms? Thanks.[/QUOTE]
that text based installer was MUCH easier for me than the mandrake GUI installer...

---

### Post by xavierh on 2005-09-09
While I would disagree with the previous post (ubuntu installer, specially their disk preparation section still needs work). as long as you take care fo your data you'll be fine. I moved form mandriva 2005 LE to ubuntu yesterday with no los of data (all 120 gigs of it).

if you want to keep your data (home directories) you'll need to choose the "manual partition". This is slightly confusion since you can acutally pformat, mount, etc. without having to re-partitioned the drive.

Once you select that option, you will see the partitions in your drive(s). mine were like this:

/
swap
home

I then told the program to format both the root partition and swap partitions, and mount them as such and then I told it to mount my home partition without deleting anything.

once you do that then proceed to "write" the changes, which will then tell the program to actually format those partitions.

you have to be aware though that your mandrake users will have different id's than the ones you will be creating in ubuntu so don't expect for, lets say john user (in mandriva) to be able to access his original home directory, once you create this user in ubuntu.

what I would do is to create anothe ruser in ubuntu, rename the old user directory, create the "john" user in ubuntu, assing him onwer rights to the old data, and then you can move it to the new home directory.

If you want to start from scratch then tell the installer to delete the exsiting partitions.

All in all it feel snappier and I have everything that I need runing on it: dvd::rip, samba, ippoder, azureus, vmware.

Hope this helps

---

### Post by UbuWu on 2005-09-09
[QUOTE=jacatone]Installing Mandrake was a snap, but when I trying install Ubuntu it has this very confusing text based interface. Is there a site that explains Ubuntu installation in easy to follow terms? Thanks.[/QUOTE]

Take a look at this page:
[http://www.mrbass.org/linux/ubuntu/install/](http://www.mrbass.org/linux/ubuntu/install/)

---

### Post by jyank on 2005-09-09
This is probably the best link I can show anyone who is unsure of anything while installing Ubuntu.

[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

---

