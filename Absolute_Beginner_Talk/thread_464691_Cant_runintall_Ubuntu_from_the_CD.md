---
title: "Cant run/intall Ubuntu from the CD"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by hsk1313 on 2007-06-04
I just the ubuntu CD yesterday and whenever I try to boot my computer using the CD, I get options like 
1. Install or load ubuntu linux
2. Run in Safe Mode
3. Check for defects in CD
and some more options. 

After I Select the 1st or 2nd option I get a screen where I can see the ubuntu logo and a kind of progress bar below it. After going through this phase nothing could be seen on the screen where as the CD-ROM keeps on reading the CD for 2 hours (since the LED inof the DVD RW keeps on blinking) and still nothing happens. The screen becomes completely blank where as the keyboard is working as the Num Lock key is working. Then the only option that I have is to restart the computer and either got through the entire process again or boot the system with Win XP.

Let me also tell you about my system, I have:

AMD Athlon 64 2800+
ASUS K8V-MX
256 M of RAM(out of which I can use 224MB, as the remaining 32 MB is for graphics)
40 GB HDD (which has 4 partitions on the 4th partition I have Win XP installed and all the reamining 3 partitions are filled with data. The free space in my Win XP drive is 4 GB where as in the remaining drive is 50-150 MB depending which drive it is.)
DVD RW
NO GRAPHIC CARD

Can you please tell me why the Linux is not working on my computer

---

### Post by Ek0nomik on 2007-06-04
Firstly, you don't have a graphics card?

Secondly, you only have 50-150MB to spare to install Ubuntu?  Ubuntu will require about 2GB to install, in fact just a tad over.  You will also need a buffer for installing library files and software.

If the Live CD won't run for you, download the Alternate CD instead.  Also, your computer is a bit on the lower end, so you may want to consider downloading Xubuntu because the graphic environment isn't as resource hogging as Gnome (Xubuntu uses XCFE, while Ubuntu uses Gnome) is.

If you have more questions or info, say the word.  But I would try the Alternate CD.

---

### Post by ca.kushagra on 2007-06-05
Also do use gparted and create a swap partition then run the cd.(Ek0nomik has adviced u correctly)

---

### Post by Marious on 2007-06-05
Trust the post above, Ubuntu Feisty Fawn is Feisty indeed, it does run on a bit higher end than your set up, if you had a graphics card it might run better, but you might also have a bad CD to boot, and Xubuntu is the way to go, you will need another hard drive if you want to try to install either of them, as well as a bit more memory and the graphic card if you want to use Ubuntu with Gnome on it.

Marious

---

### Post by PLoTTeR on 2007-06-05
Xubuntu is your best option as it works best with older computers. I have just successfully installed Xubuntu using '3) Install from a separate partition' from the page "http://www.jonlee.ca/installing-xubuntu-without-a-cd-drive-the-weekend-project-continued/". 

Tried most of the options, but because my laptop is an antique the third is the only that worked.

Good luck!

---

### Post by Saphfire on 2007-06-06
Im a linux  VERY  begginer  my self ;-)
Im  trying for days  to  install  ubuntu on my spare  HD without any luck.
Im doing the same  as  hsk1313   does  ......booting OK  chosing install...........NOTHING else

My system is   NVIDIA GeForce 6200 TurboCash
1280x1024 32 bit
AMD ATHLON 64X 2 DUAL
CORE PROCESOR 4200+
2G RAM
80G HD IDE disk

I download  as  well the Alternate CD  but as  a New  to linux  im COMPLETELY LOST
PLEASE  ADVICE......IM DYING to start using UBUNTU

PS.I checked the  Alternate cd  and Live  cd  in other pc  and working OK
REGARDS




:(:(:(

---

### Post by steve.horsley on 2007-06-06
Saphire: Please start your own thread, and begin by explaining what problem you have with the alternate installer CD. Is it that it won't boot, you don't understand some questions somewhere etc...

hsk1313: I agree, the alternate installer is better. But you do realistically need around 3 Gig to install to.

---

### Post by Saphfire on 2007-06-06
@steve.horsley
Hi mate thanks for  you reply.
Installed ubuntu from CD  OK. Just  when  im rebooting  from  Hd  i can see  Ubuntu loader for some minutee loading  and then BLACK screen......it doesnt go further
Reagrds

---

### Post by lazyart on 2007-06-06
> **hsk1313 said:**
> I just the ubuntu CD yesterday and whenever I try to boot my computer using the CD, I get options like 
1. Install or load ubuntu linux
2. Run in Safe Mode
3. Check for defects in CD
and some more options. 

After I Select the 1st or 2nd option I get a screen where I can see the ubuntu logo and a kind of progress bar below it. After going through this phase nothing could be seen on the screen where as the CD-ROM keeps on reading the CD for 2 hours (since the LED inof the DVD RW keeps on blinking) and still nothing happens. The screen becomes completely blank where as the keyboard is working as the Num Lock key is working. Then the only option that I have is to restart the computer and either got through the entire process again or boot the system with Win XP.

Let me also tell you about my system, I have:

AMD Athlon 64 2800+
ASUS K8V-MX
256 M of RAM(out of which I can use 224MB, as the remaining 32 MB is for graphics)
40 GB HDD (which has 4 partitions on the 4th partition I have Win XP installed and all the reamining 3 partitions are filled with data. The free space in my Win XP drive is 4 GB where as in the remaining drive is 50-150 MB depending which drive it is.)
DVD RW
NO GRAPHIC CARD

Can you please tell me why the Linux is not working on my computer

You don't have enough memory.  LiveCD needs 256 mb, you only have 224.  Adding memory would allow the CD to boot, but you still wouldn't be able to install because of your lack of hard drive space.


Saphire - PLEASE START A NEW THREAD WITH YOUR ISSUES.  WE CAN ADDRESS THEM UNCLUTTERED THERE.

---

### Post by Saphfire on 2007-06-06
OK proplem solved
edided xorg.conf   for my Nvidia card  bus id

WAS at BUSID:0:5:0
Now      BUSID:2:0:0

thanks

---

### Post by hsk1313 on 2007-09-16
Hey Guys,

Thanks alot for your feedback..
Well I have dumped my ol' system and right now on a Dual core system with 2 gigs of RAM including a 512 MB Graphic card.
I don't think that I should be facing any issues now with Ubuntu...

And again thanks a lot for all your help.

---

