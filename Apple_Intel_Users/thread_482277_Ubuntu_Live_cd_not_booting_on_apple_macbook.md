---
title: "Ubuntu Live cd not booting on apple macbook"
date: 2007-06-23
forum: Apple Intel Users
---

### Post by insaneliltroll on 2007-06-23
I do not know why bit I ordered some cd's from ubuntu a few months back version 6.06 lts and it wont boot on my macbook from the cd I pressed and held C for cd to load but it spits the cd right back out. Can anyone please help me?

---

### Post by ivesjd on 2007-06-23
Try rebooting with the cd in, and holding down option. That should give you a choice between OSX and the cd. Although it might say windows.

---

### Post by insaneliltroll on 2007-06-23
Well I tryed this and it doesnt seem to work I have tried several Ubuntu CD's and it just spits them out or ignores them.  Oh and It used to at one time boot ubuntu. I have no idea why it doesnt now.

!!!!!!!HELP ME PLEASE!!!!!!

---

### Post by ivesjd on 2007-06-23
Have you installed rEFIt? Your going to want it if your planing to dual-boot. If you haven't, download it and install. And make sure that you do the enable always command. Then try, post back with results.

---

### Post by insaneliltroll on 2007-06-23
Well I am just trying to boot off of the Cd like I should be able to do but I dont know why it wont work

---

### Post by ivesjd on 2007-06-23
Put the cd in the drive. Then hold down the power button. Once its off, hold down the C key, dont let your finger off of it untill you see the ISO loading text in the top right corner. And if that doesnt work I would install rEFIt. Or try the same thing but replace the C key with option.

---

### Post by ivesjd on 2007-06-23
What cd are you trying to boot by chance? You need the i386 version for the macbook. The 64bit version will also work on a Core 2 duo macbook (newer). Let me know what CD you are trying to boot. That could help, and also some hardware info. That way I know what cd you need.

---

### Post by insaneliltroll on 2007-06-23
it is the newest version off of the ubuntu website I also have version 6.06 lt . I ordered it from ubuntu so it is not my own burned version. My macbook Is a core duo not core 2 duo. it has the 2.0 ghz prosssor in it

---

### Post by ivesjd on 2007-06-23
Could you link me to the cd download that you used?

---

### Post by insaneliltroll on 2007-06-23
[http://carroll.cac.psu.edu/pub/linux/distributions/ubuntu-releases/feisty/ubuntu-7.04-desktop-i386.iso](http://carroll.cac.psu.edu/pub/linux/distributions/ubuntu-releases/feisty/ubuntu-7.04-desktop-i386.iso)

I got it from ubuntu's website not someone else. I just tried what you told me to do and I got this one loud beep coming from the computer when I held down the option key. I might try that program you said.

---

### Post by insaneliltroll on 2007-06-23
What version of rEFIt should I try to download?

---

### Post by ivesjd on 2007-06-23
[http://sourceforge.net/project/downloading.php?groupname=refit&filename=rEFIt-0.10.dmg&use_mirror=internap](http://sourceforge.net/project/downloading.php?groupname=refit&filename=rEFIt-0.10.dmg&use_mirror=internap)

---

### Post by insaneliltroll on 2007-06-23
ok so what do i do after i download it?

---

### Post by insaneliltroll on 2007-06-23
Ok I got the program and I burned it to a disk and it works but what do i do wth it. As of now I just want to use the live cd not instal ubuntu

---

### Post by dragonwings on 2007-06-23
get a copy of ubuntu 7.04 fiestyfawn  im using it my macbook to post this

---

### Post by insaneliltroll on 2007-06-23
and I get that from where?

---

### Post by Gen2ly on 2007-06-23
lol, perhaps you haven't been directed to the wiki.  in the tab community at help dot ubuntu dot com lookup macbook

---

### Post by insaneliltroll on 2007-06-23
Alls Im trying to do is run the live cd on my macbook and its not wroking. i dont want to install anything I just want to play around with it. I need help getting it to work.

---

### Post by ~joe~ on 2007-06-24
> **insaneliltroll said:**
> Alls Im trying to do is run the live cd on my macbook and its not wroking. i dont want to install anything I just want to play around with it. I need help getting it to work.
OK... try this:

[LIST=1]
[*]Turn on the Mac, boot into OS X.
[*]Insert the Ubuntu LiveCD.
[*]Reboot
[*]Since you said that rEFIt has been successfully installed, just wait until some icons come up at the boot. Use the arrow keys to select the CD icon.
[*]Hit enter, and all should be well.
[/LIST]

[edit] By the way, have you updated to the latest version of OS X and upgraded your firmware? That might do it.

---

### Post by insaneliltroll on 2007-06-24
i burned it onto a disk but i did not instal it because i did not want to mess up my computer. will it do anything if i install it?

---

### Post by ivesjd on 2007-06-24
rEFIt will not break anything. If your just trying to boot the Ubuntu cd, you shouldnt need rEFIt but for some reason you seem to need it. You can install rEFIt and uninstall it pretty easy.

---

### Post by ronocdh on 2007-06-24
> **insaneliltroll said:**
> i burned it onto a disk but i did not instal it because i did not want to mess up my computer. will it do anything if i install it?
I cannot tell whether you mean rEFIt or Ubuntu. I see ivesjd took you to mean rEFIt, and I agree, I suppose. You should know that there is a package install for rEFIt available, though, which means you can install within OS X and won't have to burn a CD. This is what I do.

---

### Post by ivesjd on 2007-06-24
The link I gave you was for a .DMG. Which is what apple uses. Just double click it and it will mount. You can then install rEFIt from there.

---

### Post by ~joe~ on 2007-06-26
I just remembered this:
[http://www.apple.com/macosx/bootcamp/](http://www.apple.com/macosx/bootcamp/)
> First, you need to make sure your Intel-based Mac has the latest version of Mac OS X and the latest firmware updates. These provide technologies that make Boot Camp possible.
I think that the firmware and software updates of Mac OS X not only make it possible for Windows to run, but also Linux. The actual Boot Camp software that you download is only a partitioning program; the actual code required to boot the thing is contained in the updates.

So... if you haven't done the updates, then that's probably why your MacBook is refusing to boot Ubuntu.

---

### Post by insaneliltroll on 2007-06-26
Well I got to work using refit and i am posting while using ubuntu now so thanks for the hel everyone I finally got it to work!

---

### Post by ronocdh on 2007-06-26
> **~joe~ said:**
> I just remembered this:
[http://www.apple.com/macosx/bootcamp/](http://www.apple.com/macosx/bootcamp/)

I think that the firmware and software updates of Mac OS X not only make it possible for Windows to run, but also Linux. The actual Boot Camp software that you download is only a partitioning program; the actual code required to boot the thing is contained in the updates.

So... if you haven't done the updates, then that's probably why your MacBook is refusing to boot Ubuntu.
This is very sketchy logic IMO. I'd wager that one could double or triple boot from a Tiger install with Boot Camp. I don't think other Apple-issued upgrades are necessary, but I'd love to be corrected on this.

---

### Post by ~joe~ on 2007-06-27
>I'd wager that one could double or triple boot from a Tiger install **with** Boot Camp.
Did you make a typo there?

Anyway, I'm pretty sure, according to this, that it wasn't possible to boot Linux before those updates were issued:
[http://en.theweeklyrant.com/modules/news/article.php?storyid=2](http://en.theweeklyrant.com/modules/news/article.php?storyid=2)

Unless, of course, Feisty already has an EFI-supported bootloader that it uses with the LiveCD?

---

### Post by ronocdh on 2007-06-27
> **~joe~ said:**
> >I'd wager that one could double or triple boot from a Tiger install **with** Boot Camp.
Did you make a typo there?

Anyway, I'm pretty sure, according to this, that it wasn't possible to boot Linux before those updates were issued:
[http://en.theweeklyrant.com/modules/news/article.php?storyid=2](http://en.theweeklyrant.com/modules/news/article.php?storyid=2)

Unless, of course, Feisty already has an EFI-supported bootloader that it uses with the LiveCD?
I believe Feisty did add EFI-awareness. If you try to install on your Mactel using the Edgy or Dapper CD, you'll get a GRUB error and it'll quit. The old MacBook guide used to have a work around for this, which involved issuing a terminal command after beginning the Ubuntu installation but before it sets up GRUB.

I did not make a typo in my statement, although I was less than clear. What I meant was that I believe a user could install Tiger from the DVD, then install Boot Camp, and be able to run Ubuntu. This was in response to your statement:
> I think that the firmware and software updates of Mac OS X not only make it possible for Windows to run, but also Linux. The actual Boot Camp software that you download is only a partitioning program; the actual code required to boot the thing is contained in the updates.
I do not believe any other Apple updates are necessary to run Linux. I think it can be done from a blank Tiger install, plus Boot Camp, foregoing any of the Apple updates offered through the Software Update utility. Again please correct me if I'm wrong!

---

### Post by ~joe~ on 2007-06-27
> **ronocdh said:**
> I believe Feisty did add EFI-awareness. If you try to install on your Mactel using the Edgy or Dapper CD, you'll get a GRUB error and it'll quit.
Odd... I've booted the Dapper LiveCD lots on my MacBook and there were no problems. Maybe my MacBook is just special. :p

[edit] Whoops! I misread. Sorry...[/edit]

> I did not make a typo in my statement, although I was less than clear. What I meant was that I believe a user could install Tiger from the DVD, then install Boot Camp, and be able to run Ubuntu. This was in response to your statement:
Oh, I see. Thanks for clearing that up. While I don't have any hard and solid proof, here's what I did about 9 or 10 months ago:

I had recently purchased my MacBook and was looking for a Linux to install on it. I thought Boot Camp would make the installation easier, so I decided to install that, but as Apple instructed, I upgraded all my firmware and software first. Then being the nerd that I am, I popped in a Slackware 10.1 CD and to my amazement it booted (although it had issues recognizing my laptop keyboard, so I didn't bother installing it).

Then I decided to do some researching for installing Linux on a Mac, and discovered that Boot Camp wasn't all that critical, so I uninstalled it. I almost never had any problems booting non-EFI aware Linux distros on it (I'm *pretty* sure Slackware isn't EFI-aware!) But that was all since that update, and I've never had Boot Camp installed again, yet my non-EFI Linux CDs continue booting fine. So my experiences may be weird, but I couldn't boot these distros before the update. And another interesting thing, I've seen some guides for triple-booting on Macs that don't use Boot Camp software at all. They simply resize everything with diskutil, and proceed with the installation, none of the crazy hacks that OnMac required originally.

> I do not believe any other Apple updates are necessary to run Linux. I think it can be done from a blank Tiger install, plus Boot Camp, foregoing any of the Apple updates offered through the Software Update utility. Again please correct me if I'm wrong!
I'm not entirely sure about the software updates, but I think it's probably the firmware updates that have more of an effect. But of course, I may be completely wrong as well. If only I could easily downgrade my firmware/software to test for sure!

[edit]
Finally! I found something interesting:
[http://www.pcauthority.com.au/print.aspx?CIID=38727&SIID=10](http://www.pcauthority.com.au/print.aspx?CIID=38727&SIID=10)
> Boot Camp is actually a collection of technologies. The key is in the firmware upgrades that Apple has released for each of its Intel systems. Intel Macs use the Extensible Firmware Interface (EFI), a modern, but incompatible, replacement for the age-old BIOS. Intel has been touting EFI for many years, but until now it has been seen mainly on Itanium systems.

The firmware updates add a Compatibility Support Module (CSM) to Apple's EFI that can boot non-EFI-aware operating systems. It's designed to boot XP from a local hard drive partition, or El Torito-style bootable CD like OS installers to live CDs, but in theory it should be capable of booting just about any standard PC operating system. 

Along with the firmware upgrade, Mac OS X 10.4.6 includes support for safely resizing OS X (or specifically, journalled HFS+) partitions, and the Boot Camp Assistant helps you repartition and burns an XP driver CD for you.

---

### Post by ronocdh on 2007-06-28
> **~joe~ said:**
> I'm not entirely sure about the software updates, but I think it's probably the firmware updates that have more of an effect. But of course, I may be completely wrong as well. If only I could easily downgrade my firmware/software to test for sure!

[edit]
Finally! I found something interesting:
[http://www.pcauthority.com.au/print.aspx?CIID=38727&SIID=10](http://www.pcauthority.com.au/print.aspx?CIID=38727&SIID=10)
This was extremely interesting to me; thank you for taking the time to make such a detailed post! I personally have never used Boot Camp with Linux... I used it briefly to toy with Win XP, then reformatted and have since been triple booting. I didn't use Boot Camp for this (it only supports the creation of one additional partition, so doesn't work for triple), but I had of course previously installed Boot Camp, so I have the firmware updates. Thanks again, this is much clearer now!

---

