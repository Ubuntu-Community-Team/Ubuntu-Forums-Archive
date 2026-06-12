---
title: "Ubuntu not showing after install"
date: 2012-05-15
forum: Apple Hardware Users
---

### Post by Lunarts on 2012-05-15
Hello community, I'm a game developer(linux will be one of my game platforms) and I tried to install Ubuntu 12.04(the mac only 64 bits .iso) on my mid 2011 iMac(21,5 inches) yesterday. Below what happened:

1 - Media not automatically detected(refused by OS X at startup); but pressing alt at startup worked to access the media.

2 - No apple wireless keyboard support, but mouse worked, and from there I just used a temporary onscreen keyboard. Internet works too.

3 - Ubuntu requested a 'bios-grub' partition during manual install, I went back and then did the 'Install side by side' option instead; ubuntu created the bios-grub partition(which I do not know what is for, since grub code cannot be installed to it) anyway. I tried installing manually again, with the 'grub-bios' partition and installing grub to the linux root partition(/)

4 - Ubuntu didn't showed at startup(after restart) by pressing alt, a 'EFI boot partition' option which was previously present also vanished, but nothing wrong happened regarding that, so I guess it is fine. 

5 - rEFIt is quite abandoned, I tried rEFInd instead; ubuntu entry still not showing at rEFInd boot screen. To be honest I wanted to boot by a so called 'grub-efi-amd64' option instead, without any boot manager.

So, that is it, ubuntu is installed, but not showing at startup; how can I proceed to make it appear at rEFInd boot manager, or more preferably, by pressing alt with the grub-efi-amd64 option instead(without boot managers)? Do I need to do that 'syncing partition table' stuff I have read elsewhere? 

Thanks for any help, ubuntu refused to work at my previous HP touch smart PC; but at iMac things seem very nice, except for the above issue.

Also feel free to check my project, called Questverse(it is on the indieDB site) if you so desire.


[I]PS1: I already had read a lot of information regarding what I want and tried myself a few, but none was actually useful to me.

PS2: Please explain the better you can how you managed to overcome this issue, I know a bit about linux terminal, but I am no expert at that.[/I]

---

### Post by Lunarts on 2012-05-16
Thanks to user srs5694 for explaining a bit about the situation, I download Super Grub 2 disk and burned to a cd, booted it at startup with alt key, selected the grub option which looks for Grub installations even if the mbr is overwritten and I managed to access ubuntu login screen, but:

1 - Apple wireless keyboard not working

2 - The same for the apple wireless mouse

Strangely the keyboard worked at Super Grub 2, and the mouse worked at the ubuntu live cd(not both); thought none works at the ubuntu login screen.

What should I do to get at least one of them(preferably both, or just the mouse) working in ubuntu, so I can proceed into making it truly bootable(without Super Grub 2 disk) ?

---

### Post by Lunarts on 2012-05-17
Stubborn ubuntu... I figured I could use my wacom tablet as a mouse(do not want to think what if I didn't had the wacom tablet); from there I requested a on screen keyboard, logged in, downloaded the system updates and language packs; installed bluesman(which enabled me to use the true mouse and keyboard), then:

1 - apple keyboard have special characters all wrong

2 - apple keyboard ceased to be detected at mac startup, making it impossible to load the Grub 2 Disk, which needs alt key at startup, otherwise super grub disk is refused. Keyboard only starts working together with the mouse too late, at the OS X login screen, and only if you hit a key from both the mouse and keyboard. Previously it worked, even with rEFInd.

Really, quite painful and frustrating process....ubuntu shouldn't be that way.

Even if I had already setup the ubuntu efi entry(as the user srs5694 said) when I could still boot super grub with alt at startup, an irresponsible keyboard would lead to OS X being booted anyway later.

If I am able to overcome this dead mac startup keyboard, then I guess all the major issues regarding ubuntu and my mac will be solved.

---

### Post by Lunarts on 2012-05-17
It seems which the keyboard issue happened somehow during my experiments with blueman, by pressing the button of the keyboard several times maybe I pressed the button in such a combination-lenght which something unexpected happened. 

Later at OS X, by pressing the button of the keyboard for some seconds I could shut it down and by doing that again I could wake it up properly, then I did the keyboard procedure in OS X(mentioned at mac manual) just in case and I could get pre boot keyboard hotkeys again.

---

### Post by Lunarts on 2012-05-17
First, I must say I fixed most of the keyboard layout problems by changing my keyboard layout from brazilian to english macintosh.

The great big issue I'm having right now is the fact which keyboard and mouse are working on ubuntu, but ceased again to work at mac pre boot due to the keyboard not being initialized when it should(thought the issue is not my fault now I guess, maybe it never was); it seems when one OS has control over the keyboard and mouse(OS X is priority, as it interferes with pre boot it seems) the other lose all the control over the keyboard and mouse.

---

### Post by SuperMiguel on 2012-05-18
So im having the same issue you are having my system is not getting detected, unless i use super grub 2... Is there a way to make it a permanent fix? and not having to boot to my cd everytime??

---

### Post by Lunarts on 2012-05-18
First, if you have anything you want to get at your OS X partition, do it now, because it is probable later you won't have keyboard input at startup anymore(couldn't fix that still). I use rEFInd(rEFIt is quite abandoned); with rEFInd and ubuntu installed and with super grub 2 disk the user mentioned above said:

> You may want to check out my page on [installing Ubuntu on a Mac in EFI mode.]("http://www.rodsbooks.com/ubuntu-efi/index.html")  From your description, I think you're probably pretty close to getting  it all to work. On my page, you should probably be able to skip to the  "Fixing the Installation" procedure, and you may be able to skip many of  the steps in that procedure, perhaps starting as late as step #11. 

---

### Post by Lunarts on 2012-05-19
As a last note, configure imediatly after ubuntu install rEFInd from OS X, so it always boot OS X(it will be entry 2), it is important for preboot apple keyboard wake up(do pairing as described in mac manual if needed); otherwise you will need to have an usb keyboard to acess OS X and preboot hotkeys.

---

