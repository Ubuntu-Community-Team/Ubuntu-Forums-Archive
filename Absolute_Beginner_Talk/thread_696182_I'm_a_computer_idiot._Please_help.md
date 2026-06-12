---
title: "I'm a computer idiot. Please help"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by GSUJake on 2008-02-13
I downloaded the Ubuntu Studio download. A friend of mine said it's very good for editing DVDs. After downloading all I can do is bring up the Power2Go and nothing else. I will admit I don't know what I'm doing. Any help would be greatly appreciated. Thanks, Jake

---

### Post by jrusso2 on 2008-02-13
What is power2go? did you install this or are you running it as a live cd?

---

### Post by raafaell on 2008-02-13
> **GSUJake said:**
> I downloaded the Ubuntu Studio download. A friend of mine said it's very good for editing DVDs. After downloading all I can do is bring up the Power2Go and nothing else. I will admit I don't know what I'm doing. Any help would be greatly appreciated. Thanks, Jake

Please tell a little more information, how did you do by installing those things?

---

### Post by GSUJake on 2008-02-13
Power2go is just what popped up when the download was done. I'm not sure what a live CD is? I have it switched over to DVD

---

### Post by GSUJake on 2008-02-13
I went to ubuntustudio.org and went to download now and clicked the 

Ubuntu Studio-Gutsy DVD Images
Official 32/64-bit DVD Image and torrent. 
Download (Canonical Hosted)  option
 
 and the I downloaded the 

PC (Intel x86) alternate install CD     option.

---

### Post by justsomedude on 2008-02-13
As far as I know, power2go is a Windows CD burning application.

What you will have to do is burning the downloaded .iso file as an image and then boot from CD.

More detailed explanation here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by macogw on 2008-02-13
Did you burn the .iso to a CD?  Did you burn it as an iso/disk image?  If you did, when you look at the CD in Explorer, you should see a lot of files.  If you only see the .iso, you burned it wrong.  If you don't know how to burn an iso, download [url=http://isorecorder.alexfeinman.com/isorecorder.htm]ISO Recorder[/iso] and install it (.msi is a Microsoft installer), then right-click the .iso file and hit burn.

When it's done burning, reboot the computer with the disk in the drive.  It should boot from the CD.  If it doesn't, click either Esc, F2, F10, or F12 when your computer shows its logo during startup (as in, when it says Dell or HP or whatever).  The one to press is whichever one says "Press __ for Setup."  Use your arrow keys to move around inside the BIOS Setup screen and set your CD or DVD drive as the first boot device (put it on the top of the pile), so it boots from the disk intead of from your hard drive.

Once you're running from the CD, you will get a little menu.  Pick the option about installing (well, you can do "check disk for errors" first if you want), then choose whatever options you want for the installation.  

If you intend to dual boot (make it so when it starts up it asks "Windows or Linux?"), I'd recommend shrinking the Windows partition before doing this.  You can use a [GParted Live CD](http://gparted-livecd.tuxfamily.org/) to mess with your partitions.

---

### Post by GSUJake on 2008-02-13
I've been trying to save it to a CD but it says the program is 812M and the CD is only 700M  :confused:

---

### Post by macogw on 2008-02-14
> **GSUJake said:**
> I've been trying to save it to a CD but it says the program is 812M and the CD is only 700M  :confused:
Re-read what you posted before:
> **GSUJake said:**
> I went to ubuntustudio.org and went to download now and clicked the 

Ubuntu Studio-Gutsy **DVD Images**
Official 32/64-bit DVD Image and torrent. 
Download (Canonical Hosted)  option
 
 and the I downloaded the 

PC (Intel x86) alternate install CD     option.

---

### Post by hyper_ch on 2008-02-14
Besides, use next time a descriptive topic title and not a genereic "noob here, need help".

---

### Post by GSUJake on 2008-02-14
Sorry I'm not a computer nerd. I just need help trying to get this program working. What are you trying to say? Put it on a DVD? The instructions clearly state CD. Also for the other guy... What would you like me to change the title to?

---

### Post by LowSky on 2008-02-14
ok so your not a nerd but do the math 812MB doesnt fit onto a 700mb disc, but it will fit onto a 4.7GB DVD disc... im no genius either but its just simple substitution

---

### Post by ayenack on 2008-02-14
Hello GSUJake and welcome to Ubuntu-Forums & Ubuntu.

Take a look at this it should sort thing out for you.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

You'll need to download the free software Infra Recorder then follow the instructions. A live CD/DVD is just a CD/DVD that can run the Ubuntu OS from CD/DVD so you can test it to see if you like it. If you do you can install from the same CD/DVD by clicking the install icon on the desktop. You'll need a writable DVD also as the above poster indicates. BTW you've downloaded the alternate CD/DVD which is not a live version of the OS so you'll either have to go for a straight install or download the live version.

---

### Post by Therion on 2008-02-14
Okay, if I understand what you've done correctly, you've downloaded Ubuntu Studio for 64-bit processors.  Unless you're absolutely certain your PC has a 64-bit processor you need to download [this file instead]("http://cdimage.ubuntu.com/ubuntustudio/releases/gutsy/release/ubuntustudio-7.10-alternate-i386.iso").  Save it to your desktop.  I say this because the only image for Ubuntu Studio I see that is 812MB is the one specifically for 64-bit.

Once the download is complete, burn the file to a DVD using the instructions found here (you are going to burn an "image" file that your PC can boot from, not a regular data DVD):  [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto).

Once the DVD is burned, leave it in the drive and restart your PC.  Your PC should boot from the LiveDVD and put you into Ubuntu Studio when it's done booting.

---

### Post by seventhc on 2008-02-14
It doesn't matter if it says its for cd or dvd. A dvd just holds more data on it. So usually if there is a DVD image it will contain more data, as opposed to 3 or 4 CD's. But for example, I have Ubuntu 7.10 on a DVD, but it would work on a CD as well since it fits onto a CD. I just don't have any CD's, so I use my DVD's instead. I also have a Debian DVD image which will not fit onto a cd. Not sure if that explains it the way I intended but I hope you get the Idea.
Basically a CD image will work on a DVD but a DVD image would be to large to fit onto a CD. Just consider your DVD as a huge CD for now.

---

### Post by ayenack on 2008-02-14
> **Therion said:**
> Okay, if I understand what you've done correctly, you've downloaded Ubuntu Studio for 64-bit processors.  Unless you're absolutely certain your PC has a 64-bit processor you need to download 

No if I understand it correctly he's download the alternate x86 image not the 64Bit image. Looks like you're correct about the size though.

---

### Post by alzie on 2008-02-14
If you are already running ubuntu, you can follow the instructions here 

[https://help.ubuntu.com/community/UbuntuStudio/Installation](https://help.ubuntu.com/community/UbuntuStudio/Installation)

to migrate from either feisty or gutsy to Ubuntu Studio

The iso you have downloaded is the full install of Ubuntu with the Studio.  

BTW it is a DVD iso, so maybe the tutorials need to be updated?

Good Luck :)

---

### Post by MarkX on 2008-02-16
Maybe slightly off topic but all the burning apps I've tried in Ubuntu mistake my 730mb CDs for 700mb ones and hence refuse to burn stacks of things that XP will with 3-4 clicks. 
I'm not impressed at all with CD/DVD burning in Linux....

---

