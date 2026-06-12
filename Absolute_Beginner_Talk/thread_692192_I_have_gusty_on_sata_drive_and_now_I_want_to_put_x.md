---
title: "I have gusty on sata drive and now I want to put xp on another drive"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by darkworld on 2008-02-09
Ok ive never done this this way round. My old pc had xp and I installed another drive and loaded feisty. Used grub to dual boot fine.

Well ive just built a new pc amd 64bit and had Gusty up and running a few weeks fine. Other members of my family asked me to install an xp drive so they can run certian applications. Ok installed a second sata drive. Next I went fdisk /dev/sdb and created NTFS partition on new drive.

Rebooted box and boot xp disk. It recognized the drive I had added but didnt recognize its type ( I used 7 from Ubuntu fdisk).  Ok I deleted the partition in the windows installer and recreated a raw partion but no matter what I did it said the partion was not a windows type.

Ok so this is opposite way round to how I would normally sort things but I dont want  to blat gusty then install xp then reinstall gusty. Is this because I didnt toggle bootable flag?

The only other  thing im also concerned about is that if I toggle the new drive with bootable flag, which maybe the problem, what will my box do with 2 MBR,s. Sorry im just not sure on all this and dont really want to balls up.

---

### Post by darkworld on 2008-02-09
ive been googling around for an answer and I cant find one. Am I right in thinking I need to blat gusty and start at the beginning by put xp on a drive then add gusty. I cant believe im going to have to do this!

---

### Post by darkworld on 2008-02-09
ok it seems windows wont attempt to install on new drive because it doesnt recognize the  the MBR on the linux disk. Obvious really. So my question is can I unplug the sata with ubuntu on then install xp.

Following that, somehow boot into ubuntu then get grub into xp....some how! aaaaargh!

Looks like its scrub gusty then do xp then do gusty. ????

---

### Post by criskat777 on 2008-02-09
Disconnect Sata drive and install Windows on the other disk and when your done reconnect the sata drive make sure it's the main boot drive (sata drive ) then add the new drive to grub it simpler then it sounds. Just visit the grub Man Page or there web page. i have done this many times and it's not that complicated.  If you fell more comfortable with a GUI for grub check out QGRUBEditor it's a very good app for grub editing and if you fell like adding a nice background (Splash screen) to Grub i find that the app Splash screen dose a better job then  QGRUBEditor. Just write qgrubeditor and splash screen on synaptic and i think there both there if not just google them.

---

### Post by darkworld on 2008-02-10
criskatt thanks for that! 

Grub is fine ive got the hang of that. 

You say make sure the ubuntu drive is the main boot drive. I didnt know that sata had a main boot drive? obviously IDE used slave and master because it shared the ribbon but sata has individual leads??? no slave master and I wasnt aware there was a main drive????

 I guess I need to check my new BIOS out???? SATA is new to me.

---

### Post by criskat777 on 2008-02-12
Yes you are write about sata not having master or slave but when you go to your bios there is a place on the boot menu that lets you chose what HD to boot from. just chose the HD you have Ubuntu on.

---

### Post by Joeb454 on 2008-02-12
Just to clear things up...it's **Gutsy**...not Gusty ;)

And yes check the bios to make sure the Sata drive with Ubuntu is the primary, and then the other drive should be the secondary boot device.

---

