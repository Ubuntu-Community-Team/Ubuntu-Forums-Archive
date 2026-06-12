---
title: "Thinkpad t60p Feisty 7.04"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Andross707 on 2007-06-02
Ok,

I am interested in Linux but I am having some problems with it as of late (feisty 7.04). I recently purchased a Thinkpad t60p with an ATI Mobility FireGL v5250 graphics card. After giving up on Linux for awhile back a few months ago I recently wanted to try again with it on this new laptop. I booted from a live CD and everything seemed to be going fine until where usually I'd see the desktop after I'd see the logo with the loading bar, now I was greeted with a blueish error message screen that referenced something like "source-x" or something I can't quite remember. From there it offered to show me some error reports which made no sense to me upon looking at them. After asking me again if I wanted to see a separate error report I selected no and was then brought to a command prompt from which I couldn't leave without control-alt-deleting out.

I have yet to try to install Ubuntu on my hard drive as I am afraid of Partitioning it and am not really sure if its worth the hassle of losing Vista (I don't think the laptop came with a cd to reinstall vista with so if anything I'd prefer to dual boot I guess) but I am interested in seeing if Ubuntu really is better in day to day life than Vista (which continually hangs on me). I found that I do have a windows anytime upgrade CD but I'm not sure if I could reinstall Vista on this computer if Linux failed me.

Any help on partitioning/going full on into it and more urgently the graphics card issue would be greatly appreciated.

---

### Post by Inxsible on 2007-06-02
Its probably your video drivers that are giving you the problem. If you would be willing, you should get a Nvidia video graphics card and install that in place of the ATI.

btw, your windows anytime upgrade CD will NOT re-install Vista for you. Its only MS trying to extract more money from you by telling you that the Vista they gave you is not that great, so you should pay them more money and buy a better one which will come with its own *anytime upgrade* disk until you reach the Vista Ultimate, and you have nowhere to go ;)

---

### Post by Andross707 on 2007-06-03
..... Is there any other way for me to at least make it to the GUI?

---

### Post by Mr.Beast on 2007-06-03
> **Inxsible said:**
> Its probably your video drivers that are giving you the problem. If you would be willing, you should get a Nvidia video graphics card and install that in place of the ATI.

btw, your windows anytime upgrade CD will NOT re-install Vista for you. Its only MS trying to extract more money from you by telling you that the Vista they gave you is not that great, so you should pay them more money and buy a better one which will come with its own *anytime upgrade* disk until you reach the Vista Ultimate, and you have nowhere to go ;)

Not sure if you were aware, but this is a laptop, so upgrading graphics adapters is not really feasible, let alone moving from one chipset to another.

Andross707.
Nice to see you are keen. If I were you, given the cost that may be associated with a mistake in your configuration I would be looking to buy a second disk and swap between them.  You should be able to do this with ease if you get a T60 had disk for the Ultrabay.
I would also have a complete backup / image of my Vista disk, in case of any problems or errors.

---

### Post by Inxsible on 2007-06-03
> **Mr.Beast said:**
> Not sure if you were aware, but this is a laptop, so upgrading graphics adapters is not really feasible, let alone moving from one chipset to another.

Andross707.
Nice to see you are keen. If I were you, given the cost that may be associated with a mistake in your configuration I would be looking to buy a second disk and swap between them.  You should be able to do this with ease if you get a T60 had disk for the Ultrabay.
I would also have a complete backup / image of my Vista disk, in case of any problems or errors.

I don't see where a second hard disk is going to help, if the problem is with the video drivers !

And we aren't even 100 % sure it is the graphics card.

---

### Post by jimrz on 2007-06-03
not absolutely certain this is true with vista, but with 95/98/2k/xp all thinkpads (well, at least as far back as my olp 600x) shipped with a recovery (maybe,not sure of the terminology) partition, for when you need to re-install windows. if yours has the blue "Access IBM" botton (mine is just above the 'f3' key) then yours probably does, as well. on my T42 that partition is listed as IBM_SERVICE in Computer Management > Disk Management. it is also picked up and listed as a boot option by grub on my dual boot setup. you can find more info on this in your T60 manual or on their support website.  hope it helps.

you might also try using the "vesa" drivers to get your live cd up and running. there is an option for that somewhere on the initial live cd screen, towards the bottom i think.

---

### Post by foofightrs777 on 2007-06-04
I have the same thinkpad as you.  What I did was install Edgy (for some reason the GUI worked in the installer).

then once you reboot do sudo gedit /etc/apt/sources.list

replece all mentions of "edgy" with "feisty"

sudo apt-get update
(this next step I don't totally remember but its something like this:)
Install the ati fglrx driver from the ubuntu repos (you may need to enable universe)
sudo gedit /etc/X11/xorg.conf
change the driver to fglrx 
press ctrl-alt-backspace to reboot X.  You hopefully should now be in X using the fglrx driver.
Now, sudo apt-get dist-upgrade

hopefully this will work for you.  Its a bit convoluted though.  Hopefully someone has a better solution.

Also, this thread has some good packages for your laptop:  [http://forum.thinkpads.com/viewtopic.php?t=41372](http://forum.thinkpads.com/viewtopic.php?t=41372)

---

### Post by Andross707 on 2007-06-04
OK that sounds feasible but I wonder how you went about the installation process. I am worried that in the partitioning I may end up accidentally erasing my "service partition" as this is my first time partitioning any computer. Also, is there a foolproof way to keep Vista on this comp.....just in case?

PS I tried to start in safe graphics mode to no avail.

---

### Post by zorkerz on 2007-06-05
Could you post the error you get when x crashes.
My bet is that xorg.conf is not configured correctly. Unfortunately ati cards can be a hassle to deal with their drivers but it can be done. There are a few threads around telling how to do it. I think you could even manage without reinstalling anything possibly. I will link to one if i can find it.

---

### Post by Andross707 on 2007-06-06
> **zorkerz said:**
> Could you post the error you get when x crashes.
My bet is that xorg.conf is not configured correctly. Unfortunately ati cards can be a hassle to deal with their drivers but it can be done. There are a few threads around telling how to do it. I think you could even manage without reinstalling anything possibly. I will link to one if i can find it.

I remember it being the "X-server" that was said to have crashed which was why it said the GUI wouldn't load. Is there a way to get the error message copied without having to write it down by hand?

---

### Post by Wynne G Oldman on 2007-06-06
Hi. You could install using the Wubi installer. It doesn't do anything to your partitions, and as far as I,m aware, Windows just sees Ubuntu as a program. Your system will then dual boot. You can uninstall Ubuntu by going into "add remove programs" in control panel. After doing this, your computer is back to Windows only, and you'd never know you ever had Ububtu on it. Great way of running both operating systems, without altering any of your partitions.

---

### Post by zorkerz on 2007-06-06
How stable is the Wubi installer at this point. I know it is a fairly new project I have no idea what state it is in.

Andross707: If my memory serves me normally when x crashes as it is with you it offers two files to look at. The second one has never been any help to me. In the first one if you scroll down it (not generally very long) each line will be prefaced with a few letters explaining what type of entry it is. There is a key at the top of the file. Errors i think start with an ER. If you just copy the few errors down probably only one really essential one. We may have a better idea of what is happening.

cheers

---

### Post by Wynne G Oldman on 2007-06-06
> **zorkerz said:**
> How stable is the Wubi installer at this point. I know it is a fairly new project I have no idea what state it is in.

Andross707: If my memory serves me normally when x crashes as it is with you it offers two files to look at. The second one has never been any help to me. In the first one if you scroll down it (not generally very long) each line will be prefaced with a few letters explaining what type of entry it is. There is a key at the top of the file. Errors i think start with an ER. If you just copy the few errors down probably only one really essential one. We may have a better idea of what is happening.

cheers

I have installed Ubuntu twice and uninstalled it once using Wubi without any problems.

---

### Post by jracosta on 2007-06-07
Hello!!!

I have been working on my new T60p. I determined that 7.04 will only install using the text installer (not the live CD).

The reason X fails to start is because the ATI Fire GL video card is not supported by the driver used by the installer.

I have obtained the driver installation pack from the ATI support site. I am still not able to boot X at all but I am working on getting the drivers to compile on my system.

I will post any results that I get. It is taking longer that I wanted and I do not expect my troubles to end after I build the driver module for the Fire GL.

I will keep you posted

--Ramón

---

### Post by nandaiyo on 2007-06-07
I have the same system and problem installing Feisty. There was a solution posted here awhile back but to save you time here it is:


> When you get to the point where it dumps you to a terminal prompt, type the following:

sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx


---

### Post by Andross707 on 2007-06-10
Ok, after a long time away due to some easy BCD issues (namely not being able to get back into vista) I tried that last suggestion of entering commands into the prompt but it couldn't seem to resolve the various ubuntu.com addresses (I guess the wireless drivers aren't ready?) I was wondering what you might be suggesting......

---

### Post by zorkerz on 2007-06-10
look at the x error log and pick out the errors that look important. That will tell us what is happening.  My bet is graphics card and that can be fixed.

If you wanted to copy the whole file you could with the command line, you would have to mount a flash drive or external harddrive.

As far as vista goes I know little, but i would have expected either a restore cd or a backup partition. As long as it did not get erased.

Best of luck

---

### Post by Andross707 on 2007-06-11
ok, nandaiyo's command lines got me to the gui and I'm typing this from within ubuntu....but now for some reason the wifi wont work I checked in the network settings and my wifi card isn't even shown...

PS the error that I was getting was 'fatal server error: caught signal 11. Server aborting'

---

### Post by Andross707 on 2007-06-14
So, I guess now my question is will installing Ubuntu on my harddrive make it so I would only have to enter those command lines once (not everytime I log in to Ubuntu) ? And also, does anyone have any clues about getting my wireless internet working with this system (its a bit of a hassle having to go downstairs to the router to plug in everytime I need to get on the internet..)?

---

### Post by zorkerz on 2007-06-14
You should only have to use them once and your card should be set up for the life of the ubuntu install. Im not sure about your card. If you search around with the card name or its driver there is probably someone else who has been working on it also.

---

### Post by moixa on 2007-06-15
Feisty is working flawless on my T60p, totally problem free

(with this [http://axiomatization.googlepages.com/ubuntufeistydebpackagesforthinkpads](http://axiomatization.googlepages.com/ubuntufeistydebpackagesforthinkpads) )

---

### Post by Andross707 on 2007-06-19
How do I install these packages? (PS some of those look familiar (like the fglrx thing) that I had to type into the command line already, do I need to get those again?) (PPS will this make the wireless card work?)

---

### Post by Andross707 on 2007-06-26
OK, so I installed the hard drive head parking thing from the synaptic package manager but how do I know its working?

PS how do I install those other packages as I can't find them on synaptic....

---

### Post by jracosta on 2007-08-25
Hello,

I have also a T60p and now I am running 7.04 fine. 

I had some problems installing  Ubuntu when I used the GUI mode. It consistently failed to start X server. The T60p has a new ATI video card that is not supported by the driver included in the live CD and this is what i had to do to install Ubuntu 7.04.

1) Download Ubuntu 7.04 "Alternate install CD"  iso and burn a CD
2) Use the "Alternate install CD"  to boot my laptop
3) Select ¨Text-based Installation¨ option. The installation will run to the end and you will end up with 
    with ubntu installed, but things do not end there.
4) You need to install the correct ATI drivers for the video card included in the T60p, You can 
    download the drivers and  aticonfig following the instructions on the following site:

       [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

After step 4 you will have Ubuntu 7.04 running Gnome using the highest resolution supported by the  T60p monitor.

Hope it helps

---

