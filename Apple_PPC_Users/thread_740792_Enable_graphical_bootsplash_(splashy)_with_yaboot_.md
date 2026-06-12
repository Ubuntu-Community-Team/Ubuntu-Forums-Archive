---
title: "Enable graphical bootsplash (splashy) with yaboot (ppc only)"
date: 2008-03-31
forum: Apple PPC Users
---

### Post by monway on 2008-03-31
Hi Folks, 

I have been reading everywhere to get the graphical bootsplash to work on debian/ubuntu cleanly from scratch on ppc. I decided to write this how-to here. (admin please sticky or move this to an how-to).

This is what i have done to make it work on my powerbook g4 17" 1440x900 screen. ready? here goes ...

**Ubuntu users**
```
 make sure you add multiverse and universe to your synaptic sources.
```**Debian users**
```
make sure you add contrib and non-free to your synaptic sources.
```**Update using synaptic or terminal**
```
sudo apt-get update
```**Download Splashy**
```
sudo apt-get install libsplashy1 libsplashy1-dev splashy splashy-themes
``` [note: [COLOR=Red]we will be appending a line to yaboot.conf which is critical to get splashy to work. we'll need to find out our VGA=xxx decimal number for our screen so that the splash is properly sized to your screeen[/COLOR].]
Visit [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions) 
to get your 3 digit VGA decimal number we need for our append line in yaboot.conf. scroll down till you see "Linux video mode numbers".

**Edit yaboot.conf**
```
sudo pico /etc/yaboot.conf
```Scroll down and add this line where the text is green.
```
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        [COLOR=SeaGreen]append="vga=867 quiet splash"[/COLOR]

```[note: [COLOR=Red]my screen is 1440x900 so my VGA decimal value is 867 yours may be different from mine so  edit the number accordingly[/COLOR]]
Press ctrl x then y to exit and save yaboot.conf

[B]Bless yaboot.conf with holy penguin pee
[/B]```
sudo ybin -v
```**Edit /etc/default/splashy**
```
sudo pico /etc/default/splashy
```set ENABLE_INITRAMFS=1 
so that Splashy will integrate itself into future initramfs images. It may already be set by default. you may go ahead and press ctrl x then y to exit and save.

**Update initramfs**
```
sudo update-initramfs -u -t -k `uname -r`
```reboot and enjoy your new bootsplash.

**Getting the list of all installed splashy themes**
```
sudo splashy_config --info
```Change splashy theme
```
sudo splashy_config -s <name of theme>
```That's it. feel free to make a simpler how-to but this gets it to work properly. I hope all you ppc linux fans out there find this helpful.

---

### Post by Cows on 2008-03-31
Works great :). For some reason when I "sudo aptitude install libsplashy1   etc...." it didn't install the rest.. it only installed libsplashy1, I had to go into Synaptics and finish installing it.

---

### Post by slacka-vt on 2008-03-31
Ironically,"Usplash is what was keeping my PowerBook G4 from booting 9 out of 10 times.
Sometimes it would boot into the "Usplash" with no problems,
other times (most of the time) it would boot into a black screen with 2 large lines about 10 pixels thick one across the middle of the screen and one across the bottom.

I would still hear the Ubuntu Bongos and I would ( i think) still login, but the Desktop never emerged.

This was very puzzling. If I rebooted enough times, it would eventually work.
 I thought it might have been a video card/driver issue but my dual-boot of Mac OS X would work everytime.
After removing Usplash  ( sudo aptitude remove usplash)
and adding "append="nosplash" and "video=ofonly" to my "yaboot.conf"
My PowerBook boots into the desktop successfully everytime.

So I have no fancy "Usplash" at boot, I actually like it.
I can see what my system is doing when it boots.


~s

---

### Post by monway on 2008-04-03
> **Cows said:**
> Works great :). For some reason when I "sudo aptitude install libsplashy1   etc...." it didn't install the rest.. it only installed libsplashy1, I had to go into Synaptics and finish installing it.

you can always also do sudo apt-get build-dep splashy
this would get all the development files needed to build and also the support files. this in general helps even if you're not planning to build it just helps with the use of the binary version. my 2 cents.

---

### Post by monway on 2008-04-03
If i'm not mistaken i believe splashy is the newer than Usplash. give splashy a try i had problems with Usplash myself and it wouldn't load xserver at all. i think the trick to all of the user splashes is all about the append line and regenerating your initramfs properly. me thinks..:popcorn:

> **slacka-vt said:**
> Ironically,"Usplash is what was keeping my PowerBook G4 from booting 9 out of 10 times.
Sometimes it would boot into the "Usplash" with no problems,
other times (most of the time) it would boot into a black screen with 2 large lines about 10 pixels thick one across the middle of the screen and one across the bottom.

I would still hear the Ubuntu Bongos and I would ( i think) still login, but the Desktop never emerged.

This was very puzzling. If I rebooted enough times, it would eventually work.
 I thought it might have been a video card/driver issue but my dual-boot of Mac OS X would work everytime.
After removing Usplash  ( sudo aptitude remove usplash)
and adding "append="nosplash" and "video=ofonly" to my "yaboot.conf"
My PowerBook boots into the desktop successfully everytime.

So I have no fancy "Usplash" at boot, I actually like it.
I can see what my system is doing when it boots.


~s

---

