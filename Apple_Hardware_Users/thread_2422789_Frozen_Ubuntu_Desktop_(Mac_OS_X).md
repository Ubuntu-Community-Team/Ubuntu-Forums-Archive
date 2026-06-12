---
title: "Frozen Ubuntu Desktop (Mac OS X)"
date: 2019-07-12
forum: Apple Hardware Users
---

### Post by ebecker on 2019-07-12
[COLOR=#242729][FONT=Arial][FONT=arial]I apologize if the solution to this problem is obvious or listed elsewhere. The closest match I found to this problem was [here]("https://askubuntu.com/questions/1133638/dual-boot-ubuntu-mac-os-x-freeze"), but it didn't receive any replies. I outlined the steps I've taken, the problem, and attempts to solve the problem below. 

For context, my computer specs are:[/FONT][/FONT][/COLOR]

[LIST]
[*][FONT=arial]macOS High Sierra version 10.13.6[/FONT]
[*][FONT=arial]processor 2.3 GHz Intel core i5[/FONT]
[*][FONT=arial]memory 8GB[/FONT]
[*][FONT=arial]Startup disk: Macintosh HD[/FONT]
[*][FONT=arial]Graphics: Intel iris plus graphics 640 1536 MB 
[/FONT]
[/LIST]
[COLOR=#242729][FONT=Arial][FONT=arial]And the specs of my USB stick are:[/FONT][/FONT][/COLOR]

[LIST]
[*][FONT=arial]16GB[/FONT]
[*][FONT=arial]Sandisk[/FONT]
[/LIST]
[HR][/HR]**[FONT=arial]Configuring USB stick[/FONT]**

[COLOR=#242729][FONT=Arial][FONT=arial]I followed Ubuntu's tutorial on how to set up my USB stick ([https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0)). The steps I took were: 
1. Installed the 18.04 Ubuntu ISO file 
2. Navigated to external disk, clicked erase in disk utility, then set format to MS DOS FAT and scheme to GUID partition map 
3. Used Etcher to copy Ubuntu ISO to USB stick 
4. Hit eject when my computer notified me that my USB stick couldn't be read.[/FONT][/FONT][/COLOR]
[HR][/HR]**[FONT=arial]Booting Into Ubuntu[/FONT]**

[COLOR=#242729][FONT=Arial][FONT=arial]This is where I ran into problems. Here are the steps I took: 
[/FONT][/FONT][/COLOR]

[LIST=1]
[*][FONT=arial]Restarted my computer holding the option key 
[/FONT]
[*][FONT=arial]Selected the first yellow EFI boot drive I saw (there were two) 
[/FONT]
[*][FONT=arial]Selected try Ubuntu without installing[/FONT]
[/LIST]

**[FONT=arial]Description of Behavior:[/FONT]**

[COLOR=#242729][FONT=Arial][FONT=arial]The Ubuntu desktop loads fine. The icons for the apps are there and so is the desktop background. My clicker appears in the lower right quadrant of the screen, but I'm not able to move it. The desktop is frozen. It also doesn't take keyboard input.[/FONT][/FONT][/COLOR]
[HR][/HR]**[FONT=arial]Attempts to Solve the Problem[/FONT]**

**[FONT=arial]Going Directly to Install Ubuntu[/FONT]**

[COLOR=#242729][FONT=Arial][FONT=arial]I tried selecting install Ubuntu instead of try Ubuntu desktop without installing, but it got stuck on the splash screen and didn't load.
[/FONT][/FONT][/COLOR]
**[FONT=arial]Disabling Secure Boot[/FONT]**

[COLOR=#242729][FONT=Arial][FONT=arial]I tried restarting, holding command R to open up OS Utilities window, selecting utilities, startup security utility, but I didn't see the option to choose no security. It turns out that my computer doesn't have an Apple T2 Security Chip, so this isn't the source of the problem.
[/FONT][/FONT][/COLOR]
**[FONT=arial]Disabling ACPI[/FONT]**

[COLOR=#242729][FONT=Arial][FONT=arial]I went into the command line and specified acpi=off, but this didn't do the trick either.[/FONT][/FONT][/COLOR]
[HR][/HR][COLOR=#242729][FONT=Arial][FONT=arial]I would enormously appreciate any help with this. Again, sorry if this has been asked already.[/FONT][/FONT][/COLOR]

---

### Post by deadflowr on 2019-07-13
*Thread moved to **Apple Hardware Users***

---

