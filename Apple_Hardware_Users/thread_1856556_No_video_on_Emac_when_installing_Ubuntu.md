---
title: "No video on Emac when installing Ubuntu"
date: 2011-10-08
forum: Apple Hardware Users
---

### Post by Ms. Daisy on 2011-10-08
I have successfully burned an Ubuntu 10.4 PowerPC live CD for my G4 Emac.  I got the computer to boot from the CD.  I got a black screen with the welcome message.  I pressed "enter", then I re-tried and entered "live video=ofonly".  In both instances the system starts loading, I get a white screen with text, then a black screen with a prompt, then the screen goes black.  It looks to me like the screen is receiving no information (like it's off), it's not just outputting a black screen.  I let it go for an hour with no change.

I suspect that it's a graphics card problem, I just don't know what to do about it.  I have an Emac PowerPC 7441 G4.  The video card is a GeForce 2 MX.  I found a thread with a similar problem ([http://ubuntuforums.org/showthread.php?t=1794238&highlight=video](http://ubuntuforums.org/showthread.php?t=1794238&highlight=video)).  At the welcome screen, I typed tab then "Linux install video=ofonly".  I get an error message "2,/vmlinux; Unable to open file, Invalid device"  I can't get as far as terminal to try other solutions.  

If there are other threads already addressing this, please direct me to them.  

BTW, I also tried to install Ubuntu 10.10 from a DVD with the same result.

---

### Post by Ms. Daisy on 2011-10-08
So do you think this is a hardware problem (graphics card) or a software problem?  I was leaning towards a software problem because I just installed a similar graphics card in my HP PC and am successfully running Natty Narwhal & Unity.  If it's software, should I type something else in at the welcome screen?

 Let me know if this is a stupid inquiry.  I'm a big girl, I can take it.  If it's hopeless, should I just forget about it?

---

### Post by rsavage on 2011-10-08
You could try:
 
live nosplash video=ofonly nouveau.modeset=0

---

### Post by rsavage on 2011-10-08
> **Ms. Daisy said:**
> So do you think this is a hardware problem (graphics card) or a software problem? I was leaning towards a software problem because I just installed a similar graphics card in my HP PC and am successfully running Natty Narwhal & Unity. If it's software, should I type something else in at the welcome screen?
 
Let me know if this is a stupid inquiry. I'm a big girl, I can take it. If it's hopeless, should I just forget about it?
 
It's software. It's fixable.  You'll probably eventually have to set up/download an xorg.conf file.

---

### Post by rsavage on 2011-10-08
This guy installed ubuntu on his emac via the alternative cd [http://ubuntuforums.org/showthread.php?t=1813822](http://ubuntuforums.org/showthread.php?t=1813822) .
 
It is just as easy to install xubuntu natty though.  Yes the instructions are intimidating, but perhaps not so when you follow them in front of the computer?

---

### Post by Ms. Daisy on 2011-10-08
Thanks, rsavage!  I tried "live nosplash video=ofonly nouveau.modeset=0" and got  to a screen that said "Ubuntu 10.04" with 4 dots beneath it.  That's the  furthest I've gotten.  
 
Right now I am pouring over the thread you linked to.  And it mentions  the battery.  AH, THE BATTERY!  The internal clock has been screwy in my  Mac OSX- it says it's set to 1969 or something.  Again, knowing nothing  about Macs, I "fixed" it by clicking the box to stop telling me about  it. XD   So maybe I should ACTUALLY fix it now.  Duh.

If the battery replacement doesn't solve the problem, then I will bite  the bullet and install Lubuntu.  But I am going to install something.   This has become an epic mission for me.  I will NOT be defeated by this  little, white Emac.

---

### Post by rsavage on 2011-10-09
> **Ms. Daisy said:**
> Thanks, rsavage! I tried "live nosplash video=ofonly nouveau.modeset=0" and got to a screen that said "Ubuntu 10.04" with 4 dots beneath it. That's the furthest I've gotten. 
 
Right now I am pouring over the thread you linked to. And it mentions the battery. AH, THE BATTERY! The internal clock has been screwy in my Mac OSX- it says it's set to 1969 or something. Again, knowing nothing about Macs, I "fixed" it by clicking the box to stop telling me about it. XD So maybe I should ACTUALLY fix it now. Duh.
 
If the battery replacement doesn't solve the problem, then I will bite the bullet and install Lubuntu. But I am going to install something. This has become an epic mission for me. I will NOT be defeated by this little, white Emac.
 
Can you not set the time in Mac OSX? If you then reboot without unplugging the emac won't it keep the time for you to use the ubuntu cd?
 
I don't think it is the battery causing your problem though since c4c used the parameters I gave you to overcome his battery problem.
 
I don't have an emac and I've never had a blank screen problem so I'm only speculating, but I think what is happening is the computer is sending out a video signal that is out of range for the monitor. The fix for this is to setup an xorg.conf file. If this is the case then it is best to use the alternative cd or use the minimal cd (like in the xubuntu/lubuntu instructions). These installers don't use fancy graphics so don't have the problem.

---

### Post by Ms. Daisy on 2011-10-09
> **rsavage said:**
> Can you not set the time in Mac OSX? If you then reboot without unplugging the emac won't it keep the time for you to use the ubuntu cd?

Thanks for hanging with me.  You're a champ! No, when I first got the used Emac a month ago I tried to reset the time, but it  just reverted back to 1969 every time I rebooted it.  A battery costs a  whopping $5, so I may as well give it a shot.
 
I'll replace the battery and try Ubuntu one more time.  If it fails again, I'm doing Lubuntu.

---

### Post by Ms. Daisy on 2011-10-09
> **beemac said:**
> Try installing "build-essential" package in Synaptics.  You will get the libc header.

I've got a total of 2 weeks of experience under my belt with Ubuntu, so I don't know what Synaptic or build essential are.  I tried to search it in this forum & Google, but I only found a feature that I would install in Ubuntu.  But since I can't get Ubuntu to install in the first place, I don't know how I would install Synaptic. Is that what you're talking about?  Or is this some kind of alternative installation CD?

---

### Post by rsavage on 2011-10-10
> **Ms. Daisy said:**
> I've got a total of 2 weeks of experience under my belt with Ubuntu, so I don't know what Synaptic or build essential are. I tried to search it in this forum & Google, but I only found a feature that I would install in Ubuntu. But since I can't get Ubuntu to install in the first place, I don't know how I would install Synaptic. Is that what you're talking about? Or is this some kind of alternative installation CD?
 
I think the post by beemac is spam or at the least posted in the wrong thread.
 
Btw Ms. Daisy, how much ram have you got?  If it is only 128mb then I don't think the live ubuntu cd will work.  You'll have to use the alternate cd or minimal cd.

---

### Post by Ms. Daisy on 2011-10-10
> **rsavage said:**
> Btw Ms. Daisy, how much ram have you got?  If it is only 128mb then I don't think the live ubuntu cd will work.

This Emac tells me it has 640 MB RAM.

---

### Post by rsavage on 2011-10-10
Ok that is great.  I would try xubuntu natty then.  Xubuntu is easier to install than lubuntu.  You literally have to type one command, although there might be a bit of fiddling to get your xorg.conf setup. 
 
It is probably better to go with natty (11.04) because it has a better driver for your graphics card I think.

---

### Post by Ms. Daisy on 2011-10-10
One command- that's right up my alley!  I'll check out xubuntu.  In the meantime, I'm waiting for my $5 battery to arrive.  No local stores carry it...

---

### Post by rsavage on 2011-10-10
I wonder if xubuntu will work without the battery because of the newer driver...... but if you've ordered it already you might as well wait I suppose.
 
Any problems just give us a shout!

---

### Post by Ms. Daisy on 2011-10-10
OK, I'm throwing more stupid questions at you. I'm looking at the xubuntu documentation and I'm not seeing alternate installs.  Do I just use the standard one "[11.04, codename Natty Narwhal. (Latest stable release).  ]("http://www.xubuntu.org/getubuntu#natty")" located here:
[http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu) ?

Also, I saw two posts in this forum:
[http://ubuntuforums.org/showthread.php?t=1689694](http://ubuntuforums.org/showthread.php?t=1689694)
[http://ubuntuforums.org/showthread.php?t=1709178](http://ubuntuforums.org/showthread.php?t=1709178)

Both threads suggest that Ubuntu be installed first, then add Xubuntu later.   Tell me that I'm not in a horrible recursive loop here.  I can't get ubuntu to install, so I should install xubuntu instead, but that requires that I install ubuntu first...

---

### Post by rsavage on 2011-10-11
> **Ms. Daisy said:**
> horrible recursive loop here
Are you a computer science student?!
 
 
Back to xubuntu..... just follow the big scary thread I wrote that you've seen before I think [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792) . Basically you do this:
 
Burn the powerpc minimal cd.
Boot it typing "cli" at the yaboot prompt.
Answer all the installation instructions (they're the same as the live ubuntu gui ones)
Reboot and login
Type "sudo tasksel" and select xubuntu desktop from the list
 
Use the big workarounds section if you find something is not working. When you see "lxterminal" written just use the terminal program that comes with xubuntu.
 
If you still get a blank screen then you'll have to setup an xorg.conf file. That's the fun bit unless you cheat and download one!
 
Keep the questions coming!

---

### Post by Ms. Daisy on 2011-10-11
OK, duh, I see the downloads now.  Thanks!  
Yup, Python is going a tad better for me than Ubuntu right now :D

---

### Post by nothingspecial on 2011-10-11
> **rsavage said:**
> I think the post by beemac is spam or at the least posted in the wrong thread.
 


Which is why it has now disappeared.

---

### Post by proxy.qtz on 2011-10-11
If you need a new battery, try a potato.

---

### Post by bspymaster on 2011-10-11
Wow, proxy.qtz. I did a science project on that once. Doesn't work very well. :/

---

### Post by Ms. Daisy on 2011-10-11
> **proxy.qtz said:**
> If you need a new battery, try a potato.
 
Good idea! I opened a shell and typed
 
from potato import power
 
Crap! No luck :(

---

### Post by Ms. Daisy on 2011-10-11
> **rsavage said:**
> Are you a computer science student?!
 
 
Back to xubuntu..... just follow the big scary thread I wrote that you've seen before I think [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792) . 

I swear I am really not this stupid.  I found the PowerPC download page. 
Clicking on the most recent available Kubuntu (9.04 Jaunty Jackalope), I get this error (from two of my computers):  
**Not Found**

 The requested URL /kubuntu/ports/releases/jaunty/release/ was not found on this server.
  Apache/2.2.14 (Ubuntu) Server at cdimage.ubuntu.com Port 80

Um, What?

---

### Post by rsavage on 2011-10-11
> **rsavage said:**
> Back to xubuntu..... just follow the big scary thread I wrote that you've seen before I think [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792) . Basically you do this:
 
Burn the powerpc minimal cd.
Boot it typing "cli" at the yaboot prompt.
Answer all the installation instructions (they're the same as the live ubuntu gui ones)
Reboot and login
Type "sudo tasksel" and select xubuntu desktop from the list
 
So Step 1 was burn the minimal cd. Not the alternate! The minimal cds are here [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) . You want the 32 bit powerpc version!!

---

### Post by Ms. Daisy on 2011-10-12
I installed the minimal CD successfully on my Emac!  However, I haven't been able to install a GUI. Here's a detailed list of what I did:

                                 I installed the minimal cd of 11.04. It says I'm missing non-free firmware files.  Can be loaded from removable media "agere_sta_fw.bin"  A quick search shows this seems to be for the wifi, so i'm not concerned about it. I'm going to use ethernet anyway.

Asks me to set up http proxy. Um, gonna have to search that...
 Found this in another thread: &#8220;Enter proxy details. If you are connecting through your own router at home, then you almost certainly won't have a proxy, so leave this blank and just press return.&#8221; God I love this forum. 


 It's loading additional components. Clock set to NYC
 

 Partitioning method- 4 choices.
 I chose "Use full disk- guided installing"
 

 It's telling me:
 "The partition tables of the following devices are changed:
IDE master (hda)
 

 The following partitions are going to be formatted:
 Partition #3 of IDE1 master (hda) as ext4
 Partition #4 of IDE1 master (hda) as swap"
 

 [installing the base system], username, account, password set up. encrypt the home folder yes. "Configuring apt-" 


 select and install software- slow process, 30 minutes or so, interrupted several times to ask;
 

     1. chose &#8220;no automatic updates&#8221; per instructions.
 

     2. Now it's asking me to install additional software!   
         chose Xubuntu desktop  
 

 "finishing the installation: wiping the swap space (may take a while)"
 finished, rebooted.
 Logged in.
 

 I have no GUI.  So I'm trying the Lubuntu directions provided by Lubuntu docs.

sudo apt-get install python-software-properties (done) sudo add-apt-repository ppa:lubuntu-desktop/ppa (done) sudo apt-get update (done) sudo apt-get install --no-install-recommends lubuntu-desktop 
   [FONT=Arial](terminal did not recognize the &#8220;--no-install-recommends&#8221; part.  Skipping this.)[/FONT] sudo apt-get dist-upgrade (0 to upgrade, 0 install, 0 remove, 0 not upgraded) sudo apt-get autoclean (done) cd /var/cache/apt/archives  sudo rm * [FONT=Arial](got message &#8220;cannot remove &#8220;partial&#8221;: Is a directory.  This was to remove installation stuff so it's not critical for now)[/FONT]  
sudo reboot  (done)

[FONT=Arial Black]NO GUI yet.  So I'm proceeding with rsavage's recommendations.[/FONT]

[FONT=Arial]I typed in your monstrosity of a line (starting with [/FONT]sudo apt-get install --no-install-recommends alsa-...)
[FONT=Arial]wow- typed that all in and only got 2 errors!: It says it couldn't find:[/FONT]
        package ubuntu-extras-keyring [FONT=Arial](don't use it anyway so I'm not worried now)[/FONT]     
package xll-utils [FONT=Arial](hmm, utils sounds important)[/FONT] 

[FONT=Arial]I installed the software center successfully. Now I'm rebooting to see what I've got. 
Logged in. Still without GUI.  Shouldn't I have some kind of GUI desktop by now?[/FONT]

---

### Post by Ms. Daisy on 2011-10-12
When I restart now, I get a message as ubuntu is loading with the 4 little dots beneath:

"The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present."

This seems to be for encrypting the home directory, which obviously I haven't set up yet because I have no GUI. Correct?

---

### Post by rsavage on 2011-10-12
Hi Ms. Daisy. I'll try and help you in a moment. I just need to shout something first whilst waving my arms about frantically. Please ignore the next sentence.
 
ARGHHHHH!!! OMG! HOW CAN ONE PERSON MAKE SOMETHING SO SIMPLE SO COMPLICATED?!!!
 
And breathe.....
 
Only joking (sort of!). I can be pretty thick at times too (not that I'm saying you're thick or anything). Like I just spent 5 minutes trying to work out why my external usb drive wasn't working only to find I'd connected it to the ethernet port! Duh! So I forgive you....
 
So you've been busy. How am i going to untangle this lot.....
 
> **Ms. Daisy said:**
> I installed the minimal cd of 11.04. It says I'm missing non-free firmware files. Can be loaded from removable media "agere_sta_fw.bin" A quick search shows this seems to be for the wifi, so i'm not concerned about it. I'm going to use ethernet anyway.
Okay, so this concerns me from the start. I've always got the agere_sta_fw.bin file in the directory /lib/firmware/ so why haven't you got it?
*EDIT*: I've worked it out. That message is probably normal since you have an airport classic card and I haven't. It is asking you incase you need the firmware for the installation to work. The file will be dowloaded later I think.
 
> **Ms. Daisy said:**
> Asks me to set up http proxy. Um, gonna have to search that...
Found this in another thread: &#8220;Enter proxy details. If you are connecting through your own router at home, then you almost certainly won't have a proxy, so leave this blank and just press return.&#8221; God I love this forum. 
Sounds okay.
 
> **Ms. Daisy said:**
> encrypt the home folder yes. 
I've never done this myself.
 
> **Ms. Daisy said:**
> 
2. Now it's asking me to install additional software! 
chose Xubuntu desktop 
Why is it asking you this?** You didn't enter "cli" at the yaboot prompt did you?! **
 
> **Ms. Daisy said:**
> "finishing the installation: wiping the swap space (may take a while)"
finished, rebooted.
Logged in.
 
I have no GUI.
So this is the point where I think you should of stopped and reviewed what you have done. This is when you should of asked for help.
 
> **Ms. Daisy said:**
> So I'm trying the Lubuntu directions provided by Lubuntu docs.
One question: why? I don't mean to be rude, but I think I made it pretty clear that the official lubuntu documentation won't work with powerpc natty. Are you still using your xubuntu natty installation at this point because that is going to cause problems I think.
 
> **Ms. Daisy said:**
> [FONT=Arial]I typed in your monstrosity of a line (starting with [/FONT]sudo apt-get install --no-install-recommends alsa-...) .
That's why I wanted you to install xubuntu.
 
> **Ms. Daisy said:**
> [FONT=Arial]wow- typed that all in and only got 2 errors!: It says it couldn't find:[/FONT]
package ubuntu-extras-keyring [FONT=Arial](don't use it anyway so I'm not worried now)[/FONT] 
package xll-utils [FONT=Arial](hmm, utils sounds important)[/FONT] 
It should be x11 (eleven not lowercase LL). It should be brought in by other packages though I would of thought. No idea about ubuntu-extras-keyring unless that is also a typo.
 
> **Ms. Daisy said:**
> [FONT=Arial]I installed the software center successfully. [/FONT]
This is something you could of done when you had a gui, but no harm in doing now I suppose.
 
> **Ms. Daisy said:**
> [FONT=Arial]Now I'm rebooting to see what I've got. [/FONT]
[FONT=Arial]Logged in. Still without GUI. Shouldn't I have some kind of GUI desktop by now?[/FONT]
Yes, but, a few things have gone wrong haven't they? 
 
What happens when you type "startx"?
You might have to look at the xorg log. Type:
sudo nano /var/log/Xorg.0.log
 
I'm tempted to say reinstall. I really don't like the idea of xubuntu and lubuntu being installed at the same time, but lets see what the log says if you can make sense of it.
 
We're going to get this thing installed I promise!

---

### Post by rsavage on 2011-10-12
Can you clarify this for me...

> **Ms. Daisy said:**
> 
[FONT=Arial]I typed in your monstrosity of a line (starting with [/FONT]sudo apt-get install --no-install-recommends alsa-...)
[FONT=Arial]wow- typed that all in and only got 2 errors!: It says it couldn't find:[/FONT]
        package ubuntu-extras-keyring [FONT=Arial](don't use it anyway so I'm not worried now)[/FONT]     
package xll-utils [FONT=Arial](hmm, utils sounds important)[/FONT] 


Did you leave out ubuntu-extras-keyring and x11-utils from the monstrosity of a line?  If you didn't and you just got the "unable to locate package" error then you won't have installed anything.

---

### Post by Ms. Daisy on 2011-10-13
[COLOR=#000000]I reinstalled. This time typed cli at the first prompt at boot. It still complained that I was missing the same Firmware. It finished, rebooted & logged in. [/COLOR] 
 
   [COLOR=#000000]Typed sudo tasksel, got menu of software & OS. I Highlighted Xubuntu desktop, pressed enter.[/COLOR]
 [COLOR=#000000]Nothing happened, got blinking prompt immediately.[/COLOR]
 
  > To get your missing firmware [COLOR=#000000]I typed: sudo apt-get install linux-firmware-nonfree  It successfully installed. [/COLOR] 
  > What happens when you type "startx"?[COLOR=#000000] It says &#8220;The program startx is not installed. You can install it by typing sudo apt-get install xinit&#8221;[/COLOR]
  > You might have to look at the xorg log.[COLOR=#000000] I typed: sudo nano /var/log/Xorg.0.log (tried both 0 and O between the periods) Both returned &#8220;command not found.&#8221;[/COLOR] 
 
I tried sudo tasksel again before and after a restart. Same effect. 

No GUI.

---

### Post by rsavage on 2011-10-13
> **Ms. Daisy said:**
> [COLOR=#000000]It still complained that I was missing the same Firmware. It finished, rebooted & logged in. [/COLOR]See edited post above.
 
 
> **Ms. Daisy said:**
> 
[COLOR=#000000]Typed sudo tasksel, got menu of software & OS. I Highlighted Xubuntu desktop, pressed enter.[/COLOR]
[COLOR=#000000]Nothing happened, got blinking prompt immediately.[/COLOR]That's wierd. Do you mean blinking cursor as in a prompt or blinking cursor like it is sort of crashed? What happens if you leave it for 5 minutes? Make a cup of tea or the american equivalent that you do in times of trouble.
 
 
 
> **Ms. Daisy said:**
> 
[COLOR=#000000]I typed: sudo apt-get install linux-firmware-nonfree It successfully installed. [/COLOR]I removed this from the edited post because I don't think it is necessary.
 
 
> **Ms. Daisy said:**
> 
[COLOR=#000000]It says “The program startx is not installed. You can install it by typing sudo apt-get install xinit”[/COLOR]Expected since you haven't installed a gui.
 
 
> **Ms. Daisy said:**
> 
[COLOR=#000000]I typed: sudo nano /var/log/Xorg.0.log (tried both 0 and O between the periods) Both returned “command not found.”[/COLOR]V strange. You shoud have nano I would of thought.
 
 
Can you give me the answer on the prompt please? If it is hanging just leave it a few mins like I say above. Don't do anything else!

---

### Post by rsavage on 2011-10-13
Sorry, forgot to say you now need to enter
 
sudo apt-get update
 
before you type "sudo tasksel".  You need to do this incase some packages have been updated since you installed the base system.

---

### Post by Ms. Daisy on 2011-10-13
> **rsavage said:**
> Sorry, forgot to say you now need to enter

sudo apt-get update

before you type "sudo tasksel". You need to do this incase some packages have been updated since you installed the base system. Do you mean since I burned the CD or since I actually installed it on the machine? I installed it 6 hours ago, they can't update it THAT often. Could that possibly be why tasksel didn't work?

> Can you give me the answer on the prompt please? If it is hanging just leave it a few mins like I say above. Don't do anything else!Sorry, I've been conducting an exhausting (not exhaustive) search of the community docs and this forum. No, the cursor just was blinking like it was waiting for me to tell it to do something. I left it for a good half-hour (while I conducted said search and general teeth-gnashing). I tried it several times, before & after a reboot.

**If the following command is unadvisable, I can always re-install (again).  **I didn't see your post until after I did the following. I stumbled upon this command:
sudo aptitude install xubuntu-desktop  
 installing from sudo tasksel didn't work, so I gave the above a shot. It installed something. Watching the scrolling script, it seemed to be mentioning powerpc a lot. Rebooted. I've got a GUI, no idea which one. Now I need to research how to get ubuntu to tell me about itself. I also don't see a browser, so I'll need to install that. The GUI is unacceptably sluggish, so I'm not there yet. 

Screen kept sleeping during install, I would press enter or arrow to wake it up, but it would execute those keys. So now I need to search if that affected the install, and if so how to wake the f#@$ing monitor up while in terminal without executing anything. Or just turn the sleep mechanism off.

Clearly something is amiss because tasksel doesn't work (unless it's due to the update part but surely it isn't).

And regarding the airport card, I don't think I can use it on my network anyway. It's only capable of WEP and I've got my LAN set up for WPA2. I've got an Ethernet cable plugged into it. That's why I was saying I wasn't worried about it from the outset. And the Emac weighs 50 pounds, not sure I was going to move it around the house much anyway...

---

### Post by Ms. Daisy on 2011-10-13
Oh, just discovered a hidden icon bar at the bottom of the page.  It only appears when you mouse over it.  Browser is present, terribly sluggish to respond.
Also found that I have xfce 4 installed.

---

### Post by rsavage on 2011-10-13
Don't know what's up with tasksel.
 
I'd of told you to try xubuntu-desktop next so you did the right thing there.
 
Can you paste the output of the xorg.0.log file please so we can see what video drivers you are using?

---

### Post by Ms. Daisy on 2011-10-13
> **rsavage said:**
> I'd of told you to try xubuntu-desktop next so you did the right thing there.That makes me so happy I could cry! perhaps there's hope for me yet.
 
> **rsavage said:**
> Can you paste the output of the xorg.0.log file please so we can see what video drivers you are using? Why yes, I would love to copy and paste it right here from my xubuntu machine (ok, not much faster than the original mac, but we're SO CLOSE!)

[    26.399]
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    26.399] X Protocol Version 11, Revision 0
[    26.399] Build Operating System: Linux 2.6.35-23-powerpc64-smp ppc Ubuntu
[    26.399] Current Operating System: Linux ubuntuUnapple 2.6.38-11-powerpc #50-Ubuntu Mon Sep 12 21:32:20 UTC 2011 ppc
[    26.440] Kernel command line: root=UUID=c93b8792-836c-4fd7-a372-419f92c925e9 ro quiet splash
[    26.440] Build Date: 11 August 2011  03:47:04PM
[    26.440] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[    26.440] Current version of pixman: 0.20.2
[    26.440]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[    26.440] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.441] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 13 20:19:13 2011
[    26.462] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.464] (==) No Layout section.  Using the first Screen section.
[    26.464] (==) No screen section available. Using defaults.
[    26.464] (**) |-->Screen "Default Screen Section" (0)
[    26.465] (**) |   |-->Monitor "<default monitor>"
[    26.466] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    26.466] (==) Automatically adding devices
[    26.466] (==) Automatically enabling devices
[    26.466] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.466]    Entry deleted from font path.
[    26.466] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.467]    Entry deleted from font path.
[    26.467] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.467]    Entry deleted from font path.
[    26.467] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.467]    Entry deleted from font path.
[    26.467] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.467]    Entry deleted from font path.
[    26.467] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    26.467] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"

---

### Post by rsavage on 2011-10-14
> **Ms. Daisy said:**
> That makes me so happy I could cry! perhaps there's hope for me yet.

Yes I'm after somebody else to answer the powerpc questions on the forum!  I'm not a people person and it shows too often!

Your xorg log seems remarkably short and doesn't say much.  I think you should have a go at setting up an xorg.conf file.  You can do it!  There are instructions on the big scary thread, but nobody seems to be able to follow them!  I reckon you should end up with something like this:

```
Section "ServerLayout"
Identifier     "X.org Configured"
Screen         "Screen0"
EndSection
 
Section "Monitor"
Identifier   "Monitor0"
VendorName   "Monitor Vendor"
ModelName    "Monitor Model"
EndSection
 
Section "Device"
Identifier  "Card0"
Driver      "nouveau"
BusID       "PCI:0:16:0"
EndSection
 
Section "Screen"
Identifier "Screen0"
Device     "Card0"
Monitor    "Monitor0"

DefaultDepth 16

SubSection "Display"
Viewport   0 0
Depth     1
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     4
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     8
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     15
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     16
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     24
EndSubSection
EndSection
```From what I gather nvidia cards have the choice of the nouveau driver (the newest) or the nv driver.  I've added a DefaultDepth line to the above.  You can try it with and without.

---

### Post by Ms. Daisy on 2011-10-14
> Your xorg log seems remarkably short and doesn't say much. I think you should have a go at setting up an xorg.conf file. OK, I think there was more to the file I produced but I couldn't figure out how to see it. This little Xubuntu Emac has a GUI (YAY!), but it's mind-numbingly slow to respond.  And I gave up trying to get the whole file when I wanted to gouge my eyes out instead of wait around for the computer to catch up with me.  I'll figure out what I'm doing with that file on my ubuntu PC (which is fantastically fast and the reason I wanted ubuntu on the Emac in the first place).  Then I'll post it in its entirety. > I'm not a people person and it shows too often!You're doing just fine with me. :)> Yes I'm after somebody else to answer the powerpc questions on the forum! Well if I ever get enough of a clue to be of any use, I wouldn't mind at all.  After my exhausting search for PowerPC info, I decided that I'd really like to see a more comprehensive (and idiot-proof) repository.  You've got a ton of really good info and I discovered that you seem to be THE keeper of Apple info out there.  Surely you could use some help. And I read that 11.10 was going to start supporting the PowerPC versions- shouldn't that make life easier?

---

### Post by rsavage on 2011-10-14
I wonder if you have this problem too [http://ubuntuforums.org/showthread.php?t=1859152](http://ubuntuforums.org/showthread.php?t=1859152) ?  What is your CPU usage like?

---

### Post by Ms. Daisy on 2011-10-14
I'm looking into CPU.  I subscribed to that thread.  
So what happens if I upgrade to 11.10? Should I solve the problems in 11.04 first? Will I get a different set of issues when I upgrade, or will the problems just compound? #hopingForAnEasyFix

---

### Post by rsavage on 2011-10-14
Wow, I can't believe you are still interested in your emac! I think most people would have chucked something through the screen by now! This is turning into an epic journey! Remember to have a break from it or you will hate it. If you are going to have a career in computers then you need to take care of yourself. I'm serious. Eye strain can be really bad. You should do yoga or some exercise that works the shoulders/neck/chest area to stop you getting repetetive strain injury.
 
Somehow digressed there....
 
Did you work out how to check the CPU usage? The easiest way is to open a terminal application and type the command "top". What are say the top three processes?
 
11.10 is brand spanking new, not sure what problems it will have or what solutions it will bring. 
 
Btw, you can have WPA with an airport card. Forgot to tell you that before.
 
> You're doing just fine with me.
Ahh stop or you'll make me blush what with you being a girl n all :oops:

---

### Post by Ms. Daisy on 2011-10-14
> **rsavage said:**
> Wow, I can't believe you are still interested in your emac! I think most people would have chucked something through the screen by now! This is turning into an epic journey!  Oh, things have been chucked, believe me! It's still not out of the realm of possibility that this Emac will make an appearance as a pinata some day.  But for now...  I WILL NOT BE DEFEATED!!!!

see the other thread for CPU.

---

### Post by rsavage on 2011-10-14
Your CPU is maxing out!!!!  No wonder you are so slow.  We need the top lines from the list below what you've quoted.  What are the names in the "command" column and what is the CPU value for each?  I'm here for about half an hour until I feel sleepy..... we could crack this in that time.

---

### Post by Ms. Daisy on 2011-10-14
CPU info:
Tasks: 146 total,   5 running, 141 sleeping,   0 stopped,   0 zombie
Cpu(s): 77.8%us, 21.9%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    635500k total,   467068k used,   168432k free,    34564k buffers
Swap:  1687984k total,        0k used,  1687984k free,   204756k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                          
  688 root      20   0  316m  57m 7588 S 19.7  9.2   0:34.58 Xorg                                                             
17469 user  20   0  379m  72m  33m R 11.1 11.7   0:46.45 firefox                                                          
15471 root      20   0 16036 3936 3260 S 10.5  0.6   0:39.94 udisks-daemon                                                    
15585 user  20   0 11660 3952 3316 S  9.9  0.6   0:37.87 gvfs-gdu-volume                                                  
15258 user  20   0  128m  15m  11m R  7.3  2.4   0:28.40 update-notifier                                                  
  314 messageb  20   0  4428 1836  876 S  6.4  0.3   0:25.71 dbus-daemon

---

### Post by rsavage on 2011-10-14
Output of 

udisks --monitor

please.  Normally it should be nothing if you are doing nothing, but I suspect you'll have a list.  We'll see....

---

### Post by Ms. Daisy on 2011-10-14
a never ending stream of:
changed:    /org/freedesktop/UDisks/devices/hdc
showing line after line after line.

---

### Post by rsavage on 2011-10-14
So it is pretty definite that you have that bug.  I assume hdc must be your cdrom drive? Don't worry if you don't know the answer to that.  What happens when you enter


hal-disable-polling --device /dev/hdc

---

### Post by rsavage on 2011-10-14
Sorry possibly 

sudo hal-disable-polling --device /dev/hdc

---

### Post by Ms. Daisy on 2011-10-14
> **rsavage said:**
> Sorry possibly 

sudo hal-disable-polling --device /dev/hdc I copied & pasted both in to terminal.  With sudo, I got "command not found."
without sudo, I got "The program 'hal-disable-polling' is currently not installed.  You can install it by typing:
sudo apt-get install hal"

---

### Post by rsavage on 2011-10-14
Hmm... okay probably best not to install that then for the moment.  Might have to look into that more.

What about thunar.  That is the file manager in xubuntu.  Is there some preference somewhere about automounting?  Try unticking that and check udisks --monitor again.

---

### Post by rsavage on 2011-10-14
From google:

Make sure Enable Volume Management under Thunar>Preferences>Advanced is not checked

---

### Post by Ms. Daisy on 2011-10-14
I opened file manager in the GUI.  I found automounting for removable devices and unticked it.  Is that what you meant?
Checked udisks --monitor again and it printed out the same thing,

---

### Post by rsavage on 2011-10-14
Probably.  Long time since I've used xubuntu.

Right, try this:

sudo nano /etc/udev/rules.d/my.rules

Put the following in:

KERNEL=="hdc", ACTION=="change", WAIT_FOR="nothing"


Press ctrl-x and enter 'y' to say yes to the save.

You might have to reboot for it to take effect.  I don't know, this is new stuff!

---

### Post by Ms. Daisy on 2011-10-14
> **rsavage said:**
> From google:

Make sure Enable Volume Management under Thunar>Preferences>Advanced is not checked
found that, it was checked.  I unchecked it, but udisks --monitor gave the same output.

---

### Post by Ms. Daisy on 2011-10-14
> **rsavage said:**
> sudo nano /etc/udev/rules.d/my.rules

Put the following in:

KERNEL=="hdc", ACTION=="change", WAIT_FOR="nothing"

Press ctrl-x and enter 'y' to say yes to the save.

You might have to reboot for it to take effect.  I don't know, this is  new stuff!I'll give that a go.  So then I'll reboot.  see you in  a while ):P

---

### Post by rsavage on 2011-10-14
With the* KERNEL=="hdc", ACTION=="change", WAIT_FOR="nothing"* thing I think you may still see the messages, but CPU usage will be down?  Fingers crossed!

It would be interesting to compare the CPU usage with the 'ham-handed' workaround "sudo stop udev".

Midnight in four minutes.  I'm sleeping then!

---

### Post by Ms. Daisy on 2011-10-14
> **rsavage said:**
> With the* KERNEL=="hdc", ACTION=="change", WAIT_FOR="nothing"* thing I think you may still see the messages, but CPU usage will be down?  Fingers crossed! No dice. after saving the kernel thing I rebooted and ran top.
Cpu(s): 77.4%us, 21.2%sy,  0.0%ni,  0.0%id,  0.0%wa,  1.4%hi,  0.0%si,  0.0%st
top 4 processes: firefox22.4%, udisks-daemon 12.1%, gvfs-gdu-volume 12.1%, update-notifier 8.5% > **rsavage said:**
> It would be interesting to compare the CP usage with the 'ham-handed' workaround "sudo stop udev".% Why not. I'll post the results of that.> **rsavage said:**
> Midnight in four minutes.  I'm sleeping then!nighty nite, sleep tight.  Thanks for all your help!!!

---

### Post by rsavage on 2011-10-15
Something new to try:

udisks --inhibit-polling /dev/hdc

You'll have to open a new terminal program to check "top" and the "udisks --monitor" commands.

If this works then there is a method to make it permanent here:

[http://unix.stackexchange.com/questions/1399/dvd-drive-constanly-spins-up-down-when-idle](http://unix.stackexchange.com/questions/1399/dvd-drive-constanly-spins-up-down-when-idle)

Some background that I have found since: This bug [https://bugs.launchpad.net/linux/+bug/379780](https://bugs.launchpad.net/linux/+bug/379780) generated the possibility to disable polling [http://cgit.freedesktop.org/udisks/commit/?id=fb86ef144bad470b3d8ed761c7bdbe94886e5edd](http://cgit.freedesktop.org/udisks/commit/?id=fb86ef144bad470b3d8ed761c7bdbe94886e5edd) .

I hope this works!

---

### Post by Ms. Daisy on 2011-10-15
> **rsavage said:**
> Something new to try:udisks --inhibit-polling /dev/hdc
You'll have to open a new terminal program to check "top" and the "udisks --monitor" commands.
I don't think it worked. opened a second terminal to run top, Still super slow.  CPU says 76% us, 21 % sy.
top processes include udisks-daemon at 11%
However, inserting a blank CD makes me zoom right along. 
> Some background that I have found since: This bug [https://bugs.launchpad.net/linux/+bug/379780](https://bugs.launchpad.net/linux/+bug/379780) generated the possibility to disable polling [http://cgit.freedesktop.org/udisks/c...bdbe94886e5edd]("http://cgit.freedesktop.org/udisks/commit/?id=fb86ef144bad470b3d8ed761c7bdbe94886e5edd") .I'm going to look at this now.

---

### Post by rsavage on 2011-10-15
What?!?!?!?!?!?!?!?!?!?!?!?!?!!?!!??!?!?!?!?!!!!!

I was sure that would work.  Maybe it has a whole load of stuff in a queue that it has to go through first.

What about the udisks --monitor command?  Still producing a list with the polling inhibited?

---

### Post by rsavage on 2011-10-15
What's the output of

udisks --show-info /dev/cdrom

please?  Btw, did you know copy in a terminal is shift+ctrl+c and paste is shift+ctrl+v?

---

### Post by Ms. Daisy on 2011-10-15
> **rsavage said:**
> What's the output of

udisks --show-info /dev/cdrom

please?  Btw, did you know copy in a terminal is shift+ctrl+c and paste is shift+ctrl+v?I trid it with the CD out of the drive and here was the output
> Showing information for /org/freedesktop/UDisks/devices/hdc
  native-path:                 /sys/devices/pci0001:10/0001:10:17.0/0.80000000:mac-io/0.00020000:ata-3/ide1/1.0/block/hdc
  device:                      22:0
  device-file:                 /dev/hdc
    presentation:              /dev/hdc
    by-path:                   /dev/disk/by-path/pci-0001:10:17.0
  detected at:                 Sat 15 Oct 2011 10:24:03 AM EDT
  system internal:             0
  removable:                   1
  has media:                   0
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        0
  block size:                  0
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  drive:
    vendor:                    
    model:                     
    revision:                  
    serial:                    
    WWN:                       
    detachable:                0
    can spindown:              0
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 1
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                  optical_cd optical_cd_r optical_cd_rw optical_dvd optical_dvd_plus_r optical_dvd_plus_r_dl optical_dvd_plus_rw optical_dvd_r optical_dvd_rw optical_mrw optical_mrw_w
    interface:                 (unknown)
    if speed:                  (unknown)
    ATA SMART:                 not available And simply for my curiosity I'm going to do the same thing with the cd in the drive:
> Showing information for /org/freedesktop/UDisks/devices/hdc
  native-path:                 /sys/devices/pci0001:10/0001:10:17.0/0.80000000:mac-io/0.00020000:ata-3/ide1/1.0/block/hdc
  device:                      22:0
  device-file:                 /dev/hdc
    presentation:              /dev/hdc
    by-path:                   /dev/disk/by-path/pci-0001:10:17.0
  detected at:                 Sat 15 Oct 2011 10:24:03 AM EDT
  system internal:             0
  removable:                   1
  has media:                   1 (detected at Sat 15 Oct 2011 11:37:29 AM EDT)
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        2048
  block size:                  2048
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  optical disc:
    blank:                     1
    appendable:                0
    closed:                    0
    num tracks:                1
    num audio tracks:          0
    num sessions:              1
  drive:
    vendor:                    
    model:                     
    revision:                  
    serial:                    
    WWN:                       
    detachable:                0
    can spindown:              0
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 1
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     optical_cd_rw
      compat:                  optical_cd optical_cd_r optical_cd_rw optical_dvd optical_dvd_plus_r optical_dvd_plus_r_dl optical_dvd_plus_rw optical_dvd_r optical_dvd_rw optical_mrw optical_mrw_w
    interface:                 (unknown)
    if speed:                  (unknown)
    ATA SMART:                 not available

---

### Post by Ms. Daisy on 2011-10-15
> **rsavage said:**
> What?!?!?!?!?!?!?!?!?!?!?!?!?!!?!!??!?!?!?!?!!!!!

I was sure that would work.  Maybe it has a whole load of stuff in a queue that it has to go through first.

What about the udisks --monitor command?  Still producing a list with the polling inhibited? Let's make sure it's the process that's not working and not just me being clueless> udisks --inhibit-polling /dev/hdcI type that in to a terminal. It says "press control C to exit" so does it stay active until I press control c?  Does it remain active until I close the terminal?  Should I give it a bit of time to work?

---

### Post by rsavage on 2011-10-15
Yeah, polling is inihibited until you press crtrl+c or close the terminal.

So don't press/close anything.  Instead, open another terminal and give the 

udisks --show-info /dev/cdrom

output again please.  Also the 

udisks --monitor 

please.

You could try rebooting and running the commands immediately.  There shouldn't be much in a queue that way.

---

### Post by Ms. Daisy on 2011-10-15
> **rsavage said:**
> Yeah, polling is inihibited until you press crtrl+c or close the terminal.
So don't press/close anything.  Instead, open another terminal and give the 
udisks --show-info /dev/cdrom
output again please.  Also the 
udisks --monitor
You could try rebooting and running the commands immediately.  There shouldn't be much in a queue that way.
Well phooey. That's how I did it.  Did you see comment #60 where I pasted my output for udisks --show-info /dev/cdrom?  Should I try to reboot & run the command immediately?

I'm reading the bug report you mentioned and it seems to me that they are discussing the same problem I have.  It seems that they updated the firmware to solve the problem, although there's a whole lot of technical talk that I'm not following.  I installed all the non-free firmware during the original installation, so I would have thought I would have gotten updated firmware at that time, no?

---

### Post by rsavage on 2011-10-15
You never said if "sudo stop udev" worked?  I see on the bug report some people also restart it and it is okay then.

Looking at the stuff you've pasted already there is no vendor/model information so we'll have to find a new way to make a permanent fix.

I'm off the computer now.  Will check again this evening after my dinner.

---

### Post by rsavage on 2011-10-15
This is the bit we are interested in:

```
detection by polling:      1
detection inhibitable:     1
detection inhibited:       0
```Detection inhibited should change to 1 when you inhibit polling.  It should be 0 when you don't.  Is this the case?

---

### Post by Ms. Daisy on 2011-10-15
> **rsavage said:**
> You never said if "sudo stop udev" worked?Ah, I forgot about it!!!  Just executed it and Top says: 91% id (which I'm assuming means idle?)  and udisks isn't in the top 15.
So I read that as SUCCESS!!!!!!!!!!!!!!!!!!!!!  \\:D/ You'll be quite relieved that you couldn't see my awkward little jig there.
Will it remain permanent or do I need to do something else?

---

### Post by rsavage on 2011-10-15
No not permanent.  It is the ham-handed fix!  You won't have hot plugging of mice/keyboard/usb drive etc without it.  Is good, but we can do better.

---

### Post by rsavage on 2011-10-15
Got a new idea about a udev rule!  Maybe possible to ignore change messages if no media is inserted?  Got to think about that some more and how that works when you actually remove a disk.  It might be possible though to have polling and get rid of this horrible bug!  Did that go over your head?  Just thought I better write it down incase I forget!
 
In the meantime, can you continue to test the inhibiting polling please?
 
Btw, hot new picture you have there!  That is one way to guarantee help from a bunch of geeks I guess! :)

---

### Post by Ms. Daisy on 2011-10-16
Thanks ;) 
Oh yes, that just sailed right past me.  Although I'm assuming you're  talking about ignoring the constant stream of messages my computer is  sending itself. I'll continue messing with inhibiting polling. I also want to see if having a CD in stops it for a long time or if CPU starts slowing maxing out again.  I think I read that's what happens in the bug report you linked to.  I'll post back the results.

---

### Post by rsavage on 2011-10-16
Don't worry about my last post I was half asleep at the time.  Don't think it makes much sense to me now in fact!

As a point of interest, when polling is enabled and your computer is super slow, if you insert a data cd like a ubuntu live cd does it get automounted?

Back to disabling polling permanently.  Assuming this will fix it, I think this is what you need to do:

sudo nano /etc/udev/rules.d/my.rules

Delete what you wrote before and instead put:

SUBSYSTEM=="block", KERNEL=="hdc", ENV{UDISKS_DISABLE_POLLING}="1"

Save (ctrl+o), exit (ctrl+x) and try a reboot!

---

### Post by Ms. Daisy on 2011-10-16
> **rsavage said:**
> As a point of interest, when polling is enabled  and your computer is super slow, if you insert a data cd like a ubuntu  live cd does it get automounted?yes, or at least the icon is  visible on the screen. (until a week ago "mounting" was something done  on a horse so forgive my ignorance).  Although i haven't been able to get the CD drive to open today.  The keyboard has an eject key, but it's unresponsive (because I stopped udev?).  I can't find a way to open the drive via the GUI. I found this **[http://ubuntuforums.org/showthread.php?t=660515](http://ubuntuforums.org/showthread.php?t=660515)**, will this work on a PowerPC or is this strictly for PCs?  
> **rsavage said:**
> sudo nano /etc/udev/rules.d/my.rules
Delete what you wrote before  nothing was there to delete.   Should it have only lasted until I rebooted, which I did last night?  Or  should it have been there?
> **rsavage said:**
> and instead put:
SUBSYSTEM=="block", KERNEL=="hdc", ENV{UDISKS_DISABLE_POLLING}="1"
Did that.  I rebooted and CPU was pegged until I typed sudo stop udev in a terminal.:confused:

---

### Post by rsavage on 2011-10-17
> **Ms. Daisy said:**
> The keyboard has an eject key, but it's unresponsive (because I stopped udev?).  I can't find a way to open the drive via the GUI. I found this **[http://ubuntuforums.org/showthread.php?t=660515](http://ubuntuforums.org/showthread.php?t=660515)**, will this work on a PowerPC or is this strictly for PCs?  

Just read the first bit of that thread.  The command

eject /dev/hdc

should work, stopping udev shouldn't have an effect with that command, not sure about with the keyboard eject key.  Not familiar with the emac, do you have to press the function key on the keyboard as well as the eject key?  On some boots I have to press the function key on others I don't.

> **Ms. Daisy said:**
> 
 nothing was there to delete.   Should it have only lasted until I rebooted, which I did last night?  Or  should it have been there?


Then something has gone wrong now or before.

If you want to edit the file in a GUI the command is

gksudo mousepad /etc/udev/rules.d/my.rules

Can you check there are no errors please?  Don't have to reboot, instead type

udevadm trigger

There should be no output from

udisks --monitor

---

### Post by rsavage on 2011-10-17
Anticipating you may have problems with that gksudo command can you please type this first 
 
gksu-properties
 
Change the authentication mode to 'sudo'.  It will now work okay.

---

### Post by Ms. Daisy on 2011-10-17
Well the CD drive magically fixed itself after a reboot. But the command  to eject a cd is useful, going to use it in the future anyway.  And I  had actually encountered the password problem with gksudo before I saw  your post, and I implemented the solution you listed in your tutorial  thread. > **rsavage said:**
> Then something has gone wrong now or  before. If  you want to edit the file in a GUI the command is "gksudo mousepad  /etc/udev/rules.d/my.rules"
 Can you check there are no errors please?  Don't have to reboot, instead  type "udevadm trigger" There should be no output from "udisks  --monitor" I copied & pasted the commands the first time and  the second time.  The rule I currently show is
SUBSYSTEM=="block", KERNEL=="hdc", ENV{UDISKS_DISABLE_POLLING}="1"
And when I run udisks --monitor, I get the never ending list as  previously and CPU usage is high, although it's not 100% like  previously- maybe it's about 80 to 90%.  I don't get the list and CPU  usage is normal with a CD in the drive.  And BTW, the CD does NOT mount  on the desktop while I get the never ending list, but that may be  because I changed the mounting per the other thread (the one with the  "ham-handed" guy).

The problem may not be solved yet, but because of your patience &  persistence I have a functioning computer.  So here's my proposal,  rsavage.  How about I take some time & read an Ubuntu manual?  I'm  certain that you have a million things you'd rather do than walk some  helpless noob through this.  I'll play around on my new Ubuntu 11.04 PC  and on my brand-new Xubuntu Emac (with a CD permanently living in the CD  drive of course).  I'll get to know how Linux works.  It's just  abundantly clear that this Emac has problems that are FAR beyond  beginning stages.  I actually spent a few hours today going over this thread and the other threads linked here.  I'm getting a clue, but I'm nowhere near understanding it all.  I'm not giving up on the thing.  I'll just revisit it  occasionally until I actually understand the problems and the  solutions.  I don't want to take advantage of your incredibly generous,  helpful soul.

---

### Post by Ms. Daisy on 2011-10-24
Found this thread: [http://ubuntuforums.org/showthread.php?t=1859322](http://ubuntuforums.org/showthread.php?t=1859322).  I want to link to it here so that if I upgrade to 11.10 and CPU usage is still high I will be able to find this again. It documents high CPU usage in 11.10.  It also has several links to some fixes.  However, they are talking about PCs rather than Apples.  The fixes are for GRUB but Apples use Yaboot.  Of course if it's flash causing the problem for him then that's an easy fix: don't install flash!

edit: found another thread.  NOOOOOOOOOOOO!!!!  [http://ubuntuforums.org/showthread.php?t=1867518](http://ubuntuforums.org/showthread.php?t=1867518)

---

### Post by proxy.qtz on 2011-10-27
Dang it.

---

