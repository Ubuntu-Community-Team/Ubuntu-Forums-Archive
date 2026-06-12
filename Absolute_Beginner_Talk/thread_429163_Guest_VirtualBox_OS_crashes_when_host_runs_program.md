---
title: "Guest VirtualBox OS crashes when host runs programs"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by pmueller on 2007-04-30
Hi,

My VirtualBox used to work very well. I have 512 RAM and I tried running PCLinux, Mepis, Puppy, and Windows XP with success. For all of these opperating systems, I assign half of my 512 RAM and this used to work. 

My troubles began when I started running out of hard disk room for both host Ubuntu and Windows XP running under VirtualBox at the same time. So, I moved Ubuntu to a much larger partition. However something wrong happened here and my virtualbox OS's started crashing when I tried to run other programs in Ubuntu. Clicking on as little as a pdf file would cause my virtualbox OS and Ubuntu to freeze up completely to the point that I would have to reboot.

In the meantime, I have upgraded from Edgy to Feisty and installed the new VirtualBox_1.3.8_Ubuntu_feisty_i386.deb. I deleted my old images  and guest additions made under Edgy. Trying to run Dynebolic with my new setup on Feisty the same things happens as before. I can run the guest OS as long as I run almost nothing else in Ubuntu. When I click on another program in Ubuntu my system freezes up and needs restarting.

Does anyone know what I should do?

Paul in New Hampshire

---

### Post by lbyrd33 on 2007-05-01
Just something to try: Give your guest os about 190 -200 Mb of ram. Whenever I used win4lin or virtualbox they always suggest slightly less than half of your total capacity of ram.

---

### Post by pmueller on 2007-05-01
Hello Again,
I reduced the RAM for Dynebolic guest  OS down to 203 RAM and I tried to start the program while I already had Firefox  and Stream Tuner open in Ubuntu. I wanted to get back quickly with an answer.

Just like before, VirtualBox and Ubuntu froze up. After waiting several minutes, I rebooted. At the start of the Ubuntu after log-in, I got a fatal error message:

"Virtual Box – Critical Error

Failed to initialize COM or find the VirtualBox COM server. Most likely, the VirtualBox server is not running or failed to start.

The application will now terminate.

Callee RC:                                                0x80004005"


Paul

---

### Post by lbyrd33 on 2007-05-01
Im sorry, I cant think of what could be the problem. Have you tried looking at the virtualbox forum on their website to see if anyone else has had the same problem.

---

### Post by kyphi on 2007-05-01
Why don't you access the host-based files from your guest system?  Have you created a shared folder yet?  It does not make sense to make demands on two operating systems at once.

---

### Post by pmueller on 2007-05-07
Hi

With work at the office and the desire to try again I decided to remove VirtualBox and try again. I removed it through Synaptic. I noticed though that I still had virtualbox listed as two different users: vbox111 and vboxusers. When I tried to remove both of these as users I got a warning: "Are you sure you want to delete group "vboxusers"? This may leave files with invalid group ID in the filesystem." So, I was scared off by the warning, which also appeared when I tried to remove vbox111 and I did not remove the vbox users.

I noticed that after removing Virtualbox I still had residual files under /etc and /home/myaccountname. I deleted the file under /home/myaccountname, but I had no permission to delete the vbox folder under /etc.

I do not know what I am doing anyway, but I figure a cleaner install is better than none.

So, I reinstalled VirtualBox with the official feisty version, the Deb package found on the website of VirtualBox. I have deja vu all over again and I have the same problems, but my problems are worse.

I can not manage to operate the guest operating system at all after after a period of time, even when I do not run any other programs in the host system. In Ubuntu I unchecked enable networking on the task bar and this seems to let me run a guest system longer without a crash, but eventually the guest will crash and sometimes also cause the host OS to crash.

You might have other ideas, but I am inclined to wipe out my feisty partition and start over again. I have the alternate install of Xubuntu, alternate Ubuntu, and the regular Kubuntu install.  I am more familiar with Ubuntu, than Kubuntu and my plan would be to install Kubuntu first and Ubuntu later and switch to the Ubuntu graphical manager during that install. Perhaps it would be best to start with a fresh Ubuntu install, but I only have the alternate disk and a slow modem connection.

I am doing this because I started fresh with Dapper and upgraded with an alternate install disk to Edgy and VirtualBox worked beautifully with edgy until I moved everything to a different partition and this seemed to start my problems. Could there have been file corruption in the move? Upgrading through alternate Ubuntu install to Feisty did not solve my problems either. Using VirtualBox under the Kubuntu and Xubuntu interface with low RAM distributions like Puppy and SAM makes little difference.

Do you think I should try something new or just reinstall a fresh version of (k) (x) ubuntu.

Any opinion is welcome!

Paul

---

### Post by pmueller on 2007-05-21
Hi,

I decided to wipe out my ubuntu dapper to edgy to feisty upgrade and start clean with a fresh Kubuntu Feisty install. I added Gmome back with an alternative Unbuntu install disk. After numerous updates over a slow modem, I installed VirtualBox again. 

It is now working for me, like it did before.   I am running Windows XP and SAM linux, which is a hoot.

Sorry, it took me this long to report back.  I have run memtest today and it looks like I have some hard disk drive issues that I must figure out. 

Thank you for all of your help.

Paul

---

