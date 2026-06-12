---
title: "howto use Live CD/USB when no GUI appers"
date: 2012-12-02
forum: Apple Hardware Users
---

### Post by abtabt on 2012-12-02
hey have been active linux user about 20 year with various distro
and has for years had sometimes problems to use Live CD to work with GUI, some mac it works without problems
but with nvidia/ati cards, it becomes worse every distro upgrade,spec GeForce2 MX/MX 400   imac 700/800 ( ilamp )and some laptops have this card 
and the nouveau driver get ugly 8 bit desktop etc.

This is one way to get the GUI to work with framebuffer     tested  L/Ubuntu 12.04 ,12.10 ,13.04,14.04 (nvidia card )
                                                                                         tested  L/Ubuntu 12.04 (ati card )
start live CD and wait for the boot prompt and write

live video=offb:off nouveau.modeset=0 single      (nvidia card )
live video=offb:off radeon.modeset=0 single      (ati card )

each command with spaces

and wait one about 5 minutes until the CD stops and you write in the dark

code
modprobe nvidiafb mode_option=1024x768-16     (nvidia card  some time you need to do this in tty7  i need this in Lubuntu 14.04 daily build)
                                                                                                   (ctrl+alt and then F7 )

modprobe aty128fb mode_option=1024x768-16     (ati card )

then the CLI  works if not retry .

code
Xorg-configure

  give you a xorg.conf if you need one later

code
start lightdm

and you have hopefully a working live CD/USB


a couple of things that can be helpful to know at least in my case


with an IMAC G4 Globe 800 WITH Live cd

*-display
             description: VGA compatible controller
             product: NV11 [GeForce2 MX/MX 400]
             vendor: NVIDIA Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=nvidiafb latency=248 maxlatency=1 mingnt=5
             resources: irq:48 memory:91000000-91ffffff memory:98000000-9fffffff memory:90000000-9000ffff

 
Lubuntu 12.04 and 12.10 cant i get working with toram

live video=offb:off nouveau.modeset=0 toram single

Ubuntu 12.04 it works with toram but you need to have
like 768 MB of RAM and swap active

Sound works
Suspend works
and this is a simpler driver for nivida card (nvidiafb)

one way too adjust swappiness default 60
 
sudo sysctl -w vm.swappiness=1   (1-10 for CPU with less power )

to check
cat /proc/sys/vm/swappiness



mode_option=1024x768-16

can be other values

and you can use the code when its installed on hd with some changes

hope it helps someone

Persistent Live USB
and Live USB have been used with succsess Lubuntu 13.04
edit and now 14.04 on a extern FW


and dont forget read
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

edit even 13.04 works on this old iLAMP

edit now 14.04 works on this old iLAMP and zram is used  (need to be in tty7 to get modprobe nvidiafb mode_option=1024x768-16 to work then good 
GUI work )

16 12 2014
edit i use mate cd [https://plus.google.com/111285327879595317710/posts/2dTTB6qBHrA](https://plus.google.com/111285327879595317710/posts/2dTTB6qBHrA) for a test ,works good i use nvidiafb driver
on a imac 700/800 with  Persistent Live FW   (its fast with FW disk )
so 14.04.1 works ok for a old Mac

---

### Post by este.el.paz on 2012-12-04
Mr abtabt:

Just following you over here on this thread, thanks for posting this information . . . and, question--do you have Lubuntu 12.10 running on your iMac 800, no problem, but having to install the retro driver for nv as per the 12.04??

Also, I personally am not understanding "toram" . . . whatever that is . . . I think on my iMac 8 I might have 612 MB of RAM???  so that might explain what? why suspend might not work?  I'm still trying various ways to "clean" the system for any problems remaining from the series of KPs, and interestingly as I mentioned in my "analyze" thread, the instructions given for booting the liveDVD worked the first time I tried, but no longer work for booting DVD . . . it just goes to end of the "boot elf32" CLI stuff and hangs there . . . .

e.e.p.

---

### Post by abtabt on 2012-12-05
> **este.el.paz said:**
> Mr abtabt:

Just following you over here on this thread, thanks for posting this information . . . and, question--do you have Lubuntu 12.10 running on your iMac 800, no problem, but having to install the retro driver for nv as per the 12.04??

Also, I personally am not understanding "toram" . . . whatever that is . . . I think on my iMac 8 I might have 612 MB of RAM???  so that might explain what? why suspend might not work?  I'm still trying various ways to "clean" the system for any problems remaining from the series of KPs, and interestingly as I mentioned in my "analyze" thread, the instructions given for booting the liveDVD worked the first time I tried, but no longer work for booting DVD . . . it just goes to end of the "boot elf32" CLI stuff and hangs there . . . .

e.e.p.

1. no install on imac 800 12.10 only use live cd and its boot and can be
used surfing , etc i use the fbdev driver i have not tried nv ,the system need to be on the harddrive 

2. only ubuntu 12.04 work toram its snappier (firefox )with more ram 
its better

3. DVD and CD is not the same, CD can work but not DVD download and try
   burn with slow speed 

4.suspend works on mine with live cd (i use fbdev with live and nv with 
 Lubuntu 12.04 on the hard drive 

i stick with 12.04 (safer)

5. toram means that you can use cd/dvd drive after boot and the files for live cd is in RAM

---

### Post by abtabt on 2013-06-28
updated

---

### Post by abtabt on 2014-04-07
updated Lubuntu 14.04

---

### Post by este.el.paz on 2014-04-10
> **abtabt said:**
> updated Lubuntu 14.04

@abtabt:

I think we have the same machine, 800 iMac, just posting this over here on this thread since it possibly relates . . . in daily build 3/28 of Lu 14.04 I can boot the LiveDVD into a low resolution screen using "live nouveau.modeset=0" . . . .  

But when I try to follow your instructions to change the module to "nvidiafb" or "rivafb" with the "mode_option whatever 1024x768" the screen doesn't recover from the black screen.

I've tried reading through the known issues and troubleshooting pages, so far nothing presents itself--I'd like to test out the Live DVD before doing an install and changing xorg.conf file.  Any way to boot into a higher resolution GUI?

e.e.p.

---

### Post by abtabt on 2014-04-12
> **este.el.paz said:**
> @abtabt:

I think we have the same machine, 800 iMac, just posting this over here on this thread since it possibly relates . . . in daily build 3/28 of Lu 14.04 I can boot the LiveDVD into a low resolution screen using "live nouveau.modeset=0" . . . .  

But when I try to follow your instructions to change the module to "nvidiafb" or "rivafb" with the "mode_option whatever 1024x768" the screen doesn't recover from the black screen.

I've tried reading through the known issues and troubleshooting pages, so far nothing presents itself--I'd like to test out the Live DVD before doing an install and changing xorg.conf file.  Any way to boot into a higher resolution GUI?

e.e.p.

i have see some trubble with 14.04 live dvd but i use Persistent Live USB and FW disk its easy to change and save for later boot (its like a install on the harddrive)
and i have a install on hd too but its need some tweak like blacklist etc 

> **este.el.paz said:**
> @abtabt:

I think we have the same machine, 800 iMac, just posting this over here on this thread since it possibly relates . . . in daily build 3/28 of Lu 14.04 I can boot the LiveDVD into a low resolution screen using "live nouveau.modeset=0" . . . .  

e.e.p.

if you do in Terminal its show the hardware etc

lshw

 
if you get low resolution screen then open LXterminal if you have black background and the text is good then its possible to get good locking GUI (nvidiafb driver in use 32mb ram)
But if you have uggly background and uggly text when open LXterminal then you have nouvau driver active and thats the trubble like 1mb videoram

so whats need to do 
nouvau driver must be removed 
nvidiafb must be load with option like 1024x768-16
its tricky but i have tree system Persistent Live USB with GUI and real Install on extern FW disk with GUI and offcourse on intern HD but i think FW is faster or same then the intern drive

so try Persistent Live USB/FW no need to wipe our HD

have a nice day

---

### Post by este.el.paz on 2014-04-12
@abtabt:

Thanks for the reply . . . yeah, it seems like the DVD is having "issues" . . . maybe when I get a few minutes I'll try to get a fresh .iso and move it into a USB drive and see how that works . . . .

e.e.p.

---

### Post by abtabt on 2014-04-14
first post updated more 14.04 info 

e.e.p. 
this make the live cd work every time (tty7)
suspend works
need to login with lubuntu and no password needs

can you post your 

lshw

---

### Post by este.el.paz on 2014-04-14
> **abtabt said:**
> first post updated more 14.04 info 

e.e.p. 
this make the live cd work every time (tty7)
suspend works
need to login with lubuntu and no password needs

can you post your 

lshw

abtabt:

Read your notes, thanks for following up on the details . . . probably be 24 hours before I can check the iMac . . . and get back to you.

e.e.p.

---

### Post by este.el.paz on 2014-04-15
> e.e.p. 
this make the live cd work every time (tty7)
suspend works
need to login with lubuntu and no password needs

can you post your lshw


@abtabt:

Spent about 1.5 hours this AM trying to get the liveDVD GUI into nvidiafb . . . so far the best I can do is low resolution screen.  If I try the "live nouveau.modeset=0" boot params I can get into a fuzzy screen, and same for LXTerminal.  If I do the "video=off single" thing, it doesn't recover.  One of the problems is that using the same commands does not replicate in results, very irritating.  In my computer trying the fn+ctrl+alt+f7 . . . is the "exit from shell command" . . . so using f3 or f4 got me from the black video off screen into a small flashing boot prompt at top left.  Then typing the "modprobe nvidiafb . . . ." nothing happens.  If I don't use the f3 option I get a single user CLI and when I type the "modprobe stuff" I get error "cannot request PCI regions" . . . I tried many different times.  Finally I typed "start lightdm" and we're back in the low resolution screen.  I launched LXTerminal and ran "sudo lshw" . . . and it provides a loong document.

Do you want me to post the whole "lshw" readout?  Or just the "Display" as you have listed in your first post here?  In 12.04 LibreOffice I don't seem to have .tar or .zip options, just odt txt and the usual.  I'll paste the "display" stuff here, let me know if you want the whole deal, I might have to try it in LM16 to see if I can get it compressed:
   *-display UNCLAIMED
             description: VGA compatible controller
             product: NV11 [GeForce2 MX/MX 400]
             vendor: NVIDIA Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
             configuration: latency=248 maxlatency=1 mingnt=5
             resources: memory:91000000-91ffffff memory:98000000-9fffffff memory:90000000-9000ffff
     *-pci:1

e.e.p.

---

### Post by abtabt on 2014-04-16
take all in lshw use 

sudo lshw 

then copy and past and save with leafpad and add .txt and upload etc

and only click on the file and open with leafpad 

in this boot have i use live cd 14.04 with live-nosplash choice in yaboot and this GUI is better then the  other way
terminal,Firefox,leafpad, etc is useful not so uggly

if you use 
live video=offb:off nomodeset single                  
 when network ready and cd is not spinning
the try to toggle ctrl+alt  F1 and F7      (not F2 -F6)
and type modprobe nvidiafb mode_option=1024x768-16  enter buttom each time (and when you get CLI then ctrl+alt  F1 and sudo start lightdm if you get a black arrow then its nvidiafb working, with right xorg.conf you can get god GUI

---

### Post by este.el.paz on 2014-04-16
@abtabt:

Thanks for your patience and your help.  I did take a quick look at your "lshw" . . . looks similar except I have a bunch more "volumes" because I did the "install OS9 drivers option" . . . but really the computer doesn't seem to be able to find OS9 anymore.

Anyway, not so much time today, I booted into 12.04 and opened the file I saved from running the "lshw" command yesterday while booted up in the LiveDVD . . . and I pasted it into a Leafpad doc, . . . added .txt to the file name . . . hope that works.

e.e.p.

---

### Post by abtabt on 2014-04-17
you have a wifi card it can be the thing with 
Suspend not working

---

### Post by este.el.paz on 2014-04-17
> **abtabt said:**
> you have a wifi card it can be the thing with 
Suspend not working

Ah . . . so interesting . . . it's funny how these things can create issues . . . thanks for that thought . . . guess I'll give up on Suspend being a part of my iMac's linux experience . . . .  Still not equipped to break open the computer and rip the wifi card out . . . maybe someday . . . .  

e.e.p.

---

### Post by abtabt on 2014-04-18
> **este.el.paz said:**
> Ah . . . so interesting . . . it's funny how these things can create issues . . . thanks for that thought . . . guess I'll give up on Suspend being a part of my iMac's linux experience . . . .  Still not equipped to break open the computer and rip the wifi card out . . . maybe someday . . . .  

e.e.p.

its easy to do see

and for more 
[http://www.xlr8yourmac.com/systems/imac_g4/imacg4_takeapart.html](http://www.xlr8yourmac.com/systems/imac_g4/imacg4_takeapart.html)

---

### Post by este.el.paz on 2014-04-18
@abtabt:

Thanks for those links and pictures . . . just need the tools . . . have to see how it goes with 14.04 . . . if it just gets run off usb flash drive or if full install; unfortunately it seems like the FW ports on the iMac have departed from function . . . can't get to my ext HD with it . . . .  No worries.  But, like I mentioned in my thread, I did again try this multiple "modprobe" technique . . . each time was different in terms of showing prompt, still when I tried to do ***exactly*** as you suggested it brought me to ugly GUI . . . and lshw still not showing "nvidia" . . . .  I'm going to try the full release version, next.

e.e.p.

---

