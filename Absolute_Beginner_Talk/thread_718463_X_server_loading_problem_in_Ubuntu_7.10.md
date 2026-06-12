---
title: "X server loading problem in Ubuntu 7.10"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by arindom on 2008-03-08
I have Ubuntu 7.10 in sdb1 and I had Suse sda1. Today I reinstalled Suse on sda1. 

Since the resinstall I can't seem to get the X server starting properly. When ubuntu is starting the X server is shown, where the progress bar proceeds, then the progress bar does not move and after some time I can only see a blank screen with the cursor blinking at the top left. 

Then if I press Ctrl + Alt + del, the X server comes up again and then I get the login prompt. After logging in everything works normally except that I can't find the Suse disk again.

I tried to run the repair Ubuntu option from the grub menu. There I find a problem with e2fck (I don't understand what's e2fck, I am just trying to give as much info as possible). What I could gather from the output, it seems some superblock details have changed for sda1 (Suse). Going by the details I feel, it is related to the reinstallation of SUSE. 

Please help.

---

### Post by mikeyphi on 2008-03-08
Possibly what's happened is that originally you installed Suse and then, later, installed Ubuntu. Ubuntu wrote the grub on sda1 - so when you reinstalled Suse it overwrote the grub on sda1 and now you have problems booting into Ubuntu.
If that is the source of the problem - updating grub, probably using a LiveCD, should fix it.

---

### Post by arindom on 2008-03-08
Thanks mikeyphi, You are absolutely correct. That is exactly what I did. 

Can you please guide me on how to update the grub by using the Ubuntu Live CD? Actually I did tried that but strangely everything freezed and the display only show some horizontal colored lines.

I hope I have explained properly.

---

### Post by jan quark on 2008-03-08
pehaaps this will help:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub)

---

### Post by arindom on 2008-03-08
I have reinstalled the grub and now just like previous the grub is correctly loading. It has overwritten the Suse written grub.

But the problem remains same. Still I have to press Ctrl + Alt + Del during X loading process to reach the graphical login prompt. After that rest of the things are correctly loading.

I again ran the restore Ubuntu option from grub. I have noted the following error reported on screen. As I cannot take any screenshot so please ignore if I make any mistake in reporting.

The error goes like this : (Note /dev/sda1 is the one where Suse is loaded).

fsck .ext3 : Bad magic number in Super-block while trying to open /dev/sda1. 
The Super-block couldn't read or doesn't describe a correct ext2 filesystem fsck.

Then ....

fsck died with ext status 8.

File system check failed.

.....

Can't find ext3fs on /dev/sda1.


Is this the reason of the problem? 

BTW I can't find the Suse drive from Ubuntu.

---

### Post by arindom on 2008-03-08
Any advise in this regard will be a great help for me.

---

### Post by arindom on 2008-03-09
It's solved now. 

The problem was with fstab entries. I had to find out the devices and change fstab.

Now it works just perfectly.

---

