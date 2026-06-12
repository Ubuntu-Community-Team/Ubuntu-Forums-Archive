---
title: "I can't boot back into OS X 10.5 - Please Help"
date: 2008-03-26
forum: Apple Intel Users
---

### Post by Trebla Nietsnie on 2008-03-26
Ubuntu boots up fine, I can see my Mac partition and files in Ubuntu. I have tried to use the apple install cd (10.5) but it wont work. I have also tried holding down option key but that does not work. Im running one of the older intel imac (white).

Can someone please help me boot back into OS X.


Thanks [http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

### Post by mrsteveman1 on 2008-03-26
Do you perhaps own one of the new Aluminum keyboards from apple?

Startup keys (option, single user, boot cd, target disk) don't work with this keyboard and some macs.

If thats not the case, can you get any of the other option keys to work?

---

### Post by Trebla Nietsnie on 2008-03-26
Good point .... I will dig out the old keybord ... i tried the option key with the old keybord but no luck it just goes to the grub stage 2 thing .... it is the option key isn't it?

---

### Post by teryowen on 2008-03-26
Is it that you see grub and press OS X and it says not there
or is it that you see grub click on OS X and you see apple doing something but it doesnt boot up?

---

### Post by Trebla Nietsnie on 2008-03-26
not quite on startup there is white screen for about 2-3secs then black screen then it says grub 2 and a few other things in white with a black background then it goes to ubuntu home/start screen

---

### Post by teryowen on 2008-03-26
hmm do you see a menu?
if not press escape a menu will show up with options see if there is an option for OS X
that is press it while you see white with black background just before it goes into ubuntu

---

### Post by Trebla Nietsnie on 2008-03-26
No OS X :( there is 3 lots of Ubuntu one says generic one says (recovery mode) and the other says memtest86+

the weird thing it that i can see all the files in ubuntu from the osx opartition so it's not lost or formated :)

---

### Post by teryowen on 2008-03-26
alright so lets add an entry for OS X

Go to ubuntu and paste the out put of the following when you type it in terminal:

```
sudo fdisk -l
```
and
```
cat /boot/grub/device.map
```

After looking at this we will add an entry to the menu.lst file so that you can boot into OS X

---

### Post by jakejackjacob on 2008-03-26
I am by no means an expert, and I doubt this would be a permanent fix, but try booting from the OSX disc by holding down "c" (rather than option). Then once you get into the OSX installer, go to utilities and select a different startup disk, then restart.

That should at least get you into OSX... from which you may be able to fix things.

<>< Jack

---

### Post by Trebla Nietsnie on 2008-03-26
ok it has a list of commands about fdisk and other things about partitions

---

### Post by teryowen on 2008-03-26
can you paste the output so that we can add an entry for OS X

---

### Post by Trebla Nietsnie on 2008-03-26
im sorry but im not sure what you mean im a noob at Ubuntu  im using my laptop now to type this so i cant copy the terminal info but i can make a copy for you if you like .... sorry if im being difficult

---

### Post by teryowen on 2008-03-26
ok basically i need to know on what hard drive and on what partition the OS X is on.

so when you type: sudo fdisk -l look for one that has HFS (i believe that the mac partition) and tell me the device

now when  you do the cat /boot/grub/device.map
i only need this if you have multiple hard drives otherwise forget about it.
if you do have multiple hard drives just type it out

anyways tell me on what device that HFS partition is on, so some thing like /dev/sdaX where X is a number or it can be /dev/hdaX or /dev/hdbX, either way just tell me the device

---

### Post by Trebla Nietsnie on 2008-03-26
ok 

of all of them (4) the largenst is OSX that reads 

Device:         /dev/sda2
Boot:            *
Start             26
End               16116
Blocks            12924228
id                   af
System         Unknown

the other 3 drives are EfI GPT, Linux and Linux swap / Solaris

---

### Post by teryowen on 2008-03-26
ok great, now on the ubuntu do the following in terminal:

```
gksudo gedit /boot/grub/menu.lst
```

now you will be editting the file to add an entry for OS X (it similar to note pad)

add these lines to the end of it

```
title Mac OS X
root (hd0,1)
chainloader +1
```

additionally look for a word "hiddenmenu"

make sure that its commented out
so if you see: 
hiddenmenu
chaneg it to
# hiddenmenu

and now save.

Now when you boot up there should be an option to boot into ubuntu (3 options actually) and 1 for OS X, hope this works.

---

### Post by Trebla Nietsnie on 2008-03-26
no luck the text edit thing was blank so i typed it in as you said and saved rebooted .... white screen then black then i pressed esc and  just the same options as last time all ubuntu

---

### Post by teryowen on 2008-03-26
very odd, are you sure you spelt it correctly when you type the thing for the text edit:

gksudo gedit /boot/grub/menu.lst

---

### Post by Trebla Nietsnie on 2008-03-26
i had a 1 at the . part not a l this looks better lots of stuff in this file

---

### Post by teryowen on 2008-03-26
Awesome so try what i said and see if it works.

---

### Post by Trebla Nietsnie on 2008-03-26
Well it says Mac OS X but when i select it it says Error 13: Invalid or Unsupported executable format

---

### Post by mrsteveman1 on 2008-03-26
You can't chainload into OS X because hfs+ partitions don't have a volume boot record, they don't boot that way on a real mac.

The boot process goes like this, the system starts, the firmware paints a grey screen, if you are holding any of the startup keys, the system does what you tell it to. If not, it checks an NVRAM variable that determines which volume to boot (this is what the Startup Disk preference pane changes). Normally the system then loads boot.efi from the os x volume, which then starts and puts the spinning wheel at the bottom of the screen.

If the nvram variable is set to boot into the Ubuntu partition by default the only way to change this is to either hold option at startup and pick the OS X volume, or hold C at startup and boot into the OS X dvd, open Startup Disk in the tools menu and select your OS X volume.

By the time you see grub, there is no way to boot into OS X. It isn't possible.

Do the startup keys work at all on any keyboard you have access to?

Try the following:

option           asks which volume to boot
c                  boots cd
command-s   does single user mode
t                  boots into target disk mode

You can review these startup keys here: [http://docs.info.apple.com/article.html?artnum=303124]("http://docs.info.apple.com/article.html?artnum=303124")

If none of those work at all, your keyboard isn't working in the firmware. Aluminum keyboards are known to not work on some macs like this, so use another one for now.

---

### Post by teryowen on 2008-03-26
Im not sure if you're correct because ive seen numerous users have grub boot up their MACs

as for the original problem boot up to the ubuntu and for the Mac entry change it to this

title Mac OS X
root (hd0,1)
kernel /pc_efi/boot_v8

so again: ```
gksudo gedit /boot/grub/menu.lst
```

I am reading numerous posts where users have this working so i think it will if it doesn't my apologies.

---

### Post by mrsteveman1 on 2008-03-26
boot_v8 is a different issue, in effect you are loading the hacked version of the darwin bootloader (which then has to be on whatever partition you point the root line at), which can then read HFS+ and load the OS X kernel. You don't want to do that on a real mac. I'm not entirely sure what it would do, because once grub loads, the firmware has already put itself into bios compatibility mode instead of native efi.

It is preferable to just fix the boot process with the OS X dvd, if you can't get the DVD to boot you have bigger problems to deal with, like the keyboard not working right :D

---

### Post by teryowen on 2008-03-27
I tried, Prolly shouldnt have approached it as a regular computer problem, I should learn more about MACs...

---

### Post by Trebla Nietsnie on 2008-03-27
I think it's getting close ... this time in the esc area osx was there and it gave a different error error 17: Cannot mount selected partition

I have tried all the option a and c pressing things and they dont work ... it's not the key bord as i swapped it for my old apple one as esc never used to work in the grub loading area .... Good ideas but mrsteveman1 thanks

---

### Post by mrsteveman1 on 2008-03-27
Hey i only know this stuff because i just got a mac mini, my startup keys don't work either haha :D

You have to hold the startup key while you are turning the computer on though, there is only a small window of time where they work before the computer continues its boot process. Once grub loads you are past it

If none of the keyboards you have access to are working with the startup keys you might have to do a hard reset (hold the power button while you plug in the machine i believe).

---

### Post by teryowen on 2008-03-27
thats exactly the same thing that happened here. [http://forum.insanelymac.com/index.php?showtopic=86401](http://forum.insanelymac.com/index.php?showtopic=86401)

try pressing 'e' while in grub when your highlighting the Mac OS entry and then 'e' over the root line and change it up to (hd0,0) or (hd0,2) or (hd0,3) as i didnt see your fdisk -l this is why we're getting the error.

Either way thats the solution for a pc on a mac im kind of feeling out of place now as im not familiar with it, but give it a shot changing the root location test it out... i dont know you never know what might happen.

---

### Post by Trebla Nietsnie on 2008-03-27
no luck with the hard boot :( I have tried a few times with the option key and the c key etc.. no luck

---

### Post by mrsteveman1 on 2008-03-27
You can try grabbing the efi loader (boot_v8 ) from netkas site if you want, but i think it just points you to an IRC channel, i'll see if i can grab it for you and post it here (its completely legal code, there is no copyright issue). Then you have to put it on your ubuntu partition and point the root line at it. Again I'm not entirely sure what will happen but you can give it a shot if you want. 

I'm also curious if there isn't a way to set the nvram variable from Ubuntu, which would solve a lot of problems. Other than those things, the startup keys are the only way to change things, and if they don't work even after using a known good keyboard, doing a hard reset, and possibly resetting the pram, you might have to just take it to an apple store.

---

### Post by mrsteveman1 on 2008-03-27
Ok i attached boot_v8 because it doesn't come with OS X (it serves no purpose on a real mac etc).

Stick it in /boot on your ubuntu partition and change the Mac OS X line you put into grub to /boot/boot_v8 and change the root line (hd0,0) to (hd0,1) etc depending on which partition it is.

Again this is a hack, but it MIGHT boot into OS X correctly, i have never tried it on a real mac. From there you will want to set your startup disk back to OS X.

---

### Post by Trebla Nietsnie on 2008-03-27
none of it works :( thanks but

---

### Post by Trebla Nietsnie on 2008-03-27
there must be something i can do to fix this does anyone know how i can change it so it boots from a cd in grub ?? Maby then i can use the Apple cd and boot from that ?

---

### Post by mrsteveman1 on 2008-03-27
I'm not sure if there is any way to get the firmware to boot into a cd from grub like that, it's not the same as a normal PC cd (which uses el torito to boot). I suppose if you can get boot_v8 to run you could possibly select the apple cd from the menu that comes up. If boot_v8 isn't working then something isn't set right with grub.

Your best bet is to either call the apple support line (its free) or take the thing to an apple store.

---

### Post by dmitrijledkov on 2008-03-28
My suggestion would be downloading rEFIt burning it onto a disk (best on another mac).

Then trying to boot into that CD. Because your Mac Install CD might be broken.

Else it could be that grub overwrote EFI partition. Than it's big times backup what you can access and reinstall.

---

### Post by cyberdork33 on 2008-03-28
> **dmitrijledkov said:**
> Else it could be that grub overwrote EFI partition. Than it's big times backup what you can access and reinstall.The EFI partition is only used for firmware updates. You do not have to have an EFI partition to boot your computer.

---

### Post by mrsteveman1 on 2008-03-28
Iif you don't have access to the startup keys, installing rEFIt will make certain things harder, because you won't be able to use the menu when rEFIt starts. 

Also, to install refit you must bless the refit binary, which i don't think you can do from anywhere but OS X.

Your best bet is to grab some more USB keyboards, one of them HAS to work with the startup keys, then you can either select your OS X installation and fix its startup, or boot the installer disc.

---

### Post by cyberdork33 on 2008-03-28
yea, holding c should boot from the cd.... period. This is part of the Mac firmware. If you keyboard is not working, then try unplugging USB devices other than the keyboard.

---

### Post by russo.mic on 2008-04-14
So,  what is the output of those commands?  We need to see the output to teach you how to add a startup entry in Grub.

Mr Stevenman1,  The keyboard bug only effects the keyboard SOMETIMES and only after you've left EFI, i.e. rEFIt will work fine, and is my recommendation.  My solution to the keyboard bug is simply to set the grub countdown to about 3 sec, long enough for me to press something if I need to stop it, but not waiting 10 sec for it to do nothing.  Besides, didn't an Apple Update fix that?

Russo

---

### Post by sunstriker on 2008-04-14
You could try putting your mac recovery disk in and press and hold C. If that doesn't you got a serious problem.

---

### Post by mrsteveman1 on 2008-04-14
The bug I'm talking about, EFI doesn't recognize the keyboard or doesn't load the keyboard driver for pre-boot control. This is the "my startup keys don't work' problem. If thats the case, you can't control rEFIt either, because refit is an efi application, it loads before any other OS kernel takes control.

They did fix the keyboard thing on some machines, but apparently not all of them.

---

### Post by russo.mic on 2008-04-14
> **mrsteveman1 said:**
> Do you perhaps own one of the new Aluminum keyboards from apple?

Startup keys (option, single user, boot cd, target disk) don't work with this keyboard and some macs.

If thats not the case, can you get any of the other option keys to work?

The keyboard only dies after you leave the EFI partition, so startup keys work fine always.  The problem only is after you've reached Grub, and you try to select a OS.  the keyboard SOMETIMES won't work.

Russo

---

### Post by cyberdork33 on 2008-04-14
> **mrsteveman1 said:**
> The bug I'm talking about, EFI doesn't recognize the keyboard or doesn't load the keyboard driver for pre-boot control. This is the "my startup keys don't work' problem. If thats the case, you can't control rEFIt either, because refit is an efi application, it loads before any other OS kernel takes control.

They did fix the keyboard thing on some machines, but apparently not all of them.I am pretty sure that only effects things after EFI passes control to the other bootloaders.... you keyboard should work in rEFIt. Additionally, this bug should be fixed in all Macs now if you have the latest firmware updates.

---

### Post by mrsteveman1 on 2008-04-14
> The keyboard only dies after you leave the EFI partition, so startup keys work fine always. The problem only is after you've reached Grub, and you try to select a OS. the keyboard SOMETIMES won't work.


I think you are talking about a different issue. With the aluminum keyboard, it's not just a "flaky behavior" thing, the keyboard itself isn't being powered while EFI drivers are being used. Caps lock light isn't on, etc, and the same thing happens 100% of the time.

The EFI partition isn't involved in booting macs, they only use it as a place to store firmware upgrades. If you mean the EFI environment, you have it backwards. Until a real operating system kernel loads, like Linux, XNU, or NT, the EFI runtime is still in control, and all hardware being used is using EFI drivers. Meaning, if the keyboard isn't working with startup keys, neither will rEFIt control, or controlling grub, because all these things run as an extension of the Apple firmware, they don't have their own keyboard drivers, they use EFI services.

They SHOULD have fixed this stuff, but it hasn't happened for some Macs, in particular the Intel Mini, there are at least 5 looong current threads on the apple forum about this issue, the aluminum keyboard doesn't work AT ALL until another OS kernel takes control and loads its own driver, prior to that EFI drivers are used, which aren't loading.

---

### Post by russo.mic on 2008-04-18
> **mrsteveman1 said:**
> I think you are talking about a different issue. With the aluminum keyboard, it's not just a "flaky behavior" thing, the keyboard itself isn't being powered while EFI drivers are being used. Caps lock light isn't on, etc, and the same thing happens 100% of the time.

The EFI partition isn't involved in booting macs, they only use it as a place to store firmware upgrades. If you mean the EFI environment, you have it backwards. Until a real operating system kernel loads, like Linux, XNU, or NT, the EFI runtime is still in control, and all hardware being used is using EFI drivers. Meaning, if the keyboard isn't working with startup keys, neither will rEFIt control, or controlling grub, because all these things run as an extension of the Apple firmware, they don't have their own keyboard drivers, they use EFI services.

They SHOULD have fixed this stuff, but it hasn't happened for some Macs, in particular the Intel Mini, there are at least 5 looong current threads on the apple forum about this issue, the aluminum keyboard doesn't work AT ALL until another OS kernel takes control and loads its own driver, prior to that EFI drivers are used, which aren't loading.

Maybe your right, I'm talking about the keyboard built into my MBP.  I've never had a problem with it not working in rEFIt or with startup keys.  I've also never used an external.

---

### Post by mrsteveman1 on 2008-04-18
Yea, the issue as far as i know, is that something about the aluminum keyboard they released last year doesn't play well with the EFI keyboard driver. Since that driver is only used with startup keys most people don't notice, once OS X loads its own driver things work fine.

They seem to have solved it with most macs with firmware updates, but some iMac and Mini users still have problems.

---

### Post by KC_HYPE on 2008-04-19
download reFit 
works like a charm
every time you start up your computer it asks which OS you want to boot in

---

