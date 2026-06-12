---
title: "GRUB / GParted question"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Miakehl on 2007-06-30
I recently decided to delete my windows partition to further better society and used Gparted on the liveCD to do it.so Now I have a two part question.

My firstquestion is: Is there some way to resize my main linux partition to use the space freed by removing the windows partition? I can't seem to do it.

Second part of my question is: Is there any way to configure Grub to boot directly into Ubuntu without showing the menu to choose which to boot to? I removed the windows partitions from the list but it still tries to make me choose one...

Thanks in advance..

~Mia

---

### Post by forestpixie on 2007-06-30
When you say it tries to make you choose - what does it try to make you choose? Windows or other kernels? 

AS far as the partition problem goes I'm not sure that will work assuming that the windows is first on the drive.

---

### Post by Tea4all on 2007-06-30
For part,1. usually no.  If your windows came first,then no. If not ya!  Otherwise, you have to copy your linux partition to another hard drive, delete your linux partition on your original drive, copy the partition back to your    
original as a bigger partition, and reinstall grub using the live cd.  Your second problem can be solved by reinstalling grub to your MBR.  Here is a link telling you how to do this. [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by forestpixie on 2007-06-30
I'm not sure OP needs to reinstall grub - if I've read correctly - he/she doesn't want to see grub menu and still has windows as an option, or it's giving the kernel and recovery options (which is a good thing!) 

If that's the case - editing grub timeout would be easier.

I think grub needs to be updated if you change it 

sudo update-grub

---

### Post by logos34 on 2007-06-30
> If that's the case - editing grub timeout would be easier.

yeah, lower your timeout to 3,2,1 or even 0 if you want, then all you'll see is 'grub loading....' flash by before it boots default kernel

and uncomment 

**hiddenmenu**

just for good measure.

Fast, invisible boot into ubuntu.  To halt the boot and choose recovery or another kernel, hit Esc key.

Why not just format the space as a separate ext3 /home partition, transfer all your personal data over there, and leave root solely for system files and apps?

---

### Post by forestpixie on 2007-06-30
Yea I nearly did that myself - just changed my timeout to 1 sec - not quite as quick as I used to be ! :D

---

### Post by coolen on 2007-06-30
Agreeing with above comment: use the free space for home. You never know what might happen to Ubuntu in the future, and you don't want to lose all your personal data (or have to suffer the anguish of DVD backups).
Nothing saying / has to come before /home.
Then, simply edit your menu.lst. Remove the references to Windows, change the default it necessary, enable hidden menu mode, and decrease the timeout. I like three seconds, personally.

---

### Post by Miakehl on 2007-06-30
Good Idea, I think Thats what i'll do I REALLY dont want to delete everything and start over because I just converted the Windows I had into a Virtual Machine so i dont have to restart all the time... If it annoys me too much I can copy that vmware file and reinstall, I've gotten good that that. =\

---

