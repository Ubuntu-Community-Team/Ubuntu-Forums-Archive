---
title: "Disgusted already...how do I uninstall Dapper?"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by JGKC9AYC on 2006-06-01
It took XP off my grub.menu.ist, I have no audio & a blank screen after the bootup (as well as pcmcia failing duriing startup).
How can I uninstall & try again?
Thanks.

---

### Post by adwait on 2006-06-01
format the partition and install again.

---

### Post by nalmeth on 2006-06-02
How did you have GRUB list in the first place? Another distro?

What do you mean blank screen. Did you get a command prompt? Or literally a blank screen with which you could do nothing?

---

### Post by JGKC9AYC on 2006-06-02
[QUOTE=nalmeth]How did you have GRUB list in the first place? Another distro?

What do you mean blank screen. Did you get a command prompt? Or literally a blank screen with which you could do nothing?[/QUOTE]

I previously had Breezy installed.
Literally a blank screen with which I could do nothing.

---

### Post by xtentual on 2006-06-02
I'm having the exact same problem, I updated from Breezy, follwing the wiki to a T, and all seemed to be working fine....until I rebooted.

If I select kernel 2.6.15-23-386 it goes to the ubuntu loading screen...loads all the modules then acts as if it is gong to boot up...then just a blank screen, no hdd activity...nothing

if i select the next kernel down 2.6.12-10(maybe dunno the numbers to be exact)
it boots fine...but i have no sound device installed...which worked fine in breezy.

any suggestions?

---

### Post by gingermark on 2006-06-02
[QUOTE=xtentual]I'm having the exact same problem, I updated from Breezy, follwing the wiki to a T, and all seemed to be working fine....until I rebooted.

If I select kernel 2.6.15-23-386 it goes to the ubuntu loading screen...loads all the modules then acts as if it is gong to boot up...then just a blank screen, no hdd activity...nothing

if i select the next kernel down 2.6.12-10(maybe dunno the numbers to be exact)
it boots fine...but i have no sound device installed...which worked fine in breezy.

any suggestions?[/QUOTE]

Are you by chance using the official NVIDIA drivers downloaded from their site? If so, you need to reinstall them for every significant kernel change. (you asked for suggestions :))

---

### Post by unicycler on 2006-06-02
Can you ssh to it from another machine?

---

### Post by Bender NZ on 2006-06-02
[QUOTE=xtentual]I'm having the exact same problem, I updated from Breezy, follwing the wiki to a T, and all seemed to be working fine....until I rebooted.

If I select kernel 2.6.15-23-386 it goes to the ubuntu loading screen...loads all the modules then acts as if it is gong to boot up...then just a blank screen, no hdd activity...nothing

if i select the next kernel down 2.6.12-10(maybe dunno the numbers to be exact)
it boots fine...but i have no sound device installed...which worked fine in breezy.

any suggestions?[/QUOTE]

I'm seeing a similar problem - I was installing a new server today (fresh install), everything installed fine and it rebooted and grabbed the packages, updated the kernel (2.6.15 i386) and then when it rebooted it would load the kernel and then sit and do nothing.

The only way I can get it to boot is with 2.6.12. I tried installing the 2.6.15 i686 version but that didn't get me anywhere either.

I've seen this on two other servers last week too - but I can't really find any decent info to file a bug report because it just hangs :/

---

### Post by xtentual on 2006-06-02
[QUOTE=gingermark]Are you by chance using the official NVIDIA drivers downloaded from their site? If so, you need to reinstall them for every significant kernel change. (you asked for suggestions :))[/QUOTE]

nope, ati card, and not using their driver either. 

not only did i try the upgrade and it not work, i dled the iso, installed it and same exact thing after doing a clean install. so much for dapper being an upgrade...breezy worked better 

substance over style

---

### Post by dvarsam on 2006-06-02
[QUOTE=xtentual]nope, ati card, and not using their driver either. 

not only did i try the upgrade and it not work, i dled the iso, installed it and same exact thing after doing a clean install. so much for dapper being an upgrade...breezy worked better.[/QUOTE]

Can you give us some full specs;

Like Mobos, Graphichs Cards, Memory, etc.?

Thanks.

---

### Post by christhemonkey on 2006-06-02
You say you can do nothing at all?

Dont mean to patronise, but have you tried pressing Ctrl+Alt+F2?
(or any F number between one and six)

---

### Post by xtentual on 2006-06-02
A64 3200+ 
In Asus K8V SE Deluxe
1gb PC3200
300gb 7200 rpm 16mb cache s-ata
ATI X850 pro
Lite-on 16x dvd+/-rw
Audigy 2 w/firewire

---

### Post by xtentual on 2006-06-02
[QUOTE=christhemonkey]You say you can do nothing at all?

Dont mean to patronise, but have you tried pressing Ctrl+Alt+F2?
(or any F number between one and six)[/QUOTE]

just rebooted to try that, none of those key combination do anything at all either, was worth a shot though.

I guess it's back to breezy till a more stable release is out. :(

---

### Post by tonto on 2006-06-05
I have the same problem with this release. I havent even try the other versions since I waited for this "final".

I can boot cd fine (well it takes about one minute to mount ntfs at the beginning...) but when I am supposed to login I cant see anything. I mean there is only blank brown screen with moveable mouse cursor. It happens with both normal and safe option from start.
I have even checked the media and it's fine.

My specs:

P4 3.2 Ghz
P4C800-E Deluxe mobo (incl. sound, network, firewire)
Ati 9800 pro.


Anything I can at least try cause I can act like a monkey even if I dont know too much about comand line in linux?


Btw, seems to me that the system isn't actually halted cause If I shut down computer from power button then Ubuntu starts putting some text again on the screen and stells me to remove cd and press ENTER. After that it shuts down just fine. So the problem is somewhere in login screen.

---

### Post by coolclassic on 2006-06-05
I had the same problem but as I had upgraded the kernel at the same time as the upgrade I needed to reinstall the graphics driver.

You can try editing your xorg.conf and edit the driver it uses i.e.
for nvidia chage to nv for a basic driver.

ati I don't know

---

### Post by tonto on 2006-06-05
Well after reading some other posts I also tried some solutions mentioned there.
So I unplugged all my usb-devices (also changed back to ps/2 keyboard) and disabled legacy usb from bios. I also unplugged my ethernet cable.

None of these seems to work for me. Mine also hangs for one minute in mounting file systems, but always continues after that. But my booting always ends at the same part 'running local boot scripts (/etc/rc.local)' .I have now waited looong time if it would eventually continue after that but no luck.



Well, just out of curiosity I also tried new Kubuntu desktop-cd and guess what? Zero problems!
It also mounted my filesystems about one minute but after that loads up just fine and gives me nice looking desktop (and not the login screen what I thought it should show earlier with Ubuntu...).

What's going on? I thought that these distros are almost identical? And yes, I have checked my Ubuntu cd and there is nothing wrong with that.

---

### Post by JGKC9AYC on 2006-06-07
Ok...i'm getting fed up here.  I get a blank screen when I boot because there seems to be an issue w/ATI cards.
Here's what I got when I go into the partition table during setup:

#1 Primary  60.3 GB     B     NTFS
#2 Primary    1.1 GB     F     Swap     Swap
#3 Primary  56.2 GB            EXT3
#5 Logical    2.4 GB      F     Swap     Swap

I'm definitely not deleting my NTFS.  Do I delete the other 3?  If so, what's the next step?
Thanks.

---

### Post by dmizer on 2006-06-07
delete these, and retry the install with some boot switches like noapic or the like.
[QUOTE=JGKC9AYC]#2 Primary    1.1 GB     F     Swap     Swap
#3 Primary  56.2 GB            EXT3
#5 Logical    2.4 GB      F     Swap     Swap[/QUOTE]
did you do an expert install?  there should not be two swap partitions.  i don't think it would cause a problem, but 3.5gig of swap is way overkill.

---

### Post by JGKC9AYC on 2006-06-08
[QUOTE=dmizer]delete these, and retry the install with some boot switches like noapic or the like.

did you do an expert install?  there should not be two swap partitions.  i don't think it would cause a problem, but 3.5gig of swap is way overkill.[/QUOTE]

I don't know why there were 2 swap partitions...i'm a newbie...hehehe.
Will the install program automatically reconize that grub's on here?

---

### Post by jnorth on 2006-06-08
[QUOTE=xtentual]A64 3200+ 
In Asus K8V SE Deluxe
1gb PC3200
300gb 7200 rpm 16mb cache s-ata
ATI X850 pro
Lite-on 16x dvd+/-rw
Audigy 2 w/firewire[/QUOTE]


I've had problems with Dapper and my ATI card doing the same thing.  I still have no sound in Dapper, but this might help figure out where some of the fault lies.  On my box, (Radeon 9250) as soon as X began to start, I got a blank screen, and no reaction from keyboard, etc (and no, killing X didn't work either, complete lockup.)
I rebooted in 'safe mode' to the shell, and edited my xorg.conf to go back to the 'universal' (mesa) display driver, and then rebooted.  If you aren;'t sure what you're editing, just run a "sudo dpkg-reconfigure xserver-xorg" and go with the bare minimum, using that same driver.
That brought my system back up to a basic display, proving for me that it was an X/display driver issue.  I was then able to search around and find the oddities of using my particular card and eventually got it back up to using the proprietary driver and full 3d accel again.

Not expert opinion by any means but $.02 worth from an X (& Ubuntu) beginner.  (Teethed on Debian/Gentoo server environments)

---

### Post by dmizer on 2006-06-09
[QUOTE=JGKC9AYC]I don't know why there were 2 swap partitions...i'm a newbie...hehehe.
Will the install program automatically reconize that grub's on here?[/QUOTE]
the #5 swap partition is probably a remnant of your old install, but it's difficult to tell for sure.

i have no idea about if it will detect grub or not because i don't dual boot, but off hand i'm like to say ... no, because i've seen many people posting with problems in their grub after installing ubuntu.

do a search here in the forums for something like "lost grub" or the like.

but i strongly suggest doing a bit of research about installing for dual boot alongside other linux distro's because it will save you a bit of headache.

of course your alternative is just to let ubuntu install grub the way it wants, and then go back in and add windows to your boot opitons.  it's not that hard to make that kind of change to grub.

---

