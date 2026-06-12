---
title: "Just about to give up..."
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by RandomBloke on 2006-04-17
Hi,

Quick round-up of last few days events.
Set up 'was' laptop running XPPro networked by ethernet to main machine which is running XPPro. Laptop serves as _nothing_ but remote desktop client. HDD on lappy CONSTANTLY spinning, I mean from boot up to shut down. BIOS settings are to stop after 5 seconds, though I've tried 10, 20, 1 min, 10 mins etc. No difference.
So, I think something in Windows is setting the driive off (note: drive is not 'accessing'. HDD LED is does not illuminate - drive motor just spins - a l l  the time...). I decide to wipe the drive completely and go to Linux. Research on the web shows Ubuntu to be the best bet, so here I am after playing with the live CD, I installed and so far, love it to bits.
Drive is still constantly spinning, though I have my remote desktop working perfectly - so aside from being free from Windows at least on one machine, I'm no further on. At least with Windows I could get some kind of GUI or config screen up with the smallest of research. With Ubuntu it's taken me a good few days to find out how to run a command line - there's not a great deal of 'new user' friendly posts here! I've been searching all over and it seems everyone presumes that you already know how to use terminal and sudo. I didn't. I just about do now. 

My question is (and I honestly do NOT mean this in any dispariging way, Ubuntu and it's communtiy seems to me to be rock solid and I'm looking forward to being around for a while) - is there somewhere I can go prior to here, where there is a more 'new user' friendly community, a bunch of tutorials not peppered with acronyms, command lines and switches?
Is Linux really so far progressed that it's just not suitable for 'newbies' ?

I'm by no means a thicko - I use HTML/PHP MySQL and PHPAdmin etc for a hobby and sometime job, and pretty much know my way around a Win based machine. I really want to move into the Linux flavour as it's a progression that's long overdue. I'd just like to find somewhere that's a bit more, shall we say, less power user and more welcoming.
Again, not being off there, just finding it hard to fiind my way.

If I could shut the damn hard drive off, I'd be happy for a start.. as it stands, I may as well just reinstall Windoze as I've come no further forward in terms of  shutting this HDD down - if I could, I'd be happy running the lappy as remote desktop to my Win machine over my home network.

(Clevo 2700C latop, 512MB Ram PIII 833 chip, Fujitsu MHM2100AT 10GB drive Ubuntu Breezy latest - BIOS is hopeless - 1997 Award jobby. No update that I can find anywhere so very limited with power management options)

Cheers for any replies, even the sarcy ones - links to sites, forums for newbies etc would be great. I've tried searching, I really have. I run a PHPBB2 and a VBulletin board myself, and I know only too well the qualities of a search first, but those users and their acronyms just pop up everywhere and make it a newbie hell for me.

;)

---

### Post by encompass on 2006-04-17
You can add me as a user to any of my chat clients and I can help answer those starter questions for you.  I have discovered that it is not that linux is beyond beginners... but more so dead on simple it's hard.  I spent so much time looking for somethings not realizings that the answer was right in front of me.
So, if you need help, I can take you on and answer anything that the forums may not.  I am no pro, but I can answer most simple questions.;)
as for your harddrive.... I highly doubt it will stop.  If it is permenently plugged in it shouldn't matter.  I run my lappy as a thin client and it's drive never stops.

---

### Post by RandomBloke on 2006-04-17
Hi mate - thanks. I have MSN installed so family can stay in touch so I'll bear that in mind. :)  Quick point I should have mentioned - my move to Linux was to stop the HDD spin that had BEGUN. It hasn't always been like this! This machine ran failry quietly with the CPU fan kicking in occasionally. Something happened somewhere and I don't remember when, how or why. I just presumed it was Windows that did it. Sometimes it does stop.. And stops completely. But it starts again eventually..! 9 times out of 10 it is a constant whirr, and I just can't stand it any longer.

Cheers for the quick reply.
I've progressed a lot in the last few hours, just discovering that command lines in Terminal need to be preceeded by 'sudo'. Something so simple..

---

### Post by macdo on 2006-04-17
Try [http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#laptopmode](http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#laptopmode)

The laptop-mode-tools package [linked]("http://www.xs4all.nl/~bsamwel/laptop_mode/tools/debian.html")  has command line installation instructions that are nearly correct for Ubuntu users. Just one thing: instead of typing ```
su
dpkg -i laptop-mode-tools_x.y.z.deb
```type```
sudo dpkg -i laptop-mode-tools_x.y.z.deb
```
You will need to change directories to the directory where you downloaded the package: for example, ```
cd /home/user/Desktop
```

I can't say that I know why your HD is spinning such a lot, but that might help. It might be worth considering that the HD is getting older and nearer its failing point...

Consider getting a book about linux - when I first installed linux, I got Linux for Dummies, and although it was woefully out of date, the basic principles were still more or less valid (things like / instead of  \, basic commands, and so on). You could also have a look at [http://www.tldp.org/]("http://www.tldp.org/").

Don't hesitate to email me at macdo10nospamplease_at_free.fr for anything that you can't find in the forums because it's too basic - if I can't answer a question, I can probably point you in the right direction

---

### Post by RandomBloke on 2006-04-17
Again, thank you for your offer of help, I shall bear it in mind. :) 
Yes, you're right, the HDD could be on it's way out - I'm just curious that it will stop eventually..?


Now, I have installed the app, and terminal reports:

"Enabling laptop mode: enabled, not active."

So I typed sudo laptop-mode start (see, I do read the forum..!) and I get "starting laptop_mode"

Now, where might I go from here?

---

### Post by Compucore on 2006-04-17
Hi Randombloke. Being a technoweanie on the hardware side of things. For the PC and laptops. It sounds like it not really linux persay and not really the hard drive itself. Its sound to me. And it can happen from time to time on some systems. Take a look in your bios settings on your laptop. There shuold be a settings for your hard drive for spinning up your hard drive. I remember seeing that in my two clone desktops here where they gave the options under the bios to spin down the hard drive after so many minutes. Take a look manually under the Bios of your laptop to see if they have that option there. My two dell GX 150 don't have them. But most brand name computer and spome clone motherboards have that option in the bios. It could be taken a look into. Sometimes its not that evident with computer systems these days. Sometimes you need to peek and poke around to see where certain things are at with problems like this. 

And it is true that sometimes you need to do the command line instead of being in the GUI environment. Its not to say that you always have to do it. But sometimes you have too. I've came and learnt from the early 90's from the command line and worked my way up. And others who are newbies never really learnt it will not know it. Its not to put either side down. But its more or less the middle of the road where you need to have both. A little bit of knowing the dreaded command line. And other times you can do it in the GUI. But thats my take on it. 


Compucore :-D 


[QUOTE=RandomBloke]Hi mate - thanks. I have MSN installed so family can stay in touch so I'll bear that in mind. :)  Quick point I should have mentioned - my move to Linux was to stop the HDD spin that had BEGUN. It hasn't always been like this! This machine ran failry quietly with the CPU fan kicking in occasionally. Something happened somewhere and I don't remember when, how or why. I just presumed it was Windows that did it. Sometimes it does stop.. And stops completely. But it starts again eventually..! 9 times out of 10 it is a constant whirr, and I just can't stand it any longer.

Cheers for the quick reply.
I've progressed a lot in the last few hours, just discovering that command lines in Terminal need to be preceeded by 'sudo'. Something so simple..[/QUOTE]

---

### Post by RandomBloke on 2006-04-17
Hi Compucore.

I was there too. In the early 80's with the Tandy TRS-80, right through the BBC Model B's and amiga's etc. I've just been spoilt with Windows, that's all!
I need to re-learn, obviously.

As I said ealrier, my BIOS is absolutely useless. Aside from a power saving option, there is nothing else and this however does not seem to work regardless of how I set it.
Perhaps this is indicative of a HDD failure.

---

### Post by Compucore on 2006-04-18
Hi Randombloke,

Well when know what each other means. And yeppers I hear you on that. And again not to put anyone down on this I am also the same on this that windows has also spoiled me too. But I am slowly going back to my old ways on some stuff like the good old command lines. I think I still have a TSR-80 over here somewhere. THe model 1 I think I have here somewhere hiding on me. But thats besides the point here. *And not on topic. Silly goose that I am on that one there.* :) We all have to on some things even myself. Darn it I knew I should have taken notes. Thats why I have my pad and pen over here for that. And then later transcribe them later. Just try this and humour me for a moment on it. Take a look at the power saving option it might be in there to tell the drive to power down after x amount of time. For some reason I thought it might be somewhere else I guess it depends from Manufacturer to manufacturer. Some companies do put it in certain places where as others put it elsewhere.  And it could be that as well. But if it was on the verge of failure It would have been doing something that would not be normal. Or at least act abnormally than it would usually do. Like let the drive ramp up past the maximum speed of the spindle motor. Or the click of death that the IOMEGA drives had a ions ago you know. Something that would actually kill it you know. Or at least give you a chance to back up your data from that computer to the other via the local LAN. 

Compucore

[QUOTE=RandomBloke]Hi Compucore.

I was there too. In the early 80's with the Tandy TRS-80, right through the BBC Model B's and amiga's etc. I've just been spoilt with Windows, that's all!
I need to re-learn, obviously.

As I said ealrier, my BIOS is absolutely useless. Aside from a power saving option, there is nothing else and this however does not seem to work regardless of how I set it.
Perhaps this is indicative of a HDD failure.[/QUOTE]

---

### Post by macdo on 2006-04-18
```
man laptop-mode.conf
```
That should give you the configuration options. The file itself is /etc/laptop-mode/laptop-mode.conf, so to open it you'll need to type ```
gksudo gedit /etc/laptop-mode/laptop-mode.conf
``` Before you start editing, don't forget to save a back-up copy!

When you've finished, restart laptop-mode.

You might want to fire off an email to Clevo support, explaining your problem - who lnows, it could be a common defect! [http://www.clevo.com.tw]("http://www.clevo.com.tw")

---

### Post by gr0kzer0 on 2006-04-18
For learning command line stuff, [http://www.linux.org](http://www.linux.org) has some good tutorials - not for any distro in particular, just generic *nix. I also use Linux Complete, book published by Sybex. A bit old, and leans toward Red Hat rather, but still useful for someone who 3 months ago hadn't even heard of a Bash shell! As for yr HD - if it spins under Windows AND Linux, probably a hardware issue?

---

### Post by encompass on 2006-04-18
haven't read every post here... but it may be important to remember not to use sudo unless you have too... sudo is how you do special things that you normally don't... so don't run everything with sudo... pretty much run it when every your can't do it in the first place, ir if they ask for you to be root.
and as for books... did you know they are coming out with a ubuntu cook book... it is a collection of tips that come in handy.  I am getting a copy, are you?

---

### Post by RandomBloke on 2006-04-18
Big thanks to everyone - really appreciate your replies and your info. 
I've made a backup of the laptop modes conf file and I'll have a play with editing later tonight. Now, I can't drop the backup into the laptop mode folder & so I was guessing that I wouldn't have permissions to edit it either. I haven't - "Permission Denied". At this point I would usually run off Googling and searching here, but someone do a guy a favour and tell me how to enable permissions globally. I hate not being able to move/copy etc stuff about.

---

### Post by r4ik on 2006-04-18
About permissions,

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Good luck !

---

### Post by macdo on 2006-04-18
It's not recommended to enable write access globally for all users - by doing that you lose all the security benefits of linux...
The better way of doing it is to either open a root nautilus window: in the command line, type ```
gksudo nautilus
``` or you can just do the copy from the command line ```
sudo cp /etc/laptop-mode/laptop-mode.conf /etc/laptop-mode/laptop-mode.conf.backup
```
The cp command means copy, so what you're doing is copying the file to a new file called laptop-mode.conf.backup. You can of course call that file anything you want!

---

### Post by WoodyMahan on 2006-04-18
Provided to me by SD-Plissken:  A host of tutorials on the command line and bash interface.  Most of this will seem familiar and be easy to put into perspective with your knowledge of DOS.

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
[http://www.perpetualpc.net/srtd_commands_rev.html](http://www.perpetualpc.net/srtd_commands_rev.html)
__________________
[http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html) [http://www.eff.org/](http://www.eff.org/) Registered Linux User #398933..

---

### Post by RandomBloke on 2006-04-18
Cheers lads and thanks for the links. Copied file successfully, ta.

Can't use the gksudo command - I get the following error:

```
(nautilus:9509): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

--- Hash table keys for warning below:
--> file:///

--- Hash table keys for warning below:
--> file:///

(nautilus:9509): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:9509): Eel-WARNING **
```


Just going to check the permissions link given by R4ik

---

### Post by macdo on 2006-04-18
Interestingly, I get the same sort of errors when I use gksudo nautilus:
```
macdo@moria:~$ gksudo nautilus

(nautilus:28094): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

--- Hash table keys for warning below:
--> file:///

--- Hash table keys for warning below:
--> file:///

(nautilus:28094): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:28094): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)
```
Difference is, Root nautilus works just fine...
Try ```
sudo nautilus
```

---

### Post by RandomBloke on 2006-04-18
[QUOTE=macdo]
Try ```
sudo nautilus
```[/QUOTE]

That works mate - thanks.
I'm a good way into a whiskey bottle right now to safely edit so will try later.
What's the difference there with gksudo and sudo?

---

### Post by RandomBloke on 2006-04-18
ok, enabled laptop mode, changed various values (researched here) to try and shut the drive down all with no luck. Plus side, I'm loving the control and command line actions - nice one.
Neg side, hard drive is still whirring away.
Fujitsu have (surprisingly, given the age of the drive and me not being a direct customer) been trying to help me but of course are limited to what they can do or advise. It's looking more and more like I need a new HDD.
That will be the last money I spend on this machine, as I've spent to upgrade chip and memory and now struggled with OS!
Cheers to all again.

---

### Post by macdo on 2006-04-18
gksudo is graphical - so it works if you use it in alt+F2 
In other words, it's a frontend for sudo, prettier but essentially the same...
synaptic has the same relationship with apt, for example.
It's often the case that there are several frontends for one actual program.

Have a drink for me - and I'll have one for you (Whisky here!)

---

### Post by RandomBloke on 2006-04-19
It was whiskey here to mate.. Suffering a little today!
I've had some success today with this HDD - at the moment now, it's is utterly silent. I'ts kicking in every now and then and stays on for a couple of mins, then shuts off again. I presume that's regular OS polling.The great thing is I've just installed a twin CPU fan I got off eBay to replace the single unit in this machine. (New unit in the inset)

[img]http://img87.imageshack.us/img87/2761/knlttw1fs.jpg[/img]

 I've now added a 1Ghz processor replacing the 833Mhz original one. I'd say with the HDD static, the case temperature has dropped by 50-75%! Something has definately gone right since installing laptop mode - I'm a bit wary of starting any apps or anything in case it sets the HDD off ;). Hope I haven't jinxed this by celebrating early, buthis laptop hasn't run so c o o l and quiet in about 4 years. Massive, massive thanks to everyone for their help. I can only presume the BIOS power management setting has somehow decided to give up and this one is taking over. I'm gonna install XP again soon to see if there's the same improvements.

Anyone know if I can get laptop mode to start with the boot-up rather than me manually starting it each time?


EDIT - 2 hours on, system still cool as a cucumber and still running silent, fan kicks in when I do processor intensive work asdoes the HDD. Both resume to silent when tasks are done and/or CPU cools.

---

