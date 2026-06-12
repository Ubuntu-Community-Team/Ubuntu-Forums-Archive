---
title: "Which VM software to use"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Chadwick17 on 2007-09-19
I'm not sure where this post should actually go, so I am putting it here...

Right now I'm running XP through a parallels VM. I'm somewhat new to Linux and very new to virtual machines. I know of 2 other programs mentioned here on the forums: VirtualBox and VM Server. Since this forum has a lot more experience in this than I do, which of the three runs the best? Or would be the best to use? Parallels installed/setup very easily for me... I like it, but wondering if I'm missing the boat on something else here...

Thanks!

---

### Post by Shazaam on 2007-09-19
-puts flameproof firesuit on-

It depends on what you want to do. Each has its merits and drawbacks. I think the biggest drawback to all of them is the lack of (or crippled) 3d support. Other than that try them all to see which one you like.

---

### Post by GSF1200S on 2007-09-19
(Also dons fire gear)

I use virtualbox. Ill tell you what it can do, and im sure some VMWare guys will chime in as well.

In virtualbox, you can install the guest editions program. Installed, it will automatically reset the resolution of your virtual OS whenever you resize the window. It will also automatically capture or release the mouse as you mouse over the window of your virtual OS- you dont have to press a host key to "release" the mouse. You also can use Seamless mode, where the windows taskbar (in the case of a Windows virtual guest) is placed on top of your Linux taskbar. With your Linux taskbars and desktop fully shown, its really nice to have Windows available as just the taskbar (when Windows is absolutely needed). When you create the .vdi file to store your virtual OS on, VBox gives you 2 options: Fixed image, and Dynamically expanding. With fixed, the .vdi immediately takes the full size youve designated (say 10GB). With dynamically expanding, the .vdi file is only as large as how much space the virtual OS uses, and can grow to the full size. The downside is it has to resize the .vdi when writing which is supposed to make it slower only in that case. I havent noticed a difference, but I dont create large files on my Virtual either. In general, VirtualBox seems extremely fast and extremely smooth, although my lappie is pretty good (core2 @2.16, 2GB@667) so that may be part of the reason. It will also make you popcorn, bring you some cheetohs, and pop open your beer:popcorn:

Seriously though.. extensive testing has been done on the Virtual software, and all of them have their ups and downs. Hopefully some of those guys will pop into this thread.

Good luck.. I had a hard time picking too..

---

### Post by Chadwick17 on 2007-09-19
Thanks for the input. I've been playing with VirtualBox for about an hour now. I think it runs faster and smoother than Parallels for sure. I've never seen XP boot up so fast - its kind of funny how it runs quicker than if I was running it natively. Its also a fresh install...so that may have something to do with it. I like how VB dynamically resizes the resolution to window size. Plus VB is free, right? I think I'll stick with it for now and continue to compare it to Parallels and hopefully find some time to give VMWare a shot... 

Right now though, off to bed - I forget that I have a job/life that I have to tend to.

---

### Post by stinger30au on 2007-09-19
i use Virtuabox cos its free and it was the first one i came across. I dont know if VMware is free or not cos i have never used it. But virutalbox runs quite fast and im impressed how it intergrates with ubuntu

---

### Post by Chadwick17 on 2007-09-20
Ok, I've been using VirtualBox more now and I've noticed that it will randomly abort - often too. I've been on teh VirtualBox forums and there doesn't seem to be an answer to this. Disappointing because it runs incredibly fast and smooth otherwise. I think its a ton smoother than Parallels. I'm going to give VMWare Server a try and see how it compares to VirtualBox - I cannot deal with the random aborts of the VM.

---

### Post by MichaelSM on 2007-09-24
Hi all.

I've never used VM gear before until now.

All I can say is that VBox is the ant's pants. (1.5.0 Edgy.deb) Get it from the VBox site.

It's a recent one and enables USB host gear. It has a nice gui, and USE IT!

You MUST download a 3+meg pdf document which explains just about everything you need to know. If you don't read the huge document then don't complain. I've never seen such straight-forward and illuminating instructions.

Like every other clown I downloaded VBox and fuddled through enough to get XP working. Sort of ....

I am NOT writing a tutorial a such. It's just that I've read a few posts and articles and the pdf instructions are perfectly clear.

A couple of matters:

Once you have, say Window$ XP running in VBox, don't use Ctrl>Alt>Delete if you have a seizure (life is not perfect) because Ctrl>Alt>Delete runs in the 'host' OS -in my case, Edgy- and attempts a re-boot of the whole system as in Linux, which is running the show after all. It's just one of those things ...

So; top left corner is 'Machine' which when clicked on will bring up a menu. Enable>Insert Ctrl>Alt>Delete which will confine that command to the VM scenario. In fact that scary Windoze box will appear. The 'End Task' one.

I'd better go back one step or two(sorry) becos this is very new to me as well.

A program has to be installed called GUEST ADDITIONS to enable mouse transitions. Assuming you have got so far as to having a virtual desktop of your chosen OS, VBox has a drop-menu at top left of screen. In my case, with XP, I click on 'Devices' which at the bottom of the list has 'Guest Additions,' Click and install.

I can't remember what it did becos I'm elderly and I don't really care. I guess it made something happen which was good. 

Ok. 

Back to when you first opened the VBox gui.

There's a list on the right-hand side with a list of blue-highlighted names. I wouldn't worry too much about Serial Ports which are a bit archaic these days, but if you click on USB then this opens a window or 'pane' which has a series of vertically-oriented quiet-looking icons at the far right. Click on the second one down, which should bring up a list of your 'host' OS- included  USB hardware. In my case I just added them all to the open pane, one by one. This exercise enables the 'guest' program to access whatever USB gear is available to your 'host' OS.

Apart from the important USB stuff, it would be good to click upon and enable the other bits there, especially the CDROM, which helps if you want to install other programs to the 'guest' OS!

This is only a general help for newbies getting started with VBox on Ubuntu Edgy, which worked like a wet dream compared with installing on Dapper, where there were kernel module issues and 44 + megs of downloads of headers etc.. 

As always there will be a problem with permissions. I did my install late at night during a few reds. There's a post or two on the Forum about getting these nailed down, and if I could find them at that stage,then anyone else can too!

To finish off. XP is easily accessed with VBox. I have only small RAM (512) but everything is fine until I wanna run a video in XP, when RAM sharing really becomes an issue!

I have one and one only program I need to run on XP, which is a tiny accounting one.

Vbox has made it simply accessible without partitioning and re-boots.

I am a VERY happy camper indeed.

Thanks to all who got me on the right road.

Mike.

---

### Post by hyper_ch on 2007-09-24
well, based on my experience:

VBox:
- it's OpenSource
- it's less ressource demanding than VmWare
- USB doesn't work as well as on VmWare

VmWare (Server):
- with the Server you can create your own virtual machines (vbox can do it also)
- VmWare Server is free (as in free beer) - however you have to register to get some serials
- it is more ressource demainding than VBox
- USB support is better
- it's more stable

I use VmWare over VBox... and those above are my findings...

---

### Post by Chadwick17 on 2007-09-24
Thats good to hear. I love Vbox too, like I stated earlier. The only problem is that one of the programs I need to use causes it to randomly abort. Just vanishes out of thin air. I haven't seen this problem with VMWare Server/Player yet...I would love to go back to Vbox

---

### Post by MichaelSM on 2007-09-24
Hi guys.

All I can say is that VBox 1.5.0 fixes any USB problems. Just update. It's relatively new. And VERY new for me as a noob.

I tried a windoze xp install of my Brother 3240C , using the disc supplied with the printer. 

What a waste of time.

VBox used  correctly migrates the already- established printer on (in my case) to the virtual USB port. This is not a big issue.

What I'm trying to say is that with basic applications, VBox has it all covered. 

I'm not spruiking for VBox.

But I am amazed how easily it wa so seamlesly to run. It's a New World for noobs like me. Just follow the. instructions in the pdf.

Mike.



I just reckon that anyone who reads the instructions on the VBox pdf download would have to be an idiot not to follow them up. It's all there in black and white.

Frankly, I'm astonished.

I didn't think it was possible.

Which is the best bit.

It IS.

Thanks to Innotek'

---

### Post by derjames on 2007-09-24
> **Chadwick17 said:**
> Ok, I've been using VirtualBox more now and I've noticed that it will randomly abort - often too. I've been on teh VirtualBox forums and there doesn't seem to be an answer to this. Disappointing because it runs incredibly fast and smooth otherwise. I think its a ton smoother than Parallels. I'm going to give VMWare Server a try and see how it compares to VirtualBox - I cannot deal with the random aborts of the VM.

Yes... What I can say is that VMware is rock solid everything works and has no random shut downs however is slow... 
VirtualBox is really fast in a significantly more  than VMware however the problem in my computer is that it ramdomly shuts down or freezes the system which is very annoying also I couldn't make VirtualBOX to recognise properly the USB ports... 

I will stick with VMware for the moment and will wait for the next version of VirtualBOX...

---

### Post by Chadwick17 on 2007-09-24
I really don't find that VMWare is as slow as people say it is. I've been running SketchUp and Revit inside of it and it seems to move just as fast as if it were native to Windows. I'm really pleased with VMWare up to this point...maybe once you go to Workstation everything runs faster...not sure...VBox or VMWare and I'm happy. Parallels, in my experience, was the VM system that ran a lot slower...

---

