---
title: "Help with Ubuntu install on g4"
date: 2008-06-01
forum: Apple Hardware Users
---

### Post by hvc123 on 2008-06-01
Hey all,

i have a imac g4 1.25 20". 

its got a brand spanking new drive and i cant seem to boot the Ubuntu install disk yet my broken tiger disk boots but fails to install (it always has)

have i got to do something funky ? 

i have tried all the vulcan death grips at boot time i.e press c to boot cdrom justs gives a white screen for a few secs then it spits the cd out. however every now and again i can boot the CRUX cd. tried the o+F and reset firmware.


i only want to have Ubuntu on the g4 i dont want to dual boot...  


any suggestions ? 

thanks

---

### Post by hvc123 on 2008-06-02
any1 help ?

---

### Post by stream303 on 2008-06-02
I can suggest making sure that you burn the CD at a low speed (don't burn to CDRW), and burn it as an iso image, not just a copy.  I'd also use the "alternate" image to install from.

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Since you only want Ubuntu on it, when it comes time to guided partitioning, just let it "use the whole disk", and all the necessary partitions will be created and formatted for you automatically.  This of course wipes out your whole drive, so backup anything you need first.

---

### Post by hvc123 on 2008-06-02
ok thanks,,

the story goes like this....

i installed ubuntu from live cd ( i had OSX INSTALLED) i then did a complete install and used the entire disk for Ubuntu.
at boot nothing worked just a flashing ? and a face.

now the cd/dvd drive doesnt seem to recognise anything but my busted osx disk.(this doesnt complete install)

every now and then though i have a CRUX install disk that boots maybe 1 outa 10 times. 
the ubuntu cd does not boot at all anymore. i will grab a new image today and burn at 1 speed.

---

### Post by stream303 on 2008-06-02
Let us know which version of Ubuntu you eventually downloaded and are trying to install.

Did you jumper the new drive just like the oem apple drive?

Looks like your machine has an Nvidia card, which shouldn't present too many problems, although we might have to edit xorg.conf just a tad - guess we'll see what happens.

btw, if you still see the flashing icon at boot, can you hold down the alt/option key and see if you can manually highlight and choose the drive, and then click the right arrow?  (assuming you get this far)

I'm not sure if I've ever met anyone with a G4 iMac 20" running here so this will be interesting...

---

### Post by hvc123 on 2008-06-02
ok .. they original was the gutsy alternate ppc version. 

if i press the vulan death grip combos i can get to OF and when there the boot cd: does not work and when i press option all i get is a right arrow and a refresh arrow even when theres a cd in there 

i think its an ati card but im not sure

---

### Post by stream303 on 2008-06-02
Man, that's weird.  How are you doing the "C" key?  Are you holding it down and then powering up, or powering up and very quickly afterwards holding down the C key?  I've read of problem when holding down the c key before powering up before...

---

### Post by hvc123 on 2008-06-02
as the chime finishes i press and hold C 

if i do this on my CRUX install cd 1 outa 10 times it boots?
if i do this on Ubuntu install i got it to work only once and now it dont work.

i have tried al1 sorts of varieties of pressing C at and before power up and if i put the osx install disk in it works 100%

im baffled... 

i have the hardy version of ppc alternate disk i will burn at 1 speed and then try again tonight.

---

### Post by hvc123 on 2008-06-02
well at least i think its a 20" 

ill look at the label on the bottom 

its a dome shape g4 1.25 i know that and has 512mb ram 
to be honest i only want this for www samba shh services.

---

### Post by hvc123 on 2008-06-02
ok this time,

hardy alternate.
burned with cdrecord at 32 speed
boots from cd everytime
installing base system as i post this. the machine has an nvidia geforcee go5200

screen defo is 20 inch or my eyes are wonky..


ok its installed to a fashion.... hardy broke 50% when installing packages.. i skipped that and now i have a bootable powermac6.1 287 (apparantly)


instaalled ubuntu-desktop seem to fix any dependcy errors i had too  :D

i have a working apt so all is good so far

---

### Post by stream303 on 2008-06-02
> **hvc123 said:**
> screen defo is 20 inch or my eyes are wonky..

I have a 20" screen as well - If you go into System > Preferences > Screen Resolution, does it show 1680x1050?

Have you turned on subpixel-smoothing in System > Preferences > Appearance > Fonts ?

In the same tab, have you also gone into the Fonts > Details and changed your DPI to 98 ?  The default of 96 is close enough, but 98-99 is a bit more accurate for that size screen.

Since we're running an Nvidia card using the nv driver with an lcd, you may want to manually edit /etc/X11/xorg.conf to add a bit of screen dithering to make small details look a little bit better.   Here's a snippet from mine with the manually added addition:

```
Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:240:16:0"
        **Option          "FPDither" "true"**
EndSection
```

> ok its installed to a fashion.... hardy broke 50% when installing packages.. i skipped that and now i have a bootable powermac6.1 287 (apparantly)

Now that the updates have been moved to ports, have you checked your /etc/apt/sources.list file to make sure that the lines that used to point to archive.ubuntu.com now point to ports.ubuntu.com ?  If not, I'd go in and edit them and run sudo apt-get update afterwards.  Make sure that in the sources gui, that the options on the main page of System > Administration > Software Sources are UNchecked, and that the ones we want are now in the *third-party* repos.  Check out the Hardy release notes abouot half-way down the page for examples:

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

> i have a working apt so all is good so far

Oops. Maybe you don't need to do anything to your sources after all.  At any rate, glad to see it up and running.  That should make a nice machine for sure.

---

### Post by hvc123 on 2008-06-02
thanks for the tipss..

i cant check that stuff yet ubuntu-desktop is still installing (had to download everything 650mb)

i basically copied my sources.lst.apt-install to sources.lst

---

### Post by stream303 on 2008-06-02
hehe.  I did the same thing during the beta phase of Hardy. :)  Just look at it again after installation to be sure..

You might end up using it for more than just ssh. :)  The updates are vitally important to get the openssl / openssh updates after the recent openssl security issue..

---

### Post by hvc123 on 2008-06-02
my screen res says 1440x9?? something or other maybe i have a 17" screen.. 

its about 1 1/2 feet wide ( total plastic suface)

---

### Post by stream303 on 2008-06-02
Just measure it diagonally - if it turns out to be 17", then there's no need to change the dpi from the default of 96 unless you really want to.

---

### Post by hvc123 on 2008-06-03
hmm maybe my eyes are wonky... :p

i gotta say gnome looks a whole lot better on a mac screen.

i dont have the nvidia driver installed at the moment and the hardware drivers dont say i need anything... should i just install the new driver ? 

does look sweet tho. 

runs ok for a 1.25 though apparently as its a ppc it will perform a whole lot better than a 1.25 x86

---

### Post by stream303 on 2008-06-03
No proprietary video drivers for Nvidia PPC, so at this stage you're done!  Well, you could edit your /etc/X11/xorg.conf and try that Option "FPDither" "True" option.

Enjoy!

---

### Post by hvc123 on 2008-06-03
yer i put that on.. before i even ran startx 

so it looks so much better than my ubuntu x86

---

