---
title: "liveCD won't boot! Can't try Ubuntu!"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by riven0 on 2006-08-08
I've got a serious problem. Maybe you guys can help me out. I'm a long time user of M$ (since 1995), but I've always been interested in Linux, but compatibility issues always stopped me.

However, I recently read up on Ubuntu & decided that perhaps it was time to make the switch over. So I downloaded the liveCd .iso and burnt it using Nero. I popped it into my comp and it brought up the introduction screen saying I had to reboot to try it out. So I did so. But it reboots to WinXP!!! :confused: 

I've tried it on both my computers (1st Pentium III, 2nd AMD 3000), but it's the same problem. I went into the BIOS and reset the boot order to CD-Rom first, DVD-Rom second and HardDrive third. Didn't work. I disconnected the harddrive & tried rebooting it again. Still didn't work. I manually tried rebooting it on my AMD using the F11 key. Still didn't work!!!

I'm at a complete loss! Somebody please help, I really want to try out Ubuntu. :sad:

---

### Post by anaconda on 2006-08-08
Many people have had problems with badly burnt CD:s. Did you check that the burn was 100% good.

I suggest that you burn another CD, but dont burn it faster than 4x speed.
And verify that the burn was successfull.

---

### Post by Jagot on 2006-08-08
Edit: ignore me

---

### Post by coffeecat on 2006-08-08
I don't understand what you are saying. I've never seen an "introduction screen saying I had to reboot to try it out" and I've used the live CD to install (successsfully) to four different machines.

When you boot up from the live Ubuntu Dapper CD (is this what you are using?) you should see the orange-brown Ubuntu logo and below this five menu choices. The first is "Start or Install Ubuntu" (which is highlighted) and the fifth is "Boot from hard disk". Below the choices are the F key options. Press enter with the first choice highlighted and the live CD will boot up. After it's finished booting you can explore the desktop and install to your HD if you wish. If you choose the fifth option on a Windows machine then, naturally, Windows will boot up. Was this what you did?

---

### Post by Klaidas on 2006-08-08
1) Check md5sum of downloaded .iso
2) Burn it at low speed
3) Make sure you burned it as an image file, that is, if you open the CD, you will see lots of files and directories, not just one single .iso file
4) Enjoy! :)

---

### Post by riven0 on 2006-08-08
> **coffeecat said:**
> 
When you boot up from the live Ubuntu Dapper CD (is this what you are using?) you should see the orange-brown Ubuntu logo and below this five menu choices. The first is "Start or Install Ubuntu" (which is highlighted) and the fifth is "Boot from hard disk". Below the choices are the F key options. Press enter with the first choice highlighted and the live CD will boot up. After it's finished booting you can explore the desktop and install to your HD if you wish. If you choose the fifth option on a Windows machine then, naturally, Windows will boot up. Was this what you did?

The cd I'm using just says Ubuntu 6.06 (DiscTree). I do see the orange-brown logo and then it opens a window showing a list of software such as Firefox, Thuderbird, Abiword, etc. On the top of the list it says **'Boot from this CD to try Ubuntu without affecting your system'**. It *doesn't* say anything about **'start or install ubuntu'** or **'boot from harddisk'**. Anyway, I reboot my comp to try it out, but it boots up XP again.  Apparently, it doesn't even recognize the cd-rom in the drive. I've tried it on both my computers and its the same problem.

[QUOTE=Klaidas]
1) Check md5sum of downloaded .iso
2) Burn it at low speed
3) Make sure you burned it as an image file, that is, if you open the CD, you will see lots of files and directories, not just one single .iso file
4) Enjoy! [/QUOTE]

I uncrompressed the .iso file using winrar and I burnt the data files at speed 24x with data verification on. Nero said it was verified successfully. But I'm going to try burning at a lower speed and see if that helps. Keep your fingers crossed for me.

Also, I'm now exploring the burnt ubuntu cd and I see the md5sum text file. Do you want me to paste it here?

---

### Post by riven0 on 2006-08-08
Klaidas, I've checked out your Ubuntu Install guide, and I'm going to try to follow the directions there.

---

### Post by coffeecat on 2006-08-08
> **riven0 said:**
> The cd I'm using just says Ubuntu 6.06 (DiscTree). I do see the orange-brown logo and then it opens a window showing a list of software such as Firefox, Thuderbird, Abiword, etc. On the top of the list it says **'Boot from this CD to try Ubuntu without affecting your system'**. It *doesn't* say anything about **'start or install ubuntu'** or **'boot from harddisk'**. Anyway, I reboot my comp to try it out, but it boots up XP again.  Apparently, it doesn't even recognize the cd-rom in the drive. I've tried it on both my computers and its the same problem.

Never heard of the 'DiscTree' disc. Doesn't sound like the proper live/install CD. Try downloading the ISO from [one of these]("http://www.ubuntu.com/download") links. You need the Ubuntu 6.06 LTS (Dapper Drake) Desktop CD.

---

### Post by riven0 on 2006-08-08
> **coffeecat said:**
> Never heard of the 'DiscTree' disc. Doesn't sound like the proper live/install CD. Try downloading the ISO from [one of these]("http://www.ubuntu.com/download") links. You need the Ubuntu 6.06 LTS (Dapper Drake) Desktop CD.

Alright, I'm re-downloading it now. It looks like the same link I donwloaded from before, but it's possible it got corrupted in transmission. If this doesn't work, I'll try to download it through BitComet.

---

### Post by Frank Golden on 2006-08-08
> **coffeecat said:**
> I don't understand what you are saying. I've never seen an "introduction screen saying I had to reboot to try it out" and I've used the live CD to install (successsfully) to four different machines.

When you boot up from the live Ubuntu Dapper CD (is this what you are using?) you should see the orange-brown Ubuntu logo and below this five menu choices. The first is "Start or Install Ubuntu" (which is highlighted) and the fifth is "Boot from hard disk". Below the choices are the F key options. Press enter with the first choice highlighted and the live CD will boot up. After it's finished booting you can explore the desktop and install to your HD if you wish. If you choose the fifth option on a Windows machine then, naturally, Windows will boot up. Was this what you did?
You will see that message if you run the CD from within XP.
(DiskTree) is at top of Ubuntu CD Browser window in XP.

---

### Post by Frank Golden on 2006-08-08
> **riven0 said:**
> The cd I'm using just says Ubuntu 6.06 (DiscTree). I do see the orange-brown logo and then it opens a window showing a list of software such as Firefox, Thuderbird, Abiword, etc. On the top of the list it says **'Boot from this CD to try Ubuntu without affecting your system'**. It *doesn't* say anything about **'start or install ubuntu'** or **'boot from harddisk'**. Anyway, I reboot my comp to try it out, but it boots up XP again.  Apparently, it doesn't even recognize the cd-rom in the drive. I've tried it on both my computers and its the same problem.



I uncrompressed the .iso file using winrar and I burnt the data files at speed 24x with data verification on. Nero said it was verified successfully. But I'm going to try burning at a lower speed and see if that helps. Keep your fingers crossed for me.

Also, I'm now exploring the burnt ubuntu cd and I see the md5sum text file. Do you want me to paste it here?
Don't uncompress anything, If you downloaded the .iso image place it on desktop or somewhere you can find it later.
Open Nero burning rom and if a compilation window open cancel it. Go to toolbar>recorder>Burn Image navigate to place you saved
.iso and choose. Make sure you have a blank CD in drive and start burn. You don't need to do any unraring or unzipping or anything else to a .iso to burn properly with Nero. You have to boot to CD to use LiveCD or install. Starting CD in Windows XP 
only allows you to see whats on CD. When burnt properly the resulting CD will be bootable. If not burnt correctly BIOS
will not recognize it as bootable.

---

### Post by Ambimom on 2006-08-08
Maybe I'm stating the obvious, but when you rebooted did you tap either F8 or F2, or whichever is your Window's boot screen setup?

You have to change the Windows boot-up sequence so it boots to the CD-Rom drive.

Keep Ubuntu disk in the drive.  Reboot and look at the Windows startup screen, upper right corner, it will tell you what key to tap into the boot sequence.  Start tapping!

It should bring you to a screen that shows the boot....move the arrow keys on your keyboard to boot to the drive that is your CD-ROm in which the Ubuntu disk is.

Hit Return, and you should boot into Ubuntu.

Sorry, if you've already done this, but from what I am reading here, I don't see that you've done that....good luck

---

### Post by Frank Golden on 2006-08-08
> **Ambimom said:**
> Maybe I'm stating the obvious, but when you rebooted did you tap either F8 or F2, or whichever is your Window's boot screen setup?

You have to change the Windows boot-up sequence so it boots to the CD-Rom drive.

Keep Ubuntu disk in the drive.  Reboot and look at the Windows startup screen, upper right corner, it will tell you what key to tap into the boot sequence.  Start tapping!

It should bring you to a screen that shows the boot....move the arrow keys on your keyboard to boot to the drive that is your CD-ROm in which the Ubuntu disk is.

Hit Return, and you should boot into Ubuntu.

Sorry, if you've already done this, but from what I am reading here, I don't see that you've done that....good luck
He said earlier that he changed the boot sequence in his BIOS.

---

### Post by riven0 on 2006-08-08
> **Frank Golden said:**
> Don't uncompress anything, If you downloaded the .iso image place it on desktop or somewhere you can find it later.
Open Nero burning rom and if a compilation window open cancel it. Go to toolbar>recorder>Burn Image navigate to place you saved
.iso and choose. Make sure you have a blank CD in drive and start burn. You don't need to do any unraring or unzipping or anything else to a .iso to burn properly with Nero. You have to boot to CD to use LiveCD or install. Starting CD in Windows XP 
only allows you to see whats on CD. When burnt properly the resulting CD will be bootable. If not burnt correctly BIOS
will not recognize it as bootable.

Alright. I just finished re-downloading the .iso from BitComet (ubuntu.com was going too slow), and now I'm going to burn it without unraring it, as you suggested. Here goes nothing. [-o<  
BTW, thanks for all your help, guys. I hope this works.

---

### Post by Frank Golden on 2006-08-09
> **riven0 said:**
> Alright. I just finished re-downloading the .iso from BitComet (ubuntu.com was going too slow), and now I'm going to burn it without unraring it, as you suggested. Here goes nothing. [-o<  
BTW, thanks for all your help, guys. I hope this works.
That should work. Just read a post from another user about
the iso appearing as a rar. Because you have Winrar installed
is why your D/L iso is appearing as a rar. This is probably why
you were confused and thought you needed to unrar first. Follow
the instructions for burning with Nero and you should have no trouble. Good luck. Actually here goes everything is probably more appropriate. If you aren't careful you might like Ubuntu.

---

### Post by Roasted on 2006-08-09
I didn't read through all of the responses, so sorry if this is a repeat.

When I had issues burning my LiveCD for Ubuntu, I came to realize I was burning as data and not as an image to the CD. 

Data - not bootable.
Image to CD - bootable.

There was my problem.

Then it turns out the first time I burnt it as an image, the cd was bad, so I thought nothing changed. But out of curiousity I tried it again and bam, it worked.

---

### Post by seshomaru samma on 2006-08-09
1) Check Md5sum
2) Don't decompress
3) Burn as 'image' 
4) Use the slowest available speed

good luck

---

### Post by riven0 on 2006-08-09
Thank you! Thank you, everyone! It works perfect. :D I was able to boot up to Ubuntu and preview everything. Now I've just got to install it & I'm ready to go!


You guys are wonderful...:KS

---

