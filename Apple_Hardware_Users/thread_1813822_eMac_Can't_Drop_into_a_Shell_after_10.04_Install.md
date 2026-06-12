---
title: "eMac Can't Drop into a Shell after 10.04 Install"
date: 2011-07-28
forum: Apple Hardware Users
---

### Post by c4c on 2011-07-28
[COLOR=black][FONT=Verdana]I recently came into (temp) possession of two Original, white, 700 MHz eMacs. I have only started to play on one of these so far. Installed Ubuntu 10.04 PPC from Alternate Install CD - two times actually (because I thought I may have screwed something up the first time), but both times it seemed to go without a hitch.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]After install and restart, I cannot drop into a shell, all I get is the black screen. I'm probably forgetting something really obvious, but I've tried Holding "Shift" and "F1" and control+alt+F1 (and F2, F3, F4, F5, F6), tried the esc key; with two different Apple USB keyboards. I'm really just wanting to load an xorg.conf file and reboot.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Should I have been trying to do this just after install, but **[FONT=Verdana]before[/FONT]** restarting? I can get into Open Firmware just fine, but have no idea what I'd do from OF except start off the CD again. I should mention I installed Debian just fine and am pretty confident MintPPC would work flawlessly, but I am trying to get Ubuntu 10.04 on here. Thanks in advance to anyone who can help. God bless.[/FONT][/COLOR]

---

### Post by rsavage on 2011-07-28
Don't know if this is it, but sometimes I have to hold down the "fn" key when I want normal F1, F2 etc behaviour.  So a control + alt + F1 becomes control + alt + fn + F1.  It only does this on some boots, others it works as expected.  I don't know why.

---

### Post by c4c on 2011-07-28
Hmm. You know I "set" the fn key in the expert install, maybe this has something to do with it? I will try your suggestion, control + alt + fn + F1. Thank you.

---

### Post by rsavage on 2011-07-29
How are you getting on?  I just tried the Fn + Control + alt + F1 combo and it did not work.  I'm sorry, I thought I had done this in the past.  For me half the boots have the fn stuck on and the other half has it off.  I wish it would act consistently so I'm interested if you know a way to make the action of the fn key stick?

---

### Post by rsavage on 2011-07-30
At the second yaboot prompt, type "Linux single".  It will boot into a menu from where you can drop into a shell.

---

### Post by c4c on 2011-07-30
Tried Fn + control + alt + F1 and Fn + control + alt + F2, even shift and esc on several reboots, but it didn't work to drop into a shell. Also tried reinstalling with the same results. Also tried installing 8.04 thinking I would just upgrade to 10.04 over the net, but I couldn't drop into a shell from 8.04 either. Also tried the other eMac, same specs, original 700 MHz; same results with both 8.04 and 10.04.

There are three possibilities I'm thinking of right now. One, is both of these eMac machines only have 256 MB RAM each. Didn't think that would be a show-stopper, but maybe it is for the Gnome desktop even though I haven't actually seen the Gnome desktop on these yet? Also wondering if this might have something to do with the USB keyboard and mouse, though every PPC iMac had nothing but, and I've installed this on G3 slot-loading iMacs, so I'm not sure about that either.

The third possibility that comes to mind is the way these eMacs hang at particular points during install. Every install and reinstall (only via CD, but I've re-downloaded, burned, re-burned,  at 24x, 8x, 4x and even 1x) has hung at the same point: Retrieving file 993 of 993, at 14%. It seemed like it wasn't really hanging as I'd hit the spacebar, or enter, or some other random key and it would jump up to 50% or thereabouts depending on when I noticed it and finish the install. But maybe this was really skipping stuff and I'm missing a/some very impotant file(s)?

---

### Post by c4c on 2011-07-30
Oh yeah. Forgot. I tried typing in "Linux single"  at 2nd Yaboot prompt too. No dice.

---

### Post by rsavage on 2011-07-30
Have you disabled KMS?  Lucid and Maverick had KMS enabled by default.
 
Natty doesn't have KMS so you could try that.  See the last page of the power pc sticky thread.

---

### Post by rsavage on 2011-07-30
Also, isn't there a yaboot option video=ofonly that it advices you to try if it can't boot?  Have you done that?

---

### Post by c4c on 2011-07-31
Thanks for coming up with options for me rsavage - I appreciate it!

I am downloading 11.04 Natty .iso (right after I write this reply) to see if that works, but I really do want, if I can, to have 10.04 running on these.

Last question answered first, sorry. Yep, I did try installing with video=ofonly, only it didn't make a difference on reboot.

So as I understand it now, to turn KMS off (in a 10.04 install) on an original eMac with NVIDIA graphics, I need to "issue" this command sometime during installation, not after:

echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

And if that is correct, can you tell me where/how during installation should I do this?

[I was thinking just after the installation asks me to remove the CD and reboot, I would remove the CD and hit <Back> instead, dropping me into a shell? Or, should I try control+alt+F1 somewhere/when else? Or, am I completely off here?]

And after this command is successfully issued; do I reboot and try again to execute a shell? Or, stay in the shell I'm in and add the xorg.conf file I have been planning to use [http://mac.linux.be/files/xorg/emac1.txt](http://mac.linux.be/files/xorg/emac1.txt) ?

Thanks again for the help! :D

---

### Post by rsavage on 2011-07-31
On 10.04 after you've installed try this on the second yaboot prompt
 
Linux nosplash video=ofonly nouveau.modeset=0
 
The nouveau.modeset=0 should turn off KMS.  If that works then we can make it permanent.
 
I think the problem is a crash, probably caused by some graphics issue.  I'm afraid I've never had this so I'm not the best troubleshooter.

---

### Post by rsavage on 2011-07-31
Some emacs seem to just to be troublesome [http://ubuntuforums.org/showthread.php?t=1108554](http://ubuntuforums.org/showthread.php?t=1108554)

---

### Post by c4c on 2011-07-31
Tried what you had asked me to type in at the 2nd Yaboot prompt (Linux nosplash video=ofonly nouveau.modset=0) and got a short error:
[    15.639349] nouveau: Unknown parameter 'modset'
saw Ubuntu - this time saw all four dots turn red (before I'd only get to see one) before the screen went black. And this time, I was able to use control+alt+F1 to get to a login prompt.
This is what I saw:
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
[OK]
 *setting sensors limits                                                                                               [OK]

ubuntu login:

Great! think I'm getting somewhere here. Now what?:)

---

### Post by c4c on 2011-07-31
Tried with subsequent reboots. After that command at the 2nd Yaboot, control+alt+F1 will still get me into a ubuntu login prompt. :KS

---

### Post by c4c on 2011-07-31
Oh yes - I'm sure this is unimportant, but the Ubuntu dots are actually going from white to yellow (not red) now.

---

### Post by rsavage on 2011-08-01
I'm a bit confused - what version of ubuntu are you using now and what yaboot parameters are you typing?
 
Your error was caused by a typo.  It should be modeset not modset.  Seems KMS is not the problem anyway.
 
I thought you wouldn't actually be seeing the ubuntu dots because of the 'nospash' parameter.  Oh well.
 
Login.  Download your xorg.conf using the wget command.  Copy across using 
 
sudo mv file_name /etc/X11/xorg.conf
 
where file_name will be whatever it is called.
 
Reboot "sudo reboot" and see if it boots up withouth any yaboot parameters.

---

### Post by c4c on 2011-08-01
Thanks for keeping with me here. I'm running Ubuntu 10.04 PPC. Sorry about the typo. When I typed it right, it worked without error to allow me to login with control+alt+F1. Downloaded [http://mac.linux.be/files/xorg/emac1.txt](http://mac.linux.be/files/xorg/emac1.txt) and saved it to xorg.conf, did sudo reboot, but wasn't able to get into Gnome. Did control+alt+del to reboot and this time again put in Linux nosplash video=ofonly nouveau.modeset=0 at the 2nd Yaboot prompt and Ubuntu/Gnome loaded :) in low graphics mode. Looks wacky of course, but you got me in. Running updates now.

---

### Post by rsavage on 2011-08-01
That xorg.conf is ridiculous.  You would be better setting up your own xorg.conf (see neighbouring thread [http://ubuntuforums.org/showthread.php?t=1815708](http://ubuntuforums.org/showthread.php?t=1815708)).  Have you tried it without video=ofonly?

---

### Post by linuxopjemac on 2011-08-01
> **rsavage said:**
> That xorg.conf is ridiculous.  You would be better setting up your own xorg.conf (see neighbouring thread [http://ubuntuforums.org/showthread.php?t=1815708](http://ubuntuforums.org/showthread.php?t=1815708)).  Have you tried it without video=ofonly?

I agree on that.

---

### Post by c4c on 2011-08-01
:P I'm in without video=ofonly! The emac6.txt [[http://mac.linux.be/files/xorg/emac6.txt](http://mac.linux.be/files/xorg/emac6.txt)] did the trick to get xorg.conf to work on this original eMac. The GUI (Gnome) is great, running the default 1024x768 @ 89 Hz it's just the way I like it. Subsequent reboots, and Shutdown, power-up - it all still works!

The emac1.txt xorg.conf *was* ridiculous. Looked like a whole bunch of tests for every possibility (I think I'll keep that one around for reference). I can't knock linuxopjemac though - he's got the easiest-to-find and easiest to load xorg.conf files for Apple/PPCs around. 

Thanks you rsavage for all your help getting me to a shell! :D

---

### Post by c4c on 2011-08-22
Just a small follow-up. Seems when these original eMacs remain unconnected to a power source for any extended period (unplugged to move or due to power outage), they can revert back to showing a black screen when booting. Fix is to issue that same command at the second yaboot prompt: Linux nosplash video=ofonly nouveau.modeset=0

---

### Post by oswaldkelso on 2011-08-22
> **rsavage said:**
> That xorg.conf is ridiculous.  You would be better setting up your own xorg.conf (see neighbouring thread [http://ubuntuforums.org/showthread.php?t=1815708](http://ubuntuforums.org/showthread.php?t=1815708)).  Have you tried it without video=ofonly?

That xorg.conf was used to fix a kernel update that left my emac (and others) with a badly broken X.
The Debian dev that asked me to test and supply him with the details also fixed the emacs mini external monitor connection and passed the fix upstream for all other Gnu/Linux users to benefit from. How ridiculous it that.

All PPC users need to share their info, were a small enough community as it is and with out this free sharing of knowledge were screwed!

---

### Post by rsavage on 2011-08-23
I don't know why you are so touchy about this?  Your post only backs up my statement.  Clearly it was an xorg.conf for testing and not for everyday use.

[QUOTE=oswaldkelso]All PPC users need to share their info, were a small enough community as it is and with out this free sharing of knowledge were screwed![/QUOTE]

Another strange comment.  You don't need to lecture me on this.  Have you read the thread and seen who was answering the questions?  Have you seen who has written a lot of the "how to" guides lately?  Sharing knowledge is good as long as it is relevant, accurate and follows best practice.

---

### Post by rsavage on 2011-08-23
c4c, forgot to comment on your post.  What you describe is very strange indeed, but I think I have read somewhere that the xorg server sometimes doesn't start if the time and date are wrong (e.g. set to the 1970s or something).  Perhaps you need to replace a battery in the emac to fix this?

---

### Post by c4c on 2011-08-27
Battery did not occur to me since the date/time was showing up properly in both eMacs - but I did have them plugged in to the network, so they may have just been getting that from the server. I'll have to try it without Ethernet hooked up.

Another thing I did not realize before was that just above the CD Drive, a small black wire going into an L-shaped silver tip was loose on both these eMacs. I just shoved it back in the hole and completely forgot about it until today when I received yet another eMac (exact same year/specs) and saw that this wire had a holder just for it on the other side of a black cover over the CD Drive. Anybody know what this is (for)? I shudder to think this could have been the cause of my CD Drive woes. :oops:

---

### Post by oswaldkelso on 2011-08-28
That'll be the Airport Extreme card slot. Best left as it is and using a usb-wifi dongle if you need one.

---

### Post by c4c on 2011-08-28
Okay, thanks for that info oswaldkelso. After installing Ubuntu 10.04 on this (actually - I'm writing on it right now) had the exact same issues with CDs and "solved" it the exact same way [eMaCDfix]("http://ubuntuforums.org/showthread.php?t=1817971"). Other than the issues on that thread and this one, Lucid runs fairly snappy on these original eMac machines. Did I mention these only have 256MB RAM? I'm pretty impressed. :)

---

### Post by c4c on 2011-09-06
Tried the two eMacs with the "losing connection to the xorg.conf" problem without plugging them into the network and (thanks rsavage) it indeed seemed to be the batteries. Ordered two and put them in (long as I was in there, bumped up the RAM a bit) and everything is fine.):P

---

