---
title: "setting up external modem"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-01-01
Hi I brand new to Ubuntu or any Linux. I have an external modem Netcomm simplemodem 56k and from memory it is working. The light goes on so it should be good. Anywa how do I get Unbuntu to say hello to it and then if you can tell me how to set up the internet connection to I would appreciate the help.

---

### Post by ieee488 on 2007-01-01
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
is good place to start

you also need to contact your ISP and ask them what kind of authentication it uses

---

### Post by rapattack1 on 2007-01-02
Thanks I did find that link/page and got the tool that detects/identifys the modem. I ended up going with an internal modem as that page did not include external(serial) modems in it's list. It just stated usb and pci. So I have installed the pci one but the tool doesn't seem to extract properly and there is an error/window that says "Could not load section-The section 'fr=extracting' does not exist in this document. If you were directed to this section from a help button in an application, please report this to the maintainers of that application" Then there ais an OK button which I press and there is a help windows undernealth. This is after I double click or run the tool named "scanModem.gz".
RA

---

### Post by ieee488 on 2007-01-02
Can't help with that error message.
scanModem worked fine for me when I followed the directions exactly as in that HowTo article
maybe try downloading it again in the event your download got corrupted

I would download on your Windows PC, copy it to a USB drive, and take the USB drive over to the PC with Ubuntu

"setting up" an external SERIAL modem is suppose to be the easier than trying to get an internal modem to work

---

### Post by rapattack1 on 2007-01-03
Yep ok will try downloading again. My friend that installed Ubuntu might take a look tomorrow anyway but I thought I would try something on my own.
That dialup how to page didn't include serial external modems as being detected by that tool. I do not have any usb device to transfer data files. I can only do this via a burnt cd. For some reason the floppy didn't want to read the file on the Ubuntu machine. And we haven't been able to get the network happening yet.
Yep setting up externals has always been easier for me in the win world.
I put the internal modem is as it was a model that was mentioned on the page that said how to set up the dialup connection. Well and that it I had it already. 
Will get that tool now.

---

### Post by rapattack1 on 2007-01-03
Ah it seems I missed a step. The command thingy. Ok that is done but it is not going smoothly. It ID's the driver as Agere which I knew but because I have Ubuntu 5.04 there is a hitch. I types in the command to go to the grub thing but nothing is happening.
Oh hang on I am in device manager and it says that the system has recognised the modem. Is that right? If it is listed there?

---

### Post by ieee488 on 2007-01-03
For me, **wvdialconf** is the quick and dirty way find out if the modem will work out of the box with Ubuntu. Just type **sudo wvdialconf /etc/wvdial.conf** in a terminal window.

If your modem isn't recognized, that's when you'll want to use scanModem to figure out what it is to see if there is anything you can do to get it working in Linux.

I have Ubuntu 5.10 and 6.06 on the same PC. In Ubuntu 5.10, my internal modem was detected at ttyS14 but on Ubuntu 6.06, it was detected at ttyS2. Go figure!

---

### Post by rapattack1 on 2007-01-04
Oh thanks my Linux friend dropped by and he saw the internal modem. He said it was a win modem so it was a no go. We got an external serial modem to work but now I can't seem to get the machine to boot into the GUI. I know there was an issue with the bios prior as a few times I/we would get into Ubuntu and the date was wrong. So we would look at the bios and sure enough the date went back to 1999 with wrong time, wrong month and day. This time it gets to after the grid and that it is searching for the boot record floppy and then it says "disk error Press any key to restart" of course I press any key and the error is repeated. When I go into bios well there seems to be an issue with the dvd-rom. I can't remember the original order of the drives but I got it to redetect the hd. This is the Primary master and then it says CD rom(which I think should be dvd-rom), sec master it says Not installed and the sec slave it says CD rom. I might have to look inside as I don't remember how I pit it together and this didn't happen when my friend was here. Odd.
By the way that is the way he got the internet happening, the way you mentioned and he downloaded some thing called GnomePPP to make it easier. There were heaps of updates but it will take to long with dialup and only 4 hour blocks. Will get onto that later.
I kind of think maybe the bios may need an update firmware? I dunno I read something about that sometime somewhere but it is something I have never done. Oh and I have a new battery for the bios so I know that is not it.

Oh that is odd about how one version of Ubuntu detects the same device for your machine.

---

### Post by ieee488 on 2007-01-04
Yeah, after you know which port the modem is on, I start using Gnome-ppp or kppp depending on whether I am in Gnome or KDE.

---

### Post by rapattack1 on 2007-01-06
Thanks I am now on the net with Ubuntu. Wow it is really good and stable. Can you tell me what would silence the modem when it is dialing in? It is super loud and there isn't a volume control on the modem itself.
Also do you have any thoughts on the bios matter I mentioned above as now everytime I turn the machine on I have to go into the bios and correct the date, time and boot sequence. Sorry fogot to mention the boot sequence is wacko too. Or should I post on that matter separately. As I said before I am trying to learn myself and do commands as my friend is not always available. Plus anyway it is always good to be in control.

---

### Post by rapattack1 on 2007-01-06
Well I think I found the answer on the bottom of this page [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9)
I did what it said and I hope I did it right. I will know tomorrow when I dial in again. If you have any thoughts or need to add some info let me know!

---

### Post by ieee488 on 2007-01-06
I don't silence my modem. I like knowing and hearing when it connects even though it usually connects without any problems.

As for the BIOS, may be your CMOS battery is low? 

Can't help with the other stuff. I haven't had any weird problems like that on my PC.

---

### Post by rapattack1 on 2007-01-07
Well themodem is way too loud and as I get on the net late at night and I live in an apartment I need the volume to be at least low. Well whatever I did made no difference to the volume. This is the loudest modem I have ever heard. I will have to try again. Maybe I will just try the low volume thing.
I got a new battery for CMOS. Someone suggested I clean the holder for the CMOS and even clean the motherboard. MMMmmmm not sure if I am that brave yet. The computer is pretty old.
Thanks so much eh. I am really liking what I am experiencing so far with Linux, It is everything and more compared to the **** I went though with windoze.
Now to get onto testing/installing some peripherals:-k :p . You and this forum have been a big help and I much appreciate it!
rapattack

---

### Post by wdbreen on 2007-01-07
Rapattack,
As you stated that you are using gnome-ppp, there should be a field in "setup" that changes the volume of the modem to loud, low or off.
Try this if you havent already.

Wayne

---

### Post by ieee488 on 2007-01-07
If the suggestion about Gnome-ppp does not work, try this.

I bought an external modem on eBay, and the owner had put a piece of double-sided tape over the holes for the modem's speaker.

---

### Post by rapattack1 on 2007-01-08
Thanks I will try both those things. I am afraid I didn't set up the internet connection. My IT friend did. I am learning though.

---

### Post by rapattack1 on 2007-01-09
Thanks the volume is lower I think. I moved everything around on my desk so maybe because the modem is in a corner I can't hear it as loud. I will try it with no volume and see. Thanks again.

---

