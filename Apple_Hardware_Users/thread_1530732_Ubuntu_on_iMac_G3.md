---
title: "Ubuntu on iMac G3"
date: 2010-07-14
forum: Apple Hardware Users
---

### Post by dede468 on 2010-07-14
A friend asked me if I could install Xubuntu on his old 2001 model G3, 350M, 64Mb RAM. rather than dump it. It took 47 hours to load the xubuntu alternate CD but it loaded OK I think.... 

I got the run up data but when I should have the GUI - nothing... just a blank black screen.   I get the default error sound if I press certain keys etc

I can access terminal no problem from cntrl-option-F1 and can login to read xorg.conf

As I at least have the terminal can anyone help from here please?

This is the model I have:

[http://www.everymac.com/systems/apple/imac/stats/imac_350.html](http://www.everymac.com/systems/apple/imac/stats/imac_350.html)

---

### Post by elliottmatthew on 2010-07-14
As per my experience , probably the most simple of the installs, the Ubuntu devs seem  to have worked long and hard on making the GUI install as nice as  possible, for this install we would require the "Ubuntu Live CD" or one  of its Varients Kubuntu/Xubuntu.

---

### Post by dede468 on 2010-07-14
Read that word for word elsewhere so tried the ubuntu live cd first but the cd wasn't detected [using a cd which runs fine in my own machine].  The ONLY install cds that were detected were the original mac 9 install cd and the xubuntu 6.0.6 alternate cd for mac which has loaded fine, albeit no video.

---

### Post by linuxopjemac on 2010-07-14
don't do a reinstall. It's just a X issue. I will post you a working xorg.conf file soon. Don't use the liveCD.

---

### Post by dede468 on 2010-07-14
I had an idea it was an X issue - thanks very much for the help... look forward to it.

---

### Post by mathieub on 2010-07-14
put Cd in drive reboot , push C straight away (boot from cdrom
at second prompt boot:
type in "live video=ofonly" wait 10 mins and ther you have it. if of course the CD;'s  is an iso image of the ubuntu 10.04 alternate PowerPC image. works for me I am using it to type this on a 1999 G3 Imac 400 Mhz (but 512MB RAM) Pimped out....
:popcorn:

---

### Post by dede468 on 2010-07-14
Thanks for that and will give it a try this evening. First I have to download the 10.0.4 alt cd......... which I don't have.

At present I'll be very pleased if I can get the installed one working as I think the old cdrom is slowwwwwww plus I only have 64 RAM [ I am living in Turkey and can't find any extra SO-DIMM 100 ] - took 47 hours to load xubuntu from a new cd :D

---

### Post by linuxopjemac on 2010-07-14
Which version of xubuntu?

---

### Post by dede468 on 2010-07-14
Ubuntu 6.06.1 alternate - powerPC  which I found recommended elsewhere - I always look for recommendations first.  Should I use a later one? Not looking forward to another 47 hours loading!!

---

### Post by Joe of loath on 2010-07-14
I very much doubt you'll even be able to run a GUI with 64mb of RAM. I can only JUST manage puppy Linux on my Celeron 433mhz box with 128mb!

---

### Post by linuxopjemac on 2010-07-14
he is probably right...

---

### Post by linuxopjemac on 2010-07-14
Try LXDE....or even better OpenBox.

---

### Post by dede468 on 2010-07-14
Originally I had my suspicions on that one too when my friend told me he only had 64Mb but I was reading other forums and one guy is very happy with his same spec G3 running Xubuntu 6.06.1 alt powerpc cd so thought I'd give it a go.:neutral:

---

### Post by linuxopjemac on 2010-07-14
Which version of xubuntu did you put on ? 6.01 ?

---

### Post by dede468 on 2010-07-14
Version I used was as I said earlier in the thread, 6.06.1 alternate Powerpc. Only those marked as powerpc are detected by the computer - I've tried lots as I have lots of other linux on my other comps.  Having read on another forum that someone was happy with the way it worked on 64Mb RAM.  Not only that, but somewhere I read that the alt cd does work down to as low as 64 Mb RAM.

As linuxopjemac suggested, I have now downloaded LXDE and will give this a shot. I'll be back to report on progress as I'm sure this will all help someone else in the future......

P.S. Don't have - don't understand iPod

---

### Post by linuxopjemac on 2010-07-14
You don't need to download and install again. We first get your X working and then you can go to LXDE, it's just some package you need to install.

---

### Post by linuxopjemac on 2010-07-14
What you need to do is replace your current xorg.conf file. Do the following:

```
wget http://mac.linux.be/files/xorg/imac4.txt
sudo mv imac4.txt /etc/X11/xorg.conf
```

reboot

---

### Post by dede468 on 2010-07-14
Right - I'll do this later. It's 3pm here in Turkey and I have to go out to do some business but I'll certainly try this when I return - thanks very much.

I also have to get it connected to the internet as at present there's no connection.

---

### Post by dede468 on 2010-07-15
Didn't get chance to do any more until now but the new xorg.config file has fixed the video problem. Looks really good. Computer is of course painfully slow as I had expected but my friend has visitors from UK coming in a week or two and is buying extra memory on ebay which they will bring with them.

I'm now going to change the hd and try out this download of LXDE.  If it's a lot better than the 6.06 download for speed etc, I'll probably leave that on for him instead but hey... Operation successful.  Many thanks for your help.

---

### Post by linuxopjemac on 2010-07-15
what you need to do now is the following (in a terminal):

```
sudo apt-get install lubuntu-desktop
```

Then logout. In the display manager you don't choose Gnome, but LXDE. Login and enjoy a complete new desktop, which is a lot faster.

---

### Post by dede468 on 2010-07-15
Terminal msg reads 

E: Couldn't find package lubuntu-desktop

Downloaded LXDE on my laptop last evening and certainly looks good. Would certainly like to use it.

---

### Post by linuxopjemac on 2010-07-15
Try to install [this]("http://launchpadlibrarian.net/42928501/lubuntu-desktop_0.13_powerpc.deb").

```
sudo dpkg -i lubuntu-desktop_0.13_powerpc.deb
```


Otherwise, you just install lxde, it will also work. It won't give you the whole bunch of applications associated with the lubuntu-desktop, but you can add them yourself later

```
sudo apt-get install lxde
```

---

### Post by dede468 on 2010-07-15
No luck I'm afraid . Terminal msg 

dpkg: error processing lubuntu-desktop_0.13_powerpc.deb (--install): cannot access archive: No such file or directory
Errors were encountered while processing:
lubuntu-desktop_0.13_powerpc.deb

---

### Post by dede468 on 2010-07-15
sudo apt-get install lxde

Started building dependency tree than said 
E: couldn't find package lxde

---

### Post by linuxopjemac on 2010-07-15
You have to download that file (lubuntu-desktop....) first of course.

---

### Post by linuxopjemac on 2010-07-15
are you connected to the internet with that box?

show me the output of:
```
cat /etc/apt/sources.list
```

---

### Post by dede468 on 2010-07-15
yes this machine is on the net but is so slow that I cannot use it directly to talk to you. I am using my main machine for that. It is presently telling me:

cat /etc/apt/sources.list

many lines here but all say 

Line commented out by installer because it failed to verify 

I'll check the repos to see if anything needs uncommenting

---

### Post by linuxopjemac on 2010-07-15
If all lines are commented out, you have a problem.

It should look like this:
[http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc](http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc)

---

### Post by dede468 on 2010-07-15
OK thanks I've just been checking them out and the msgs are that hardy powerpc packages are not found. The network connection is working fine and several updates have been received. Maybe I should try installing the LXDE cd on another hd and leave this one intact to come back to?

---

### Post by linuxopjemac on 2010-07-15
I see, you are on hardy...Very old....maybe there are no repositories left for this one....I am sorry to say, but I think you better install something newer...

You might want to try my version of Linux mint.
[http://mac.linux.be/content/linux-mint-lxde-debian-50-ppc-fact](http://mac.linux.be/content/linux-mint-lxde-debian-50-ppc-fact)

---

### Post by dede468 on 2010-07-15
But will it run with only 64 Mb RAM?  I am thinking that maybe I should retry this after the extra RAM arrives in a couple of weeks.  As a matter of interest, I tried the LXDE cd on my laptop as I said earlier - great - but when I tried it on the iMac it said that there was no disc.  Unless the disc is a powerpc alt disc it cannot recognise it so I can't try that either.

---

### Post by linuxopjemac on 2010-07-15
Linux Mint LXDE needs less resources as compared to Ubuntu Gnome Hardy. I would also wait for your extra RAM.

---

### Post by dede468 on 2010-07-15
Yes, I think I'll wait for the RAM.  In the meantime I have downloaded and started to install 10.04 powerpc alt with a view to trying LXDE on it but when I start the install, I get as far as Detecting Network Hardware and it goes into spasm... continually flashing the same screen at me with " detecting network hardware - KILLED"  over and over until eventually the video drops out. Is Mint LXDE a powerpc download? I cannot get ANY cd to start unless it's a powerpc version.

---

### Post by linuxopjemac on 2010-07-15
Of course it's PowerPC based. Just follow the intructions:
[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)

---

### Post by towmasters on 2010-07-15
I Have an imacg3 400   model m5521 
400/IN/64/10G/CD/128P/56K/FW/VGA/APR
i installed ubuntu 9.04 ppc with the alternate install cd
i used the command 
install Video=ofonly

ubuntu is running in low graphics mode

i can get gnome to load.. i have tried multiple xorg.conf files sites and even modified the yaboot.conf and removed the ofonly tag.... (that causes a kernel panic)  i believe i am only getting 256 color.. 

i've been running puppy on my toshiba laptop for 2 years now.. this imac is driving me nutz.  any help would be appreciated.

---

### Post by towmasters on 2010-07-15
ok so i figured it out. it was the boot splash crashing the machine.
check this website
[http://tjworld.net/wiki/Linux/Ubuntu/PowerPC/AppleiMacG3](http://tjworld.net/wiki/Linux/Ubuntu/PowerPC/AppleiMacG3)

then i updated 
yaboot.conf,

i renamed the coppied the linux entry to another entry called ofonly
then i changed append "nosplash"
here is my xorg.conf
Section "Device"
    Identifier      "Rage128PR"
    Driver          "r128"
    BusID           "PCI:0:16:0"    # values are DECIMAL
    VideoRam        8192            # may not be needed since it usually detected
    MemBase         0x94000000      # obtained from 'lspci -vv' output
    IOBase          0x0400
EndSection

Section "Monitor"
    Identifier      "iMac Monitor"
    HorizSync       58-62
    VertRefresh     75-117
EndSection

Section "Screen"
    Identifier      "Default Screen"
    Device          "Rage128PR"
    Monitor         "iMac Monitor"
    DefaultDepth    24
    SubSection "Display"
       Depth     24
       Modes     "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Module"
    #Disable "glx"
    #Disable "dri"
EndSection 

Section "ServerLayout"
    Identifier "Default Layout"
    Screen "Default Screen"
EndSection
Cheers!

---

