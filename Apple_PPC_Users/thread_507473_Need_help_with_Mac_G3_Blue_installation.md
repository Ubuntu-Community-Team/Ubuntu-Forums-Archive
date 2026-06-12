---
title: "Need help with Mac G3 Blue installation"
date: 2007-07-23
forum: Apple PPC Users
---

### Post by Midwest-Linux on 2007-07-23
I have a Mac G3 BLUE 300 mhz - 384 RAM - 3.6 HD - 9.0 mac OS    .The CD rom works fine.

I tried installing the Kubuntu Live 6.0 for Mac, problem is the computer says it cannot open the extensions. Even then if it did you could only open up one file at a time It would be impossible to click on the whole program to start it.

So I decided to use the alternate install Kubuntu 6.0 instead. it would not boot from the CD ROM when starting the computer it would go to mac 9.0 OS instead. 

I tried using the hold down C and turning on the computer, it went to the Mac 9.0 OS instead.

I tried using the cmd + option + p + r to get to the prompt and to reset the OF defaults and get me to the command line. It went to Mac 9.0 OS instead.

Next I tried Apple+Option+O+F now I am faced with a blank screen. I typed ctrl-option-F1 to  get to the command prompt and see nothing. I still have a blank screen. I got these tips I mentioned from the various ubuntu/kubunu forums.

What do I need to do from this point?  Thanks for your help in advance.

---

### Post by Midwest-Linux on 2007-07-23
Just a update I tried this , Command - Option -Shift -Delete. Now instead of a dark screen or the Mac OS 9.0 running. The screen is white. 

What do I do now?

---

### Post by Midwest-Linux on 2007-07-23
Anyone?

---

### Post by amicheals on 2007-07-23
hello,

I hope this helps. I found this post somewhere, I don't remember:

How do I get Ubuntu working on an iMac G3?
Do you get a blank screen after booting? The problem is that xorg.conf is not set up properly for the iMac G3.
Follow these steps to fix xorg.conf:
After booting is complete:
0.	Type: ctrl-option-F1 (should give you a command prompt, may take a couple of tries)
0.	Type: sudo nano /etc/X11/xorg.conf (return)
0.	In the Monitors section, change "HorizSync" to 58-62 and "VertRefresh" to 75-117.
0.	Disable DRI. In the the Modules section, put a hash mark (#) at the beginning of the line containing "load dri".
0.	Type: ctrl-O (return) to write edited file
0.	Type: ctrl-X to exit nano back to command line
Type: sudo /etc/init.d/gdm restart (return) to restart Gnome. (In Dapper and Edgy, the restart command is broken. Use sudo killall -HUP gdm instead.)

Amy

Let me know if this works

---

### Post by Midwest-Linux on 2007-07-23
Thanks Amy

I think I have may found a part of the problem. Nothing has been assigned for the  keyboard commands for the F1 through F12. Now, what do I associate F1 with? 

Thanks again for your suggestions.

---

### Post by Midwest-Linux on 2007-07-24
I am still having problems. I hold the following down Apple+Option+O+F and turn the G3 on with the dapper dan iso disc using the alternate install disc for power pc for mac. Then the screen goes black then I hold ctrl-option-F1 ...nothing happens. I try ctrl-option-F1 several times and still nothing happens. 


I read several posts about Apple's use of hot keys for F1 - F12 and it seems in one post that for simple commands like the one I am trying to do which is go to the command prompt should not be a problem.

 However in yet another it seemed to say I must set up the F keys and associate them. This is getting fustrating. My problem isn't trying configure Ubuntu or setting it up. But rather trying to get to the command prompt to change the video settings so I can finally install this.

Is there another way to get to the command prompt? Do I have to associate the F keys before I can use ctrl-option-F1 ? What am I missing here?

---

### Post by tonyr on 2007-07-24
First of all, you don't have to hold down any keys until after you power on the machine, normally
after you hear the power-on chime.

It is possible that the alternate CD is bad. How did you create it?  Does it boot on any other Mac?

Did any of your installations complete at all?  The Ctl-Alt-F1 sequence only works to get to a
console (virtual terminal) if Ubuntu is actually installed.  

I have installed Edgy (6.10) and Feisty (7.04) on many G3 machines without problems.  Did
you consider using one of these newer distributions?

- tony

---

### Post by tonyr on 2007-07-24
More stuff.

Apple-Option-O-F is for booting into the OenFirmware monitor, and has nothing to do with booting
from the CD.  OpenFirmware is Apple's (New World) kind-of-equivalent to BIOS in the PC world.  After you turn on the machine and hear the chime, then hold down Apple-Option-O-F, and keep
holding them.  If things are working correctly, you should eventually see an Open Firmware
welcome message and a prompt that looks something like '0>'.

Again, this has nothing to do with getting the installation to boot from the CD.

- tony

---

### Post by Midwest-Linux on 2007-07-24
Thats all I need to do is to get to the prompt and I can take things from there. I only have one Mac, this one..so I cannot try the install disc on any other mac. 

 Does it matter is I have the install disc in when I want to get into the prompt? Or should I try to go to the prompt with or without the install disc in to change the video setting?


 Right after the chime I pressed the Apple-Option-O-F and held it down for 3 minutes , the monitor blinked and continued to stay black. Its like the machine refuses to into prompt or refuses to display prompt. 

Could it be the monitor? Its a FPD1760 Gateway LCD monitor. It works normally with every computer I connected it with, including the Mac when running 9.0 OS. 

Could something be wrong with the Mac bios preventing me to see the prompt or go to prompt?

---

### Post by 3rdalbum on 2007-07-25
I believe the original poster has not yet booted Ubuntu/Kubuntu.

Midwest-Linux, what program did you use to burn the CD?

If you just drag the .iso file to a CD, that will not suffice to boot up your Mac. Neither will opening the .iso file and dragging its contents to a CD. **You MUST use the "Disc Image" function of your burning software.** On some versions of the Mac OS, opening the .iso file will destroy it; so if you have already done that you will need to download a fresh copy of the disc image.

---

### Post by Midwest-Linux on 2007-07-25
Thanks for the reply, I am using Nero Smart Start -Burn image to disk. And yes I am using the power PC version alternate install of Kubuntu 6.06.1, I even tried the Ubuntu 7.04 power pc version alternate install. is there a different Ubuntu/Kubuntu I should be using?

I also previously used Nero Smart Start- Burn Image to Disk when I installed kubuntu on another computer a windows based machine . If there is something else I need to be using to burn the ISO disc, please let me know. Also I am using Tayo Yuden Fuji CDs for the image burn disk.

One last thought, do you think that maybe I should be looking at a completely different reason on why this is not going to prompt or booting? What if I  replace the battery (3.6 volt lithium) and reset the CUDA as I seen in a post on these forums. I didnt consider this before as the Mac OS 9.0 is able to boot without a problem and some posts in different forums seem to say that the Mac  OS would not boot if the 3.6 volt lithium is shot. Again the Mac OS 9.0 boots, so could the battery still be bad yet?  How important IS the 3.6 volt battery for installing ubuntu/kubuntu anyway, would a bad battery prevent me from booting the install disk and also prevent me from going to prompt?

---

### Post by Midwest-Linux on 2007-07-25
> **thanos12 said:**
> i had the same problem a year ago :(
[IMG]http://s4.bitefight.gr/c.php?uid=15792[/IMG]

Was it the battery that kept you from installing ubuntu/kubuntu on a G3 Mac?

---

### Post by pxwpxw on 2007-07-25
> **Midwest-Linux said:**
> Just a update I tried this , Command - Option -Shift -Delete. Now instead of a dark screen or the Mac OS 9.0 running. The screen is white. 

What do I do now?

When this happens, do you see anything on the screen?  0> ? It sound like openfirmware.
If you can get into open firmware you should be able to boot from there, using files copied from the CD.

---

### Post by Midwest-Linux on 2007-07-25
> **pxwpxw said:**
> When this happens, do you see anything on the screen?  0> ? It sound like openfirmware.
If you can get into open firmware you should be able to boot from there, using files copied from the CD.

 Nothing but white, like the background white like when the OS 9.0 is starting up..but no cursor or anything. Thats what I just did right now yet again and I see nothing but white. No cursor, no prompt...just white. 


This is unlike anything I have ever encountered with a windows based machine. A windows based machine its real easy to get to the prompt. A windows based machine ( in most circumstances) will boot from a CD . Apple made a entirely different animal, and seemingly more complicated. 

This is why I am thinking that must be some other issue that I am overlooking, maybe the battery which controls the bios and its not enough power to let me go to prompt, though that should not be a issue because other forums have stated if the battery was shot...I would not be able to boot at all. And the battery should not BE a issue because the power from the wall is certaintly enough to power the board.

Maybe I have video card issue, but if that is the problem...then Mac OS 9.0 would have issues with resolution and it doesn't. I cannot see the prompt, therefore I cannot go to prompt, it will not display the prompt. I doubt it is the video card.

Then I was thinking its the monitor, but that cannot be as I am able to view the Mac OS9.0 just fine and when I installed Kubuntu on a windows based machine I was able to see the dos prompt on that monitor.

Then I see on this computer that I am supposed to associate the F1 through F12 keys before I am able to use F1. So that means I cannot use Ctl-Alt-F1 . So then if thats the issue...then what DO I associate F1 with? Or am I missing something here and the F1 - F12 association is not even a issue.

I still have a white screen after Command - Option -Shift -Delete and nothing else is displayed.

---

### Post by Midwest-Linux on 2007-07-26
The next thing I tried to do is to get a new battery for it, to see if a bad battery is keeping me from installing ubuntu. The Mac G3 runs on a 3.6 Lithium battery for the bios, model er3s. I went to Radio Shack, Best Buy, Circuit City and even tried Walgreens and none of them carried it. They did carry a   CR2 a 3 volt camera battery but I need a 3.6 volt and a correct size. It looks exactly like 1/2 the size of AA. 

 Why did Apple use such  a obscure battery that no one has ever heard of or ever carried  and why 3.6 volts? I see they are plenty of sources on the net which to buy the 3.6 volt battery that I need, but now that means a week or so delivery and more waiting and even then I am not sure that is the problem of why I cannot go to prompt or boot the install ubuntu Cd. The computer is plugged into the wall and that isn't enough power to run the bios and only a 3.6 battery can?

I am going to try either 3 volts or 4.5 volts using two or three AA batteries in series as a alternative before I waste $10 on a wild goose chase.  I think I finally know what the G stands for in Mac G3.

---

### Post by Midwest-Linux on 2007-07-26
I have 3 volts on the bios board now, I once again pressed cmd + option + p + r to change the time from 1956 to today and it still reads 1956..nothing got updated. So that likely means that I still will not be able to go to prompt either and 3 volts is not doing it. I'll have to try 4.5 volts next....thats even if the bios battery is the issue of the whole problem.

---

### Post by pxwpxw on 2007-07-26
I think you are way off track with the problem. Check your battery voltage on a voltmeter. The time only gets reset if you are network connected, usually by macos setting the time then restarting. If you have bad time that may well be the total problem  Try that, then need to get back to base without all the confusing factors arising from unfamiliarity with mac. The first thing is to get into openfirmware which is fundamental. Also please exactly what AppleMac G3 have you got there, there are some differences in open firmware basics.

---

### Post by Midwest-Linux on 2007-07-26
If I could get into open firmware I know it would solve a lot a problems. The problem is I cannot get to firmware, I cannot get to prompt, I cannot boot from the CD, I cannot even run from a live CD because Mac OS 9.0 does not know or recognize what programs to open up the live CD with . So I went with the text based installer Dapper Dan PPC alternate CD , and I could not boot from it, run  from it. It might be going to prompt, but the video is a blank screen.

I have a Mac G3 BLUE 300 mhz - 384 RAM - 3.6 HD - 9.0 mac OS .The CD rom works fine. As far as firmware, I have no idea. Is there another way of displaying firmware or prompt?  Like a back door way of going into the system setup?

 AM I right in saying that the battery backup in the bios is not important to keep me from going into the firmware, prompt, or booting from a CD ? Or is that 3.6 battery holding me back from everything? Is everything displaying like it should and my monitor is just  not picking it up?

---

### Post by pxwpxw on 2007-07-26
Sorry but "Mac G3 BLUE" is meaningless to me.
Is it an iMac or a Powermac (tower)?
Does it have firewire or scsi ports?
That might narrow it down.

---

### Post by 3rdalbum on 2007-07-26
If possible, try downloading and installing the firmware updates; it sounds like there's something wrong with your firmware.

Another thing you could try is holding down Command-Option-N-V, which resets the NVRAM (the memory that holds OpenFirmware's settings). In my humble opinion you're looking in exactly the wrong place - this is not a PC, this is a Mac, and on Macs the battery holds time and date and very little else. The NVRAM holds the majority of the interesting bootup settings, and does not need any power to maintain its settings (NV stands for "non-volatile".

Also, forget about Command-Shift-Delete - it won't boot up a CD. You must hold down the C key instead.

When you talk about the blank white screen, is this before or after you get the Yaboot text on the screen? It's before, right?

---

### Post by tonyr on 2007-07-26
Batteries:  Many people report that Radio Shack does indeed have them, but that saying 'Apple' 
or '/Mac' might cause some response like "We don't carry Apple parts".  This web page 
 [http://www.academ.com/info/macintosh/]("http://www.academ.com/info/macintosh/")
gives some information about replacement batteries, and even mentions Radio Shack as one of
the suppliers.  
The red/silver version of the battery (probably the one you currently have) is a 
**Maxell ER3S LS14250 SBAA02 1/2 AA Lithium Battery**, picture at
[http://cgi.ebay.com/NEW-Maxell-ER3S-LS14250-SBAA02-1-2-AA-Lithium-Battery_W0QQitemZ300133927921QQihZ020QQcategoryZ80034QQrdZ1QQssPageNameZWD2VQQcmdZViewItem]("http://cgi.ebay.com/NEW-Maxell-ER3S-LS14250-SBAA02-1-2-AA-Lithium-Battery_W0QQitemZ300133927921QQihZ020QQcategoryZ80034QQrdZ1QQssPageNameZWD2VQQcmdZViewItem")

Another popular one is **SAFT Lithium 3.6 Volt Battery LS 14250 1/2 AA**, picture at
[http://cgi.ebay.com/One-Pair-SAFT-Lithium-3-6-Volt-Battery-LS-14250-1-2-AA_W0QQitemZ170133686242QQihZ007QQcategoryZ101364QQcmdZViewItem]("http://cgi.ebay.com/One-Pair-SAFT-Lithium-3-6-Volt-Battery-LS-14250-1-2-AA_W0QQitemZ170133686242QQihZ007QQcategoryZ101364QQcmdZViewItem")

---

### Post by tonyr on 2007-07-26
To test the battery it HAS to be removed from the board.  If it shows anything less than 3.4v, it's
starting to go bad.  A good one generally tests in the range 3.64v to 3.69v.

Firmware updates have to be installed from Mac OS 8.5 or 9 as far as I can tell, and they have to be
installed from an installer copy that is resident on the hard drive.  Here [http://lowendmac.com/lab/05/0301.html]("http://lowendmac.com/lab/05/0301.html")
is an article about how to do it.

- tony

---

### Post by Midwest-Linux on 2007-07-26
> **pxwpxw said:**
> Sorry but "Mac G3 BLUE" is meaningless to me.
Is it an iMac or a Powermac (tower)?
Does it have firewire or scsi ports?
That might narrow it down.

 It is the tower, it has two USB ports, one firewire connection, CD-ROM, floppy slot loader.

---

### Post by Midwest-Linux on 2007-07-26
> **tonyr said:**
> Batteries:  Many people report that Radio Shack does indeed have them, but that saying 'Apple' 
or '/Mac' might cause some response like "We don't carry Apple parts".  This web page 
 [http://www.academ.com/info/macintosh/]("http://www.academ.com/info/macintosh/")
gives some information about replacement batteries, and even mentions Radio Shack as one of
the suppliers.  
The red/silver version of the battery (probably the one you currently have) is a 
**Maxell ER3S LS14250 SBAA02 1/2 AA Lithium Battery**, picture at
[http://cgi.ebay.com/NEW-Maxell-ER3S-LS14250-SBAA02-1-2-AA-Lithium-Battery_W0QQitemZ300133927921QQihZ020QQcategoryZ80034QQrdZ1QQssPageNameZWD2VQQcmdZViewItem]("http://cgi.ebay.com/NEW-Maxell-ER3S-LS14250-SBAA02-1-2-AA-Lithium-Battery_W0QQitemZ300133927921QQihZ020QQcategoryZ80034QQrdZ1QQssPageNameZWD2VQQcmdZViewItem")

Another popular one is **SAFT Lithium 3.6 Volt Battery LS 14250 1/2 AA**, picture at
[http://cgi.ebay.com/One-Pair-SAFT-Lithium-3-6-Volt-Battery-LS-14250-1-2-AA_W0QQitemZ170133686242QQihZ007QQcategoryZ101364QQcmdZViewItem]("http://cgi.ebay.com/One-Pair-SAFT-Lithium-3-6-Volt-Battery-LS-14250-1-2-AA_W0QQitemZ170133686242QQihZ007QQcategoryZ101364QQcmdZViewItem")

 The manager of the Radio Shack store said to me, " I never even seen one of these",instead  I found a place in Cincinnati called Batteries Plus that sells the 3.6 volt batteries I will go there tonite. On the battery it is stamped 98 - 12 , probably the date of manufacture. Its the maxell OEM battery.

---

### Post by Midwest-Linux on 2007-07-26
> **3rdalbum said:**
> If possible, try downloading and installing the firmware updates; it sounds like there's something wrong with your firmware.

Another thing you could try is holding down Command-Option-N-V, which resets the NVRAM (the memory that holds OpenFirmware's settings). In my humble opinion you're looking in exactly the wrong place - this is not a PC, this is a Mac, and on Macs the battery holds time and date and very little else. The NVRAM holds the majority of the interesting bootup settings, and does not need any power to maintain its settings (NV stands for "non-volatile".

Also, forget about Command-Shift-Delete - it won't boot up a CD. You must hold down the C key instead.

When you talk about the blank white screen, is this before or after you get the Yaboot text on the screen? It's before, right?

Probably the firmware is corrupt, if Apple has firmware updates for free..I can probably do it.  The thing is the firmware will get erased anyway when and If I ever get linux installed on the G3.

I very well am likely looking in the wrong place. Unfortunately what has tripped me up with this battery and time thing is the following comment 

" The second problem that can turn up is whats kindly reffered too as the "date bug", basically OF (Open Firmware, Apples version of a bios) stores all its data with the help of a pram battery, a lot of people would refer to it as a kind of bios battery. This bug can and will break the install of Ubuntu in many cases causing very weird things to happen."   [http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)


I tried the C Key to boot the CD, and every combination recommended here so far. Either these prompts ended with leaving me with nothing but the Mac OS 9.0 booting up as normal, or a dark screen with no prompt, a white screen with no prompt. I have not been able to go to firmware, boot, prompt...nothing. I can run the Mac 9.0 OS . The CD Rom works fine as I was able to install some Mac browsers on it like Opera and Netscape.

Another thing If I try CRTL-Shift-F1 to take to the terminal (like I have seen in other comments), a window pops up asking me to associate the F1 through the F12 keys. So what do I have to associate F1 with?

I worked on different machines before been around computers for a little while, I never seen anything like the issues I have with this machine. It should have been a 30 minute simple installation and a few more hours to tweak. Its been days now just trying to get to a prompt or firmware menu. 

(I had some issues trying to install Kubuntu on a different win based machine. I ended up using boot and nuke to wipe the HD clean, then used the alternate text based installer and a hour or so that was it)

---

### Post by Midwest-Linux on 2007-07-26
> **3rdalbum said:**
> If possible, try downloading and installing the firmware updates; it sounds like there's something wrong with your firmware.

Another thing you could try is holding down Command-Option-N-V, which resets the NVRAM (the memory that holds OpenFirmware's settings). In my humble opinion you're looking in exactly the wrong place - this is not a PC, this is a Mac, and on Macs the battery holds time and date and very little else. The NVRAM holds the majority of the interesting bootup settings, and does not need any power to maintain its settings (NV stands for "non-volatile".


I pressed Command-Option-N-V . The Mac OS 9.0 booted up as normal and now a window pops up and asks if I want to rebuild my desktop file on main. What should I do now?

---

### Post by Midwest-Linux on 2007-07-26
> **Midwest-Linux said:**
> I pressed Command-Option-N-V . The Mac OS 9.0 booted up as normal and now a window pops up and asks if I want to rebuild my desktop file on main. What should I do now?

 I hit yes and it rebuilt my desktop and nothing else happened I am back into the Mac OS 9.0 with no apparent changes.

---

### Post by Midwest-Linux on 2007-07-26
Well I bought the 3.6 volt Lithium battery, installed it. Did all the command prompts I tried in the past and no success. I downloaded the G3 firmware updates onto the mac. I dragged the update icons to the desktop (Mac will not let you click on the icons from the disc...you have to drag them to desktop then click on them to install the updates...why? Did I have to install into the main c drive instead? How do I do that through the prompt which I cannot access???) Did I mention the date still says 1956?

Clicked the G3 firmware updates, it said the computer has updated firmware. The readme file says to push that programmers button in on the bottom right to the main power button and start it up and it should go to prompt with some instructions. Guess what, I did that and no prompt, no instructions...just a blank screen.

Well,to  be honest I think its time to mothball this project. Something is definately seriously wrong with this computer and frankly I'd be wasting my time and more of everyones time here trying to make something work that cannot be done. Thanks for your comments and help. I need to move on to other projects now and will stick with win/pc based computers that I can work with. Thanks for all your help.

---

### Post by pxwpxw on 2007-07-27
Did you reset the date/time manually from Macos?

---

### Post by Midwest-Linux on 2007-07-27
> **pxwpxw said:**
> Did you reset the date/time manually from Macos?

 Yes I did, it was done through Control Panel, Date and Time and Update through network. I even updated the software using the software update which is 1.2 from Mac. Ok, but I could not go to prompt, view prompt, I had a blank screen no matter what commands I tried to get to boot the disc or no matter what I did to get to prompt open firmware menu...it would not view it or bring it up. Its not a monitor problem either as I have switched monitors tonight to see if that was the problem..it wasn't. 

For some reason the computer is not letting me go to the prompt cursor, or letting me view it. I tried all the commands at least 20 times each, clearly something wrong  is with the computer as seemingly every post I read in the Apple PPC ubuntu forums, everyone was able to view their firmware or was able to get to the prompt. Thats the problem I have been having, I cannot get to/view/bring up/display anything other than a working Mac 9.0 OS. 

Either something is turned off in this computer thats stopping me from going to/viewing the prompt/firmware..or this computer is just unable to . The Mac OS 9.0 works good otherwsie and so does the CD-ROM. 

Maybe I am supposed to light a candle and chant while looking for the blessed firmware or prompt.

---

### Post by pxwpxw on 2007-07-27
I think you should have a lot more tries at the basic open firmware access 4 keys
Command(Apple) - Option - O - F
On every Apple Mac I know of, this is universally the way tp get into open firmware.
You can hold these keys down first then restart and keep holding them down, you should get a whitish screen with some text and the 0> prompt.
There are some refs say to hold them down after you hear the chime but before it stops.

Another easy option is to hold donw the Option key while starting up with the CD int the drive, on most macs that should produce a screen with boot icons (before Macos get started), but this may noit happen it there is only the one system to boot (i.e. macos).

But the results depend to some extent on the Mac vintage and model, and I am still mystified about that.
Some early mac G3's open firmware did not put output on the screen until reconfigured to do so (by typing blind or with macos utilities). You might have one of them, we dont know.

The suggestion above by 3rdalbum to try Comand - Option - N - V shoudl also be tried.

You should also "Zap the Pram"  4 keys Command - Option - P - R  at startup before the chime and until you hear a second chime. That will reset openfirmware. You should do that first.

Finally try setting the time again and see if it sticks. And recheck your battery voltage.
The relevance of this is that incorrect time has been the cause of some install failures, 
and will cause great problems if not fixed in ubuntu,
but that is not really and issue until you get an install started, you are no where near that stage, you have a Apple mac problem it seems.

As there are a number of actions to do, you may have to work through it and repeat some.

Its not a windows pc its a mac.
Good luck.:)

---

### Post by Midwest-Linux on 2007-07-27
I will try those commands yet again. 


I downloaded Edgy desktop for ppc Nero Smart start Tayo Yuden Fuji CD ISO image burned at 4X (my lowest setting). Put disc in the  Mac G3, shut down and hit start pressing C, screen went dark and then the screen is total white and thats where I am at now....I do not even hear the HD running now and CTRL+OPTION+F1 is not doing anything. 

I am spending way too much time on this for what should be a simple installation. I have ubuntu/kubuntu on two other win/pc machines that needs tweaking yet. My plan was to install this on the G3 get up and running, go back to the other 2 computers and tweak them out and go back to the G3. 

( One computer a pc/win based Compaq 1200 Presario laptop gave me a lot of issues including the white screen  problem that I am having now...however the solution for that was to use Boot and Nuke HD eraser free utility from Soundforge...wipe the HD clean..then install the text based version and it worked though I have to do some serious tweaking yet on that machine..it says it needs force one and fairly slow boot up)

(On yet another machine I have Ubuntu already installed on a Pentium 3 700Mhz 256 MB, I bought it off the net for a good price pre-installed, works fine...I just need to tweak that machine so I can stream audio off the net..can't get there yet...something needs to be tweaked....but thats another whole issue)

---

### Post by Midwest-Linux on 2007-07-27
> **Midwest-Linux said:**
> I will try those commands yet again. 


I downloaded Edgy desktop for ppc Nero Smart start Tayo Yuden Fuji CD ISO image burned at 4X (my lowest setting). Put disc in the  Mac G3, shut down and hit start pressing C, screen went dark and then the screen is total white and thats where I am at now....I do not even hear the HD running now and CTRL+OPTION+F1 is not doing anything. 

 OK it has been over a hour after I booted Edgy desktop for ppc. I am still having a white screen and the thats the way it is been for over a hour. I press CTRL+OPTION+F1 several times and nothing happens. 

OK..what am I doing wrong?

---

### Post by pxwpxw on 2007-07-27
> **Midwest-Linux said:**
> It is the tower, it has two USB ports, one firewire connection, CD-ROM, floppy slot loader.

Ah, missed that. Floppy might be useful. Not sure if that makes it a 'Blue&White' will check.

---

### Post by pxwpxw on 2007-07-27
> **Midwest-Linux said:**
> OK it has been over a hour after I booted Edgy desktop for ppc. I am still having a white screen and the thats the way it is been for over a hour. I press CTRL+OPTION+F1 several times and nothing happens. 

OK..what am I doing wrong?

You re jumping too far ahead.

Ctrl Opt F1 only relates to a Ubuntu system after the installer has been started, means nothing to the Mac or Macos, 

Also there is no command line prompt in Macos8 or 9. Not even a terminal. No use looking for that.

There is command line in Open Firmware, but its a bit weird, runs on Forth.

I need to check about that floppy drive and what Mac versions it existed , you can boot using that. Most important is to confirm that Open Firmware is OK by  cmd  opt  o f, Open Firmware starts off the whole system. Just give that another  good try while I check re that floppy drive. You might also confirm that in Macos everything works properly - it is macos9 is it?

EDIT:
Does that mean the CD actually booted, how can you tell?

---

### Post by pxwpxw on 2007-07-27
Is this your G3?


[http://ubuntuforums.org/showpost.php?p=2948648&postcount=24]("http://ubuntuforums.org/showpost.php?p=2948648&postcount=24")

---

### Post by Midwest-Linux on 2007-07-27
> **pxwpxw said:**
> You re jumping too far ahead.

Ctrl Opt F1 only relates to a Ubuntu system after the installer has been started, means nothing to the Mac or Macos, 

Also there is no command line prompt in Macos8 or 9. Not even a terminal. No use looking for that.

There is command line in Open Firmware, but its a bit weird, runs on Forth.

I need to check about that floppy drive and what Mac versions it existed , you can boot using that. Most important is to confirm that Open Firmware is OK by  cmd  opt  o f, Open Firmware starts off the whole system. Just give that another  good try while I check re that floppy drive. You might also confirm that in Macos everything works properly - it is macos9 is it?

EDIT:
Does that mean the CD actually booted, how can you tell?

The screen is still white from 5 am this morning . Just sitting there doing nothing. That floppy drive doesn't work, I tried putting a floppy in and it would not take unless its some sort of zip drive. 

So Mac does not have a command line...Ok ...I been looking in the wrong direction. I do not know if it booted, it seemed to boot as  you can hear the CD-ROM spinning , when I pressed start and held down C. (I tried start and hold down C a couple of days before and nothing happened) . I pressed start and held down C, the screen went dark, then white and you could hear the CD-ROM spinning on and off and then the screen went white...so something happened....I assume it booted...

 I am going to  do the cmd+opt+o+f yet again...I thought I did it after putting the new battery in yesterday . I must have done all the commands like 20 times in the past week. 

I just did the cmd+opt+o+f  and now the screen is black...

Like I said earlier...it think its time to end this project...this is taking way too much time..I have my other linux projects to work with and I must move on... I am doing the same commands, burning the same discs, 4 pages here on the forums, spent $ 10 on a new battery, burned many ISO's wasted good CDs on, dapper, fiesty, edgy, desktop and alternate install, did the firmware updates, set the time and date, and nothing has been fixed, solved or installed...I appreciate everyones help...but there is a bug in this computer, maybe its just me who cannot grasp the "simplicity" of a Mac machine. Time to move on.

---

### Post by pxwpxw on 2007-07-28
Re reading the thread the black or white screen problem may well be due to incompatible video mode between open firmware, the installer and the LCD monitor, even assuming the video card is the original. This is preventing you seeing what is going on. You may get a clue from the LCD monitor on-screeen display of video resolution when the black screen is happening. LCD screens were not so common in the Blue&White G3 era. 

When/if you want to do any more you can probably get much better hands-on help out of Apple Discussions for B&WG3. link below.

[URL="http://discussions.apple.com/category.jspa?categoryID=105"] Apple.com > Support >   Discussions   >  Older Hardware Products  
 Category : Older Hardware Products [/URL]

---

### Post by Midwest-Linux on 2007-07-28
> **pxwpxw said:**
> Is this your G3?


[http://ubuntuforums.org/showpost.php?p=2948648&postcount=24]("http://ubuntuforums.org/showpost.php?p=2948648&postcount=24")

correct

---

### Post by Midwest-Linux on 2007-07-28
> **pxwpxw said:**
> Re reading the thread the black or white screen problem may well be due to incompatible video mode between open firmware, the installer and the LCD monitor, even assuming the video card is the original. This is preventing you seeing what is going on. You may get a clue from the LCD monitor on-screeen display of video resolution when the black screen is happening. LCD screens were not so common in the Blue&White G3 era. 

When/if you want to do any more you can probably get much better hands-on help out of Apple Discussions for B&WG3. link below.

[URL="http://discussions.apple.com/category.jspa?categoryID=105"] Apple.com > Support >   Discussions   >  Older Hardware Products  
 Category : Older Hardware Products [/URL]

This explanation makes more sense than anything I heard to date. Maybe a low tech CRT monitor would solve the problem...I do not have one...I'll see If I can borrow one. It will be days before that happens. But I belive this is the problem. The  monitors one is a 17" Gateway LCD, the other one is a 13"  E-Machine LCD, I tried swapping them out to see if would solve the issue..it didn't. Kind of surprising that I have the only problem like this of all the Apple PPC posts here....thanks again.

---

### Post by Midwest-Linux on 2007-07-28
> **Midwest-Linux said:**
> This explanation makes more sense than anything I heard to date. Maybe a low tech CRT monitor would solve the problem...I do not have one...I'll see If I can borrow one. It will be days before that happens. But I belive this is the problem. The  monitors one is a 17" Gateway LCD, the other one is a 13"  E-Machine LCD, I tried swapping them out to see if would solve the issue..it didn't. Kind of surprising that I have the only problem like this of all the Apple PPC posts here....thanks again.

 So again my problem trying to install Ubuntu on a G3 seems to stem from me not seeing the install process, but I can otherwise view the Mac OS 9.0 fine. So if that is the issue, a low end CRT monitor might be the answer...but are there any other methods to correct this? 

 I there any way of going into the video card menu and changing its values so it would display the install so I can see whats going on? Is there any apple updates I can use so my monitor can view the install? Would a outboard converter (which I have) that changes the monitor output to a TV signal work and bypass the display problem? Am i the only one with this issue? What kind of monitors is everyone using? LCD? CRT? There is got to be a simple answer as I won't be able to borrow a CRT monitor for a few days.

---

### Post by ckarston on 2007-07-29
> **Midwest-Linux said:**
> So again my problem trying to install Ubuntu on a G3 seems to stem from me not seeing the install process, but I can otherwise view the Mac OS 9.0 fine. So if that is the issue, a low end CRT monitor might be the answer...but are there any other methods to correct this? 

 I there any way of going into the video card menu and changing its values so it would display the install so I can see whats going on? Is there any apple updates I can use so my monitor can view the install? Would a outboard converter (which I have) that changes the monitor output to a TV signal work and bypass the display problem? Am i the only one with this issue? What kind of monitors is everyone using? LCD? CRT? There is got to be a simple answer as I won't be able to borrow a CRT monitor for a few days.
I also have the iMac G3 blue and am having some issues with the Feiesty install. Also, I was a hard core Windows/LINUX/UNIX user. I got the iMac G3 for free and bla bla... I upgraded the RAM to 512 Meg and droped in a 40GB drive. Loaded Mac OS 9.0 no prob. And proceeded to download and update to OS 9.2 with the hard drive firmware.  My goal was to get OS X but this thing doesn't have a DVD drive so off to Ubuntu 7.04 Desktop. I have installed this on several PC's but never on Apple. I downloaded and burned the install on my XP machine, loaded the CD into the iMac, Shutdown, and mashed the c (lowercase) on boot up until I hear the drive whir and see the thing is clearly booting off the CD. Here is where my troubles begin. It takes FOREVER to boot, but shows signs of progress all the way. Some errors come up like "tty1 main process ended, respawning" and "unknown powerbook version" but eventually it gets to the main screen with examples, and install. This whole process from initial boot to desktop display takes about an hour. Then when I click on install. examples, Firefox, nothing happens. I tried ctrl+alt(option)+F1 - F12 to get to the text based login but ran out of time and patients. I rebooted and am almost up to the desktop again. 
**Long story short: I wonder if you update to the very latest OS 9 stuff with the firmware updates if it will get you to as far as the next problem :-)**

Good Luck

ckarston

---

### Post by Midwest-Linux on 2007-07-29
> **ckarston said:**
> I also have the iMac G3 blue and am having some issues with the Feiesty install. Also, I was a hard core Windows/LINUX/UNIX user. I got the iMac G3 for free and bla bla... I upgraded the RAM to 512 Meg and droped in a 40GB drive. Loaded Mac OS 9.0 no prob. And proceeded to download and update to OS 9.2 with the hard drive firmware.  My goal was to get OS X but this thing doesn't have a DVD drive so off to Ubuntu 7.04 Desktop. I have installed this on several PC's but never on Apple. I downloaded and burned the install on my XP machine, loaded the CD into the iMac, Shutdown, and mashed the c (lowercase) on boot up until I hear the drive whir and see the thing is clearly booting off the CD. Here is where my troubles begin. It takes FOREVER to boot, but shows signs of progress all the way. Some errors come up like "tty1 main process ended, respawning" and "unknown powerbook version" but eventually it gets to the main screen with examples, and install. This whole process from initial boot to desktop display takes about an hour. Then when I click on install. examples, Firefox, nothing happens. I tried ctrl+alt(option)+F1 - F12 to get to the text based login but ran out of time and patients. I rebooted and am almost up to the desktop again. 
**Long story short: I wonder if you update to the very latest OS 9 stuff with the firmware updates if it will get you to as far as the next problem :-)**

Good Luck

ckarston

My problem is my monitor goes completely dark, or white in depending on the commands.Yet in Mac OS9.0 the screen is absolutely fine and I can use Mac 9.0 OS just fine. I cannot view the firmware, the installation of ubuntu, the boot of the CD, nothing...its either the Mac 9.0 or nothing. There is where my problem lies. I tried two different LCD monitors and with the same result. Its like the video cuts out when I try to install ubuntu. I never did get as far as you did, as I cannot see it on my screen...yet Mac 9.0 views fine. I installed a new 3.6 battery, changed the time and date through the network, did updates, tried the desktop and alternate iso ppc discs. It HAS to be a video problem....just what do I need to do...its been a week nearly so far.

---

### Post by pxwpxw on 2007-07-29
> **Midwest-Linux said:**
> So again my problem trying to install Ubuntu on a G3 seems to stem from me not seeing the install process, but I can otherwise view the Mac OS 9.0 fine. So if that is the issue, a low end CRT monitor might be the answer...but are there any other methods to correct this? 

 I there any way of going into the video card menu and changing its values so it would display the install so I can see whats going on? Is there any apple updates I can use so my monitor can view the install? Would a outboard converter (which I have) that changes the monitor output to a TV signal work and bypass the display problem? Am i the only one with this issue? What kind of monitors is everyone using? LCD? CRT? There is got to be a simple answer as I won't be able to borrow a CRT monitor for a few days.

One thing you should try is, in Macos, set the screen resolution and colour to lowest values - say 640x480 256 color. In some cases, the settings from macos are saved and then used on restart  for say open firmware or the installer CD. maybe 800x600 or try some others, experiment. What happens in macos is much more flexible than the installer, and you can also see how the monitor reacts. The installer defaults to some fairly low resolution and color, and  you can normally control this from the boot menu, but if you cant see the boot menu thats a bit difficult. In older macs this was an issue, maybe still so for the G3.

---

### Post by Midwest-Linux on 2007-07-29
> **pxwpxw said:**
> One thing you should try is, in Macos, set the screen resolution and colour to lowest values - say 640x480 256 color. In some cases, the settings from macos are saved and then used on restart  for say open firmware or the installer CD. maybe 800x600 or try some others, experiment. What happens in macos is much more flexible than the installer, and you can also see how the monitor reacts. The installer defaults to some fairly low resolution and color, and  you can normally control this from the boot menu, but if you cant see the boot menu thats a bit difficult. In older macs this was an issue, maybe still so for the G3.



 Thanks, I'll give that a try. But am I the only one here with this problem? I spent a lot of time looking at posts and none mention this inability to display during booting or installation of ubuntu.

 ( I had almost the same issue when installing Kubuntu on a Compaq Presario 1200 Laptop, I could not view the install process on the desktop version, just a blank screen....I wiped the HD clean ( it had Windows ME on it)  using Nuke and Boot from Soundforge and used the text based installer version and I was able to view the text based installer and it installed with very little difficulty)

---

### Post by pxwpxw on 2007-07-29
Just to clarify, the video card setting is the possible problem, not the monitor. The Macos sets the adapter card  resolution and color, then when you restart to the ubuntu CD, that setting is possibly  inherited and may be wrong for the installer (or the open firmware), so if your monitor can go to a lower resolution and color setting, something may change, without having to change the monitor. A problem also arises if there is an onboard video chip and a second pci adapter, with video going to the onboard original while the monitor is on the pci card. Dont think you have that problem though. This is only an install problem with restricted video.

You might get better info out of the Apple Discussions Blue and White G3 forum, more G3 people there.

---

### Post by Midwest-Linux on 2007-07-29
> **pxwpxw said:**
> Just to clarify, the video card setting is the possible problem, not the monitor. The Macos sets the adapter card  resolution and color, then when you restart to the ubuntu CD, that setting is possibly  inherited and may be wrong for the installer (or the open firmware), so if your monitor can go to a lower resolution and color setting, something may change, without having to change the monitor. A problem also arises if there is an onboard video chip and a second pci adapter, with video going to the onboard original while the monitor is on the pci card. Dont think you have that problem though. This is only an install problem with restricted video.

You might get better info out of the Apple Discussions Blue and White G3 forum, more G3 people there.

  See this is what didn't make sense , why wouldn't a LCD monitor work? I am quite sure others here have installled ubuntu using LCD monitors....why should my G3 any different? I never read any posts here on the forums that one must use a CRT or Apple certified monitor to view the firmware, the boot or ubuntu installation.

 Like I mentioned earlier with the Compaq problem ...the Live CD would not install because it would not let me see it (the blank screen problem) . But the Compaq installed fine after wiping the HD and using the text based installer. 

Too bad it is not that easy with a Mac G3, here I thought the Mac was easier to work with..... By the way I do not have a Mac OS 9.0 install disc if anyone is wondering.

---

### Post by pxwpxw on 2007-07-29
So did you try changing down to lower res and color in macos, and then restart try cd boot or try open firmware boot? LCD should work at lower res ok.

---

### Post by Midwest-Linux on 2007-07-29
> **pxwpxw said:**
> So did you try changing down to lower res and color in macos, and then restart try cd boot or try open firmware boot? LCD should work at lower res ok.

I'll try this tomorrow morning. Thanks for the tips.

---

### Post by tonyr on 2007-07-30
Here's a random observation.  Getting into OpenFirmware with Apple+Option+O+F should 
happen no matter what the OS in the hard drive is, and whether or not there is anything in the
CD drive.  It should happen with a newly wiped hard drive and nothing in the CD drive.  It
might even be that it should happen even if there isn't a hard drive installed (I'm not
really sure about that one; the Apple version of POST might complain with a beep at start
up insteda of a chime like it does when no memory is installed).  If you can't get into 
OpenFirmware under any of these circumstances, then I suggest, as has been pointed out
earlier, that something about OpenFirmware is out of whack.   

Other unanswered questions:  Where did this B&W G3 come from?  Is the original video
card in it (should be in the first, smaller, PCI slot), or some other video card on one of the
other PCI slots (**pxwpxw** hinted at this earlier)? 

- tony

---

### Post by Midwest-Linux on 2007-07-31
> **tonyr said:**
> 
Other unanswered questions:  Where did this B&W G3 come from?  Is the original video
card in it (should be in the first, smaller, PCI slot), or some other video card on one of the
other PCI slots (**pxwpxw** hinted at this earlier)? 

- tony

 I got this G3 from my brother in law. 

MYSTERY SOLVED or another episode of "As The Hard Drive Spins"

First off a big thank you for solving my problem! This has to be one of the most fustrating and mind numbing projects I have ever run into. I don't just have one video output, I have two. This is the kicker, I have been trying to install Ubuntu using the bottom (one of the two) video outputs. 

I kept using the bottom one without even noticing the top one, without even thinking that this was a video output too! Why the heck would anyone have two video outputs is beyond me. See I figured that output has to be for something else because the bottom one is the video one and thats it. And even then who would have thought that both video outputs react differently! 

 It gets better, I had pretty much shelved the project until i had more time and I was going to try a different approach. I was going to try Yellow Dog 5.0 as my next option and if that did not work, then try Yellow Dog 3.0. I took the G3 out of the spare room again to get ready to burn the Yellow Dog ISO's and something told me to look at these posts again and I saw your post about the placement of the video cards. 

I figured OK, yes i see TWO outputs and let me see if I can get video out of the other output (the top most one). So at this time I had the Mac OS 9.0 was running, I unplugged the monitor from the bottom output, and plugged it into the top one. well guess what? .....Well there was Mac OS 9.0 too! Why two video outputs? Surely they would be the same anyway...right? So then I figured It doesn't hurt to try again to attempt to install Ubuntu 7.04 using the alternate disc like I tried so many times in the past. 

With the Ubuntu 7.04 Alternate disc into the CD Rom Drive, hold down C and hit power on. Now I have the monitor plugged into the top output. So the machine starts up and the screen goes white, blue and black...and then TEXT from the 7.04 Alternate Disc installer! 

 Yep that was the problem, There are TWO video outputs on this computer, they both WOULD display Mac OS 9.0 the same , but on boot or prompt or text one output would mute or go dark, and the other one would display it (the top output!). 

Right now I am installing Ubuntu 7.04 on this machine. I hope I have enough HD space as it is only 3.2 gig.  I am still installing the Ubuntu 7.04 and its at the point where it is installing "select and Install Hardware". Thanks to everyone else for their support and quick responses...I am sure I will have to do some tweaking and changing things and maybe adding another Hard drive at some point and all  that should be a piece of cake compared to what I spent in hours, days and over a week of trying to get this running.

 Hey, please by all means throw this solution in with the Installing Ubuntu thread, it very well could help others from this problem. 

Again, thanks to everyone and a big thanks to pxwpxw and Tonyr for helping to solve this mystery.

---

### Post by 3rdalbum on 2007-07-31
As I was reading this thread again I started thinking "Hey, I wonder if he's got two video out ports on his computer, and he's using the second one?". You beat me to the solution by four hours :-)

I'm glad you got things working.

Incidentally, someone I know had the same problem when they plugged their computer after getting it back from the repairers. Took me a good 20 minutes to realise that was the problem :-)

---

### Post by Midwest-Linux on 2007-07-31
It only took over a week...lol How the heck did I miss that one "simple" answer??


I have some minor issues to iron out, when I log in and get to the desktop...I have to click the little logo on top with the two computers in the top right corner. And then it gives me a option for wireless or wired. So I click wired and then it connects....a very minor issue...In other words instead of being automatically connected to the internet after you log in and get to the desktop (like Windows)...you have to manually click on it...no big deal....

Another one regarding internet radio.....I tried going to the website of the internet radio station and trying three options to listen...they are

[http://www.republicbroadcasting.org/32k.pls](http://www.republicbroadcasting.org/32k.pls)  (winamp)
[http://www.republicbroadcasting.org/32k.asx](http://www.republicbroadcasting.org/32k.asx) (windows media)
[http://www.republicbroadcasting.org/32k.ram](http://www.republicbroadcasting.org/32k.ram) (real player)

I  could not connect.
So then I bought  up the music player and select internet radio and type in the url it cannot connect either...

However....

I went to the movie player, tried to manually type in the url of the internet radio station and it did not want to connect. I saw some options/plug ins, and I installed these options...I went back and retyped the url in the movie player and I was able to listen to my internet radio station that I wanted. So internet radio did not work in the music player, but works in the movie player only after i downloaded some plug ins.

Well I figured since I was now able to access my internet station on the movie player, I figured I would try the music player again. I went to the selection again where you type in the url and it could not connect. 

So at least I am able to access internet radio, but there must be a better way. I could not access internet radio under Mac 9.0 OS but here I could...in a backward kind of way....Now I went to a different website...where it says click here for winamp...I clicked it and it bought up a option to use the movie player....and I clicked it and it went right to the audio...

---

### Post by tonyr on 2007-07-31
> **Midwest-Linux said:**
>  Why the heck would anyone have two video outputs is beyond me. See I figured that output has to be for something else because the bottom one is the video one and thats it. And even then who would have thought that both video outputs react differently! 
 

It's becoming quite popular to have 'dual-displays', two terminals.  Some video cards have
two video out connectors.  More often  people add a second video card; I see it all the time.
Mac OSX is MUCH better (IMHO) at handling this situation, and video configuration in general, 
and especially in handling a video card in any other slot than the top one.  

- tony

---

