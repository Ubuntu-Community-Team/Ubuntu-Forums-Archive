---
title: "my primary app is not supported"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by XRzero4 on 2007-10-21
If this belongs in a different area of the forum, please direct me.
My problem is an app called emachineshop.( [www.emachineshop.com](www.emachineshop.com)). This is very unique 3D design freeware I was in the process of using when the switch to linux became unavoidable.
The problem is that the application is just not supported under linux that I can find at all. I found a program called WINE that claims to act as king of a "brigde" between windows apps and the linux environment, and I found EMS in its app database, but with reports of Dismal results.
If Ubuntu is truly going to work for me, I need to get it to work with emachineshop.
I can follow instructions and figure things out, but I need help.
Has anyone out there tried to play with this app besides me?
Partitioning and dual booting is not an option because my copy of ME is Toast and I don't have the money to spend for a fresh one. 
Does anyone out there have even the slightest clue how to get this windows app to function in this enviro??

---

### Post by Espreon on 2007-10-21
If you don't know how to run things in Wine do this in a terminal:

```

wine (drag and drop exe here)

```

If the app won't run under Wine then, try running Windows in a VM (at least it is better than dual-booting).

But that app looks pretty interesting...

I tried it out but it does not work in Wine, it will start but it is unusable.

---

### Post by XRzero4 on 2007-10-21
> **Espreon said:**
> If you don't know how to run things in Wine do this in a terminal:

```

wine (drag and drop exe here)

```

If the app won't run under Wine then, try running Windows in a VM (at least it is better than dual-booting).

But that app looks pretty interesting...

I tried it out but it does not work in Wine, it will start but it is unusable.


Okay, terminal- With you there. 7.10 has the appropriate terminal within it, correct?
Next: VM:  Was ist Das???
what's vm, do i need to DL it, what's it do, how might it help? VERY new user here...

---

### Post by Shazaam on 2007-10-21
VM= virtual machine.
VMware, VirtualBox, etc. use it. Run Ubuntu as host with Windows as guest (on top).

---

### Post by XRzero4 on 2007-10-21
> **Espreon said:**
> If you don't know how to run things in Wine do this in a terminal:

```

wine (drag and drop exe here)

```

If the app won't run under Wine then, try running Windows in a VM (at least it is better than dual-booting).

But that app looks pretty interesting...

I tried it out but it does not work in Wine, it will start but it is unusable.

Haven't yet even downloaded wine because i was able to determine from their page that it had been tried with EMS and failed. this prompted my search for help in this forum.
I'm looking for ways around this unfortunate situation, like perhaps another WINE-like conversion program,
or perhaps a linux-based version of an EMS type application.
Any crumbs for me to follow at all?

---

### Post by buzzmandt on 2007-10-21
vmware and virtual box run a virtual system of windows, but you have to have a windows install disc for it to work, judging from your original post (OP) you no longer have access to a windows install disc, is this the case?

---

### Post by XRzero4 on 2007-10-21
> **Shazaam said:**
> VM= virtual machine.
VMware, VirtualBox, etc. use it. Run Ubuntu as host with Windows as guest (on top).

The problem with that is that mein vindoze ist kaput. it's so buggy I just physically took that whole hard drive out of the machine and installed gutsy on a blank one. I assume I need windows to at least work in order to use virtual machine?

---

### Post by XRzero4 on 2007-10-21
> **buzzmandt said:**
> vmware and virtual box run a virtual system of windows, but you have to have a windows install disc for it to work, judging from your original post (OP) you no longer have access to a windows install disc, is this the case?
 install disc is thing of distant past

---

### Post by Niniel on 2007-10-21
If your Windows is toast, you can try, as a last resort, [ReactOS,]("http://www.reactos.org/en/index.html") which is an alpha version of a Windows clone, I mean, a rebuild from the ground up. 
Failing that, you could try to find Win9x on the net, or even Win2000, and install that.
Your program won't work in Linux, and if Wine can't run it, then you are just plain out of luck unless you can find a similar software that was written for Linux.

---

### Post by XRzero4 on 2007-10-21
> **Niniel said:**
> If your Windows is toast, you can try, as a last resort, [ReactOS,]("http://www.reactos.org/en/index.html") which is an alpha version of a Windows clone, I mean, a rebuild from the ground up. 
Failing that, you could try to find Win9x on the net, or even Win2000, and install that.
Your program won't work in Linux, and if Wine can't run it, then you are just plain out of luck unless you can find a similar software that was written for Linux.

I don' wanna be outta luck! 
Has anyone heard of a similar program to Emachineshop in this particular universe?
(praying for luck)

---

### Post by buzzmandt on 2007-10-21
I got it to work (seemingly) quite well in wine......
I'll post screenshots and a "how to" on how i done it shortly

---

### Post by XRzero4 on 2007-10-21
looked into reactOS, and as I was advised, it's in Alpha. That makes me nervous. 
Has anyone used it?

---

### Post by XRzero4 on 2007-10-21
> **buzzmandt said:**
> I got it to work (seemingly) quite well in wine......
I'll post screenshots and a "how to" on how i done it shortly

Okay so I need to run wine in order to run reactOS?. This gets trickier and twistier all the time.
But I WON'T need VirtualMachine at any point in this process will I?

---

### Post by Niniel on 2007-10-21
Why don't you try it? It can't be any worse that your destroyed WinME installation, so at worst you'll have wasted a couple of hours installing it.

---

### Post by buzzmandt on 2007-10-21
OK, I don't know the ins and outs of the program but it seemed to work pretty good, 
I'm running feisty (will test in gutsy if you need), with wine v.0.9.47 (current latest release as far as I know).

Go to winehq.org, follow the links for installing in Ubuntu for your release of ubuntu.  once installed use terminal and type "winecfg" (without the quotes).  

Under applications tab set windows version to windows 98

Under graphics tab check "allow directx apps to stop the mouse leaving the window", no check on the second one "Allow windows manager....." and check the 3rd, "Emulate virtual desktop"  Set to desktop size you want, mine is set to 1024x768  (my ubuntu desktop is 1600x1200)

(the following is how i installed emachines, It's better to install from terminal but when the easiest way works that's how I do it)
download emachines installer to desktop
right click on the exe file and select open with wine windows emulator,  If the option isn't there then select "open with other application" then select "use custom command" then type "wine" (again without the quotes).
During the install the 3d test screen comes up behind the 2d test screen, move the top window to the side to show the 3d test screen, then you can test if the rotations and such work,
after installing, run the program as normal


that's how I got these screen shots:

---

### Post by buzzmandt on 2007-10-21
> **XRzero4 said:**
> Okay so I need to run wine in order to run reactOS?. This gets trickier and twistier all the time.
But I WON'T need VirtualMachine at any point in this process will I?


My above how to didn't use reactos.....If you get errors post them here and I and others will try to help you further, I'm no wine expert but I have it working as the screenshots show

---

### Post by Niniel on 2007-10-21
No no, ReactOS is a separate OS, just like Ubuntu. Has nothing to do with Wine on Linux.

I've never used it, but I figured if nothing else works, it might be worth a try.

---

### Post by buzzmandt on 2007-10-21
sorry, just remembered, during the install process the 3d test screen appears behind the 2d test screen, move the top one over to see the 3d test screen and it works, rotates, etc....

updated original how to post to include this

---

### Post by XRzero4 on 2007-10-21
> **buzzmandt said:**
> sorry, just remembered, during the install process the 3d test screen appears behind the 2d test screen, move the top one over to see the 3d test screen and it works, rotates, etc....

updated original how to post to include this

I'm taking this to mean you got it to actually WORK, not just sit there and be broken.
I'm going to try the whole shebang, so I'll be posting my results in maybe an hour or so.
I have a spare hard drive I can devote to ReactOS, Have a whole spare Machine, actually, case open, patient on life support. My work is cut out for me now- 
Thanks, all

---

### Post by buzzmandt on 2007-10-21
Refer to my above post, yes i got it working and i have screen shots to show it....Follow the directions I posted and it should work.....

Wine is not perfect, what works for me may not for you, but it's a good place to start.

last but not least.....Good luck

---

### Post by MegaSvensk on 2007-10-21
I just want to warn about using ReactOS. It totally fried my VMware installation when I tried it and who knows what it'd do to real hardware.

Good luck getting your app working.

---

### Post by buzzmandt on 2007-10-21
just tested on gutsy, and it works, but you must have wine v. 0.9.47 .

---

### Post by XRzero4 on 2007-10-21
Okay, more Issues...
I've been doing all of this from the liveCD, and in trying to deal with wine I've decided  the first step is to go ahead and do the install to the hard drive. BUT...What if I can only use the liveCD because gutsy can't see my HDD for some reason? 
Can I still use wine? where does it go if not the hard drive? 
I just installed a blank hard drive in this machine, and the BIOS detects it, but gutsy doesn't seem to want to. I'm leery of trying to load wine until I get this issue straightened out, and get the OS properly installed on the machine.
What am I missing This Time?

---

### Post by buzzmandt on 2007-10-21
You should install ubuntu before trying to install wine.  If you are having trouble installing ubuntu you should start another thread detailing that issue.  You'll get it resolved much quicker than putting different issues into the same thread.

---

### Post by XRzero4 on 2007-10-21
> **buzzmandt said:**
> You should install ubuntu before trying to install wine.  If you are having trouble installing ubuntu you should start another thread detailing that issue.  You'll get it resolved much quicker than putting different issues into the same thread.

point taken, issue resolved, onto the next problem. Posted new thread detailing graphics and video drivers issues regarding same application...

---

### Post by XRzero4 on 2007-10-21
WAS goint to post this in a new thread, but really it's the same issue. Still trying to get emachineshop to play nice with ubuntu so I can get back to work.

Using wine I got it to load, but I have video drivers issues, no doubt because I'm using an ATI card. 

emachineshop tells me to try disabling hardware acceleration. No idea how to do that.

the only other solution is a new card with different drivers.

I have other cards, and I'm attempting to make use of one of them, but before I start messing with what seems to finally be a stable system(even if my primary app is NOT working)
I want more info  on what I'm getting into here.
I know I can't just pull the ATI out and put another one in without problems, like not having drivers.
How do I go about performing this swap? Once I find the correct drivers, How do I install them so the hardware will work right the first time? 

Most likely card is an S3 savage 3D, which I can wind windows drivers for, but not linux. Any ideas?
Must this be done from Terminal? If so how?

---

### Post by XRzero4 on 2007-10-21
looking before leaping here...
I found a driver for the video card I want to use in system/ screen and graphics/ choose driver,
so I Should be able to just put the new card in, go there and choose that driver, right?
I won't do the physical swap and get a screen full of gibberish?

---

### Post by Niniel on 2007-10-23
How did it go?

Regarding ATI cards, I may have said this before, but I have not had any problems with mine. Both the generic driver and ATI's own "restricted" driver worked for me without any problems.

---

### Post by XRzero4 on 2007-10-27
Looked into ReactOS, downloaded and made the liveCD, tried running it on a HDD that I Just formatted with GpartED, and... Nothing happened. Nothing. I had the BIOS set to boot from the CD and everything, it just sat there.
Dunno what I did wrong.
I'm going to try a different approach. The error messages I've been getting lead me to believe the real problem here is with my video adapter and its drivers, which are both kind of long in the tooth, so I'm going to try coming at this with a little better equipment.
I'm prepping a different machine with a Nvidia GEforce 6800 vid card. As soon as I get it up and running, I'm going to transfer this whole operation to that machine, and we'll see what ind of success we have. 
I haven't posted on this thread in about days because I've been monkeying with that machine and trying to solve it's issues to get it to this point. Now I have to Flash it a new BIOS.
This thread will most likely be dormant for a couple more days while I work with that machine, but I'll pick it back up, so those interested in the EmachineShop saga should watch this space, and moderators should be tolerant with me for not marking it as resolved just yet. (I got a PM about that with another thread) 
I WILL use that app without capitulating and buying VinDoze, and it's an AWESOME app, (How 'bout designing your own custom heat sinks and having them *Delivered*, just like that!), so I want to share the info.
Workin' on it...

---

