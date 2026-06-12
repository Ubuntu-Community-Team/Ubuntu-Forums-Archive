---
title: "[SOLVED] Can't instal ubuntu server edition 7.10"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by jamesrfla on 2007-10-27
I just downloaded Ubuntu Server edition 7.10. I put it in my computer to install  it. I got to Installing the base system then it came up with a error. It said Install the base system Debootstrap warning file corrupt. I hit continue. It came up next with Warning Couldn't download package libncurses5.It came up many times saying couldn't download a different package name. I downloaded Ubuntu Server edition 7.04 and I tried installing it and it came up with the same problem. I did check CD for defects on both editions of server edition and said [!] Configuring cdrom-checker-menu Integrity test failed (a long file name) file failed the MD5 checksum verification. Your CD-ROM of this file my have been corrupted. Ubuntu desktop edition works on the same computer. Why can't I install Ubuntu Server edition?:confused:

---

### Post by taurus on 2007-10-27
If the test failed, no need to go any further because it will not install.  Make sure you do the checksum of the .iso image before you burn it to a CD.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by jamesrfla on 2007-10-27
What is a checksum?

---

### Post by lpevey on 2007-10-27
In short, it is a way to check the integrity of a download.

Try re-burning the disc to see if you get the same errors.  You might want to check out this page for some tips:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by lavinog on 2007-10-27
sometimes a dirty cd can be the cause, or an incomplete download, or just a bad download.

It is a good practice to check md5 checksums before using a file (it will save you the time and the discs)

one way to check is use the command md5sum filename
it will give you a bunch of numbers and letters that you can check with the associated md5 file on the site you downloaded from.

also there is a md5sum.txt file on the cd where you can do
md5sum -c md5sum.txt
and it will check all the files on the cd and tell you if you will have problems.

I had a problem downloading an ubuntu desktop cd recently because of all of the network traffic recently and it timed out on the last 20 megs...
I didn't notice the time out but the md5 sum told me of the problem.

---

### Post by jamesrfla on 2007-10-27
I am not sure what I did. I already had a ISO recorder. I removed so programs rebooted my computer and did something and now Ubuntu Server is installing. My other question is It asked me what to install like mail server. I checked all of them except two. I don't know what they do but I am going to try to find out.
Thanks for the help. What is a LAMP Server?

---

