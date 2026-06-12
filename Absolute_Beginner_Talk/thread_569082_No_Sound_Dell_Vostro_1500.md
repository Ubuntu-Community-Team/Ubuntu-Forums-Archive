---
title: "No Sound Dell Vostro 1500"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by ~chinook~ on 2007-10-06
I installed the Gutsy Gibbon beta. Everything is working except for sound. My sound card does not seem to be recognized. Any help will be greatly appreciated. Before you ask here is my lspci -v for my sound card

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 0228
        Flags: fast devsel, IRQ 21
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by overdrank on 2007-10-06
> **~chinook~ said:**
> I installed the Gutsy Gibbon beta. Everything is working except for sound. My sound card does not seem to be recognized. Any help will be greatly appreciated. Before you ask here is my lspci -v for my sound card

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 0228
        Flags: fast devsel, IRQ 21
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

Hi not real familiar with Gutsy myself right now but maybe this will help some
 [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by ~chinook~ on 2007-10-06
No dice.

---

### Post by CyberK on 2007-10-06
I just want to chime in and add that I have exactly the same problem. Same onboard audio controller w/ same lspci readout (different motherboard though, it's not a Dell at all), worked fine in Feisty (out of the box) and not all in the Gutsy beta.

**Update:** I downloaded a whole bunch of updates with the update manager (nothing specific  to do with sound, but some things pertaining to the kernel, I believe), and rebooted. It works now! Thank God for the Update Manager.

---

### Post by ~chinook~ on 2007-10-06
I downloaded all the updates too. Still not working for me :(

---

### Post by ~chinook~ on 2007-10-06
I guess I will just have to wait until a solution comes out. I am not the only one with the problem.

---

### Post by boydthomson on 2007-10-07
Yep, exact same problem with my Vostro1500.

---

### Post by Zenith_ on 2007-10-07
Same problem with my Inspiron 1520...hope there's a fix soon, I hate being without sound.  :)

---

### Post by ~chinook~ on 2007-10-07
Everything else has went without a hitch. It is running silky smooth too. I am just getting a little impatient. I want to listen to some tunes, watch some vids etc. Hopefully, they have a fix soon.

---

### Post by ~chinook~ on 2007-10-08
the solution 

sudo apt-get install module-assistant (useless cause you already have it if it's not the first time you do the trick)
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

---

### Post by cherry316316 on 2007-10-08
> **~chinook~ said:**
> the solution 

sudo apt-get install module-assistant (useless cause you already have it if it's not the first time you do the trick)
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Thanks a million dude
i got my sound after 2 weeks :) , 
only thing was i have  to reboot
and now its working :)

---

### Post by dahlheim on 2007-10-08
> **~chinook~ said:**
> the solution 

sudo apt-get install module-assistant (useless cause you already have it if it's not the first time you do the trick)
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

didn't work for me.  after trying several things, i re-installed via a recently made gutsy beta dvd.  :(

---

### Post by fak3r on 2007-10-09
No go for me either, just ran all tonight's updates, and tried the module assit, to no avail.   No worries, everything else major works - running great!

---

### Post by fak3r on 2007-10-11
Found the solution in the forums, for the Vostro 1500, I got sound to work by adding:

options snd-hda-intel model=5stack

to /etc/modprobe.d/alsa-base and then rebooting.  Give it a go!

---

### Post by fromans on 2007-10-16
> **~chinook~ said:**
> the solution 

sudo apt-get install module-assistant (useless cause you already have it if it's not the first time you do the trick)
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

I have a Dell Latitude D830 with this same exact issue. This solution fixed my problem except that the speakers will still play even if you plug in headphones. Is this issue occurring for anyone else? Possible solution to it as well?

---

### Post by dahlheim on 2007-10-16
> **fromans said:**
> I have a Dell Latitude D830 with this same exact issue. This solution fixed my problem except that the speakers will still play even if you plug in headphones. Is this issue occurring for anyone else? Possible solution to it as well?

just "for the record" (in case anyone is keeping track), this one didn't work for me either.  working fine since my slightly-earlier-beta reinstall, just ignoring any updates unless i feel like i need one or another (which seems a good rule of thumb anyway).

(sorry, on an XPS-M1210)

---

### Post by wwoollff on 2007-10-17
works perfectly on dell inspiron 1520 :D this thread should be renamed, because it could help other guys that are trying desperately to enable their system sound.

thx again

---

### Post by Merlin7777 on 2007-10-20
I can confirm that the "solution" that was posted on the bottom of the first page works for my Dell Vostro 1500.

---

### Post by jsgarvin on 2007-10-21
> **~chinook~ said:**
> the solution 

sudo apt-get install module-assistant (useless cause you already have it if it's not the first time you do the trick)
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

I'm on a Vostro 1700 and sound worked fine in Feisty by default.  The above mostly solved the problem in Gutsy.  Sound works now but as someone else reported, speakers continue to make sound when headphones are plugged in.  I booted back into my Feisty partition and confirmed that the speakers *do* properly mute in Feisty when headphones are plugged in.  Would like to find out what the rest of the fix is for this.

UPDATE: And then my speakers quit working at all.  After a little experimenting, I've figured out the following. (A) If there are no headphones plugged in when the machine boots, then speakers will work, but will also play when headphones are plugged in. Headphones also work, so sound is coming from two places. (B) If headphones are plugged in **when the machine boots** then speakers will be muted until the next time the machine is rebooted, regardless of headphone status.  Headphones will work, as long as their plugged in.

---

### Post by dumbmatter on 2007-10-21
> **jsgarvin said:**
> After a little experimenting, I've figured out the following. (A) If there are no headphones plugged in when the machine boots, then speakers will work, but will also play when headphones are plugged in. Headphones also work, so sound is coming from two places. (B) If headphones are plugged in **when the machine boots** then speakers will be muted until the next time the machine is rebooted, regardless of headphone status.  Headphones will work, as long as their plugged in.

This is what I've noticed too.  It happened in Feisty as well.

---

### Post by XNYE on 2007-10-22
> the solution

sudo apt-get install module-assistant (useless cause you already have it if it's not the first time you do the trick)
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

I tried this and all but the 'sudo m-a a-i alsa worked.

When I tried sudo m-a a-i alsa I get a module-assitant, error message:

> Installation of the alsa-source source failed.

Ignoring this package.  Maybe you need to add something to th e sources.list, maybe the contrib and non-free archives.

I have no idea what this means.

Note:I still have no sound... or at least I cannot do anything with the sound icon on the upper right corner.

---

### Post by XNYE on 2007-10-25
> matt@matt-laptop:~$ sudo apt-get install module-assistant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
module-assistant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
matt@matt-laptop:~$ sudo m-a update

Updated infos about 85 packages
matt@matt-laptop:~$ sudo m-a prepare
Getting source for kernel version: 2.6.22-14-generic
Kernel headers available in /usr/src/linux-headers-2.6.22-14-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


That's what I get after the first 3 commands then the "sudo m-a a-i alsa" command I get this:

> [QUOTE]matt@matt-laptop:~$ sudo m-a a-i alsa

Updated infos about 1 packages
Getting source for kernel version: 2.6.22-14-generic
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
download 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  alsa-source: Depends: debhelper (>= 5.0.37) but it is not installable
               Depends: debconf-utils but it is not installable
E: Broken packages

Updated infos about 1 packages

module-assistant, error message &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;       
       &#9474;                                                                    &#9474;       
       &#9474; Installation of the alsa-source source failed.                     &#8593;       
       &#9474;                                                                    &#9646;       
       &#9474; Ignoring this package. Maybe you need to add something to          &#9618;       
       &#9474; sources.list, maybe the contrib and non-free archives.   [/QUOTE]

Help me get my sound working, por favor.

Thanks

---

### Post by sascha99 on 2007-10-25
moin,

i have a similar problem with my Vostro 1700, I get the message:

No Gstrem plugin and/or "Mischpultelemente" could be found.

I searched the aplications but i don't find anything..

The option of this thread didn't work for me.

Do someone know the soluttion for my problem ?

Thanks

I solved my problem by this link: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
Method G is working fine .

---

### Post by archangeleon on 2007-10-25
Thanks a lot Chinook!  I just installed Gutsy a couple of hours ago and had the same problem as everyone else here, and your solution took care of it perfectly.  I can't wait to start playing with the new Ubuntu!

---

### Post by wolfsta on 2007-10-29
Hey

Im using a dell vostro 1500 the solution at the bottom of page 1 fixed my sound issues too.. But im havin the same issue with the headphone jack and wanna play some sounds through my stereo :(  

Anyone got any further with this? 

Cheers 

Wolfsta

---

### Post by XNYE on 2007-10-31
Wow... I am so stupid.  The solution was on the first page but I felt like being illiterate and didn't read that I needed to put the Install disc in after the sudo m-a prepare command... THEN pressing enter.  

Thanks

---

### Post by acormack on 2007-11-04
Chinook

Many Thanks - This worked perfectly for me.

---

### Post by linusr on 2007-11-04
> **Merlin7777 said:**
> I can confirm that the "solution" that was posted on the bottom of the first page works for my Dell Vostro 1500.

Not working in my Dell vostro 1500. After this sound mixer is enabled & I can chage volume leve but no sound in spaekers or headphone.

Any idea?

---

### Post by mptpro on 2007-11-04
I tried chinook's method and I get the same error in the module-assistant as 
user XNYE, post #21 in this thread.

vostro 1500
ubuntu 7.1

no sound.

thanks for all help!

---

### Post by moritzf on 2007-11-08
Hi, I tried to follow the steps but still get no sound.
I'm completely new to Ubuntu and Linux so I might have made a mistake while changing alsa-base
Thats what it looks like now:
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
options snd-hda-intel model=5stack
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388



------------
I'm using a dell Vostro 1500 and Ubuntu 7.10 64bit

---

### Post by inchaos on 2007-11-12
Soooo...
Before I tried this, with lspci -v my soundcard came back as:

[CODE]00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01f3
        Flags: fast devsel, IRQ 20
        Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>[CODE]

Now, I click on my volume control applet and I get this:

"No volume control GStreamer plugins and/or devices found."

So...can I un-do this?  :-\

---

### Post by eternal-one on 2007-12-04
Hallo!!

 this didn't work in ubuntu studio 7.10, And I cannot see my windows partition now. How do I undo? Must I reinstall ubuntu?

thanks!

---

### Post by eternal-one on 2007-12-04
alright I fixed the little update issues, still no sound...aargg!!

---

### Post by mushroomcloudwarrior on 2007-12-12
I see this is quite a problem with all the Dells. I thought i was the only unfortunate one!

I guess we'll just all have to wait and see, i have my sound working..just don't have the headphone jack working yet, i'm using kubuntu..

it's difficult to show off linux when the headphones don't work :P

---

### Post by Ben Cole on 2007-12-19
The solution at the bottom of the first page worked for my Vostro 1500. Thanks chinook.

---

### Post by grantandre on 2008-01-10
~chinook~ ... 

Your solution worked perfectly for me on my Dell Vostro 1700 (same dell/intel hardware, larger monitor) and I've tried numerous other posted suggestions with no luck. Thanks!

One note to other users who may want to try this suggestion: you'll need to have your install CD (iso image) handy as one of the steps requires that you insert this CD.

I have sound! WooHoo!

These are the steps I followed:

[INDENT][COLOR="DarkRed"]sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa[/COLOR][/INDENT]

---

### Post by chokas on 2008-01-10
Hey All, I have a dell vostro and had the exact same problems at first... it was frustrating I know but i kept trying...

I have an intel HD Audio controller and this worked beautifully for me...
[URL="https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller"]
https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller[/URL]

Method F: Compile and install linux kernel 2.6.23 ...

*does work: Vostro 1500 (STAC9205)

Download latest kernel from kernel.org Follow instructions in [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158). Make sure hda-intel drivers are enabled under Device Drivers>Sound>Advanced Linux Sound Architecture>PCI Devices

Fixes: * Sound does work after suspend * Headphones do mute external speakers

Remaining problems with this method: * If headphones are present when resuming from suspend (or at boot?) internal speakers do not work. * Fix only works first time booting into the new kernel, then system reverts to previous state. 

I hope it works for some of you too =) There are more methods for more vostro-type laptops :)

---

### Post by viragoboy on 2008-01-16
Thanks dude, it worked like a charm! That was the last issue I had to get my Vostro 1500 all set up.

---

### Post by kacharya on 2008-02-10
Works on my vostro 1500.  FYI I am running Ubuntu 7.10
Thanks!!

---

### Post by cherry316316 on 2008-02-18
> **fromans said:**
> I have a Dell Latitude D830 with this same exact issue. This solution fixed my problem except that the speakers will still play even if you plug in headphones. Is this issue occurring for anyone else? Possible solution to it as well?

yes , this is happening with me also from long time, did you found the solution, i have to reboot everytime , if i change from microphone to laptop speaker or vice versa.

also , is your mic working , mine it doesnt seems to be working !!!

---

### Post by pemailid on 2008-02-23
Hi guys,
after trying many solutions this one finally worked for me on my Dell vostro 1500 with ubuntu 7.10. Try it out along with other solutions.
I did the updates first(all of them) and then followed this guide.
[http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html](http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html)

---

### Post by ninja nicco on 2008-02-29
I finally got the sound working on my vostro 1500 by installing:

apt-get install linux-backports-modules-generic

as explained in this guide: [http://linuxblog.pansapiens.com/2007/11/29/ubuntu-gutsy-gibbon-710-on-a-dell-vostro-1500-laptop/](http://linuxblog.pansapiens.com/2007/11/29/ubuntu-gutsy-gibbon-710-on-a-dell-vostro-1500-laptop/)

---

### Post by cherry316316 on 2008-04-02
no sound in hardy 8.04 :((( 
any help ???

---

### Post by cherry316316 on 2008-04-02
got it, for some reason, hardy installed both generic and 386 kernel during update and
386 was default.
when i change to generic , the sound is working

---

### Post by abuhijleh on 2008-07-07
I did that but I still have the problem. I am suspecting that I have not reloaded the drivers after installation, could anybody direct me how to do so?

thanks

---

