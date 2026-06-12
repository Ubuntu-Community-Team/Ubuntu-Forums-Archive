---
title: "Please help"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by SoulReaper on 2006-01-04
I am a current XP user


I really want to start playing with Linux, and Ubuntu was reccomended to me.  I have a Pentium III with 128mb of ram, and 250gb hard drive that I am using as my linux machine.  I get the installation going fine, but the Key installation phase always says it missed a step.  I have tried over and over, it is the step just after you partion the harddrive.  I am going to try it again, and then I will post my erroro message.  Is it possibly something wrong with my download/cd I burned?

I really just want to start using Linux.

---

### Post by bluefrog on 2006-01-04
check the md5sum of the iso. to check the cd type expert at boot and shortly u should be able to select verify cd from the menu.

james

---

### Post by SoulReaper on 2006-01-04
Ok I will try that right now.  Thanks.

---

### Post by mustang on 2006-01-04
To ensure that your burned CD is not the problem, verify the integrity of the disc by using the checksum option. I haven't installed Ubuntu for months so I don't precisely remember where the option is presented but I believe its towards the beginning before the installation phase.

edit: doh! bluefrog beat me to it

---

### Post by SoulReaper on 2006-01-04
Ok I did that ( I think lol) and it says CD-Rom Detected 5.10 Breezy Badger.  Installation will now continue.


edit:  Ok now it's checking the inegrity.

---

### Post by SoulReaper on 2006-01-04
The /pool/main/l/language-pack-af/languagepack-af_200510111_all.debfile failed MD5 Checksum.  File or CD may be corrupted

Dang.  I wonder if this is a problem with my burner or my d/l though

---

### Post by mustang on 2006-01-04
You can check if it's a problem with your download by running a MD5 checksum test on the .iso file.

---

### Post by SoulReaper on 2006-01-04
I think it's working.  We will see.  It is trying to install the base file system.  ( Iburned a new CD and it passed the check.)

I hope this works!

---

### Post by GreyFox503 on 2006-01-04
I would definitely reburn the disc since it failed that check. To see if your download is intact, you can verify the .iso image file you downloaded. Here are the MD5 sums:

[http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/MD5SUMS]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/MD5SUMS")

If you are running a linux computer, just use the md5sum program to check your iso. If you are running Windows, it does not come with that utility, so you can download a free one to check it for you.

Like this:

[http://www.etree.org/md5com.html]("http://www.etree.org/md5com.html")

If the MD5sum your program reports is the same as the one on the Ubuntu website, then your download is OK. If the sums are different, then you need to redownload the image file.

Either way, when you burn it again, do it at a low speed like 4x to help prevent errors.

EDIT:  Looks like you fixed it.

---

### Post by SoulReaper on 2006-01-04
Thanks for the help guys.  It finished installing the base system which is where it was failing previously.  I may have ubuntu up and runing shortly.

---

