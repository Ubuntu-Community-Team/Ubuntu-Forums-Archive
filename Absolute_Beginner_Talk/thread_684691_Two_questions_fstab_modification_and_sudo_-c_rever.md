---
title: "Two questions: fstab modification and sudo -c reversal"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by jdix123 on 2008-02-01
Couple of questions:

First, I have two hard disks in my machine.  I initially installed Ubuntu 6.06 onto the first hard drive (I had data I wanted to keep on the second drive).  I them moved all the data to /hda1 and formatted /hda2 into ext3.  I want to put two things on the second hard drive:  the /tmp directory and a shared folder to use with windows/samba networks.  And I want to modify the whole drive to noexec for security reasons.

I'm not sure how to do all that.

Secondly I read that activating root like this

```

sudo -c

```

makes it a lot easier to gain access than if I'd left it alone and just did everything with sudo.  If this is true, can I change it back?

---

### Post by bodhi.zazen on 2008-02-01
> **jdix123 said:**
> Couple of questions:

First, I have two hard disks in my machine.  I initially installed Ubuntu 6.06 onto the first hard drive (I had data I wanted to keep on the second drive).  I them moved all the data to /hda1 and formatted /hda2 into ext3.  I want to put two things on the second hard drive:  the /tmp directory and a shared folder to use with windows/samba networks.  And I want to modify the whole drive to noexec for security reasons.

I'm not sure how to do all that.

You will need to make a partition for /tmp and a second one for share.

Mount them in fstab

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

[http://www.linuxconsultingteam.com/articles/2006/10/14/secure-filesystem-mount-points](http://www.linuxconsultingteam.com/articles/2006/10/14/secure-filesystem-mount-points)

[http://www.funtoo.org/en/articles/linux/partitioning/2/](http://www.funtoo.org/en/articles/linux/partitioning/2/)


> **jdix123 said:**
> Secondly I read that activating root like this

```

sudo -c

```

makes it a lot easier to gain access than if I'd left it alone and just did everything with sudo.  If this is true, can I change it back?

You should use :

sudo <command> for single commands.

sudo -i for a root shell

and 

gksu (kedsu on KDE) for graphical applications.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jdix123 on 2008-02-01
Ok, I know that's what I need to do...I'm asking how.  I rebooted to the live cd to format/partition the second hard drive and used gnome's partition manager.  This did not give me an option to make logical vs primary partitions, or to set mount points.  I know how to do this if I do a clean install from the beginning, but I don't know how to do that without losing the data I need.


I followed the directions at your third link and it appears to be working.  Woohoo!  But I'm still having a bit of a problem.  How do I set a password to make the shared folder accessible over the network?  When I try to view it from an XP machine I get a login window, and it doesn't accept the password for the user on the linux machine.  I remember reading how to do this somewhere but I can't re-find it.


Second, I know that those are options I should use rather than sudo -c, but my question was: did I do something to make my system less secure by using that option, or did it simply go away when I typed exit?  Perhaps I should have been more clear.

Thanks for the prompt response, and the reading.

---

### Post by jdix123 on 2008-02-01
First problem solved...I didn't know ; was a comment out like # in the smb.conf file.  I just changed security  = user to security = share

Still wondering about the second one though.

---

### Post by bodhi.zazen on 2008-02-01
> **jdix123 said:**
> Ok, I know that's what I need to do...I'm asking how.  I rebooted to the live cd to format/partition the second hard drive and used gnome's partition manager.  This did not give me an option to make logical vs primary partitions, or to set mount points.  I know how to do this if I do a clean install from the beginning, but I don't know how to do that without losing the data I need.


I followed the directions at your third link and it appears to be working.  Woohoo!  But I'm still having a bit of a problem.  How do I set a password to make the shared folder accessible over the network?  When I try to view it from an XP machine I get a login window, and it doesn't accept the password for the user on the linux machine.  I remember reading how to do this somewhere but I can't re-find it.


Second, I know that those are options I should use rather than sudo -c, but my question was: did I do something to make my system less secure by using that option, or did it simply go away when I typed exit?  Perhaps I should have been more clear.

Thanks for the prompt response, and the reading.

OK, sounds as if you have the partitioning solved ? If not, re-post here and give an update.

sudo -c does not damage to your system or to sudo, it is gone when you "exit".

If you are having problems with samba, try this link :

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

or start a new thread, so it is more visible.

---

### Post by jdix123 on 2008-02-04
Pretty sure I got it, thanks :)

---

