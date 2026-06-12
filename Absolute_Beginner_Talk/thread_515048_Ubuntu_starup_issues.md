---
title: "Ubuntu starup issues"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Snipedogg22 on 2007-08-01
OK hey guys I have a question i was here a while back and i was having troubles getting ubuntu to start. I was able to get help but now i switched to a nvidia geforce 6200 graphics card from my intel graphics and i think ubuntu dosent have a driver for it or something like that.Also i was told with my first problem that i had to type in on the edit section linux acpi=off when the live cd started up  and i wanted to know 1 how can i get ubuntu to work on the new video card and 2 how can i permantly edit the code so that i can install ubuntu on my hard drive.

---

### Post by FleetAdmiral74 on 2007-08-01
You might look into a program called Envy. It is designed to install drivers for video cards that are giving you trouble out of the box.

Can you at least access the command line from recovery mode, or boot up normally and then alt-F1 to get into the terminal?

edit: woopsee, thats probably the wrong command. I can't remember the right one...

---

### Post by alienexplorers on 2007-08-01
To get into terminal mode hit CTRL+ALT+F3  to return back to GUI hit CTRL+ALT+F7.  Have used Envy in the past to load drivers for my Nvidia FX5200 card when I could get nothing else working.  My FX5200 no runs like a champ.

---

### Post by lambros on 2007-08-01
It seems to me that you have two separate problems here:
1) The need to use "acpi=off" as a Linux boot parameter
2) The failure of the X server to start up, because you've changed your graphics card from Intel to nVidia

Does the Live CD work OK?  Is your problem with getting the LiveCD booting to a graphical desktop?

Or are you trying to install Ubuntu onto a hard drive and having problems booting your hard-drive installation?

To solve 1), you would need to press the Esc key when your computer starts to boot off the hard drive.  That should get you into the Grub boot menu, where you can edit the boot parameters (add acpi=off to the end of the boot command-line) and then continue booting.  You would then want to make this change permanent in your system, so you don't have to do this manually every time you boot. I could post instructions for this if that's what you need.

To solve 2), we need to know whether your problem is with booting the Live CD, or with an installed system.  The solution will be different in either case.

Lambros

---

### Post by Snipedogg22 on 2007-08-01
lambros u have my solution i think but the thing is my live cd works fine and i want to install it onto my hardrive by either wubi or install directly from the disk so i think what i have to do is run envy and then after that i want to be able to install it to my hardrive and then be able to permantly edit it so that every time i log on i dnt have to type it in evertime.

---

### Post by lambros on 2007-08-02
> **Snipedogg22 said:**
> lambros u have my solution i think but the thing is my live cd works fine and i want to install it onto my hardrive by either wubi or install directly from the disk so i think what i have to do is run envy and then after that i want to be able to install it to my hardrive and then be able to permantly edit it so that every time i log on i dnt have to type it in evertime.

Wubi is an Ubuntu installer that runs from within Windows.  Since you already have a working Live CD, there is little point in you running Wubi.  You would end up re-downloading over 600MB of stuff that you've already got on your Live CD.  Unless, of course, you want to help the Wubi project by volunteering as a guinea-pig to test the Wubi installer?

I think your best bet is to boot up from your Live CD.  Then, use the "Install" shortcut on the desktop to install Ubuntu onto your hard drive.  Once you have finished the hard-drive installation, then you can think about solving whatever problems you have with booting up, graphics, or whatever.  But you have to get Ubuntu installed first.

[Edit] On second thoughts, if you don't have 3D working with the Live CD, I can see why you might want to solve this issue before going ahead with the install.

If you have the Feisty version of Ubuntu, then that already comes with the "Restricted Driver Manager" which should let you enable your 3D graphics with a couple of mouse clicks.  If you are new to GNU/Linux, please remember that third-party tools such as Envy are **unsupported** by Ubuntu.  Therefore, only use them as a last resort, when you can't get things working otherwise.

Lambros

---

### Post by Snipedogg22 on 2007-08-03
ok so i can solve everthing once i get it on my hardrive the thing is im a gamer and i wanted to know if there is any free/ open source hard drive partion programs that i can use so i can still play my games on windows and enjoy ubuntu for everthing else. Also i cant even get to the boot up of ubuntu becasue of the graphics drivers.

---

### Post by lambros on 2007-08-04
> **Snipedogg22 said:**
> ok so i can solve everthing once i get it on my hardrive the thing is im a gamer and i wanted to know if there is any free/ open source hard drive partion programs that i can use so i can still play my games on windows and enjoy ubuntu for everthing else.

Yes, there are F/OS hard drive partitioning programs - in fact, you already have such software on your Live CD! :-)  The Live CD comes with its own installer that has everything you need to set up a dual-boot system.  That includes the ability to create new partitions and resize existing ones.  I'm told that setting up a dual-boot is very easy, even if that means resizing your Windows partition to make room for Ubuntu.  If you do need to resize the Windows partition, then I'm told you should defragment the Windows drive 2 or 3 times first.

Just remember to back up your existing data, just in case things go pear-shaped.

> **Snipedogg22 said:**
> Also i cant even get to the boot up of ubuntu becasue of the graphics drivers.

Sorry, you've got me confused here!  :confused:  You said earlier: "but the thing is my live cd works fine".  How can it work fine, but also stop you from "getting to the boot up"?  :-)

I'm curious to know if your Live CD boots fine, but shows some kind of command prompt instead of the graphical desktop.  Do you get a login prompt? (That's different from a "boot:" prompt - we need to know these kind of details.)  If so, is it a graphical screen, or just a textual "login:" prompt?

I think your problems will be easy to resolve (permanently, as you want), and you would end up with a perfectly good dual-boot system.  So please don't give up yet! :-)  But we need to get a better, detailed understanding of your problems before we can give you good advice.

Lambros

---

### Post by Snipedogg22 on 2007-08-07
the live cd goes to the options page u knw like start install ubuntu and other options and i type in linux acpi=off in the f6 option thing and then i run the live cd but then i get the driver check list after the kernals loaded and then it just sits there and stays on that page and i cant do anything but i checked the live cd image on my parents computer and it works fine i really think its my graphics driver i hope this clarifies   it for u.

---

### Post by lambros on 2007-08-07
> **Snipedogg22 said:**
> the live cd goes to the options page u knw like start install ubuntu and other options and i type in linux acpi=off in the f6 option thing and then i run the live cd but then i get the driver check list after the kernals loaded and then it just sits there and stays on that page and i cant do anything but i checked the live cd image on my parents computer and it works fine i really think its my graphics driver i hope this clarifies   it for u.

Thanks for the clarification - it's **extremely** helpful for us to know that the Live CD works on someone else's PC but not yours :-)

I'm not sure I'm the best person to help, because I'm not much good at troubleshooting Live CD problems.  To be honest, I've never seen one fail to boot up! :-)

But I'll ask some questions, in the hope we can get more info:

Could you tell us more about your Live CD?  Is it the Feisty version?  32-bit or 64-bit?  Ubuntu or Kubuntu?  Use the Feisty version if possible.

As far as I can tell, your graphics card (nVidia GeForce 6200) should work just fine with the nVidia driver that Ubuntu provides.  When you get the first Options screen, there should be an option: "Start Ubuntu in Safe Graphics Mode".  Could you highlight that option, then press F6, then type "acpi=off" (without the quotes), then press Enter?  Please tell us if that gets your 2D graphics working.

If you still can't get the graphical desktop working, please describe the "driver check list" you mentioned.  Does it look something like this: on the left column, you have messages like "* Starting basic networking", and on the right column, you have lots of "[ OK ]" entries?

Please tell us what the bottom two lines are (I guess you'll need a pen and paper to write them down).

When it gets stuck on that page, press Ctrl-Alt-F2.  Does the screen change?  Does it show a prompt that looks like:
```
ubuntu@ubuntu:~$

```

If not, try Ctrl-Alt-F3.  Let us know if you can get a command-prompt similar to this, or a prompt that says "login:".

Lambros

---

### Post by Snipedogg22 on 2007-08-08
I have Ubuntu 7.04 version and i believe its feisty version im not sure if its 32 or 64 i got it for a Intel PC from the home page if that helps and i tried your solution and i get to the part  where it says Ubuntu and it has the bar that goes back and forth  then it starts to load and the loading bar stops after a while and i let it sit for like 3 hrs today and still nothing all it does is at the Ubuntu start up screen with a little of the bar filled.

---

### Post by lambros on 2007-08-09
> **Snipedogg22 said:**
> I have Ubuntu 7.04 version and i believe its feisty version im not sure if its 32 or 64 i got it for a Intel PC from the home page if that helps and i tried your solution and i get to the part  where it says Ubuntu and it has the bar that goes back and forth  then it starts to load and the loading bar stops after a while and i let it sit for like 3 hrs today and still nothing all it does is at the Ubuntu start up screen with a little of the bar filled.

If you can see the Ubuntu splash screen with the progress-bar, I would be inclined to think your problem is **not** graphics-related.  You can see the graphical logo, so your graphics card is working fine at a basic level.  It sounds like something **else** is getting stuck somewhere, and is preventing the system from completing the boot process.

When the system gets "stuck" like that, could you try pressing Ctrl-Alt-F1, then Ctrl-Alt-F2 ?  Keep going along the function-keys, and see if anything interesting happens.  Try to describe in as much detail as you can.  Even if **nothing at all** happens when you press Ctrl-Alt-F1, please tell us that.  If you see a screen full of text, try to give us the bottom two rows, at least.

Tell us if you can get a command-prompt.  We'd really like to know, so we can suggest lots of things to type into it!  :-)

Could you tell us more about the kind of PC you have?  Manufacturer, model number, CPU, motherboard, etc. as much as you can.  Somebody else might have a similar system to yours, and they might have some helpful suggestions on getting it to work.  You might have to type some other stuff on the boot prompt, or you might have to tweak your BIOS settings, fiddle with IRQs, disable unneeded stuff, that kind of thing.  I'm sorry I'm not the best person to help with this kind of low-level problem.  I'm just trying to ask the right questions so others might step in with some better ideas.

Lambros

---

