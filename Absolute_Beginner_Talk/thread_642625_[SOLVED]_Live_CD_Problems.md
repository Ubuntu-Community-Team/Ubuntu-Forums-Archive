---
title: "[SOLVED] Live CD Problems"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by archiphile on 2007-12-16
So...I am all set to Dual Boot Linux and XP, I have partitioned my HD, and add a line in the MBR to allow Linux as an option...I insert the "Live CD" into my drive and....nothing, I have tried to boot from the disk. My BIOS is all set, I have booted and installed from this media before, but now nothing. I have even gone so far as to download and "burn" the distro again. Is as if the CD is blank or something.  If you all have any thoughts on what has happend please let me know. 


Machine specs:

IBM ThinkPad T 23
P III
160 GB HD
1GB RAM
Windows XP SP2
S3 Super  Savage Video Card

---

### Post by lamalex on 2007-12-16
can your computer boot from any cd? do you have a windows disk or something you can try?

---

### Post by dummyhead3 on 2007-12-16
Are you saying that it boots into Windows?
When you start your PC, the first thing ther is which button to press for BIOS, and another one for Boot menu, Press the boot menu key, and then choose CD ROM. See what happens.

---

### Post by archiphile on 2007-12-16
It boots to xp, I will try another cd
Modification of the MBR could not have cause this could it?

---

### Post by jken146 on 2007-12-16
> **archiphile said:**
> Modification of the MBR could not have cause this could it?

No, because you should be booting directly from the CD.  No MBR is involved.  Check if you can boot from another bootable CD and/or check the settings in your BIOS.

---

### Post by Sef on 2007-12-16
> It boots to xp, I will try another cd
Modification of the MBR could not have cause this could it?

It sounds like you need to set your BIOS to boot from your CD-ROM first, then have it boot from the hard drive.  The BIOS is usually gotten into from pushing one the following buttons upon start up (keep pushing it until you get into the BIOS):  F2, del, esc, F12 or maybe another.  Usually at the bottom of the screen, it tells you what button to push.

---

### Post by archiphile on 2007-12-16
My BIOS settings are correct..I have pressed F 12 (in my case) to select a Temporary Boot Device. I wonder if it was the burning program that I used? Has anyone (who still uses MS Windows) had problems with Nero?  Anyhow I am going to check and see if I can boot from my xp install cd tomorrow. It is late and I have to be up @ 0500 hrs to go to work and I have school in the evening. (last class of the semester thank you lord)  Anyhow I will post more info on the morrow.

Thanks,

Archiphile

---

### Post by archiphile on 2007-12-17
So I have inserted my XP install disk, restarted my computer and booted from that CD.  So my drive and the BIOS is all working properly.  So now I am at a loss as to why this does not work with the Ubuntu (Gutsy & Hardy), PSLinuxOS, Xubuntu (Hardy).  Any and all of your thoughts are welcome.  Thank you for all of your help.


Best,

Archiphile

---

### Post by lswest on 2007-12-17
well the only other possible option is that you might need to try a different burner software (maybe you've been burning the ISO improperly? i don't want to offend, i just thought i'd mention it).  You can always give DeepBurner a try (it's free, so no big problems, and it worked for me.) [find it here]("http://www.deepburner.com/")

---

### Post by archiphile on 2007-12-17
**Update**

So I have downloaded new burning software and I am burning a image of 7.10...(Cross your fingers) I am also going to change the MBR again and I will let you all know how thinngs go shortly.  I wanted to thank all who have responded to this thread.  Your comments and suggestions have been extremely helpful.  I hope to have a dual boot up and running smoothly w/in the next hour or so. 

Best,

Archiphile

---

### Post by archiphile on 2007-12-17
:mad:Burning the image failed...I think that I might need a new CDRW Drive.... This really makes me angry.  I have burned many a cd on this device and know it decides to up and die on me.l....

---

### Post by Frunkis on 2007-12-17
I had a similar problem getting my cd to boot, and I am still working on it now, but my original problem was that I was using the Windows CD writer to burn the disk. When I loaded everything up in Nero and set it to burn a data boot disk, it worked fine. I burned it as 12X. I've used Nero for years and never had a problem.

---

### Post by Bartender on 2007-12-17
What speed did your burn utility burn at?  Crank it down to 4X or so if you can.  Also take your CD over to  a friend's house and see if it'll boot.
Another thing to do - boot into windows.  Toss your burned CD in the tray.  Let it spin up, then Explore the CD.  If you burned it as data, there will be one folder on the CD.  That's wrong.  If you burned it as an image, there will be several folders and a handful of files.  That's what you want to see.

---

### Post by archiphile on 2007-12-18
I have tried to burn this cd @8x. I have tried it as data and as an image. Nothing:(:confused:I just have no idea what else to do short of ordering a cd. I am still going to try it @ 4x and will let you know what happens.


Best,

Archiphile

---

### Post by x-to-tha-t on 2007-12-18
You say you selected a temporary boot device in your BIOS. I may be wrong but there is usually an option to change to boot order of all drives permanently (well, until you change them back). It could be that feature that isn't working. Try checking out the advanced BIOS settings and changing it so that CD-ROM boots before HDD. If you're not sure how to do this try googling - you should be able to find a guide. If not, post your BIOS and I'll try.

---

### Post by learning curve on 2007-12-18
I had the same problems with my Gutsy Live CD.  I downloaded it again and then slowed my burn  down to 8x speed and it worked fine. :guitar:  Remember that the live CD is slow to load, so be patient, especially if it is a slow computer you are  installing it on.  It could take several minutes to fully load.

---

### Post by Skidpad on 2007-12-18
> **archiphile said:**
> I have tried to burn this cd @8x. I have tried it as data and as an image. Nothing:(:confused:I just have no idea what else to do short of ordering a cd. I am still going to try it @ 4x and will let you know what happens.


Best,

Archiphile
If you don't get it working, I'll be glad to mail you my Gutsy cd.  PM me if you are interested, and I can send it out tomorrow...provided you live in the US...  :)

---

### Post by archiphile on 2008-01-03
**Update**
I have returned from holiday and I have received a cd from skidpad, I popped in my machine and it booted fine. I will now attempt to dual boot.I just wanted to thank all who have responded to this thread for their assistance and advice it has all been very helpful. Thanks again

Best,

Archipile

---

