---
title: "Lubuntu on a Powebook G4 15&quot; 1.67Ghz"
date: 2012-11-23
forum: Apple Hardware Users
---

### Post by galvatron1983 on 2012-11-23
Has anyone installed Lubuntu on a Powerbook G4 15" 1.67GHz (late 2005)? 

I have one myself and Im thinking about replacing the OSX install on there with Lubuntu. 

Just wondered what things will/wont work straight after install ie Wifi, media playback, keyboard backlight, sleep mode activates when the lid is closed etc?

Just want to know what I'm up against!

---

### Post by powerpcliberation on 2012-11-24
In my experiences Lubuntu loves G4 chips.  It's the only Ubuntu family member I would ever put on a G4.  I have five G4 towers and it runs great on all of them.  One of my blog readers has a PowerBook the same as yours and his sound worked in everything but VLC for some reason.  His wifi needed a fix to get working though.

On all my G4 towers along with a G3 tower with a G4 upgrade the sound works perfectly out of the box.  I don't use wifi at all myself.

Here are a couple links that point directly to fixes for these two issues if you happen to encounter them.  Both are from the PowerPC FAQ on the Ubuntu PowerPC Wiki.

[**Sound**]("https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F")

[**Wireless**]("https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F")

---

### Post by Lars Noodén on 2012-11-24
I have Lubuntu on an older model and Lubuntu runs well, including the wireless.  But it is likely a different model / brand of wireless interface.  Lately there has been a little weirdness with certain graphics cards during the installation, but just during the installation, so if you run into a problem then it is fixable.

---

### Post by galvatron1983 on 2012-11-24
Hey guys, 

Thanks for the feedback! 

Not having much luck so far..... initially the Live CD boots into a desktop with graphics glitches and the colours garbled. Used the "live video=ofonly" command at Yaboot to get past the graphics issues but the live CD just hangs at a black screen after attempting to boot. 

Any ideas??

---

### Post by powerpcliberation on 2012-11-25
It sounds like you're using 12.10 from the results you're explaining.  On PowerPC at least it isn't 100% usable yet and I would recommend using 12.04 for month or two while the quirks get worked out by the community developers.  The PowerPC builds are community maintained vs. the x86 builds that are officially supported.  This means that fixes take longer.

If you still want to try installing 12.10 simply enter this command at the yaboot promt when booting the 12.10 iso:

live video=radeonfb:1024x768-32@60

Replace the 1024x768 with your screens default resolution which would be either 1280x864, 1440x900 or 1440x960 depending on which 15" 1.67 model you have.

I also wrote an install guide on my blog which is based on 12.04 for now if you need any guidance.  It's a very easy install but there are some default things that don't work properly on the PowerPC versions.  I explain these workarounds.  The guide can be found [**here**]("http://powerpcliberation.blogspot.ca/2012/10/lubuntu-install-guide.html") if you're interested.

---

### Post by abtabt on 2012-11-25
try this on Lubuntu 12.04 live cd mabey Ubuntu 12.04 live cd work too

with naividia card
live video=offb:off nouveau.modeset=0 single

with raedon card
live video=offb:off radeon.modeset=0 single

This will freeze or give you a blank screen. You will have to judge blind when the machine has finished booting which can be longer than you think. Type the command (you won't see what you type):

with naividia card
modprobe nvidiafb
 
with radeon card
modprobe radeon

Text should now appear on the screen. You can now start the desktop with the "sudo start lightdm" command.

---

### Post by powerpcliberation on 2012-11-25
> **abtabt said:**
> try this on Lubuntu 12.04 live cd

live video=offb:off nouveau.modeset=0 single

This will freeze or give you a blank screen. You will have to judge blind when the machine has finished booting which can be longer than you think. Type the command (you won't see what you type):

modprobe nvidiafb 

Text should now appear on the screen. You can now start the desktop with the "sudo start lightdm" command.


12.04 installs almost never mess up and boot to the live desktop without issue.  I have done at least 45-50 12.04 installs on about 20 different Macs and none of them needed anything but the live command to startup and install.

Why do you assume that the original poster will have those issues?  From my experiences he won't.

---

### Post by abtabt on 2012-11-26
> **powerpcliberation said:**
> 12.04 installs almost never mess up and boot to the live desktop without issue.  I have done at least 45-50 12.04 installs on about 20 different Macs and none of them needed anything but the live command to startup and install.

Why do you assume that the original poster will have those issues?  From my experiences he won't.

[/QUOTE]    galvatron wrote

 Hey guys, 

 Thanks for the feedback! 

 Not having much luck so far..... initially the Live CD boots into a desktop with graphics glitches and the colours garbled. Used the "live video=ofonly" command at Yaboot to get past the graphics issues but the live CD just hangs at a black screen after attempting to boot. 

 Any ideas?? [/QUOTE]



if you have like me then you need do things to get live cd to work and if you install you need to do some too (xorg.conf yaboot.conf etc)

its good that you have installed 20 mac with out trubble but if look 
in ubuntu forum and others forums  then you see some that have problem with Xorg it depends on the video card, as the current Mac has and there are too many types of old and new, and of course how the core is set

and i belive 12.04 Lubuntu and Ubuntu 12.04 live cd  is two diffrent kernel settings

---

### Post by galvatron1983 on 2012-11-26
> **powerpcliberation said:**
> 12.04 installs almost never mess up and boot to the live desktop without issue.  I have done at least 45-50 12.04 installs on about 20 different Macs and none of them needed anything but the live command to startup and install.

Why do you assume that the original poster will have those issues?  From my experiences he won't.

Thanks for the tip! I've downloaded 12.04 so Im gonna have a go at installing that. Would it work better if I upgraded to 12.10 from within 12.04?

---

### Post by abtabt on 2012-11-27
> **galvatron1983 said:**
> Thanks for the tip! I've downloaded 12.04 so Im gonna have a go at installing that. Would it work better if I upgraded to 12.10 from within 12.04?

12.10 is a development version not an LTS but if you are an experienced Linux user so try

---

### Post by TomInAZ on 2012-12-13
[B]Glad that I found this thread....

I  need some help getting Lubuntu to run on a MAC PowerPC Powerbook G4  laptop. Here are the specs: PPC 1.5Ghz, 12" screen, 1.25Gb Ram, 60Gb HD,  NVIDIA GeForce FX Go5200 with 64MB of DDR SDRAM.

Lubuntu 12.10 installs, but  glitches at the login screen. I can not see how to log in, and can not get to a  command prompt to try to fix it. I am a somewhat noob on Linux stuff, but am  willing to learn. After reading this thread I will try to install or run Lubuntu 12.04 as listed with the above settings. Also, I am assuming that this is the correct image to be using: [http://cdimages.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-desktop-powerpc.iso](http://cdimages.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-desktop-powerpc.iso)

At the moment I have Ubuntu 10.4 installed and is working fine for the most part. The fans are constantly running, and it didn't always do that on the early versions of OSX (10.3).

Honestly I just want  something that will be more efficient for my older Mac as I was running OSX 10.5.3, and it was SLOW and the hard drive was constantly running the swap file! 

Thanks to everyone who has helped the OP, hopefully it will get my system running. I really love this little MAC of mine (purchased in 2005), and am happy that it will still work well for me going forward. 
Tom
[/B]

---

### Post by TomInAZ on 2012-12-14
I did get Lubuntu 12.4 to install, but it seemed glitchie, and it was doing some constant freezing with the mouse, so I went back to Ubuntu 10.4.

---

### Post by mellac on 2012-12-16
hello there,

I am also new to this forum and to linux in general.
I am trying since several days to install Lubuntu 12.10 on my powerbook g4 12 (2005).
I have downloaded the 'live' iso.file, burnt the cd and restarted pressing 'C'
Everything seems to work but then it stops, saying:

* starting pbbuttonsd OK
* stopping anac(h)ronistic cron OK
* starting NTP server ntpd OK
* starting crash report submission daemon OK
* stopping System V runlevel compatibility OK
* Starting
* Starting
* Stopping

Is there anybody that could help me? what does it means?
I have tried to do also live-powerpc and even check (which resulted ok)

I would appreciate any suggestion, hint..

best,

Marcella

---

### Post by TomInAZ on 2012-12-16
> **mellac said:**
> hello there,

I am also new to this forum and to linux in general.
I am trying since several days to install Lubuntu 12.10 on my powerbook g4 12 (2005).
I have downloaded the 'live' iso.file, burnt the cd and restarted pressing 'C'
Everything seems to work but then it stops, saying:

* starting pbbuttonsd OK
* stopping anac(h)ronistic cron OK
* starting NTP server ntpd OK
* starting crash report submission daemon OK
* stopping System V runlevel compatibility OK
* Starting
* Starting
* Stopping

Is there anybody that could help me? what does it means?
I have tried to do also live-powerpc and even check (which resulted ok)

I would appreciate any suggestion, hint..

best,

Marcella
Marcella, try out Ubuntu 10.04 just for kicks. It runs much better at the moment than the other Live-CD you used. 

Also once you have 10.04 installed, go to System/Administration/Hardware Drivers and then install the Braodcom B43 driver to make your wireless work.

---

