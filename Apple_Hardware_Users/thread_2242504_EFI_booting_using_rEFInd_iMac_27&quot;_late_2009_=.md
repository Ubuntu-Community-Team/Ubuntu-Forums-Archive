---
title: "EFI booting using rEFInd iMac 27&quot; late 2009 = no unity"
date: 2014-09-02
forum: Apple Hardware Users
---

### Post by c@ssie on 2014-09-02
I've been having tons of problems trying to get ubuntu to work properly when EFI booting using rEFInd.

I installed rEFInd using  $> sudo install.sh --alldrivers in OS X
I installed ubuntu using $>sudo ubiquity -b from the Ubuntu 14.04 LiveCD

When I selected the Ubuntu logo in the rEFInd boot screen it started booting them went all black.

from the black screen I blindly logged in and installed fglrx.  
After rebooting I was able to get to the lightdm login screen but unity wouldn't load.

using a text console (ctl-alt-F1)  I logged in and did the following

$> export DISPLAY=:0.0
$> metacity --replace &
$> gnome-terminal &

then I returned to the xserver (ctl-alt-F7)
and could launch programs from the terminal there, but I had no destop/panel/launcher/etc.

It appears that compiz will not work, and unity depends on compiz.  
How can I get ubuntu to be fully functional on my iMac without  resorting to installing BIOS emulation and creating a Hybrid MBR?

---

### Post by este.el.paz on 2014-09-02
> **c@ssie said:**
> I've been having tons of problems trying to get ubuntu to work properly when EFI booting using rEFInd.

I installed rEFInd using  $> sudo install.sh --alldrivers in OS X
I installed ubuntu using $>sudo ubiquity -b from the Ubuntu 14.04 LiveCD

When I selected the Ubuntu logo in the rEFInd boot screen it started booting them went all black.


It appears that compiz will not work, and unity depends on compiz.  
How can I get ubuntu to be fully functional on my iMac without  resorting to installing BIOS emulation and creating a Hybrid MBR?

@cassie:

Looks like you have skilz . . . more than I do . . . but I have a MBPro triple boot set up and I've had to re-install rEFInd a few times . . . .  If you read rodbooks instructions it seems like it's "better" to install rEFInd **in** OSX . . . which you may or may not have done, can't exactly tell.  But, I do it the ***easy*** way in OSX admin Terminal . . . using the "drag and drop" method on the "install.sh" file . . . there was something typed in CLI, but can't remember . . . but it works well . . . it creates an "EFI" folder in the HD . . . I didn't put it someplace complicated.

I haven't used "Ubiquity" in my computer, but in XFCE or MATE . . . I don't think "compiz" is installed . . . and does have to be added . . . but for installing from a LiveDVD . . . of which I've done many, I use the GUI installer . . . and then there is the "additional drivers" app that can be used to get the video card drivers or wifi . . . and then "synaptic" or CLI to "apt-get install" . . . anything else . . . .  But, black screen??? . . . no GRUB menu?  Sometimes the installer seems to skip the GRUB partition . . . did you set up a small <10MB partition labeled "bios_grub" . . . and was the / partition "flagged"???  These kind of questions . . . lately I have been "manually" setting up the partitions.  Then it seems after the install . . . shut down and do a cold boot.

e.e.p.

---

### Post by c@ssie on 2014-09-02
> **este.el.paz said:**
> @cassie:

Looks like you have skilz . . . more than I do . . . but I have a MBPro triple boot set up and I've had to re-install rEFInd a few times . . . .  If you read rodbooks instructions it seems like it's "better" to install rEFInd **in** OSX . . . which you may or may not have done, can't exactly tell.  But, I do it the ***easy*** way in OSX admin Terminal . . . using the "drag and drop" method on the "install.sh" file . . . there was something typed in CLI, but can't remember . . . but it works well . . . it creates an "EFI" folder in the HD . . . I didn't put it someplace complicated.

I haven't used "Ubiquity" in my computer, but in XFCE or MATE . . . I don't think "compiz" is installed . . . and does have to be added . . . but for installing from a LiveDVD . . . of which I've done many, I use the GUI installer . . . and then there is the "additional drivers" app that can be used to get the video card drivers or wifi . . . and then "synaptic" or CLI to "apt-get install" . . . anything else . . . .  But, black screen??? . . . no GRUB menu?  Sometimes the installer seems to skip the GRUB partition . . . did you set up a small <10MB partition labeled "bios_grub" . . . and was the / partition "flagged"???  These kind of questions . . . lately I have been "manually" setting up the partitions.  Then it seems after the install . . . shut down and do a cold boot.

e.e.p.
I apreciate your desire to be helpful, but I'm sorry but I don't understand what you are trying to say here??  

Ubiquity is the ubuntu installer, so you probably have used it.  Compiz is the window manager that ubuntu installs by default. I'm not using grub, and my computer doesn't have BIOS.   


Does ubuntu actually work correctly on a Mac  (not a hacked up Mac with "Bootcamp" fake BIOS)?  If not is there a distro that does??

---

### Post by este.el.paz on 2014-09-02
> **c@ssie said:**
> I apreciate your desire to be helpful, but I'm sorry but I don't understand what you are trying to say here??  

Ubiquity is the ubuntu installer, so you probably have used it.  Compiz is the window manager that ubuntu installs by default. I'm not using grub, and my computer doesn't have BIOS.   


Does ubuntu actually work correctly on a Mac  (not a hacked up Mac with "Bootcamp" fake BIOS)?  If not is there a distro that does??

@cassie:

Sorry . . . confusion is all I can offer . . . .  : - ))  Yeah, a while after I posted I was thinking it was "Unity" that I should have typed . . . ???  And the "compiz" thing I know I've had to add into XFCE DE to get the "cairo dock" feature going . . . stems . . . seeds, etc.    

But, none of that is too important; to answer your question . . . yes, ubuntu runs fine on my '10 MBPro . . . although on my '02 iMac running PPC took some serious "fiddling" . . . .  But, lets say in the midst of my unclear post you could see the letters XFCE????  that was my attempt to suggest that you use the XFCE DE aka Xubuntu . . . and the other suggestions were my way of pointing out some details of installation that **might*** make a difference, i.e., using GRUB, needed or not . . . and putting rEFInd in OSX using the simple "drag/drop" in the Terminal . . . rather than, not sure what, in the "BIOS" . . . .  

I have Xubuntu 14.04 with added MATE DE option running very well in my MBPro after adding in the "mactel" ppa stuff for fan control . . . I could use the OSX manager perhaps, but I have the option to use rEFInd to select the OS . . . and if I pick ubuntu labeled as "windows" it will go to the GRUB menu . . . and then to the splash for Xubuntu . . .  takes a little bit to boot it up--but it works cleanly.

There is also Virtualbox if you want to run ubuntu in OSX, or there is now a "amd64+mac" iso . . . perhaps that would not need rEFInd . . . although possibly GRUB might be needed???  I've found that the md5sum number is much more critical to outcomes in the installation than it used to be.  And, I've also found that if an install goes "wonky" . . . if the md5sum number checks out, it's easier to just nuke and pave than it is to spend time trying to "fix" a potentially bad install . . . .  I've done quite a few installs on my 3 apple machines . . . and for the most part with some fiddling ubuntu has been the most stable . . . .  Any thing else I can confuse you with . . . let me know . . . .  : - )

e.e.p.

[Edit:  BTW I found it better to ***not*** use Bootcamp to set up the partitions . . . it seems to "lock" the disk so that further adjustments to partitions can't be done.  I just used DU to roughly set up the partition I wanted for linux and it can be set as "Free Space" or "FAT" . . . not "extended journaled" . . . and then using "Ubiquity" or whatever . . . the GParted disk utility in the installer to cut that into 3 parts . . . Home ext4, swap, and bios_grub . . . .  It used to be if you had "Free space" you could use "automatic" install in largest free space . . . but that seemed to "not work" lately so using "manual" is the choice . . . and shut down after install . . . .]

---

### Post by este.el.paz on 2014-09-02
> **c@ssie said:**
> I've been having tons of problems trying to get ubuntu to work properly when EFI booting using rEFInd.

When I selected the Ubuntu logo in the rEFInd boot screen it started booting them went all black.

from the black screen I blindly logged in and installed fglrx.  
After rebooting I was able to get to the lightdm login screen but unity wouldn't load.

and could launch programs from the terminal there, but I had no destop/panel/launcher/etc.

It appears that compiz will not work, and unity depends on compiz.  
How can I get ubuntu to be fully functional on my iMac without  resorting to installing BIOS emulation and creating a Hybrid MBR?

@cassie:

Trying to follow up for more clarity . . . first thing, rEFInd IS the app that lets you run linux w/o installing "BIOS emulation or creating a hybrid MBR" . . . and since you've said that you can get to the rEFInd screen . . . that part should be OK . . . and you are even "getting to the lightdm login screen" . . . but not a DE except a black screen . . . ???  So does that mean you saw the "Ubuntu 14.04" splash window?  Since I don't have any CLI chops I can't tell whether your CLI install would include a DE or whether you would have to add it in . . . suggesting XFCE or MATE as an option . . . that ***might*** explain how you can launch apps from the terminal only . . . no DE to do that???

So, either there was some errant detail in the install, md5 number issue, and so running a fresh install; or, simply adding a DE and seeing if that fixes the problem . . . are too very clear options . . . hope that is less confusing . . . .

e.e.p.

---

### Post by c@ssie on 2014-09-04
I could easily get XFCE or MATE working just fine, but that is totally irrelevant.   I'm really NOT looking for "workarounds", I'm interested  in solutions.  Solutions are things that will get my computer*  booted  into ubuntu 14.04 and the default unity desktop loaded and working  correctly**

* my Computer: 
Late 2009 27" iMac with 12 GB RAM and 4TB Hard drive that has 12 **GPT** partitions and **does NOT (and won't EVER) have BootCamp or**** Hybrid a MBR**

**  Working correctly means with: hardware 3D acceleration; Native video  resolution; WiFi and ethernet able connect to the internet; Heat sensors  functional and fans running at the appropriate speed; Able to read and  write to DVD, USB, and Firewire.

---

### Post by este.el.paz on 2014-09-04
> **c@ssie said:**
> I could easily get XFCE or MATE working just fine, but that is totally irrelevant.   I'm really NOT looking for "workarounds", I'm interested  in solutions.  Solutions are things that will get my computer*  booted  into ubuntu 14.04 and the default unity desktop loaded and working  correctly**
* my Computer: 
Late 2009 27" iMac with 12 GB RAM and 4TB Hard drive that has 12 **GPT** partitions and **does NOT (and won't EVER) have BootCamp or**** Hybrid a MBR**
**  Working correctly means with: hardware 3D acceleration; Native video  resolution; WiFi and ethernet able connect to the internet; Heat sensors  functional and fans running at the appropriate speed; Able to read and  write to DVD, USB, and Firewire.

@cassie:

Well, this is where I get to say that what you are saying in your subject line and this post . . . is ***confusing*** . . . .  The subject line says there is an issue with "EFI booting" . . . and say you "log in to a black screen" . . . but now you are saying that "you could easily get XFCE working"???  I did some ersatz research on "unity" and as far as I can tell it is just a DE . . . just as XFCE or MATE are . . . so if the goal is to "get 14.04 running" . . . then the question is simply, which DE works best?  Having tried out a fair number of DEs on my '10 MBPro . . . the one that runs the cleanest is XFCE . . . i.e., in Ubuntu flavors that is Xubuntu 14.04 . . . they are all running the 14.04 base, and you could have a number of DEs that you could select to log into.

Again, if you are logging into a "black screen" . . . it is either a matter of the [possibly Nvidia] video driver that needs to be selected in "additional drivers" . . . or, for some reason the install did not select a DE . . . so there is no "unity" or "xfce" installed . . . hence the blackness.  But, looking at the subject line, if you can get to the rEFInd log in manager window . . . you aren't having a problem with "rEFInd booting" . . . it's either that you haven't installed GRUB and the computer can't figure it out . . . ??  Or, you "don't like" XFCE . . . ???  

I can't comment on "3D acceleration" . . . I believe that the 64 bit choices should provide that . . . and it should be possible to run the "amd64+mac" version on the iMac????  I'm thinking that the amd-64 +mac  iso should have the "mactel ppa" repository added and so the fan control stuff is already added . . . I had to follow the sticky and with mike braxners help I got the fan temp thing installed . . . but, those aren't "workarounds" . . . that is "linux" . . . things have to be added or adjusted or tweaked as a "normal" course of business in linux.  

So, in terms of "iMac" . . . and the ins and outs of getting linux running on the intel iMac . . . those details I can't help you with; I posted to engage any questions on rEFInd that I could address . . . since no one else has stopped by in the last couple days, I'm again posting--to try to help you.  I did need to create an xorg.conf file for my PPC iMac . . . and it's possible you might need to do that . . . the iMac might have "multiple DVI ports" and that might make video difficult . . . hence needing an xorg.conf file . . . .  

For my MBPro I did not need to do that, but again, I have rEFInd installed, I have GRUB installed, and I have Xubuntu 14.04 running . . . along with 10.6.8 in one partition, and 10.9.3 in another . . . which BTW, the linux system has to go in after OSX . . . .

For the rest hopefully someone else who is running 14 on an iMac might drop by and help you out with the details . . . .

e.e.p.

---

### Post by este.el.paz on 2014-09-12
@cassie:

Did you find your "solution"??  Is your question "solved"?  Any updates on what you have tried out?  

e.e.p.

PS:  I'm typing this in my Xubuntu 14.04 partition using the MATE DE . . . and it's going OK . . . did take some fiddling.  : - )

---

### Post by c@ssie on 2014-09-19
> **este.el.paz said:**
> @cassie:

Did you find your "solution"??  Is your question "solved"?  Any updates on what you have tried out?  

e.e.p.

PS:  I'm typing this in my Xubuntu 14.04 partition using the MATE DE . . . and it's going OK . . . did take some fiddling.  : - )

No I didn't find any solution. I'm no closer to an answer than when I first asked the question.  

Maybe it's just impossible to get unity working on a mac without resorting to hacks hybrid MBR's and bios emulation.

---

### Post by este.el.paz on 2014-09-22
> **c@ssie said:**
> No I didn't find any solution. I'm no closer to an answer than when I first asked the question.  

Maybe it's just impossible to get unity working on a mac without resorting to hacks hybrid MBR's and bios emulation.


@cassie:

Possibly so . . . I guess it depends on you . . . you haven't really said here what you have tried, more or less what you don't want.  But, educate me, have you tried rEFInd, or that is exactly what you are trying to avoid?  Because, whatever it is, it bridges the difference between BIOS boot systems and EFI systems . . . pretty simple to install and use.

Perhaps the simplest solution would be to use VMFusion or Parallels or Virtualbox to run any linux system within OSX . . . that way you wouldn't have to worry about fan control issues . . . it looks like you have enough RAM and power in your machine that any "lag" in speed would almost be imperceptible.

e.e.p.

---

