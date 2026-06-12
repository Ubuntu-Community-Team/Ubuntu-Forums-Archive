---
title: "Kali Linux - Live boot - Kernel Panic"
date: 2014-01-11
forum: Any Other OS
---

### Post by cracker89 on 2014-01-11
I ve been trying to create a live bootable usb key running kali linux.

so i downloaded the 32 bit version from the site and followed the instructions, (using the dd command) and created a pendrive version.

however, upon booting from it, this happens:-

[ATTACH=CONFIG]249375[/ATTACH]

im no pro, but i have a keen suspicion that this is due to the 32 bit version and that my hardware needs the 64 bit version. is that correct?

if not, tell me what my laptop is trying to tell me when it goes into kernel panic.

anyone got any ideas??

also, whats a good way to make sure that ur live bootable pendrives work on all sorts of hardwares???

---

### Post by houstonbofh on 2014-01-11
Nope.  A 64bit CPU will run 32bit OS just fine.  (Otherwise, XP would have been in a world of hurt) That looks more like a bad block on your thumb drive that just happens to be where the boot image is.

---

### Post by varunendra on 2014-01-11
> **houstonbofh said:**
> Nope.  A 64bit CPU will run 32bit OS just fine.  (Otherwise, XP would have been in a world of hurt) That looks more like a bad block on your thumb drive that just happens to be where the boot image is.

Yup, I fully concur with houstonbofh. Try recreating the Live USB. All of these have been working fine for me -

[LIST]
[*]Native "Startup Disk Creator" program included on the iso itself (I usually boot a virtual machine to use it).
[*]Unetbootin
[*]Universal USB Creator (used it only once or twice, to test it)
[*]YUMI
[/LIST]

Unetbootin is highly recommended on these forums.

---

### Post by cracker89 on 2014-01-13
thanks for the clarity on the 32 bit/64 bit doubt. infact that is why i used the 32 bit version, for maximum compatibility...

however, from the docs available at the kali linux website, the dd command is recommended. in fact, the people over there specifically discourage the use of unetbootin to make a live image.. 

why would the dd command method fail?  i also attempted to add persistence to the live boot.. can that create complications? the pendrive used was 16gb and formatted in fat32...

---

### Post by varunendra on 2014-01-13
It is not always the 'method'. Sometimes it can be the USB flash drive itself, sometimes it can be a particular BIOS which boots only with some particular kind of flash drives or boot managers.

For instance, I had a Kingston Pen drive long ago which couldn't boot 'Any' computer that booted fine with a transcend pen drive of the same capacity, same methods, same boot managers.

Currently, I have two 8GB Kingston (Ubuntu/Lubuntu), and a 1GB PNY (clonezilla - created using Unetbootin) drives. Tried to boot a Compaq laptop a few days ago - failed to boot. It booted fine with USB hard disk (any kind of boot-manager - YUMI (whatever it uses), LILO, Grub2..). All those pendrives can boot other systems perfectly fine.

So the point is - USB booting still seems to be a job of patchworks at the firmware level. There is no one standard that one can recommend confidently for all systems. Just try different available ones (different filesystems (fat/fat32... even ext2 in case of "Slitaz"), boot-loaders, creation methods etc.).

As for this -
>  i also attempted to add persistence to the live boot.. can that create complications?
I don't think adding persistence can add any complications. It is same for all methods - a "persistent" flag in the boot-loader, which looks for a "casper-rw" (or "home-rw") partition or file. If the device is able to boot, the function (and 'complexity') of persistence will be same for all methods.

---

### Post by cracker89 on 2014-01-14
> **varunendra said:**
> It is not always the 'method'. Sometimes it can be the USB flash drive itself, sometimes it can be a particular BIOS which boots only with some particular kind of flash drives or boot managers.

For instance, I had a Kingston Pen drive long ago which couldn't boot 'Any' computer that booted fine with a transcend pen drive of the same capacity, same methods, same boot managers.

Currently, I have two 8GB Kingston (Ubuntu/Lubuntu), and a 1GB PNY (clonezilla - created using Unetbootin) drives. Tried to boot a Compaq laptop a few days ago - failed to boot. It booted fine with USB hard disk (any kind of boot-manager - YUMI (whatever it uses), LILO, Grub2..). All those pendrives can boot other systems perfectly fine.

So the point is - USB booting still seems to be a job of patchworks at the firmware level. There is no one standard that one can recommend confidently for all systems. Just try different available ones (different filesystems (fat/fat32... even ext2 in case of "Slitaz"), boot-loaders, creation methods etc.).

(Scratch this - i have a dell gig)

or its the usb... a sad old Sandisk. I just installed backbox on the same pendrive and tried to boot, gives me this error:

```
 
[  12.640732] Kernel Panic - not syncing: Attempted to kill init! exitcode=0x000000100
[  12.640732] 
[  12.640733] drm_kms_helper: panic occurred, switching back to text console
 
```

And that is all.. This is the same error I was getting with Kali Live.. Trying now to boot up diffrent hardware, but taking your advice, before I do so, I've ordered in for a bunch of pendrives of different makes..

From what I understand about Kernel Panic, its an internal error which is fatal.. so.. the install definitely has a bad block or something.. im concluding that this pendrive is whack.

> **varunendra said:**
> 
As for this -

I don't think adding persistence can add any complications. It is same for all methods - a "persistent" flag in the boot-loader, which looks for a "casper-rw" (or "home-rw") partition or file. If the device is able to boot, the function (and 'complexity') of persistence will be same for all methods.

Thats very helpful, thanks.

---

### Post by cracker89 on 2014-01-14
> **varunendra said:**
> Yup, I fully concur with houstonbofh. Try recreating the Live USB. All of these have been working fine for me -

[LIST]
[*]Native "Startup Disk Creator" program included on the iso itself (I usually boot a virtual machine to use it).
[*]Unetbootin
[*]Universal USB Creator (used it only once or twice, to test it)
[*]YUMI
[/LIST]

Unetbootin is highly recommended on these forums.

I tried Kali with unetbooting and the Startup disk creator.. both the installs stayed stuck on the part which involves the extraction of the SQUASHFS... so im concluding that this was a bad iso.

Next, however, I tried to install backbox and used the startup disk creator - smooth install, very well done.. 

but when I try to boot from the key, the error described above appears. no go... 

getting a new pendrive in the mail soon.. hopefully it should work out,..  thank you!

---

### Post by cracker89 on 2014-01-14
ok.. i got a new kingston pendrive... and i installed backbox 32  bit.. same results as above. tried 3 diff methods of installing.. still goes into [COLOR=#000000][FONT=Ubuntu Mono]Kernel Panic - not syncing: Attempted to kill init! exitcode=0x000000100

on one boot, when i booted up from the key, i selected the option check disk, it ran its check and reported that 4 files have errors.. where do i go from here
?[/FONT][/COLOR]

---

### Post by varunendra on 2014-01-14
> **cracker89 said:**
> ok.. i got a new kingston pendrive... and i installed backbox 32  bit.. same results as above. tried 3 diff methods of installing.. still goes into [COLOR=#000000][FONT=Ubuntu Mono]Kernel Panic - not syncing: Attempted to kill init! exitcode=0x000000100

on one boot, when i booted up from the key, i selected the option check disk, it ran its check and reported that 4 files have errors.. where do i go from here
?[/FONT][/COLOR]

Have you run memtest yet? Sounds like a problematic hardware to me now, most probably the RAM or an I/O controller corrupting everything that goes through it.

If you have a different system with decent hardware available, try using a virtual machine on it to boot the ISO to make sure the iso itself works (aside from checking its **[MD5Sum]("https://help.ubuntu.com/community/HowToMD5SUM")** to make sure it is intact). You may use the same VM to create the pen drive live bootable again with Startup Disk Creator.

**PS:**
My favourite has been Transcend - Jetflash model (Transcend Jetflash 4 GB). Fastest and most compatible so far..
An old post of mine, with immature opinion, incomplete info : [http://ubuntuforums.org/showthread.php?t=1845802&p=11262197#post11262197](http://ubuntuforums.org/showthread.php?t=1845802&p=11262197#post11262197) *(at that time, I didn't use to consider the fact that 'Model' per brand also matters, for example, 'jet flash' models seem to be good, 'data traveler' models - crappy to say the least)*.
I wish the forums had an option to search through the archives. I was searching for another detailed post regarding my experience with different pen drives, but can't find it now. Google could find only the above one.

---

### Post by cracker89 on 2014-01-14
> **varunendra said:**
> Have you run memtest yet? Sounds like a problematic hardware to me now, most probably the RAM or an I/O controller corrupting everything that goes through it.

If you have a different system with decent hardware available, try using a virtual machine on it to boot the ISO to make sure the iso itself works (aside from checking its **[MD5Sum]("https://help.ubuntu.com/community/HowToMD5SUM")** to make sure it is intact). You may use the same VM to create the pen drive live bootable again with Startup Disk Creator.

**PS:**
My favourite has been Transcend - Jetflash model (Transcend Jetflash 4 GB). Fastest and most compatible so far..
An old post of mine, with immature opinion, incomplete info : [http://ubuntuforums.org/showthread.php?t=1845802&p=11262197#post11262197](http://ubuntuforums.org/showthread.php?t=1845802&p=11262197#post11262197) *(at that time, I didn't use to consider the fact that 'Model' per brand also matters, for example, 'jet flash' models seem to be good, 'data traveler' models - crappy to say the least)*.
I wish the forums had an option to search through the archives. I was searching for another detailed post regarding my experience with different pen drives, but can't find it now. Google could find only the above one.

Ill run a memtest tonight... ive already checked the sums and everything is in order. will do the VM later, no time now, work and everything... 

im continuing to test different brands and models of pendrives, will update my progress...

however, i found this researching on the internet... it seems relevant, but i cant make much sense of it, a) becuase its originally in italian; and b) because im not very tech savvy. [http://forum.ubuntu-it.org/viewtopic.php?t=60613](http://forum.ubuntu-it.org/viewtopic.php?t=60613)
but im sure someone with a lil more knowledge can help me out..


EDIT: also this - [https://bbs.archlinux.org/viewtopic.php?id=156882](https://bbs.archlinux.org/viewtopic.php?id=156882)

---

### Post by cracker89 on 2014-01-14
running the memtest... this guy was getting the same error as me (Call Trace), and his solution lay in the bios setting... however, i havent upgraded/downgraded my bios at all.... havent touched it...

[http://ubuntuforums.org/showthread.php?t=1874044](http://ubuntuforums.org/showthread.php?t=1874044)

n00b ques: what is call trace?

---

### Post by cracker89 on 2014-01-14
memtest is 79%pass w/o errors... however, getting hotter with my research... [http://ubuntuforums.org/showthread.php?t=1968798](http://ubuntuforums.org/showthread.php?t=1968798)

[http://ubuntuforums.org/showthread.php?t=1843810&page=2](http://ubuntuforums.org/showthread.php?t=1843810&page=2)

---

### Post by cracker89 on 2014-01-14
this is definitely a hardware issue now. managed to use the same pendrive with the same install on another machine.. everything is working spotless... Sony vaio, i3, whereas my machine is i5...

im a lil more convinced its a bios issue... 

alternatively, also thinking of giving the 64bit version a shot... maybe thats the hang up...

---

### Post by mastablasta on 2014-01-15
well these all have different BIOS (somehave same/similar). it's best to consult the manufacturer's manual to see how to set up BIOS or UEFI as the usualyl use now. 

another thing - do you mabye have UEFI? i was just thinking i can't remember if there was a kernel panic or not, but for some reasons i couldn't get the USB to boot on an older mashcine. itried a couple of boot creators. i tried the USB on another mashicne and it worked fine. the USB was even recognised propperly in BIOS. upon doing the disk check i got error on 1 or 2 files (can't remember). i didnt' get this error on another mashicne and i knwo the image was good. i almost went nuts with that install. took me 3 hours. i decided to sleep over it. next day i came armed with 12.04.3 32bit DVD sure enough it boots normal. upon install i found out that it seems the old disk died (still need to troubleshoot that) so i had to reinstall it putting the bootloader on newer disk. in the end all is well and works as expected (except i have 32bit OS on 64 bit CPU). 

my point is that if you can, you could try to boot from DVD. perhaps there will be no errrors. 

it's hard to say what went wrong or if there really is a hardware error - it could be an odd BIOS/UEFI setting, a hardware error, or it could be that you just need to use one of the boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

edit: Also what system are we working on now?

---

### Post by cracker89 on 2014-01-15
> **mastablasta said:**
> well these all have different BIOS (somehave same/similar). it's best to consult the manufacturer's manual to see how to set up BIOS or UEFI as the usualyl use now. 

another thing - do you mabye have UEFI? i was just thinking i can't remember if there was a kernel panic or not, but for some reasons i couldn't get the USB to boot on an older mashcine. itried a couple of boot creators. i tried the USB on another mashicne and it worked fine. the USB was even recognised propperly in BIOS. upon doing the disk check i got error on 1 or 2 files (can't remember). i didnt' get this error on another mashicne and i knwo the image was good. i almost went nuts with that install. took me 3 hours. i decided to sleep over it. next day i came armed with 12.04.3 32bit DVD sure enough it boots normal. upon install i found out that it seems the old disk died (still need to troubleshoot that) so i had to reinstall it putting the bootloader on newer disk. in the end all is well and works as expected (except i have 32bit OS on 64 bit CPU). 

my point is that if you can, you could try to boot from DVD. perhaps there will be no errrors. 

it's hard to say what went wrong or if there really is a hardware error - it could be an odd BIOS/UEFI setting, a hardware error, or it could be that you just need to use one of the boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

edit: Also what system are we working on now?

no,, no UEFI. I tried booting on a system with UEFI, didnt even pick up my pendrive. no kernel panic.. 

hahah... sh*t that sounds like a real bummer. but if all this effort wasnt involved, I might as well BUY my OS from a shop window (pun intended)

hmmm... i thought of doing that too, the DVD install.. its on my agenda. 

ooh oops. sorry, should have put up my system details in the begining itself... im working on a a Dell Vostro that came preloaded with Ubuntu. Full specs are here - [http://www.dell.com/in/business/p/vostro-2520/pd](http://www.dell.com/in/business/p/vostro-2520/pd)


a couple of very busy days ahead.. will have to take out time...

---

### Post by cracker89 on 2014-01-17
@varun - there is truth to what you say about chipsets and pendrives... i took the same iso and put it on different pendrives, using the same installation method. i tried a transcend too . . but in the end i got SOME success with a little sony 8gb key.. but not victory. the iso was for back box, and with the sony key i was able to get the os loading, however, the boot happens way too quickly than on other systems and instead of getting the backbox desktop, im presented with a brand new ubuntu 12.04 (the os on sda), prompting me to make an account on ubuntu one... so yes. thats as far as ive been able to get till now... thank you for your help man...

---

### Post by danny.techify on 2014-02-02
The problem might be that the iso image wasn't written to the USB stick correctly so you could try again. If that dosen't work try a different program to put the iso onto the usb stick like UNetBootin.

---

