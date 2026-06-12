---
title: "Modem and Live Distro CD"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by steliodj on 2006-12-06
Hi there,

Well this is the first i try linux and what can i say UBUNTU looks perfect....didn't installed yet...just runed the live distro.

My question is can i install modem drivers on live distro just to check if i will have a modem to dial-up after the install on the hard disk.
Well i tried...but can anyone please explain me what this means:
sl-modem-modules-2.6.10-5-386 depends on linux-image-2.6.10-5-386; however:
  Package linux-image-2.6.10-5-386 is not installed.
dpkg: error processing sl-modem-modules-2.6.10-5-386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sl-modem-modules-2.6.10-5-386



Thank you in Advanced
Stelios

---

### Post by kakalaky on 2006-12-06
The package depends on a different kernel than the live cd is using.  If you install it to your hd you shouldn't have that problem.

---

### Post by steliodj on 2006-12-06
Ok...that was a really fast reply,

I used scanModem to find my modem...if i paste here the rsults is it possible to tell me someone what to to download and how to install it for my my modem ?



Thanks kakalaky

---

### Post by kakalaky on 2006-12-06
I can't guarantee it will work, as not all hardware works with any OS, but I will do my best to help.

---

### Post by steliodj on 2006-12-06
Your thanks is very much appriciated,

This is what i get in ModemData:

--------------------------  System information ----------------------------
 Ubuntu 6.06 LTS 
Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
 scanModem update of:  2006_November_07


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 0000:00:1b.0	8086:27d8	103c:30a5	0403: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 66:        863   IO-APIC-level  HDA Intel

 --- Bootup diagnositcs for card in PCI slot 0000:00:1b.0 ----
[4294764.035000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 66
[4294764.035000] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===


And this is what i got in the other file(created by scanModem):

PCIDEV=8086:27d8
CLASS="Class 0403: 8086:27d8"
NAME="0403: Intel Corporation 82801G "
Vendor=8086
Device=27d8
SUBSYS=103c:30a5
SUBNAME=" Hewlett-Packard Company: Unknown device 30a5"
SUBven=103c
IRQ=66
Test="./scanModem test 8086:27d8 103c:30a5"
SOFT=8086:27d8
SLMODEMD_DEVICE=modem:1
PORT="modem:1"
Driver=snd-intel8x0m
DRIVER_=snd_intel8x0m
KDRIVER=SND_NTEL8X0M
MPLACE=


Thank You i advanced

---

### Post by steliodj on 2006-12-06
Anyone ?

---

### Post by kakalaky on 2006-12-06
It apparently needs snd_intel8x0m, which is provided in the install.

---

### Post by steliodj on 2006-12-06
I know that might it may be a stupid question but i'm so new....

It is provided in the install, but it is not in the live distro ?

Please reply :confused: 

Thanks for the help again.

---

### Post by kakalaky on 2006-12-06
getting it up and going should look something like this:

```
sudo modprobe snd-intel8x0m
sudo slmodemd --alsa -c YOUR_COUNTRY modem:1
```

Edit:  more info [here]("http://ubuntuforums.org/showthread.php?t=155170")

---

### Post by steliodj on 2006-12-06
And also...can anyone tell me where i can autodetect my modem in Ubuntu 6.10...i found it on 6.06 but can't find it in 6.10?

And how can i connect using the dialuo connection...i found where to add my username and password and the dial number...but can'd find how to dial or creation a new connection.

Would i need anything else to download so ican have my modem working after the installation?


Thanks in advanced.

---

### Post by steliodj on 2006-12-06
Anyone please? I'm desperate

---

### Post by steliodj on 2006-12-07
Anyone can see my post?

---

### Post by steliodj on 2006-12-07
Ok, well why nobody answers me? is my question that stupid...or linux is not just for everyone ?

---

### Post by steliodj on 2006-12-08
Well my thread is in 11 page or something like that ...again and still no answer what can i do ?

---

### Post by seshomaru samma on 2006-12-08
I can't help you with your modem cause I never used a modem in my life but I can offer you two options to find information about it:
1. this forum contains close to 2 million posts , use the search function on the top left to look for your people with similar problems. Put your model name in the search box .
2. log in to Ubuntu's IRC channel where you can get help online
you can do it on the Live Cd ,
first install Xchat:
```
sudo apt-get install xchat
```
then
choose 'freenode' ,wait a few seconds and when a new screen apears choose 'connect to channel:ubuntu'

Also If your modem is detected by the 6.06 version ,why not install 6.06 ?

---

### Post by steliodj on 2006-12-08
Hi seshomaru samma

thank you for your reply
but...for the 1 option i couldn't get my modem work reading the threads :(
option 2) i can't have internet access through ubuntu because i use a dialup access 


and i din't said that my modem worked on 6.06 i said that in 6.06 i could find an autodetect button(couldn't detect my modem anyway) but in 6.10 wasn't an autodetect button.

waiting for more replies please ](*,)

---

### Post by _duncan_ on 2006-12-08
Click on the 2nd link on my signature (Dial-Up Modem Wiki). It's a good starting point...

---

### Post by steliodj on 2006-12-08
thanks for the replu _duncan_ i'll try it now

---

### Post by steliodj on 2006-12-08
Hi there ...tried to install slamr i found the command i downloaded slamr...but i receive this message: opperation not permited.

---

### Post by Eddie Wilson on 2006-12-09
Hello,
My modem worked in 6.06 but I never could get it to work in 6.10.
Eddie

---

