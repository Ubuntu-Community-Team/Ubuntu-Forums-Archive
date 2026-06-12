---
title: "Motion Computing M1400, non-PAE"
date: 2013-12-28
forum: Any Other OS
---

### Post by mikeisme93 on 2013-12-28
Ok so i've been banking my head on the wall for a good week now trying to solve this problem, searched every forum and tutorial, all the youtube videos the internet has to offer it seems. its possible i have missed the information but i dunno. ok so heres the problem:

I have a Motion Computing M1400 which I decided to install UBUNTU on and did so with a roundabout method as the BIOS does not support USB boot. it does support cd and floppy boots but has neither a floppy drive nor a cd drive, it does however have two usb drives (one of which is used for the keyboard). Ok so it was over a year ago when i installed Ubuntu, so the version is 11.10? I dont know for certain. and if memory serves me right i believe i used plop (or a program similar to) in order to boot to my usb to install it. It has not worked since. It appeared to have installed OK but now it does not want to boot and i find myself in a pickle. Here is what it does:

Turn on: loads bios fine, get to grub2 menu fine, 
'ubuntu'
            black screen with white flashing underscore in top left corner. it hangs there forever, will not change
'advanced options for Ubuntu'
     'ubuntu, with linux 3.5.0-17-generic'
            Loading Linux 3.5.0-17-generic ...
            Loading initial ramdisk ...
            then it clears and all i see is that demented flashing underscore in the top left corner.
     'ubuntu, with linux 3.5.0-17-generic (recovery mode)'
            Loading Linux 3.5.0-17-generic ...
            Loading initial ramdisk ...
            Lots of really fast text eventually hanging with this being the last line:
            [    0.237707] pci 0000:00:1e.0: >  bridge window [mem 0x20000000-0x25ffffff pref]
            then i get that sinister flashing underscore.

ok so ive tried everything ive found suggesting on booting to the ubuntu command line in hope that i could figure something out from there but that was in vain.
from there i have tried to find a way to boot a live usb drive from the grub2 command line to no avail seeing as how i do not have access to the operating system on the computer.
i then searched far and wide for some sort of way to boot a usb drive without access to the operating system and without usb bios support and return with nothing. 

I'd like to figure this thing out since its a cool little thing when it works but right now im at a loss for what to do! Please help me!!

---

### Post by Jack_Mathews_Jr. on 2013-12-28
Here's a couple of links that may help. [http://debian.livejournal.com/346277.html](http://debian.livejournal.com/346277.html) and [http://wrexallen.blogspot.com/2010/05/ubuntu-1004-on-motion-computing-m1400.html](http://wrexallen.blogspot.com/2010/05/ubuntu-1004-on-motion-computing-m1400.html). The second seems to be the easiest.

---

### Post by Bucky Ball on 2013-12-28
Do you get a list of options to boot when you start the computer? If not, try hitting ESC or Shft and that should bring up a menu list to choose kernels from. The second one down should be the recovery kernel. Choose that. 

You should see a whole bunch of text and eventually get to a list of options. One of those allows you to drop to a root shell. Do so. Log in and then type:

```
startx
```

If that gives you nothing, try:

```
startlightdm
```

If you get that far, one of those commands should get you to a desktop. If it does not, please report back the error. Report back regardless of where you get to. ;)

PS: 11.10 is well out of support. End of life was April 2013 so you want to reinstall somehow anyway. How did you install it in the first place???

PPS: @Jack_Mathews_Jr.: Those links are very dated, but you never know, might get lucky ...

---

### Post by C.S.Cameron on 2013-12-28
Plop has worked great for me

[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

---

### Post by mikeisme93 on 2013-12-30
thanks jack, ive actually already found your second link and it has not helped me but ill use the first links advice and try to use my old hp to solve the problem, ill post back with my results.

bucky ball and c.s.cameron, you two did not read the original post.

---

### Post by mikeisme93 on 2013-12-30
ok thats a negative, as i had expected but it was still worth a try. the hard drive is not compatible with my old hp sooo im back to square one, how can i put anything on this hard drive?? is there anything i can do with the grub2 command line that could take information from USB?? Since this thing doesnt want to finish the boot process for ubuntu i basically have no operating system and i dont think that grub2 even supports booting to a usb or anything like that. is there any way to  trick it into thinking its a usb CD Drive?? would that even do any good?

OK I MAY HAVE FOUND SOMETHING BUT DONT KNOW WHAT TO DO WITH IT
int the grub2 CLI:
grub> chainloader (hd1)+1  

so im pretty sure hd1 is my flash drive because when i run that command the light on my flash drive flashes, but when i use "boot" it says no operating system found, its a live bootable flash drive do i need something else on it??

I keep updating this as i find things, so chainloader will basically switch me from the grub on my HD to grub onto hd1? is that right? thats how ive been reading its functionality, so from there, is there a way to put grub onto my flash drive and from there boot whatever OS i put on the flash drive?

---

### Post by mikeisme93 on 2013-12-30
PROGRESS!!
so i have a flash drive with bodhi linux on it made with unetbootin.

from GRUB2 CDI:

grub> set root=(hd1)
grub> chainloader +1
grub> boot

that brings me to the unetbootin screen but every option to boot into the live interface gives me a message stating the kernal requires features not present on the cpu: pae

---

### Post by mips on 2013-12-30
> **mikeisme93 said:**
> PROGRESS!!
that brings me to the unetbootin screen but every option to boot into the live interface gives me a message stating the kernal requires features not present on the cpu: pae

Ubuntu have decided to no longer provide non-pae kernels.

You can try and jump through these hoops to make it work,
[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

or switch to another distro that does have out of the box non-pae support.

---

### Post by mikeisme93 on 2013-12-30
ok ill probably end up trying those then if i have no success with android, (right now id like to just see this thing running again), I tried non-pae bodhi last night and it wasnt booting to the live session. i deleted the quiet splash and it seemed to be booting fine until it hung at the same line as in the original post. Could this be a hardware issue? or could it just be that my computer does not like ubuntu (bodhi being based on ubuntu)

UPDATE
nothing is working. Ive tried lubuntu, ubuntu again, bodhi, debian, puppy retro, and android for the m1400, nothing works. they ALL hang as soon as i try to boot the live session or hang if i try to install, except android. android loads the splash screen and gets to the unlock screen but at that point nothing works, the stylus doesnt work and i can do nothing with the keyboard or mouse, Im at a loss here i dont know what to do i read about people running linux on these (like debian, puppy, and bodhi), but i have zero luck on getting anything to run. This thing ran windows fine (well sort of, the keyboard would randomly give up on it) and now i cant seem to do doodoosquat with it. any suggestions?

---

### Post by mörgæs on 2013-12-30
Some boot options you could try with Bodhi:[URL="http://wrexallen.blogspot.com/2010/05/ubuntu-1004-on-motion-computing-m1400.html"]
http://wrexallen.blogspot.com/2010/05/ubuntu-1004-on-motion-computing-m1400.html[/URL]

---

### Post by mikeisme93 on 2013-12-30
that link was already posted. but i believe i figured it out and im shocked/slightly disappointed that nobody was able to provide the answers, hopefully somebody having my previous struggles can see this.

so i made a bodhi non-pae live usb drive

from grub2 cdi
> set root=(hd1) *****where hd1 is my flash drive
> chainloader +1
> boot

from there hit TAB and add this to the boot string (I added it right before quiet splash or whatever it is)
acpi=off

bam, easy as that, its sad that it took so long to figure that out buuuttt i got it, bodhi is installing right now.

---

### Post by fas000 on 2014-01-22
Hi Mike. Firtsly, Thanks about your info, it help me to install Bodhi in my Motion computing m1400, but even the stylus does not work. did you achieve it? How to?.. Thanks again.

---

