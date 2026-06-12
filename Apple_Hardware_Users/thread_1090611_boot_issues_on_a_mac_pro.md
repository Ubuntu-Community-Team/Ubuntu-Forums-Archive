---
title: "boot issues on a mac pro"
date: 2009-03-08
forum: Apple Hardware Users
---

### Post by desertskymc on 2009-03-08
Hi I am totally new and Green to Ubuntu, but a reckless adventurist. After installing with mixed results on a PC, I was curious how this Os would fair on my Mac Pro, I briefly scanned installation info online, I had a fat 32 partition on a 3rd internal drive and used bootcamp on os X 5.2 to install Ubuntu on that partition, Things went seemingly well, after 3 reboots i had a promising os ,with Video Drivers, sound, and something i had had a problem with on the PC, a flash plugging for firefox. 
 So wishing to return to OS X i rebooted with the option key.....Oh Dear, my main Os 10.4.11 from which i have my critical music apps was no longer available as a boot option. less importantly the Ubuntu install was also invisible. After staying up all night, and reading threads, I tried rEFIT with trepidation, after 3 boots from the CD i followed the partition table  recommendations and lucked out, Now I have my os 10.4.11 boot option back ....(sigh of relief)  I also have a legacy and Linux boot option on start up, BUT! they point to drive 0 the os 10.4.11 drive, and no Linux or Ubuntu lives there!
Does any one of you MAC/UBUNTU vets know how I can make the Ubuntu install on drive 3 appear in the boot menu, and also preferably erase or fix the non existant Linux boot options on drive 0?

---

### Post by cyberdork33 on 2009-03-08
> **desertskymc said:**
> Hi I am totally new and Green to Ubuntu, but a reckless adventurist. After installing with mixed results on a PC, I was curious how this Os would fair on my Mac Pro, I briefly scanned installation info online, I had a fat 32 partition on a 3rd internal drive and used bootcamp on os X 5.2 to install Ubuntu on that partition, Things went seemingly well, after 3 reboots i had a promising os ,with Video Drivers, sound, and something i had had a problem with on the PC, a flash plugging for firefox. 
 So wishing to return to OS X i rebooted with the option key.....Oh Dear, my main Os 10.4.11 from which i have my critical music apps was no longer available as a boot option. less importantly the Ubuntu install was also invisible. After staying up all night, and reading threads, I tried rEFIT with trepidation, after 3 boots from the CD i followed the partition table  recommendations and lucked out, Now I have my os 10.4.11 boot option back ....(sigh of relief)  I also have a legacy and Linux boot option on start up, BUT! they point to drive 0 the os 10.4.11 drive, and no Linux or Ubuntu lives there!
Does any one of you MAC/UBUNTU vets know how I can make the Ubuntu install on drive 3 appear in the boot menu, and also preferably erase or fix the non existant Linux boot options on drive 0?

i think you are going to have to reinstall grub, and make sure it is pointing to the correct location, but first...

when you select the linux icon, what DOES happen?

---

### Post by desertskymc on 2009-03-10
hi thanks for your response, when i select the linux penguin icon on boot up in refit i get a black screen with flashing white dash top left, like maybe i could enter something, however keyboard is 
not operational for text, if i select the legacy i get the grey bootcamp icon...thats all folks
    So what is grub? that i may have to install and is it possible to, and how could i select a boot on the third drive? lastly if i swapped the 3rd disk with linux installed onto bay one hd, would it find the linux boot? or even better if i duped my hd drive, bay one on a bigger disk with a partition for linuxand replaced hd drive one would that work? :KS

---

### Post by pxwpxw on 2009-03-10
> **desertskymc said:**
> hi thanks for your response, when i select the linux penguin icon on boot up in refit i get a black screen with flashing white dash top left, like maybe i could enter something, however keyboard is 
not operational for text, if i select the legacy i get the grey bootcamp icon...thats all folks
    So what is grub? that i may have to install and is it possible to, and how could i select a boot on the third drive? lastly if i swapped the 3rd disk with linux installed onto bay one hd, would it find the linux boot? or even better if i duped my hd drive, bay one on a bigger disk with a partition for linuxand replaced hd drive one would that work? :KS

Before re-arranging the hardware, you could probably boot ubuntu from drive 3 initially by using grub64.efi, then if you have ubuntu running is is easier to re-do the grub-pc install for multiple drives.

[http://ubuntuforums.org/showpost.php?p=6854492&postcount=377](http://ubuntuforums.org/showpost.php?p=6854492&postcount=377)

Just unpack grub64.efi.gz and put grub64.efi in the root of the Mac OSX partition, rEFIt should show it and boot grub6.efi.

Then from the efi grub command line
```

 grub> search /vmlinuz

```
will show you if it can find the ubuntu partition.

You can then try booting linux, but you will have to use the correct root=/dev/sdxx
which might be /dev/sdc2 (or it might be sdbx or sday) 
but this  should confirm that it is booting.
```

 grub> search --set /vmlinuz
 grub> linux /vmlinuz root=/dev/sdc2 video=efifb single
 grub> initrd /initrd.img
 grub> boot

```

It may need more boot options depending on the ubuntu kernel version.
 such as these -
 noefi 
 acpi=force

---

### Post by pxwpxw on 2009-03-14
**desertskymc**
> 
i tried downloading the grub 32 and 64bt files, placed them one at a time in the refit efi folder and rebooted, it did not come up on the reboot.. a discrepencey i noticed was the un packed files only
had the one file in it not the files visible in your jpeg guide, 


Put grub.efi in the root of the OSX partition, as shown for grub32-335.efi in the picture in grub.efi thread- post #1.
Its easier that way.

The other files - grub cfg and grub.icns (rename grub.icns to match your grub.efi if you want to see a grub icon) are in the post#377 grub2021 package, but you dont need them for the grub> command line, just grub64.efi or grub32.efi, whichever works.

---

### Post by desertskymc on 2009-03-14
I am not sure of the definition of mac osx 'Root" is that the area visible where all osx folders reside ie applications ,Library etc, for the life of me it looks like you placed it in the efi folder where refit resides, if there is another diagram please post a hard link, as i am not sure how to navigate posts on this site, thanks. also do you manually create a folder entitled 'grub' either 32/64  where you put the .efi file and logos?

---

### Post by desertskymc on 2009-03-14
ok got grub 32 to boot, first command gave this response hd4,4 which i believe is where ubuntu was installed, the  second command 'search set/vmlinuz' is replied with 'no such device' ?

---

### Post by desertskymc on 2009-03-14
hi i got this far, no booting, screen freezes at end ,here is the command line and reply:
       search /vmlinuz
hd4,4
grub> search --set /vmlinuz
-
 grub> linux /vmlinuz root=/dev/sdc2 video=efifb single

[linux-bz image, setup=0x3000,size-0x2393000
video mode: 1280x1024'32e0
cant find frame buffer address

 grub> initrd /initrd.img
[initrd, addr=0x74991000, size=0xb44fd51

 grub> boot
ACPI : 0x7fbba000

computer then doesnt respond
thanks, made progress ,maybe? no success, i also substituted sdbx and sday same result i dont know how or where to put the other system alternatives in the code,

---

### Post by pxwpxw on 2009-03-15
> **desertskymc said:**
> hi i got this far, no booting, screen freezes at end ,here is the command line and reply:
       search /vmlinuz
hd4,4
grub> search --set /vmlinuz
-
 grub> linux /vmlinuz root=/dev/sdc2 video=efifb single

[linux-bz image, setup=0x3000,size-0x2393000
video mode: 1280x1024'32e0
cant find frame buffer address

 grub> initrd /initrd.img
[initrd, addr=0x74991000, size=0xb44fd51

 grub> boot
ACPI : 0x7fbba000

computer then doesnt respond
thanks, made progress ,maybe? no success, i also substituted sdbx and sday same result i dont know how or where to put the other system alternatives in the code,

Well you found the ubuntu system partition and kernel and got grub32.efi working loading the kernel.

Your input looks correct so far, but the problem  with the video frame buffer address is preventing any display. Let me try some things with grub32.efi here and get back.

Is that 1280x1024 correct for your display? 

Meanwhile you could try 

 grub> linux /vmlinuz root=/dev/sdc2 video=efifb single noefi acpi=force

Also without 'single'  which just stops it in the text console before any graphics.

At this stage the /dev/sdc2 does not matter until  start up successfully indicated by scrolling linux startup messages.

---

### Post by desertskymc on 2009-03-15
hi ,well that setting is correct for the second display, I have a 24 and 17inch screen grub only accessed the 17 inch one, but Ubuntu when operating only used the 24 inch one, I was going to work on that later if possible, 
I will try some of the new command options thanks, I assume I start out as before with search /vmlinuz etc

---

### Post by desertskymc on 2009-03-15
new command with or without single produces same result

[linux-bz image, setup=0x3000,size-0x2393000
video mode: 1280x1024'32e0]
cant find frame buffer address

---

### Post by desertskymc on 2009-03-15
oh by the way the 'e ' at the end of the video data-32e0 is not an e looks like one kind of i dont know the character

---

### Post by bean123 on 2009-03-15
> **desertskymc said:**
> new command with or without single produces same result

[linux-bz image, setup=0x3000,size-0x2393000
video mode: 1280x1024'32e0]
cant find frame buffer address

You can use the EFI shell to find the frame buffer address. In rEFIt, launch the shell, then enter command:

pci -b

This would show the pci devices, look for the display controller, for example, in my macbook, it shows:

```

00 00 02 00 ==> Display Controller - VGA/8514 controller
     Vendor 8086 Device 2A02 Prog Interface 0
00 00 02 01 ==> Display Controller - Other display controller
     Vendor 8086 Device 2A03 Prog Interface 0

```

Then enter (skip the first 00):

pci 00 02 00 -i -b

At the last page, it shows the address like this:

000000051000000 Mem 64 Bits No  000000000100000 0000000501FFFFF
000000040000000 Mem 64 Bits YES 000000010000000 0000004FFFFFFFF

---

### Post by pxwpxw on 2009-03-15
> **desertskymc said:**
> hi ,well that setting is correct for the second display, I have a 24 and 17inch screen grub only accessed the 17 inch one, but Ubuntu when operating only used the 24 inch one, I was going to work on that later if possible, 
I will try some of the new command options thanks, I assume I start out as before with search /vmlinuz etc

I dont know if the 2 screens is a problem - let assume not just yet.

I did some tests grub32.efi but on a MacBook with intel graphics chip.


The 'can't find frame buffer...' is not fatal, it just means you wont see anything useful until it gets to the ubuntu desktop - about 30 seconds maybe a minute, but 'single' stops it too soon.

So remove the 'single' option which leaves it in limbo.

Try just this minimal linux line leaving out the efifb since it is not working -
```

grub> search --set /vmlinuz
grub> linux /vmlinuz root=/dev/sdc4 
grub> initrd /initrd.img
grub> boot

```

Then just wait for about 1 minute - imagine it booting up until with luck the graphics login.

May not work, my MacBook has Intel graphics chip, I expect the MacPro has other, but may still work.

However the root=/dev/sdc4 has to be correct to get there,
may take a few tries -
  
> 
hi i got this far, no booting, screen freezes at end ,here is the command line and reply:
search /vmlinuz
hd4,4


That makes it partition 4, that should be correct
but hd4 could be sdc or something else.

You might get abetter idea by running
```

grub> ls -l

```
(To show what is on  hd0, hd1, hd2, hd3, hd4 )

---

### Post by pxwpxw on 2009-03-15
> **bean123 said:**
> You can use the EFI shell to find the frame buffer address. In rEFIt, launch the shell, then enter command:



Thanks, I missed your post there.

---

### Post by pxwpxw on 2009-03-15
> **desertskymc said:**
> oh by the way the 'e ' at the end of the video data-32e0 is not an e looks like one kind of i dont know the character

This is how it should look - (numbers for my MacBook2,1)
```

Video mode: 1200x800 - 32@59
Video frame buffer: 0x40000000
Video line length: 8192

```

Can you get the EFI shell info for your MacPro for bean123. (post #13)

You get into the EFI shell from rEFIt screen,  the bottom left terminal icon , and 'exit' to leave, restart after leaving.

 On my MBP I had to page down from 
 Shell> pci 01 00 00 -i -b
to find the Display Controller address information, not at the end.
(attachment shown for MBP41 )

bean123 can probably fix the grub code for your MacPro model frame buffer address and the boot should all work normally into ubuntu for you, would be good to have that for the MacPro users.
 Much better solution than trying to work around it.

---

### Post by desertskymc on 2009-03-15
command ls - l revealed following info about macpro drive structure:

device hd0: Partition table
device hd1: Partition table
device hd2: Partition table
                  Partition hd2,1: Filesystem type fat, label EFI    ,UUID 2860-11f4
                  Partition hd2,2: Filesystem type hfplus
Device hd3: Partition table
                  Partition hd3,1: Filesystem type fat, UUID4646-150a
                  Partition hd3,2: Filesystem type hfplus
                  Partition hd3,3: Filesystem type hfplus
                  Partition hd3,4: Filesystem type hfplus
Device hd4: Partition table
                    Partition hd4,1: Filesystem type fat UUID 3f3c-1af6
                     Partition hd4,2: Filesystem type hfplus
                    Partition hd4,3: Filesystem type fat UUID 354c-13eb
                      Partition hd4,4: Filesystem type ext2, UUID 883aee28-e5d1-4ac0-8d70-0a11
5c360901
                     Partition hd4.5: Unknown filesystem
Device cd0: Unknown filesystem

the shortened command line produced the same result ,freeze, I waited 5 mins no response
I will next try, beans suggestion from EFI shell
thanks

---

### Post by desertskymc on 2009-03-15
I tried the shortened command again it booted what do i do in Ubuntu to get this boot to register in refit so it is a boot option or can I?

---

### Post by pxwpxw on 2009-03-15
> **desertskymc said:**
> I tried the shortened command again it booted what do i do in Ubuntu to get this boot to register in refit so it is a boot option or can I?

Are you getting a usable Desktop, how are the graphics?

Put grub.cfg with grub32.efi and you get a menu, if thats what you mean (it must be named just grub.cfg).
grub32.icns gives you the icon in refit.

Attached is a full grub.cfg I made, the menunentry "Linux sdc4" is what I think you are booting with, correct it if not.

```

menuentry "Linux sdc4" {
	search --set /vmlinuz
	linux /vmlinuz root=/dev/sdc4
	initrd /initrd.img
}

```

You dont need a 'boot' command in the menu.

With that boot, you wont be able to change from desktop to a console, the console video wont work because the efifb is not enabled ( correct me if I am wrong ).

To set up the old grub-pc from ubuntu can be done using the grub command line in ubuntu,
when you have the grub.efi working as backup - might need some trial and error.

You should still get the frame buffer address info for bean for a proper Mac Pro grub32.efi solution.

---

### Post by desertskymc on 2009-03-16
Well I had booted once using the grub 32 visible in refit, using the shortened command line without video specs, however i havnt had any success repeating this,so therefor i am again 'locked out'
 within the ubuntu operating system i had attempted to locate the boot cd utility that was installed in the synaptic to make a cd backup, but could not find where the app was accessable from any menus, i also had some 'graphic' problems related to the mouse where the listed options under 'system. applications' and all other menus at the top of the desktop disappeared then later reappeared making it difficult and frustrating to make progress. I am thinking Ubuntu 64bit may be buggy and disfunctional on this mac, maybe i should switch to 32 bt anyway ?
 In the meantime i havnt a clue where i enter the code you have written but will try putting that file where the others live in the Mac hd roots EFI folder so at least i can get back to the Ubuntu OS environment, and , if the new code lines are intended for the grub 32 accessable via the refit menu i try bash in it out. I will also try beans EFI shell to get that info

---

### Post by pxwpxw on 2009-03-16
Re-setting grub-pc in ubuntu -

grub-pc as installed in ubuntu differs comlpletely from grub-efi.

From ubuntu -
Assuming the default grub package  is installed ( and not grub2-pc )

Assuming that Mac OSX is on drive /dev/sda and grub-pc stage1 will boot from there -

This will reinstall grub files in ubuntu and grub bootcopde to the MBR of sda, and rewrite the grub-pc menu.lst. Hopefully it will correctly find the sda MBR.
```

$ sudo grub-install /dev/sda
$ sudo update-grub

```
Edit /boot/grub/menu.lst to increase timeout and comment out 'hidden menu'
```

timeout		13
## hiddenmenu

```

Restart into refit and select the Partitoning Tool icon, update the MBR, restart again should give a TUX icon for grub-pc menu.

If anything fails, use grub32.efi to boot back into ubuntu to try something else.

---

### Post by pxwpxw on 2009-03-16
That instruction for reinstalling grub-pc assumed you were booted into ubuntu. You can possibly get a Supergrub cd or a grub2 cd download in OSX and burn to rescue boot the ubuntu OS, then as above, also better check the 'recover' or 'rescue'option on your install CD, it may let you boot other drives. 
It gets more difficult if you try to do multiple drives when not booted into the ubuntu HD installation. But if bean can fix the frame buffer address that is a good option. The amd64 should not be a problem at this stage, wait until you have a stable boot to evaluate it.

Try this one -
[http://ubuntuforums.org/showthread.php?t=1057600](http://ubuntuforums.org/showthread.php?t=1057600)

---

### Post by desertskymc on 2009-03-16
i edited the grub in ubuntu, have no idea how or where to edit grub list: timeout		13
## hiddenmenu
putting the grub.cgi in the efi folder with grub32.efi had no visable effect on the menu , and i have discovered the grub32 efi command that boots ubuntu is sdc4 not sdc2 if that has any significance. 
changing the grub in ubuntu has had no effect in the refit partitioning table, all is synced. and no changes to the refit icon menu have been implemented so far.

---

### Post by pxwpxw on 2009-03-16
> **desertskymc said:**
> i edited the grub in ubuntu, have no idea how or where to edit grub list: timeout		13
## hiddenmenu
putting the grub.cgi in the efi folder with grub32.efi had no visable effect on the menu , and i have discovered the grub32 efi command that boots ubuntu is sdc4 not sdc2 if that has any significance. 
changing the grub in ubuntu has had no effect in the refit partitioning table, all is synced. and no changes to the refit icon menu have been implemented so far.


grub.cgi? grub.cfg?
supposed to be in the root, not in /efi.
The grub.cfg I gave you has  root=/dev/sdc4.
No point trynig to edit menu.lst util you can boot into ubuntu on the HD.

Try that grub2-pc rescue cd, it may do it.

Better confirm what you have been using to boot grub32.efi, maybe you got a lucky configuration.

---

### Post by desertskymc on 2009-03-16
bean 123
i ran the numbers in efi shell for the display controller
the last page did not reveal any bit info the last line looks like this the other 20 or so have only changes in the front ie 00000fa0

last line:
00000ff0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00  *..........*
if you want me to check previous pages let me know thanks

---

### Post by pxwpxw on 2009-03-16
> **desertskymc said:**
> bean 123
i ran the numbers in efi shell for the display controller
the last page did not reveal any bit info the last line looks like this the other 20 or so have only changes in the front ie 00000fa0

last line:
00000ff0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00  *..........*
if you want me to check previous pages let me know thanks

See my post $#16 and attached picture - what you are looking for.

---

### Post by desertskymc on 2009-03-16
sorry typo .cfg is the suffix, I dont get it! all the grub32.efi etc files are in the efi folder and they work, as in boot in refit menu, and that is where they are in your jpg guide it would appear, please tell me explicitly where the 'root' is in which they should be placed, bearing in mind they currently work, except for the file i added, by the way there was an identically named file grub.cfg i removed rather than overwriting to put the latest one in
 another strange thing i dont have a grub64.efi in the folder yet it comes up in refit menu as well as the 32 maybe its reading them from the mac desktop? as thats where i have the only copy, wierd
   I was unable to get the grub2 CD it appears to be a broken link,please post a live one if you know where it resides, thanks

---

### Post by pxwpxw on 2009-03-16
> **desertskymc said:**
> sorry typo .cfg is the suffix, I dont get it! all the grub32.efi etc files are in the efi folder and they work, as in boot in refit menu, and that is where they are in your jpg guide it would appear, please tell me explicitly where the 'root' is in which they should be placed, bearing in mind they currently work, except for the file i added, by the way there was an identically named file grub.cfg i removed rather than overwriting to put the latest one in
 another strange thing i dont have a grub64.efi in the folder yet it comes up in refit menu as well as the 32 maybe its reading them from the mac desktop? as thats where i have the only copy, wierd
   I was unable to get the grub2 CD it appears to be a broken link,please post a live one if you know where it resides, thanks

Can you post picture(s) of finder windows showing where you have put eveything, need to be sure we know what is being use, and avoid confusion with duplication, may have missed a winning combination.

The root is the top level of the Mac OSX partition where you see top level folders Applications Library System Users and so on.

You should have grub32.efi and grub.cfg in the OSX root and remove all grub stuff from /efi (save it on a usb stick or in a desktop folder if you want to).

The broken link is in the #1 post, there is a good link in post #6.
It is very slow to download but it gets there, I just got the latest one (by date) and it works well for one drive, hopefully for your multi-drives.
> 
As for grub2 cd image, use this link (maybe a little slow):
[http://nufans.net/grub4dos/grub2/](http://nufans.net/grub4dos/grub2/)


---

### Post by desertskymc on 2009-03-17
here are screen shots of display info for bean 123 (100_2794) this is the only page displayed with info. cant see frame buffer . and 2nd pic is grub file location on mac system disk ,music 2 with leopard installation

---

### Post by bean123 on 2009-03-17
> **desertskymc said:**
> here are screen shots of display info for bean 123 (100_2794) this is the only page displayed with info. cant see frame buffer . and 2nd pic is grub file location on mac system disk ,music 2 with leopard installation

The frame buffer address seems to be 0xE0000000, please try attachment #405 at:

[http://ubuntuforums.org/showthread.php?t=995704&page=41](http://ubuntuforums.org/showthread.php?t=995704&page=41)

And see if it can detect fb properly.

---

### Post by desertskymc on 2009-03-17
Here is a screen shot of refit boot with grub files in Mac osx root, now at least i have a workable. all be it, round about  access to Ubuntu, thanks, for that.
 By clicking on the new grub configuration i now have a choice of osx or a linux boot off hd 4,4. There remains the messy blind alley icons of linux and legacy viewable  in refit, and osx options (labeled Windows in Osx without refit start).  I can live with them, but it would be nice to fix cleanly.
 I am glad Bean123 has been able to read frame buffer, the error message could be from having the 2nd monitor connected, which is inactive with the refit, grub, menus, however in reverse, Ubuntu uses the large alt monitor but does not access the small monitor where all grub and refit pages appear. Osx of course uses both in Split Screen mode.

---

### Post by pxwpxw on 2009-03-17
> **desertskymc said:**
> Here is a screen shot of refit boot with grub files in Mac osx root, now at least i have a workable. all be it, round about  access to Ubuntu, thanks, for that.
 By clicking on the new grub configuration i now have a choice of osx or a linux boot off hd 4,4. There remains the messy blind alley icons of linux and legacy viewable  in refit, and osx options (labeled Windows in Osx without refit start).  I can live with them, but it would be nice to fix cleanly.
 I am glad Bean123 has been able to read frame buffer, the error message could be from having the 2nd monitor connected, which is inactive with the refit, grub, menus, however in reverse, Ubuntu uses the large alt monitor but does not access the small monitor where all grub and refit pages appear. Osx of course uses both in Split Screen mode.

If you have ubuntu system on the internal drive running thats good.

Now move grub.icns (your previous scrren shot) to the same level as beans new grub32.efi and grub.cfg in the root of music2, then rename grub.icns to grub32.icns. You should then see the  grub icon in rEFIt screen instead of the '3 cubes' default icon.

The other icons and the alternative TUX boot by grub-pc can be tidied up later, after your ubuntu system is reliably running.

Could you please post the text of the grub.cfg file you are now using.
Also perhaps an update screen shot showing location of the various grub files, some should be removed.

---

### Post by desertskymc on 2009-03-18
here is the Grub .cfg text:

# grub.cfg pxw 20090316
# comment lines are ignored
timeout=20
default=0
set F1=ctrl-x
set F2=ctrl-c
set color_normal=yellow/red
menuentry "OSX" {
	search --set /usr/standalone/i386/boot.efi
	chainloader /usr/standalone/i386/boot.efi
}
menuentry "Linux sdc4" {
	search --set /vmlinuz
	linux /vmlinuz root=/dev/sdc4
	initrd /initrd.img
}
menuentry "CD" {
   appleloader CD
}
menuentry "MBR1" {
   appleloader HD
}
menuentry "REBOOT" {
	reboot
}
I occasionally get some bad system boots when the Mac is switched on , grey blank screen, and a boot option of just the Music 2 leopard drive along  with written options 'verbose loggin' and some other random text. Grub Icons are now visible on normal refit start. 
Ubuntu boots straight to desktop. I figure the start up will not work until the Grub boot code includes the Frame Buffer info, am I supposed to still use the Grub 2 CD? and how?

 I have some issues with Ubuntu, I installed Envyng and now have 2 screens however, I have to set the Nvidia X server settings to twinview on every boot as the settings will not save. Also as I have said previously the boot cd backup application installed from the synaptic package is not visible under any menu i find, and I would like to backup the Ubuntu system as it grows more 'configured' for my use. 
If any body knows now to configure Jack to use an Apoge Rosetta 800 audio interface connected to a Maestro  pci in Ubuntu please post, I have seen conflicting info about the possibilities

---

### Post by pxwpxw on 2009-03-18
> **desertskymc said:**
> 
I occasionally get some bad system boots when the Mac is switched on , grey blank screen, and a boot option of just the Music 2 leopard drive along  with written options 'verbose loggin' and some other random text. 

Sometimes needs a second start or start using the option key.
> 
Grub Icons are now visible on normal refit start. 
Ubuntu boots straight to desktop. I figure the start up will not work until the Grub boot code includes the Frame Buffer info, am I supposed to still use the Grub 2 CD? and how?

If you are booting ubuntu desktop now with grub32.efi, that may be all you need. The frame buffer is used by adding 'video=efifb' option to the menuentry and editing the Ubuntu xorg.conf for Driver "fbdev". You only need it if you want to switch to a text console from the desktop - using Control Alt F1.
Are you using the Grub2 CD.
If you restart with CD or usb stick, that will change all the grub drive names and cause troble.
The CD was only for backup.
> 
 I have some issues with Ubuntu, I installed Envyng and now have 2 screens however, I have to set the Nvidia X server settings to twinview on every boot as the settings will not save. Also as I have said previously the boot cd backup application installed from the synaptic package is not visible under any menu i find, and I would like to backup the Ubuntu system as it grows more 'configured' for my use. 
If any body knows now to configure Jack to use an Apoge Rosetta 800 audio interface connected to a Maestro  pci in Ubuntu please post, I have seen conflicting info about the possibilities
Thats beyond my comfort zone, deserves separate threads.

-----

Looking at the pictures - 

You can configure to start direct into the grub.efi menu by using the 'bless' function in Mac OSX and set the grub.cfg to default to boot linux, but it is safer to go via the rEFIt screen with Mac OSX default.

In the finder files screen shot, the grub files you are using to boot are the grb32.efi, grub.cfg, grub32.icns in the music2 top level.

The files in the 'grub2021' folder are just text files for information, not used in any way for booting.

If there are any grub files left over in the /efi folder with refit, they are not being used and can be removed.

When you get the Ubuntu grub-pc reinstalled you can boot from the refit TUX icon or using Option key 'windows' disk icon.

---

### Post by desertskymc on 2009-03-19
'When you get the Ubuntu grub-pc reinstalled you can boot from the refit TUX icon or using Option key 'windows' disk icon.'

could you please explain how i do this i would like to have the 'window' partition directed correctly under the optiom key, thanks

---

### Post by pxwpxw on 2009-03-19
> **desertskymc said:**
> 'When you get the Ubuntu grub-pc reinstalled you can boot from the refit TUX icon or using Option key 'windows' disk icon.'

could you please explain how i do this i would like to have the 'window' partition directed correctly under the optiom key, thanks

Ok, first need to get updated info on your system, so as to get ubuntu grub configured without breaking something.

Mostly info about drives and partitions, but first about grub on the Ubuntu istallation at sdc4, not grub-efi on the OSX partition. 

Remove all CD's and usb sticks.
Restart into rEFIt screen and run the Partiton Tool, and let it Update the MBR if needed.
Restart again into ubuntu on sdc4. (I hope you can post direct from ubuntu)

In a terminal run these commands and post the lot.
```

$ df

$ sudo dpkg -l grub grub-pc

$ uname -a

$ lsb_releasee -a

$ sudo parted /dev/sda p free

```

Then restart into Mac OSX, and in  a terminal 
```

$ diskutil list

```
Should list all 3 drives and partitons.

How to do the actual ubuntu grub reinstall will depend on which grub version found in ubuntu.

Oh, and you need to make a rEFIt CD - download the Mac disk image from refit web site and burn in Mac OSX.
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

### Post by desertskymc on 2009-03-21
df

$ sudo dpkg -l grub grub-pc

$ uname -a

$ lsb_releasee -a

$ sudo parted /dev/sda p free

this command is responded by 'cant find grub-pc'

---

### Post by pxwpxw on 2009-03-22
> **desertskymc said:**
> df

$ sudo dpkg -l grub grub-pc

$ uname -a

$ lsb_releasee -a

$ sudo parted /dev/sda p free

this command is responded by 'cant find grub-pc'

Thats ok, what about the other output?

---

### Post by desertskymc on 2009-03-26
sorry for the delay, not sure what you mean by other output.
also .....................Update
I am installing a new promary drive I want to partition this with my Os x 4.11 music disk image, possibly a leopard partition and then a Ubuntu Studio 32bit 8,10 partitition, as you know I have refit in my number 2 drive in a Leopard partition, from refit  I have Grub accessing Ubuntu on disk 3: partition 4,4 . and finally 2 Linux ghost options to non existant legacey and linux os partitions on the current primary disk ,which i am replacing. have you any pointers on the best safest drama free way to create this build so all os installs will be available for booting in refit ?
 thanks

---

### Post by cyberdork33 on 2009-03-26
he gave you 6 different commands, what was the output of each of them?

---

