---
title: "Windows to Ubuntu easy, but Ubuntu to windows???"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by Blur-king on 2006-05-29
Dear All, 

I have sort of got the hang of ubuntu and is slowly learning more about it. Now I am trying convert my wifey windows 98 to Ubuntu. She has agreed for me to try out but with the proviso that I can convert it back to Windows 98 is she does not like it. I know I can partition it but her hard disk is only about 20G hardly much room to play aroung with. So going all out for a full install but can the hard disk be reformatted to FAT32 if I need to reinstall Windows should she not like Ubuntu. Any pointers to the right direction is appreciated.  Thanks.

---

### Post by manicka on 2006-05-29
Yes, you can. You just reformat/partition the disc as fat32 with fdisk and reinstall windows

---

### Post by Sef on 2006-05-29
You can dual boot 20 GB hard drive, but as you pointed out there is not much room.  Best way is to get her to start using programs that can be used in both Windows and Ubuntu: firefox (internet), thunderbird (email client), and OpenOffice.org (Office Suite) or Abiword (word processor.)

I would definately get her off Windows 98 because after 11 July, Microsoft will drop all support for it, so no more patches or updates.  Hence any holes not fixed or discovered after that date will be free to be exploited.  

I did dual boot my 20 GB hard drive, so it is possible, but there is not much room.  I would do it this way:

Partitions:

Windows 98 - 6 GB

Ubuntu -        6 GB

Home -          5 GB

Swap -           double your ram

FAT 32 -         The rest of the hard drive.  (To share files)

Note: If Windows 98 is formatted as FAT32 then you don't need a separate FAT32 partition.  Instead use it to increase the home partition.

Check out this site for how to dual boot:

[dual boot]("http://users.bigpond.net.au/hermanzone/")

---

### Post by Blur-king on 2006-05-29
thanks guys, but I think I'll go the Sef way and once she's hook on ubuntu kill the windows98.....:mrgreen:

---

### Post by Sef on 2006-05-29
You're welcome.  Please post any more questions that you have.

---

### Post by aysiu on 2006-05-29
I would propose a different partitioning scheme.

First of all, you don't need a separate FAT32 partition to share files, since Windows 98 uses FAT32, not NTFS. So Ubuntu can read/write off the Windows partition anyway.

Also, the /home partition should be a lot larger, I think, if you're going to dual-boot.

I would propose something like:

6 GB Windows 98 (FAT32)
8 GB /home (Ext3)
5 GB / (Ext3)
swap double RAM

For more on partitioning schemes, read this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by CronoDekar on 2006-05-29
Tell your wife that Windows 98's not going to get any more security updates starting July 11th.  Certainly she wouldn't want an unsecure system!

[http://www.microsoft.com/windows/support/endofsupport.mspx](http://www.microsoft.com/windows/support/endofsupport.mspx)

Actually stumbled upon this info myself when I was considering setting up my parents' old comp as a WIn98/Ubuntu dual boot.

---

### Post by Noelinho on 2006-05-29
To be perfectly honest, I don't really see that Windows 98 is really going to be much use to her now compared to an operating system released within the last couple of years. She'll be forced to move off of it soon anyway, not least because no new programs are supported by it.

Wouldn't it actually be easier to accept that Windows 98 is now just too old and go full-in with Ubuntu? She'll learn to use it much quicker that way and I expect that for what she'll want to use it for, it won't be difficult to learn at all really.

---

### Post by aysiu on 2006-05-29
People are making sense here.

After all, almost all Windows applications that run in Windows 98 will work in Wine, anyway.

And there are some nice Windows-looking skins out there--Smooth-XP for Gnome or the Redmond themes for KDE.

---

### Post by catlett on 2006-05-29
[QUOTE=aysiu]People are making sense here.

After all, almost all Windows applications that run in Windows 98 will work in Wine, anyway.

And there are some nice Windows-looking skins out there--Smooth-XP for Gnome or the Redmond themes for KDE.[/QUOTE]
That's a good point. I didn't think of that. Wine can run anything she is used to. The biggest problem I see posted about wine is that cutting edge XP programs and games don't run or run well on wine. But since she is used to 98 all of her favorite programs can be run on ubuntu with wine. 
Sounds like this conversion is going to be easier than you think.:-D

---

### Post by magomago on 2006-05-29
Make sure that you literally set up everything perfect.  All the chat junk is setup, she has extra smileys to play with ;)  Make sure that her email client is setup, make sure that additional thigns like Flash is done, make sure you have any conceivable program that she will use installed.  

Then make it look pretty and aesthetically pleasing...because right behind functionality, if it looks reallly ugly then people will shy away from it (Which is wrong!) but given that you want to wean her away from win98 that shouldn't be too hard ;)  That and with a little wallpaper change, customizing the window/application bars just a little bit (color alteration, etc) Dapper can look quite pleasing at default settings!

And try to write a little guide that will explain to her where 99% of the stuff she will use:

"Chatting is found here: Applications-->Intnert-->Gaim Instant Messenger" If you can do things like include a picture with all the menus open and the mouse highlighted gaim that is a huge plus.  This will help to no end

It isn't that people are not willing to learn something new, or get used to a simple idea...but rather we are so impatient if we can't get help immediately we get frustrated.  If you provide functionality once they learn it...that will ultimately trump all IF they can spend with it.  That is why you have clean, pretty interfaces because they t hink "wow this is nice" and will allow their patience to go slightly further than with butt ugly design.  The little help guides are enormously helpful because they can see what they want to get done FAST.  You could tell her to go to the Ubuntu Docs, but depending on the person they may want that little bit of extra help in the beginning.

Anyways good luck!

---

### Post by joshrobinson on 2006-05-29
[QUOTE=magomago]
Anyways good luck![/QUOTE]


yeah a pretty operating system is always a plus for me, if ubuntu was ugly as sin, and couldnt be customized i wouldnt be running this distro. dapper gets nicer by the day also.. you could always use dapper instead of breezy, cause release day is coming soon :-D

thursday right?

---

### Post by Noelinho on 2006-05-29
Indeedy-doody, Thursday it is.

---

### Post by joshrobinson on 2006-05-29
[QUOTE=Noelinho]Indeedy-doody, Thursday it is.[/QUOTE]

haha yeah thats what i thought.. yay!:D

---

### Post by decaturcomp on 2006-05-29
magomago makes good points above.

how about adding another hard drive, though? They're getting to be cheap as dirt. Then you can use the old (probably slower) drive for file storage later when you've ditched windows.

---

### Post by nalmeth on 2006-05-29
Don't depend on wine too much. I usually say wine run's most thing's most of the time. Likely there are linux equivalent's for those old app's anyway.

Perhaps she would prefer KDE? Try both, if she can't hack one, she may like the other.

AMSN is pretty good if she only needs MSN messaging.

---

### Post by Blur-king on 2006-05-30
Thanks guys, been letting the wife read this thread, and she is just amaze at how complete strangers are willing to help anyone with Ubuntu. She is now trying out my box and will inherit it while I will burn her windows and install dapper this weekend...:D . dapper here I come...

---

### Post by macdo on 2006-05-30
Hehe 
World domination is assured!

I wish I could have the same succcess with my GF - she's addicted to Photoshop :-(

Please Mr Adobe, give us a Linux version!

---

