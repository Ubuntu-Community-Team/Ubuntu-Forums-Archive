---
title: "How do I install ndiswrapper-1.8 in Ubuntu???"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by mkylman on 2007-06-01
I have recently installed the Wubi Ubuntu Installer beta 3;

I want to install ndiswrapper-1.8 so that I can install my wireless card, yet everytime I try to follow the instructions that the installer speaks of, I get various errors which are all over the place;

Can someone give or direct me to a STEP by STEP, complete idiot's guide to doing this? I am really quite new to this aspect of linux...

Note: I already have the files downloaded, I just need to know what to do in the terminal phase of installation


Mkylman

P.S. I have noticed various people mention a program called synaptic...simply put, what the hell are they talking about?

---

### Post by mkylman on 2007-06-01
Nobody!? Come on man...

---

### Post by chamberlain2006 on 2007-06-01
I don't know if you need help installing it and configuring it, but to install it, go to Synaptic Package Manager and install ndiswrapper-common and ndiswrapper-uils-1.9 or 1.8, whichever is available.

---

### Post by southernman on 2007-06-01
I am not familar with ndiswrapper so I can't help with that much, other than to say, it may help if you post the specs of your computer/laptop. From what I've read the installation might be hardware ( and OS - including which version) specific.

Now synaptic is found in System > Administration > Synaptic Package Manager.

Good Luck with this...

---

### Post by mkylman on 2007-06-01
> **chamberlain2006 said:**
> I don't know if you need help installing it and configuring it, but to install it, go to Synaptic Package Manager and install ndiswrapper-common and ndiswrapper-uils-1.9 or 1.8, whichever is available.

I do not have the synaptic package manager, I have the adept package manager on here...what do I do from there? I kind of poked around there but to no avail...

Also, as a side note, since this was an install using the Wubi installer, I don't have a disc image to obtain the files from; However I did download a tar.gz file from the net which contains the files needed; However every time I follow the install instructions there, it tells me that improper information was passed down from the header files or some bullcrap like that...

---

### Post by mkylman on 2007-06-01
Bump!

---

### Post by mkylman on 2007-06-01
EDIT: Bump

Sorry for being a jerk, i'm just kinda going into panic mode here -_-

---

### Post by southernman on 2007-06-01
> **mkylman said:**
> Bump again...

Wtf guys, gimme a freakin' hand here I'm dying and begging!It's attitudes like that, which make people want to just fall all over themselves to stop what they are doing to be at your beckon call.

Really! Could you be bothered by such a lame request I made, to post your system specs? Not yet! It may help whomever tries to help you.

Could you be bothered to write down, take a screen shot, or anything of the sort to post detailed info on the errors you are getting? Not!

Give the community a break and don't be so anxious! Relax. While your waiting for someone to help YOU out do some more searching of the forums and google.

---

### Post by mkylman on 2007-06-01
PC Specs:

Dell Inspiron 4000
256 MB Ram
700 Mghz Processor
Wireless Card: Netgear WG511v2 w/ Marvell Chipset
CD-RW/DVD-R Drive

I've done a lot of searching on how to install the driver for the wireless card and it all points to NDISWRAPPER!

Anyway I recently downloaded wubi which makes it easy to install ubuntu linux next to windows w/o a partition

I set it all up w/ kubuntu, the kde interface;

I downloaded ndiswrapper 1.8 from their sourceforge, along w/ the necessary wireless card driver...

But I can't figure out how in the hell to install ndiswrapper!!!

I followed the instructions that came in the folder, but they failed and gave me weird errors about incorrect pointer information;

Someone mentioned using synaptic to install it, however I don't have this;

I have Adept Package Manager which comes from Advanced Packaging Tool or something...I can't figure out how to install from my tar.gz file(compressed or otherwise) and it does not show up in ANY of the windows...so I have no idea what to do and I desperately need my wireless card to function, otherwise putting kubuntu on there would have no purpose...


Sorry for being a jerk, I'm going into panic mode here -_- My apologies

Mkylman

---

### Post by bobplano on 2007-06-01
if you want to install ndiswrapper the easy way but you don't have internet, then go to [www.packages.ubuntu.com](www.packages.ubuntu.com), search for ndiswrapper and download ndiswrapper-common and ndiswrapper-utils onto a usb stick or something. then just click the files in kubuntu and they should install. the tar.gz needs to be compiled so this is the easiest way to install ndiswrapper 1.9

---

### Post by mkylman on 2007-06-01
In the event that I am unable to transfer the files, how do I compile a tar.gz file?

---

### Post by bobplano on 2007-06-01
put in your ubuntu cd and then run these commands
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

then go into the untarred directory and run
```
sudo make uninstall
make
sudo make install
```

if these don't work then you might also need the "linux-headers" package. you can find this on [www.packages.ubuntu.com](www.packages.ubuntu.com) because i don't know if its on the cd. 
first run the command
```
uname -r
```
to find out your kernel number. then search that site for "linux-headers-*whatever the numbers were*
and then install that. then try rerunning the commands

EDIT: if you can't transfer files then look for the headers on the cd. you might not need them, but if you do, after you run the sudo apt-get install build-essential, then try
```
 sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by mkylman on 2007-06-01
I don't have the CD though, it's all from the Wubi Installation which uses a different alternate .iso file, although I think that I can do these commands anyway...for now I'm gonna switch back to windows and probably try some of this tomorrow...

Any more ideas anyone?

---

