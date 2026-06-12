---
title: "eMac Ubuntu upgrade"
date: 2008-08-05
forum: Apple Hardware Users
---

### Post by djpup on 2008-08-05
Hello,

I'm new to Ubuntu and I think that these boards are extremely helpful.  I have a question about upgrading Ubuntu.  I installed 7.04 on my eMac (1.25, 1GB Ram) can I just use the update manager or should I burn an iso?  I tried to run the update manager last night and it was installing the system then I got an error.  It took forever to get 7.04 back on the eMac, I'm a little gunshy to try it again.  Any suggestions?  Thank you in advance.

---

### Post by typetokill on 2008-08-05
Not sure about that, it should install from the update manager? I am a complete noob with ubuntu but i found this on ubuntu.com

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Not sure if it will help, perhaps burning the image and then trying the update, that way you can just use the disk if it goes wrong...

Brian

PS: You can upgrade with the disk to, instead of reinstalling the whole thing?

Upgrading using the alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1.Download and burn the alternate installation CD.
   2.Insert it into your CD-ROM drive.
   3.A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4.Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

> gksu "sh /cdrom/cdromupgrade"

Or in Kubuntu run the following command using Alt+F2:

> kdesu "sh /cdrom/cdromupgrade"

---

### Post by stream303 on 2008-08-05
My first suggestion is to write down your /etc/X11/xorg.conf file, and also your /etc/yaboot.conf file immediately to some other media, or even paper.

Personally, I think that if you are upgrading to an LTS like 8.04, I would go the wipe-it-clean and start with a fresh iso route.

If it is the earlier 7.10 Gutsy, possibly not much of an issue, but just have the xorg and yaboot.conf files handy if you have to go back in with rescue mode.

---

### Post by djpup on 2008-08-05
The install of 7.10 went to completion.  I restarted the computer and I got the black screen.  I tried all of the things on the boards, but nothing worked.  I reinstalled 7.04 for now.  Is there any other Linux software that works on eMacs, and is still supported?  Thanks for your help, I appreciate it.

---

### Post by stream303 on 2008-08-05
Hmm.  Almost any recent distro is probably going to require you to manually edit your /etc/X11/xorg.conf file after install.

However, I'd be interested to see if Debian 4.0_r4, which just got released, would come up without manual intervention on the eMac.

Might be worth a shot - OswaldKelso and a few others have posted xorg.conf files that work for the eMac, so it shouldn't be too hard if you have to revert to a manual edit.

---

