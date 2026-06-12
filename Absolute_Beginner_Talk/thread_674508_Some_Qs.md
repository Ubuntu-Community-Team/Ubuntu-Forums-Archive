---
title: "Some Qs"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Ciwan on 2008-01-21
Hi guys

I'm new to Ubuntu, and I would like to know a few things

1) Can I use Rapiduploader in Ubuntu >> Rapiduploader, is a programe that enables you to upload files to Rapidshare.com.

2) Can I use Winrar, I'll be downloading movies in 8 Parts, and I want to be able to Extract and join (combine) these files into an AVI movie.

3) What programe will I be using to view AVI movies ?

4) Will I be able to run iTunes ?? Cause I have an iPod ! and so I need to upload music and stuff...etc

That is all I can think of atm. I would greatley appreciate it if someone can help me out

Thanks Guys :)

---

### Post by omi291 on 2008-01-21
> **Ciwan said:**
> Hi guys

I'm new to Ubuntu, and I would like to know a few things

1) Can I use Rapiduploader in Ubuntu >> Rapiduploader, is a programe that enables you to upload files to Rapidshare.com.

2) Can I use Winrar, I'll be downloading movies in 8 Parts, and I want to be able to Extract and join (combine) these files into an AVI movie.

3) What programe will I be using to view AVI movies ?

4) Will I be able to run iTunes ?? Cause I have an iPod ! and so I need to upload music and stuff...etc

That is all I can think of atm. I would greatley appreciate it if someone can help me out

Thanks Guys :)

1) I'm not sure, but if it works in windows and not in linux, try using wine (go to the add/remove menu and search for it)

2) Yes, winrar is available for linux: it's also in the add/remove programs menu

3) there are a lot of media players for ubuntu that would work, i recommend VLC

4) I would recommend trying to run itunes using wine, but i've never tried so i'm not sure 

hope that helps :D

---

### Post by Ciwan on 2008-01-21
What is Wine ?? :)

Thanks :)

---

### Post by jleaker01z on 2008-01-21
1.  If it is an .exe file, that is a Windows file.  It may work with Wine (can be installed under Applications>Add/Remove...search for wine) but don't hold your breath.

2.  No.  WinRAR is a Windows program.  You CAN use the open source RAR, installabe via Synaptic (System>Administration>Synaptic Package Manager...search for RAR)

3.  There are many programs you could use, although most will need the codecs installed in Ubuntu first.  You can do this via Applications>Add/Remove...search for gstreamer plugins and install them all.  (You need them for mp3s, DVDs etc also...might as well get them all at once)

I use VLC (available via Applications>Add/Remove...search for VLC) which has all the codecs built in.  Installing the codecs is still advisable tho so you can burn audio cd's and such.

4.  No, again iTunes is for Windows/Mac.  There are optional programs you can use tho.  But I dont use iTunes and don't know which ones there are, or which is the best.

---

### Post by CCNA_student on 2008-01-21
Wine is a program that allows you to run Windows programs in Linux. And if only want to manage your iPod and do not buy music from the iTunes store, then I would use gtkpod instead. That is what I use for my little iPod shuffle. 
    And if you are going to install Ubuntu Linux, I would recommend that you keep your Windows partition too. Linux is a lot different than Windows, so make sure you back up all of your important data and dual-boot to. Some people lost all of their data because they were not careful. Do not become one of them. And if you are interested I put some installation instructions and how-to's on my Linux User's Group website. I hope that you enjoy Linux.

      Sin Cere,

      CCNA

---

### Post by Ciwan on 2008-01-21
OK I check Rapiduploader and it is a [ .exe ] file.

With the Open Source RAR, will I be able to combine RAR Archives ? I have a WAREZ forum you see, and so it is Crucial that I am able to Create, and unpack RAR Archives.

Is there not a single person on Ubuntu that is into WAREZ and has an iPod? lol :)

---

### Post by jleaker01z on 2008-01-21
Yes it will handle multiple files.  It will work from within the Archive manger's GUI and you should have no problem with it.  Works much like the Windows things you are used to.

---

### Post by Ciwan on 2008-01-21
We posted @ the same time CCNA :)

When you use gtkpod, do you see the album image in your iPod ? like you would if you were using Windows.

I hate Dual Booting, I'm thinking of having Ubuntu only. and I've allready backed up everything ;)

I've got two hard drives, will my 2nd HDD be detected in Ubuntu ?

---

### Post by jleaker01z on 2008-01-21
> **Ciwan said:**
> We posted @ the same time CCNA :)

When you use gtkpod, do you see the album image in your iPod ? like you would if you were using Windows.

I hate Dual Booting, I'm thinking of having Ubuntu only. and I've allready backed up everything ;)

I've got two hard drives, will my 2nd HDD be detected in Ubuntu ?

What are your system specs?  You could always keep a 'backup' copy of Windows always available via a Virtual Machine, just in case you run into something you absolutely must use Windows for.  But a Virtual Machine does need a decent machine (doesnt have to be top of the line, I use a Sempron64 3000+ w/1gb Ram and Windows runs fine in a VM).  If you are interested in that research a program called 'VirtualBox'.

And yes, your 2nd HD should be detected.

---

### Post by Ciwan on 2008-01-21
One HDD has all my media on it

So my plan was:-

1. Disconnect my Media HDD (very important) from my Motherboard
2. Format First HDD and install Ubuntu
3. Reconnect my Media HDD to Motherboard

Will this plan work ???

---

### Post by Ciwan on 2008-01-21
My Specs are pretty good:

Asus P5K-E Wifi App
Intel Core 2 Quad Q6660
2x 250GB HDD
2 GB RAM
725 MB EVGA GeForce 8800 GTX
2x DVD-RW

What exactley is this VirtualMachine ?

---

### Post by jleaker01z on 2008-01-21
> **Ciwan said:**
> One HDD has all my media on it

So my plan was:-

1. Disconnect my Media HDD (very important) from my Motherboard
2. Format First HDD and install Ubuntu
3. Reconnect my Media HDD to Motherboard

Will this plan work ???

Yes, in fact I do the same thing...its smart ;)

The only thing is, your media drive will probably not be automatically mounted.  Just click Places>Computer and you will see the media drive.  Right click it and select 'mount volume'.

---

### Post by jleaker01z on 2008-01-21
> **Ciwan said:**
> My Specs are pretty good:

Asus P5K-E Wifi App
Intel Core 2 Quad Q6660
2x 250GB HDD
2 GB RAM
725 MB EVGA GeForce 8800 GTX
2x DVD-RW

What exactley is this VirtualMachine ?

Yea a VM will run on your box no sweat.  A virtual machine allows you to run Windows from within Ubuntu (or vice versa).  Basically, if Ubuntu is you 'host' OS, Windows will run within a Window on your desktop.

---

### Post by CCNA_student on 2008-01-21
> **Ciwan said:**
> 

When you use gtkpod, do you see the album image in your iPod ? like you would if you were using Windows.


You mean a picture of the album right? I am not sure as what I listen to(baroque, opera, classical, etc.) is over a hundred years old and really has no album art. I also have never used iTunes. And here is a picture of what gtkpod looks like. And I would suggest that you keep your Windows partition, at least for a short time. It will take time to adjust to Linux.

---

### Post by Ciwan on 2008-01-21
Alright man :) thanks

I'll go and Install Ubuntu now :)

---

### Post by Ciwan on 2008-01-21
You know how in Windows > you are able to change the looks of a music folder and make it show the picture of the album inside the folder

e.g. a Johnny Cash folder will have a Johnny Cash picture

Can that be done in Ubuntu ?

CCNA, couldn't you try and upload some modern music to your album just to see if an image of the album is shown in the iPod. I hate many of the modern stuff too, I love Classic, Blues and Country. In Classic my favourites are Vivaldi, Johann Strauss II and Beethoven ;)

---

### Post by CCNA_student on 2008-01-21
Ok, give me a few minutes.

---

### Post by Ciwan on 2008-01-22
Good Morning :)

CCNA did you try some modern music with Album Art ? Did it show up on your iPod ??

I gave you a day lol :) not only a minute :D

Thanks Bro

---

