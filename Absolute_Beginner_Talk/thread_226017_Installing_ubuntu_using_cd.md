---
title: "Installing ubuntu using cd"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by xtgar00 on 2006-07-30
I have a question regarding using the live cd to not nessacarily install ubuntu but to preview it first.  I thought that I had read that it wouldn't matter if you had some other O/S on your hard drive that it would boot from the cd as long as you have your boot priority set up correctly, which I do.  Floppy first and then CD-rom.  After downloading the ISO I used CD Burner XP Pro to create the image and it appeared to have created the CD correctly although I did not run the CheckSum routine to validate.  Would I need to have a formatted HD prior to running the CD?  If I did need to have a formatted HD, how would I format it or re-partition it if I currently have a version of FreeBSD?

Thanks in advance for any insight you all might have!

Tim

---

### Post by Engnome on 2006-07-30
> **xtgar00 said:**
> I have a question regarding using the live cd to not nessacarily install ubuntu but to preview it first.  I thought that I had read that it wouldn't matter if you had some other O/S on your hard drive that it would boot from the cd as long as you have your boot priority set up correctly, which I do.  Floppy first and then CD-rom.  After downloading the ISO I used CD Burner XP Pro to create the image and it appeared to have created the CD correctly although I did not run the CheckSum routine to validate.  Would I need to have a formatted HD prior to running the CD?  If I did need to have a formatted HD, how would I format it or re-partition it if I currently have a version of FreeBSD?

Thanks in advance for any insight you all might have!

Tim

No need to change anything on your harddrive, infact you can run without it if you want.

---

### Post by jISh on 2006-07-30
The LiveCD will completley ignore your hard drive and everything. Loads it all into RAM.

---

### Post by xtgar00 on 2006-07-30
Thanks for the reply Engnome!

Well, then that begs my next question...  Why won't it boot from the CD then?

---

### Post by taurus on 2006-07-30
1.  Did you set your BIOS to boot from the CD first?

2.  Did you burn the .iso as an image file, not a data file meaning you are not supposed to unpack it and then copying everything over to the CD?

---

### Post by xtgar00 on 2006-07-30
Thanks for the reply jISH!

Taurus, in answer to your questions, Yes.  I did an iamge burn using the ISO that was downloaded and did not unpack it and then copy it.  

Is there a way to validate what I burned?  I've seen for other software there is a check sum software, is there something for this as well?  If so, where would I find it?

Thanks again!!

---

### Post by xtgar00 on 2006-07-30
Taurus, I forgot to answer your first question.  Yes, I made the change in the BIOS to make it boot from the CDRom first.

Tim

---

### Post by taurus on 2006-07-30
Do you have another computer available to see if you can boot from that CD?  Also, if you insert the CD into the drive (in Windows), you would see a bunch of files and directories instead of one big file!

k3b in Linux does the checksum before it burns...

---

### Post by xtgar00 on 2006-07-30
Thanks for the thoughts Taurus!

I put the cd in my other computer and looked and all it has it just the one big ISO file.  Apparently, when I did the burn, I didn't do it correctly.

Do you have any thoughts on what I need to do as far as the burn so that it does these expand?

Here's how I performed the burn.

Opened CD BurnerXP Pro 3
Clicked on create new compilation
It asks if I want to create a new Data-CD/RW,Data-DVD/RW, Video-DVDor create and/or burn an ISO Image.
So I clicked this and it opened up the new compilation window.
I added the .iso file that I downloaded, it says that it's type is a WinRAR Archive, does that make any difference?
I then click the Burn button and it starts it's burn process.

This is apparently and incorrect process as it did not work.  Any additional help would be appreciated.

Thanks

Tim

---

### Post by xpod on 2006-07-30
Did you check "make cd bootable"...i seem to remember THAT "must do"last week when i was at that stage

---

### Post by taurus on 2006-07-30
> **xtgar00 said:**
> Thanks for the thoughts Taurus!

I put the cd in my other computer and looked and all it has it just the one big ISO file.  Apparently, when I did the burn, I didn't do it correctly.

Do you have any thoughts on what I need to do as far as the burn so that it does these expand?

Here's how I performed the burn.

Opened CD BurnerXP Pro 3
Clicked on create new compilation
It asks if I want to create a new Data-CD/RW,Data-DVD/RW, Video-DVDor create and/or burn an ISO Image.
So I clicked this and it opened up the new compilation window.
I added the .iso file that I downloaded, it says that it's type is a WinRAR Archive, does that make any difference?
I then click the Burn button and it starts it's burn process.

This is apparently and incorrect process as it did not work.  Any additional help would be appreciated.

Thanks

Tim
Pick the "burn an ISO Image" option!!!  Again, after you have downloaded the .iso, just leave it alone; don't unpack with with WinRAR, UltraISO, or whatever...

---

### Post by ubuntu27 on 2006-07-30
**xtgar00**

Followthis guide for burning iso using CD Burner XP

[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by xtgar00 on 2006-07-30
Thanks Ubuntu27 and everyone else that assisted with my questions!  

It's so cool!  I'm installing it now!!

Thanks again!!

Tim

---

