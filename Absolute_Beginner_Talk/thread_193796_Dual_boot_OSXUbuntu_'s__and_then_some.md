---
title: "Dual boot OSX/Ubuntu ?'s  and then some"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by sleestak on 2006-06-10
I am fairly new to Linux and want to convert my Blue and White G3 to a server/test box. (I know G4/G5's are only listed but have seen many successful listings online using G3's and Ubuntu was my distro of choice after doing my research)

so here are my questions:
 [LIST=1]
[*]I want to set this up as dual boot (OSX and Ubuntu)... which OS should I install first?
[*]When partitioning, what would be the ideal format?
[/LIST]

Another thing I am debating is desktop vs. server.  I would like to play with this as if it were a desktop, but also want to serve music to the rest of the house and do some php/mySQL testing on it.  Suggestions on which to use?

---

### Post by linear on 2006-06-10
Start with OSX, then install Ubuntu. Don't worry about format, let the installer take care of it.

First read these:

[https://wiki.ubuntu.com/Installation/PowerPC]("https://wiki.ubuntu.com/Installation/PowerPC")
[http://www.askdavetaylor.com/how_do_..._mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")

This worked for me:

0. Read up in the PPC forums on any model specific quirks (the older Breezy PPC forum has a lot of good material).
1. Back up OS X partition, if you want to save it. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition disk. Make two partitions, leave first as free space and second for OS X. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively.
3. Restore or re-install OS X on its partition, if you used Disk Utility.
4. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.

---

### Post by sleestak on 2006-06-10
wow, thanks! very thorough...I appreciate all the links and info :cool:

---

### Post by sleestak on 2006-06-18
well, I read up and got the install process going....which by now I can do with my eyes closed because I have gone through it so many times...here is my issue:

Partiion drive - Install OS X - Install Ubuntu on Free Space

Install goes great without a glitch until it goes to reboot, then I get the flashing folder icon for a minute, then asks me what to boot...I press "L" and it boots into OS X ?!!

I tried numerous installs and even tried 5.1, but still get the same issue. I am not sure what I am missing here. Its obvious that Yaboot see's both OS's, how come I cannot get it to boot ubuntu?

---

### Post by linear on 2006-06-19
If possible, post the contents of yaboot.conf. Someone may be able to spot a problem.

---

### Post by sleestak on 2006-06-20
k...but is it normal for me to get a grey screen with the flashing folder icon before the mac goes into that balck yaboot screen?

---

### Post by linear on 2006-06-20
[quote=sleestak]k...but is it normal for me to get a grey screen with the flashing folder icon before the mac goes into that balck yaboot screen?[/quote]
 
No, I wouldn't call that normal...

---

### Post by sleestak on 2006-06-20
ok, well thats what happens...even if I use just the ubuntu disk to completely wipe the HD and do its own thing. grey screen, flashing icon - into a black screen where I press "l" for linux and it starts loading the second bootstrap and just dies. Sits there with a flashing icon again on a black screen.

While I am a complete n0ob at installing linux, I am not a complete and utter 'tard. I work in web design/development (even do OOP), but this is getting to the point of "smoke and mirrors".  I have easily spent over 36 hours trying to just see linux on my screen.

---

### Post by linear on 2006-06-20
Best bet might be to repost in the Mac/PPC forum: [http://www.ubuntuforums.org/forumdisplay.php?f=133](http://www.ubuntuforums.org/forumdisplay.php?f=133)
More Mac users hang out there; someone with a B&W G3 has doubtless been down this road before...

Oh, never asked: are you trying to install Dapper or Breezy? (Some people have reported problems when trying to use the Dapper desktop CD, and recommend the alternate CD or Breezy followed by a dist-upgrade.)

---

### Post by sleestak on 2006-06-21
I tried both actually, with the same results.  But I think I found a good answer...that being scsi related.  Found a thread where someone had the same unit as mine, same issues(pics and all):[http://www.ubuntuforums.org/showthread.php?t=102440&highlight=load+bootstrap](http://www.ubuntuforums.org/showthread.php?t=102440&highlight=load+bootstrap)

Swapped SCSI for IDE and worked fine. He never got scsi to work.

---

### Post by sleestak on 2006-06-27
finally got my hands on a ATA HD and pulled the scsi and card. installed osx, installed ubuntu. moving right along now.

looks like I will be CraigsList'ing SCSI stuff, lol.

---

