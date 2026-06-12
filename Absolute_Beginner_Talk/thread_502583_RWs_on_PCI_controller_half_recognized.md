---
title: "RWs on PCI controller half recognized"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by TeaSwigger on 2007-07-16
Hello all, :)

Being deliriously delighted with Kubuntu on my first PC (completely trouble-free and great performance!) I'm installing it on my 2nd box, dual-boot w/XP. So much for luck; having plenty of probs. Many I've solved thanks to searching this forum, but I could use some help with the few left. Here's the situ:

PC - old Dell 2350 Celeron. Motherboard's secondary IDE went south, so it's now running this way:

mb's Primary IDE - 2 hard drives. No issues.
PCI IDE ATA/133 controller card, Primary IDE - 2 DVD-RW. No issues in XP. Only 1 of the drives recognized in Kubuntu (does run the 1 recognized drive).

...where to from here?

---

### Post by DBStevens on 2007-07-16
Would you please post the output from dmesg, lspci -nnvv, and lsmod.

---

### Post by TeaSwigger on 2007-07-17
Certainly, DBStevens -

20kb dmsg, so had to zip it:
[ATTACH]38421[/ATTACH]

lspci -nnvv
[ATTACH]38419[/ATTACH]

lsmod
[ATTACH]38420[/ATTACH]

Interest appreciated :)

---

### Post by TeaSwigger on 2007-07-17
...Just wondering if I shoulda plopped this into the beginner forum or a more advanced one eh heh 8-[

---

### Post by DBStevens on 2007-07-17
Could you provide make and model numbers of the two r/w optical devices on your sil controller and when you do that could you verify the jumpers and swap the ide cable end at the drives and let me know if the working drive changes.

I'm finding references to this problem that point towards a particular driver. 

Normally it manifests as a drive time out at boot and a real slow boot up, but that isn't always the case.

---

### Post by TeaSwigger on 2007-07-18
Certainly:

(1) (master) - Optiarc AD-7170A
(2) (slave) - Hi-Val HDVDRW4D (rebranded Accutek DD0203 afaik, identified as Generic DVD-RW to XP)

In case it helps:
Rosewill 208 PCI ATA/133 Controller (Silicon Image SiI 0680)

Box is otherwise 'stock':
Intel 845GL chipset
Intel 82845G/GL/GL/PE/GV integrated AGP graphics
Integrated AC97 audio

Switched positions and jumpers on the IDE cable, producing this layout:
(1)(master) - Hi-Val
(2)(slave) - Optiarc

Result: both drives work! However, while both appear to be reading data fine as far as I could tell, the titles of my test discs do not display on Konqueror's title bars when used in the former no-show (1 master Hi-Val), while behavior is as expected in the other (2 slave Optiarc). I don't know if this is a drive difference and leave well enough alone, or suggestive that some sort of underlying problem remains that should be solved.

All still works ok XP-side. The Kubuntu boot/shutdown is slow and problematic and performance less than super; one thing I've had to do is to specify 'nosplash' on boot as a (successful) work-around until I can figure out that boot issue. Hadn't assumed it was related. Might be a 'two birds with one stone' case?

Again, interest appreciated :)

---

### Post by DBStevens on 2007-07-18
Interesting by any chance was the cable loose or is it possible that you are using a 40 conductor instead of an 80 conductor IDE cable?   That Optiarc (Sony-NEC) device really should be on an IDE channel using an 80 conductor cable as it can operate in UDMA mode 4.   Operation on a 40 conductor IDE cable can be a bit problematic.

I can't speak to Konqueror's actions.

---

### Post by TeaSwigger on 2007-07-18
DBStevens, I checked the IDE cable and yes it does happen to be a 40 conductor! I can go out tomorrow and see if the store nearby has an 80 conductor. Then I'll test its behavior and report the findings. :)

---

### Post by TeaSwigger on 2007-07-21
The next time I booted by the by, that 2nd "generic" drive disappeared in kubuntu again. :(

Welp finally got my hands on an 80 connector IDE cable - had to buy one online. Yeah it's a great, great place to live out here but really, really sad in that way lol

Configurations tried:

1)
(IDE 1 master) Optiarc
(IDE 2 slave) generic
2)
(IDE 2 slave) Optiarc
(IDE 1 master) generic

Result: Same as before.

XP - All's well. Optiarc is at DMA mode 4 now, generic at mode 2.
Kubuntu - Optiarc detected and working, generic no-show.

:confused:

---

### Post by DBStevens on 2007-07-21
Them's the breaks I guess, still getting the same messages in dmesg?

I'll bet the Optiarc is happier, I'll poke around a bit more but right now I haven't much to latch a hold of, if the power cable isn't plugged in tight things could be funny.  

I had problems with one of my IDE drives untill I did a minor adjustment to the power connector and it manifested in the drive being there and then not.

---

### Post by TeaSwigger on 2007-07-22
Well the rules mention being persistant, so I'm abiding by 'em ;) 

Thought I'd toss in another try. I checked BIOS; all drives are listed in correct manner. Unfortunately fussing about with the power connectors etc didn't change anything. 

Things being as they are, thought I'd try "restoring" the PC to essentially "stock" config. Removed the 2nd hd (just use it for excess storage in XP anyways) and removed the PCI IDE Controller card, restoring the 2 opticals to the motherboard's secondary IDE channel (but with new 80 cond. IDE cable). Result: exactly the same! Good thing I'd been given the PCI card free, as it looks like it never needed it, only an 80-cond IDE cable. Everything listed in BIOS. Everything working in XP. Only one optical in kubuntu. 

And then I plugged in my scanner and printer. HP Scanjet 5370c and DeskJet 932c (boy were those good units). Everything worked on XP. Kubuntu is playing ball with the printer, but doesn't even seem to detect anything on the USB circuit, let alone operate it. At various times I use the PC to scan, print, websurf, email and burn my music; so far kubuntu is ranking half-par on all fronts: no USB scanner, yes printer, no email, yes websurf, one of 2 drives detected. Oh and a slowish non-graphical boot only. Arr.

In case anyone made it this far (hehe) and is inclined to take a peek, here is the dmesg taken at the prompt on a safe-mode bootup, with the above configuration: 1 hd in dual-boot w/XP, 1 Optiarc DVD-RW, 1 'generic' DVD-RW, 1 HP Scanjet scanner (USB), 1 HP Deskjet printer (parallel). I have no idea if the safe mode selection matters for this, but figured I might as well try things differently.

dmesg
[ATTACH]38798[/ATTACH]

---

### Post by DBStevens on 2007-07-22
I have the same issue with my USB scanner, it is supposedly a kernel option issue,  some folks have been able to work around it, the work around doesn't work for me and I haven't done a custom kernel under Ubuntu yet.  Done more than a few for other distros.  

I have a boot option you might want to try, add this:

pci=routeirq

after the ro on the kernel line when you get the grub menu at boot time.

What is your email issue?

---

### Post by TeaSwigger on 2007-07-28
DBStevens, I'm tackling the email issue in another post:
[http://ubuntuforums.org/showthread.php?t=506574](http://ubuntuforums.org/showthread.php?t=506574)
Thanks for the kind interest :)

I was able to get back on last night and try your boot suggestion. It did seem to help speed the sluggish boot. I still had to go back to using 'nosplash' as well, however as it would still hang up with the splash on.

Re: the optical drives; I switched the "generic" DVD-RW for an old CDRW I had sitting around, and while it failed to install the CDRW on its own, it was detected and is running, thus I was able to 'manually' mount it. A bit messily but I'm working on that ;) While this will do for the time being I'm no wizer as to the root of the problem.

Subsequently I installed Xubuntu instead of Kubuntu on this second PC, in hopes it would be a bit snappier. It is. I'll still use Kubuntu on my 'primary' PC but go with Xubuntu on this second PC. Fine OS in its own right, Xubuntu. Both the boot and the optical drive situation are the same with the fresh Xubuntu install.

Might come back to this, but unless anyone has some ideas occur I'll leave things as is for now and get to frying the other fish.

---

