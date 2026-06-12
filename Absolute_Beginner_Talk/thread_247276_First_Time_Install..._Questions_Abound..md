---
title: "First Time Install... Questions Abound."
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by claude05 on 2006-08-30
Hello all: 
Thanks to this site I am about to take the Linux plunge. 
This is my first post so bare with me. I'm fairly excited, but I'm the cautious type and need some answers before I get on with it.

I've downloaded both the 32bit and 64bit versions of Ubuntu, however, from what I've read so far it seems that the 64bit version is still fairly tricky to get going and since I am a beginner it makes sense to install the 32bit version. Am I right in this assumption? Taking into account that I know nothing about
Linux would the 32bit version be vastly simpler for me? 

My other questions are hardware related for the most part. 
My box's specs are as follows:

[B]Amd X2 3800 dual core processor
asus A8v Deluxe motherboard
Nvidia 6800 vid card (vanilla)
2 WD 250gb 16mb SATA Hd's in Raid 0
M-audio 5.1 sound card
2gb of ram
Dell 2005fpw Lcd[/B]

Would any of these devices be troublesome with regards to getting drivers to work? Are the Drivers used in Xp compatible with Linux(ie chipset drivers) or are only Linux specific drivers usable? from the little I've read so far it seems like everything except my sound card would work right off the bat (M-audio hasn't released a new driver for Xp since 2004 let alone for linux. its non existant..). I wouldn't mind having to get a new sound card for the system if I had to, but I would rather not use the onboard sound from my Mobo since it's always been subpar with regards to audio quality. 

I will be dual booting Ubuntu with Win Xp Pro. I will be creating the new partition as soon as my files are backed up. I currently have my Xp installation running on a Via Sata Raid on an Asus A8v Deluxe motherboard. 
Now when I first installed Xp on the raid I needed to load drivers just to get the operating system to see the array. Will the same have to be done for Ubuntu? Or would it be recognized with out them? 

Well that's all I can think of right now, but I am sure I will have more questions coming. Thanks for your patience and mainly thanks for your help.

---

### Post by John.Michael.Kane on 2006-08-30
The spec's listed should work with the excetion of the M-audio this hardware i'm not sure if theres known drivers for it or if you would have to compile your own. the folks over in [**Ubuntu Studio**]("http://ubuntuforums.org/forumdisplay.php?f=128") maybe able to offer some info on that card's support.

Theres guides for setting up your nvidia card,and most everything else.

Since you have xp installed the ubuntu installition should pick up xp mbr,and offer the add it the grub for you to allow for dual booting.

**Note**: If your running vista beta i'm not sure dual booting is allowed with that version

As to 32 or 64bit only you can determand what to use. both will eventually require the enduser to use the CL no escaping that.

bottom line it's about your comfort leavel. if your willing to run some commands,and scripts then you will have little to no issue getting the 64bit version going.

should you go the 64bit route there is a [**64-bit Processor Users**]("http://ubuntuforums.org/forumdisplay.php?f=134") section on the forum.

---

### Post by Dinerty on 2006-08-30
> **claude05 said:**
> Hello all: 
Thanks to this site I am about to take the Linux plunge. 
This is my first post so bare with me. I'm fairly excited, but I'm the cautious type and need some answers before I get on with it.

I've downloaded both the 32bit and 64bit versions of Ubuntu, however, from what I've read so far it seems that the 64bit version is still fairly tricky to get going and since I am a beginner it makes sense to install the 32bit version. Am I right in this assumption? Taking into account that I know nothing about
Linux would the 32bit version be vastly simpler for me? 

My other questions are hardware related for the most part. 
My box's specs are as follows:

[B]Amd X2 3800 dual core processor
asus A8v Deluxe motherboard
Nvidia 6800 vid card (vanilla)
2 WD 250gb 16mb SATA Hd's in Raid 0
M-audio 5.1 sound card
2gb of ram
Dell 2005fpw Lcd[/B]

Would any of these devices be troublesome with regards to getting drivers to work? Are the Drivers used in Xp compatible with Linux(ie chipset drivers) or are only Linux specific drivers usable? from the little I've read so far it seems like everything except my sound card would work right off the bat (M-audio hasn't released a new driver for Xp since 2004 let alone for linux. its non existant..). I wouldn't mind having to get a new sound card for the system if I had to, but I would rather not use the onboard sound from my Mobo since it's always been subpar with regards to audio quality. 

I will be dual booting Ubuntu with Win Xp Pro. I will be creating the new partition as soon as my files are backed up. I currently have my Xp installation running on a Via Sata Raid on an Asus A8v Deluxe motherboard. 
Now when I first installed Xp on the raid I needed to load drivers just to get the operating system to see the array. Will the same have to be done for Ubuntu? Or would it be recognized with out them? 

Well that's all I can think of right now, but I am sure I will have more questions coming. Thanks for your patience and mainly thanks for your help.

Your specs seem fine, apart from the sound, but don't despair you never know it may get picked up, simplest thing to do is put the Ubuntu CD in your drive and fire it up, if you hear the logon sound you know it has detected it :)

Your windows drivers will not work on Linux, check my sig for guides on installing Ubuntu and drivers.

I have heard of a few issues with 64bit, but did not pay to much attention as I'm 32 bit, but check the 64 bit section of the forum and see what the guys say :)

---

### Post by claude05 on 2006-08-30
Thanks for the quick reply. However I'm still confused, mostly because of some of the terms being used. I have spent the entire day reading up but still haven't gotten the hang of the speak. I'd kill for a Linux glossary of terms. So please remember I am a total new comer to this. Please talk to me like I'm a child. :) 

I will not be running vista. I do have the beta but so far Ubuntu seems more interesting. The reason why I keep Xp instead of doing a clean install is simply because of the work I do, ie video editing and Photography, hence why I am reluctant to give it up since I still need it to make some bread.
 I have read the Nvidia installation guides on this site and think its fairly straight forward, but thought is different from action so we'll see. I did think that my Soundcard would be a pain. It runs well on Xp but perhaps its time to upgrade it to something better maintained. Thanks for the Studio link I will check it out. 

I am willing to run commands and scripts but considering that this is new territory for me, I think I will go 32bit and switch over when I feel more comfortable. 

Thanks again.

---

### Post by claude05 on 2006-08-30
> **Dinerty said:**
> Your specs seem fine, apart from the sound, but don't despair you never know it may get picked up, simplest thing to do is put the Ubuntu CD in your drive and fire it up, if you hear the logon sound you know it has detected it :)

Your windows drivers will not work on Linux, check my sig for guides on installing Ubuntu and drivers.

I have heard of a few issues with 64bit, but did not pay to much attention as I'm 32 bit, but check the 64 bit section of the forum and see what the guys say :)

Thanks for the tips! your install anything in Ubuntu guide is a breath of understandable fresh air, thanks!

---

### Post by Dinerty on 2006-08-30
My main advice would be to search for information/answers now, so once you have Ubuntu installed you don't have to spend time looking for them then, instead you can immediately begin installing software and drivers.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

&

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Are great places to find information and get you on you way.

Now back to software, take a look at what programs you currently use on Windows and then take a look at:

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

For linux alternatives, this will give you a rough idea of what to expect

---

### Post by Fully216 on 2006-08-30
The pre-installed nvidia drivers will work, athough you will not have 3D acceleration and will not be able to use some of the more cool features that your graphics card offers.  

You may use the nvidia driver found on their website, which is what worked for me.  It is very easy to install and adds some flare to your graphics.  As in my case, I noticed a difference right away.  Granted I have a different video card, but the general procedure should be very similar.  

You can find more information in this thread, related to an older nvidia graphics card.

[http://www.ubuntuforums.org/showthread.php?t=229490](http://www.ubuntuforums.org/showthread.php?t=229490)

Aside, if the driver doesn't work, you can always rool back the bundeled nv driver that comes with ubuntu and works just fine.

Otherwise, I don't forsee any issues.

FYI, I use 64-bit ubuntu for amd systems.  The only real problem I have is getting flash to work, so I use 32-bit firefox to browse the web.  Otherwise, everything works just peachy.

---

### Post by toasted on 2006-08-30
There are a few ways to run Windows software in the Linux environment. Some software works, some doesnt. Wine is a free one that with a little coaxing you can get photoshop to work I believe. 

Here is a link for wine:

[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by Nytram on 2006-08-30
[QUOTE=claude05;1441790]Hello all: 

This is my first post so bare with me.

Hmm you want us to undress with you?!

---

### Post by claude05 on 2006-08-30
> **Nytram said:**
> [QUOTE=claude05;1441790]Hello all: 

This is my first post so bare with me.

Hmm you want us to undress with you?!

That'd be nice, but its too early for me to get myself banned.;)

---

