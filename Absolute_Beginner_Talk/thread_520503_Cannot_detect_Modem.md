---
title: "Cannot detect Modem"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by racu on 2007-08-08
Im a super newbie to Ubuntu and I want to connect to the internet via dial up.
I just finished installing Ubuntu, kernel 26-20-15-generic as my OS.

Firstly, I downloaded gnome-ppp. I used used it but it did not detect my modem. But when I tried System -> Administration -> Preferences -> Hardware Information, I can see my modem there: it is SmartLink Smart PCI1561 56k Modem.

From what I have read in some forums, some suggest to use scanModem, so I tried it. I just followed the instructions:

gunzip scanModem.gz
chmod +x scanModem
sudo ./scanModem

Then, I followed some steps in the ModemData.txt

$ tar zxvf slamr*.tgz
 Move into the unpacked folder
 $ cd slamr-2.6.20-15-generic
 Look around
 $ ls
 Run the 
 $  sudo ./setup

In the gnome-ppp gui, under the Modem tab, there are many options in selecting the Device:
dev/modem
dev/ttys0
dev/ttys1
dev/ttys2

When I try to connect using the dev/modem device, gnome-ppp says that it cannot find modem.
But when I tried the other devices, gnome-ppp says the my modem is not responding. I do not know what is happening here and I do not know what to do. And Im not sure if what I did was correct. Can somebody help me in configuring my modem and dial up connection?

---

### Post by edwardLS on 2007-08-08
My son uses the SmartLink modem successfully, but he does it using Dapper Drake.  It is my understanding from the discussion on this forum that Dialup configuration and use progressively worsened with Edgy Eft, and then further with Feisty Fawn.  

I use both Dapper and Feisty with a modem, but it is not the Smartlink modem.  I do know that I have more issues with the Feisty Dialup/Modem than I do with Dapper.  Both are installed as Multi-Boots on the same hardware.

---

### Post by _duncan_ on 2007-08-08
Usually, after a successful smartlink modem driver compilation, /dev/ttySL0 will be created, and /dev/modem will be linked to it. If /dev/modem doesn't work while setting up the dialer program, you can try /dev/ttySL0 and see if it works.

If not, you may have to check if the driver compilation was really successful. I can't judge based on the info provided since I have a different way of compiling the driver. However, it doesn't mean that your method is wrong. Different variants of smartlink modem chipsets sometimes require different ways and drivers to compile.

PS. Be careful when typing modem locations. It is case-sensitive. /dev/ttys0 is not the same as /dev/ttyS0.

---

### Post by racu on 2007-08-09
> Usually, after a successful smartlink modem driver compilation, /dev/ttySL0 will be created, and /dev/modem will be linked to it. If /dev/modem doesn't work while setting up the dialer program, you can try /dev/ttySL0 and see if it works.

If not, you may have to check if the driver compilation was really successful. I can't judge based on the info provided since I have a different way of compiling the driver. However, it doesn't mean that your method is wrong. Different variants of smartlink modem chipsets sometimes require different ways and drivers to compile.

PS. Be careful when typing modem locations. It is case-sensitive. /dev/ttys0 is not the same as /dev/ttyS0.

Thanks for the reply.
How can I check if the driver was compiled successfully? And what other info can I provide so that you can help me compiling the modem driver? (and where can I find these info?) By the way, I used slamr-2.6.20-15-generic.tar as the ModemData.txt stated. (Is that info useful?)

Sorry for me being a super newbie, I just want to use my Ubuntu to connect to the internet. Can someone also provide step by step instructions of how will I compile the modem driver? Thanks a lot...

---

### Post by _duncan_ on 2007-08-09
Take a look at the following link:

[http://ubuntuforums.org/showthread.php?p=3152820]("http://ubuntuforums.org/showthread.php?p=3152820")

The second link on my signature is also a good resource for getting dial-up to work.

---

