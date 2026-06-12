---
title: "ok installed ubuntu,what next ?"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by nikef on 2007-08-08
hi all
i have now installed ubuntu
i dont think win xp is there anymore ?[COLOR="Red"]no theres no windoze [/COLOR]
i dont have any internet acsess as i cant get my wireless adaptor to work  [COLOR="Red"]i do now,i was using the wrong belkin adapter lol[/COLOR]
do i need ndsiswrapper if so how do i get it without internet [COLOR="Red"]no i dont,as i have internet now :0)[/COLOR]
i also get this on start up, unable to locate RSDP
Pc does not shut down  [COLOR="Red"]i can live with this for a bit[/COLOR]
is there any thing else i need to do ,i am using fiesty fawn :) and i am very,very new to linux [COLOR="Red"]just updated ubuntu,but it got stuck on 34/45 so i cancelled it and got an error[/COLOR]
ok,theres 73 software updates do i need all these?

---

### Post by skymera on 2007-08-08
what type iofm wireless card do u have>?

USB or PCI?

you can try ndiswrapper. altrhough i didnt need to.

try get your internet sorted.
as for the shutdown problem,. i dont know.
sorry

---

### Post by igknighted on 2007-08-08
> **nikef said:**
> hi all
i have now installed ubuntu
i dont think win xp is there anymore ?
i dont have any internet acsess as i cant get my wireless adaptor to work 
do i need ndsiswrapper if so how do i get it without internet 
i also get this on start up, unable to locate RSDP
Pc does not shut down
is there any thing else i need to do ,i am using fiesty fawn :) and i am very,very new to linux

Can you tell us some more about your hardware?  What kind of wireless adapter is it?  If you are unsure, type 'lspci' in the terminal (no quotes) and look for an output that looks like wireless.  Also, can you type "ifconfig" and "iwconfig" in the terminal and tell us what those say as well?  Finally, is there any way you can plug in to a wired connection for a little while in order to set stuff up?  There are other options, but having a connection is the easiest way.

---

### Post by Rul on 2007-08-08
For the RSDP stuff this thread may be helpful

[http://ubuntuforums.org/showthread.php?t=517386&highlight=rsdp]("http://ubuntuforums.org/showthread.php?t=517386&highlight=rsdp")

---

### Post by Hospadar on 2007-08-08
If you can avoid using ndiswrapper, that would be ideal, but try it, it may work fine for you.

You'll want to poke around and try and figure out what chipset your wireless card is, this might take some googling but try searching for something like "<the name of your card> linux chipset" etc (probably amtel, rt##, broadcom or something like that).  Then you will want to look for drivers/installation guides based on that chipset.  sourceforge or google or these forums would be a good place to start.

If you need to download ndiswrapper, you can do so manually by going to the fiesty package site [here]("http://packages.ubuntu.com/feisty/").  I would just go to the full list (at the bottom of the page) and search for ndiswrapper, make sure you manually download it's dependancies.

If you are going to be getting some open source drivers (off sourceforge for example) you will probably need the "build-essential" package as well.  manually download it and it's dependancies.

When you manually download these packages, you will get some *.deb files.  just save these to a disc or usb drive and double click them in linux to install them.

---

### Post by nikef on 2007-08-08
hi its a belkin wireless g usb network adaptor 802.11g
when this is connected my pc freezes  :( and i have to take out and reboot :(


hi igknighted do i need to do what you mentioned with the wireless adaptor plugged into pc,as it freezes
pc when plug in.

thanks for any help :)

thanks RUL will read that laters  :)

---

### Post by igknighted on 2007-08-08
Yes, you need to do it with it plugged in.  Try having it plugged in from boot time and seeing if it doesn't freeze then.

---

### Post by nikef on 2007-08-08
> **igknighted said:**
> Yes, you need to do it with it plugged in.  Try having it plugged in from boot time and seeing if it doesn't freeze then.

just plugged it it,but terminal will not open,while trying pc froze :(

i have a bt broadband hub,connected to my main pc,will this work do you think

---

### Post by igknighted on 2007-08-08
Oh, it should work just fine.  I wonder if the rsdp error might be causing the freeze due to hardware detection flaws.  Try fixing that issue with the info in that link, then see if you can plug the wifi adaptor in.  Do you have a more specific model name/# for that wifi stick?  The specific chip in it is very important for determining what drivers you need (Belkin uses several different types of chips, so we would need the exact model and probably even revision #... this info should be listed right on it)

---

### Post by nikef on 2007-08-08
GRRRRRRRR
this is driving me crazy by the minute,its a damn old pc,theres no ethernet at the back of pc    :(

any way this is the model number of the belkin g usb network adaptor
f5d7050b
sorry cant find the version 

thanks for helping me,will look into fixing the rsdp

---

### Post by igknighted on 2007-08-08
> **nikef said:**
> GRRRRRRRR
this is driving me crazy by the minute,its a damn old pc,theres no ethernet at the back of pc    :(

any way this is the model number of the belkin g usb network adaptor
f5d7050b
sorry cant find the version 

thanks for helping me,will look into fixing the rsdp

There are lots of how-tos for that adapter on the forums, try typing that into the search box in the upper right and looking at some of the threads.  I've never personally used on of those, so I really can only point you towards someone/some thread with a solution.  The freezing thing is weird, I have to believe its related to the RSDP stuff.  There doesn't seem to be any other reports of that adatper doing that to other computers.

---

### Post by univremonster on 2007-08-08
> **nikef said:**
> 
Pc does not shut down


Have you tried typing in the terminal

sudo shutdown -h now

---

### Post by silent1643 on 2007-08-08
can you list your full system specs?

---

### Post by nikef on 2007-08-08
> **igknighted said:**
> There are lots of how-tos for that adapter on the forums, try typing that into the search box in the upper right and looking at some of the threads.  I've never personally used on of those, so I really can only point you towards someone/some thread with a solution.  The freezing thing is weird, I have to believe its related to the RSDP stuff.  There doesn't seem to be any other reports of that adatper doing that to other computers.


hi thanks you have been a great help ,will try and look for the drivers on the forum  :)

---

### Post by nikef on 2007-08-08
> **univremonster said:**
> Have you tried typing in the terminal

sudo shutdown -h now


hi and thank you,will give that a go :)

---

### Post by nikef on 2007-08-08
> **silent1643 said:**
> can you list your full system specs?



hi heres the specs of the pc

processor 750 megahertz
128 kb primary memory cache
64 kb secondary memory cache
40 gb usable hard drive
26.32 gb hard drive free space

ADAPI dvd - rom 16x [cd-rom]
samsung cd rom
floppy disc

installed memory
368 mb

display
sis 300/305/630/540/730 [ display adaptor]
maxdata 12.9 [monitor]
multimedia
sis 7018 audio driver
standard game port
internet acsess would be a belkin wireless adaptor

---

### Post by pearlie on 2007-08-08
[Click here]("http://ubuntuforums.org/showthread.php?t=400236&highlight=pearlie") to find a good tutorial on getting your Belkin wireless dongle to work.  You've picked something a little difficult to tackle for your first go at Ubuntu, but you should be able to do it.

I just installed a Belkin wireless dongle on another computer recently, and I had the same problem with the system locking up when I plugged in the dongle.  That's because of a conflict with some drivers that are already installed on your system.  The trick to get around it is to blacklist the drivers before you plug in the dongle.  Here's how to do that:

Start up the computer without the dongle plugged in.

Go to this link: [(click here)]("http://ubuntuforums.org/showthread.php?t=400236&highlight=pearlie") Dont' start right at the beginning of the tutorial; skip right down to Step 11, which tells you to open up a terminal (go to Applications > Accessories > Terminal), and then to copy and paste this command into the box that appears:

```
gksu gedit /etc/modprobe.d/blacklist
```  

This will open up another text window with some lines of code in it; to add the items you want to blacklist, copy and paste the following lines at the end of the existing list:

```
# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib
``` 

Hit "save", and then go ahead and close the box.

Now you can restart your computer with the Belkin dongle plugged in, and follow all the steps in the tutorial from the beginning... except that you can skip Step 11, you've already done it.

Good luck, and let us know how you're doing with it.

---

### Post by nikef on 2007-08-08
> **pearlie said:**
> [Click here]("http://ubuntuforums.org/showthread.php?t=400236&highlight=pearlie") to find a good tutorial on getting your Belkin wireless dongle to work.  You've picked something a little difficult to tackle for your first go at Ubuntu, but you should be able to do it.

I just installed a Belkin wireless dongle on another computer recently, and I had the same problem with the system locking up when I plugged in the dongle.  That's because of a conflict with some drivers that are already installed on your system.  The trick to get around it is to blacklist the drivers before you plug in the dongle.  Here's how to do that:

Start up the computer without the dongle plugged in.

Go to this link: [(click here)]("http://ubuntuforums.org/showthread.php?t=400236&highlight=pearlie") Dont' start right at the beginning of the tutorial; skip right down to Step 11, which tells you to open up a terminal (go to Applications > Accessories > Terminal), and then to copy and paste this command into the box that appears:

```
gksu gedit /etc/modprobe.d/blacklist
```  

This will open up another text window with some lines of code in it; to add the items you want to blacklist, copy and paste the following lines at the end of the existing list:

```
# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib
``` 

Hit "save", and then go ahead and close the box.

Now you can restart your computer with the Belkin dongle plugged in, and follow all the steps in the tutorial from the beginning... except that you can skip Step 11, you've already done it.

Good luck, and let us know how you're doing with it.

hi and thanks for helping me

this is the results i get when i type in the terminal
sudo modprobe-vrt73...........command not found 
sudo ifconfig wlan0 up ...error getting interface flags,no such device
sudo iwconfig wlan0 essid.....xxxxxxx unrecognised wireless request
sudo iwconfig wlan0 key ......xxxxxxxxxxx  no such device
sudo dhclient wlan0 ............internet systems consortium dhcp client  v3.0.4.copyright 2004-2006 internet systems consortium all rights reserved then it gives me an internet addy to go to 
siocsifaddr no such device
wlan0 : error while getting interface flags no such divice 
](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by nikef on 2007-08-09
ok i have typed this into the teminal

install needed dependencies,take from the how to's link up above
this is what i typed 
sudo aptitude install build -essential linux-headers -uname-r
then it loaded some packages on and asked me for the live disc,it also asked if i realy wanted to install theses g++ or something,any i said yes rebooted everything seems fine,i hope i have not done anything wrong :confused:

anyway still have probs with the belkin  adaptor
when i typed lspci theres no mention of wireless anything :(

---

### Post by nikef on 2007-08-09
ok,the belkin g usb adaptor still playing up :)

have downloaded the drivers and put them on a flash dongle and transfered to the ubuntu pc

i have tried to follow the instructions in that link,but the terminal just says command not know :confused:

i have copied the drivers into my home folder and extracted them ,is this where they should be :confused:

---

### Post by nikef on 2007-08-09
still not working  :confused:
although the drivers are in the right folder,the terminal will not get them :confused:

---

### Post by nikef on 2007-08-10
:):guitar: ok got my wireless working now, i am typing this from ubuntu  :)
do i need all the 73 software updates ?

thanks :guitar:

---

### Post by Rul on 2007-08-15
Yes, it's actually quite amazing all what you have been able to do without them.

In order to fit in a 700MB disk the live cd only installs the basic software to work, and some applications only have the basic functionalities. You need all that updates to finish your installation. It will take a while so be patient

---

### Post by nikef on 2007-08-16
> **Rul said:**
> Yes, it's actually quite amazing all what you have been able to do without them.

In order to fit in a 700MB disk the live cd only installs the basic software to work, and some applications only have the basic functionalities. You need all that updates to finish your installation. It will take a while so be patient

thanks Rul
downloaded all of them :)

---

