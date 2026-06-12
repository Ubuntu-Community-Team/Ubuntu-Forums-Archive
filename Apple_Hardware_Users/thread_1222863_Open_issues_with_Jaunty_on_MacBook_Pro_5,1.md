---
title: "Open issues with Jaunty on MacBook Pro 5,1"
date: 2009-07-25
forum: Apple Hardware Users
---

### Post by Nikos.Alexandris on 2009-07-25
Hi all!

While Jaunty is pretty stable now on MBP5,1 (and other MBP's as well), there are a series of issues (which maybe important or just annoying, or very generic) which may or may have not been reported in the forum/ Launchpad. In any case, those are issues (at least for me).

My idea is to collect open issues and mention them in the wiki [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty") under an independent section. Following [s]the[/s] issues [s]I "still" experience[/s] collected from this thread (from users with Jaunty 64-bit running on MBP5,1).

[COLOR="Red"]11.Sept.2009: Partially updated the wiki![/COLOR]

*By Nikos A*
[LIST]
[*][s]The system does not reboot.[/s]
[s][COLOR="Blue"]Now it does!!:-) [/COLOR] What was the problem? I don't know. What has been changed is updates/dist-upgrades, latest PulseAudio packages, using TwinView.[/s]
**And it does NOT work again. :-( Could it be a random effect?**


[*]The ambient light sensor does not work ([COLOR="RoyalBlue"]correctly!?[/COLOR]) for both the display backlight and the backlit keyboard. See also [[COLOR="Blue"]https://bugs.launchpad.net/ubuntu/+source/hal/+bug/285815[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/285815").


[*][s]I often receive the following message (for example when I execute **gksudo SomeFile**) [COLOR="DarkSlateGray"]Xlib:  extension "RANDR" missing on display ":0.0".[/COLOR] This may be relevant with the Nvidia driver (?).[/s]
[COLOR="Blue"]Fixed by using TwinView (+effects activated) and dropping the (...pardon me) "horrible" Xinerama :-p[/COLOR] :-)


[*][s]Whenever I try to run Pulse Audio Volume Control I get the error message [COLOR="DarkSlateGray"]Connection failed: Connection refused[/COLOR][/s]
[COLOR="Blue"]Fixed by removing everything, then following this guide/ppa [[COLOR="RoyalBlue"]http://webupd8.blogspot.com/2009/05/how-to-install-latest-pulseaudio-0915.html[/COLOR]]("http://webupd8.blogspot.com/2009/05/how-to-install-latest-pulseaudio-0915.html") for latest pulse packages and afterwards following instructions in the wiki [[COLOR="RoyalBlue"]https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Sound[/COLOR]]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Sound").[/COLOR] :-)


[*]I've tried several things to get *gnome-lirc-properties* to work and "train" the remote control but no luck. Only *volume up*, *volume down* work. The rest of the buttons seem to send a signal which is executed correctly (current active button-field flashes).
For example (assuming you have gnome-lirc installed): [COLOR="Blue"]System[/COLOR] > [COLOR="Blue"]Preferences[/COLOR] > [COLOR="Blue"]Remote Control Properties[/COLOR], give your password, (remote is autodetected, if not try out the *Auto-detect* button, it will work) > [COLOR="Blue"]Custom Configuration[/COLOR] > [COLOR="Blue"]Key Codes[/COLOR] > Select a "key" (e.g. [COLOR="Blue"]Menu[/COLOR]) > [COLOR="Blue"]Learn[/COLOR].
The error message that I always get is: [COLOR="DarkSlateGray"]Learning of Key Code Failes - Could not initialize hardware[/COLOR].


[*]I think the NV Clock works constantly at 500 MHz (=no GPU scaling at all). **Comment by Nikos A:** yes, I use **Coolbits "1"** in xorg.cong


[*][s]I often work with an external LCD (using Xinerama). I face the following oddity: with the external USB mouse I can move the pointer around the whole virtual display (I mean both the laptop display and the external display). When I use the trackpad the pointer is limited solely to the laptop's display!![/s]
[COLOR="Blue"]Fixed by using TwinView :-)[/COLOR]
[COLOR="Red"]Update (22.08.2009):[/COLOR] unfortunately using twinview introduced a new problem: [COLOR="Red"]window decoration/ borders are missing and are (re-)activated only when I turn on the effects (compiz)[/COLOR]. Is there a work-around for this?


[*] when booting in EFI mode (see thread [http://ubuntuforums.org/showthread.php?t=995704]("http://ubuntuforums.org/showthread.php?t=995704"), post **#906**) the power-manager does not work correctly. Display/keyboard brightness don't work as well.
[/LIST]

*By GeneralSunTzu*
[LIST]
[*] [s]trackpad does not work fully, even closely following the wiki instructions (I am obliged to use a USB mouse, if I want to click and drag an object)[/s]The configurability of the trackpad with an obscure and not very well documented text file (gsynaptics) is not great... [COLOR="Blue"](see post #36)[/COLOR].


[*] it still overheats significantly, if compared with Mac OS X


[*] repositories do not contain the latest NVIDIA proprietary driver.
[/LIST]


*By swarup*

[LIST]
[*] [s]Can't disable the touchpad.[/s]
[COLOR="Blue"]Install *gsynaptic* from the repositories. Then **System** > **Preferences** > **Touchpad** > In the **General** tab uncheck **Enable Touchpad**.
[/COLOR]

[*] [s]Disable Touchpad While Typing[/s]
[COLOR="Blue"]Already solved and very well documented at [https://help.ubuntu.com/community/MacBook2-1/Jaunty#Disable%20Touchpad%20While%20Typing]("https://help.ubuntu.com/community/MacBook2-1/Jaunty#Disable%20Touchpad%20While%20Typing").[/COLOR]
**Comment by swarup:** There were only a few scattered occasions on which it moved the cursor somewhere else when it shouldn't have.
**Comment by Nikos A:** the cursor is moved too many times somewhere else.


[*] The MBP runs quite a bit hotter with Jaunty than it does with OSX
**Comment by Nikos A:** Extensively discussed. Let's test various things, support tests for efi-booting, perhaps a solution can be found and make it to Karmic Koala?
[/LIST]

Please add your issues or solutions so we can extend the wiki. All the best, Nikos

---

### Post by GeneralSunTzu on 2009-07-26
I would add:

- trackpad does not work fully, even closely following the wiki instructions (I am obliged to use a USB mouse, if I want to click and drag an object);
- it still overheats significantly, if compared with Mac OS X;
- repositories do not contain the latest NVIDIA proprietary driver.

The trackpad problem may have been the object of a bug reported, I know, but there is no solution I know of.

---

### Post by Nikos.Alexandris on 2009-07-26
> **GeneralSunTzu said:**
> I would add:

I took the liberty to add you suggested issues in the first post. However I don't experience all of them so I'll add my comments on yours (something that, hopefully, somebody will do with mine to shorten the list of "open issues") :-)


> - trackpad does not work fully, even closely following the wiki instructions (I am obliged to use a USB mouse, if I want to click and drag an object);

I don't have this problem. For me the trackpad works very nice (tapping, double tapping, smooth scrolling, selecting, etc.). I think I've just followed the wiki.


> - it still overheats significantly, if compared with Mac OS X;

I am almost convinced that this is because the constant use of the GT9600M discrete graphics device. Try to run OS-X _only_ with it and watch the temperature for a while. People have managed to get grub-efi working (I am still fighting with it) and this should give as longer lasting battery and lower temperatures.



> - repositories do not contain the latest NVIDIA proprietary driver.

That is something we simple users can't change and have to live with it I guess. Or we start getting involved deeper (as devs?) where we might have the option to make things roll faster or... ?


> The trackpad problem may have been the object of a bug reported, I know, but there is no solution I know of.

That was exactly my idea. No matter if reported or not, things that don't work should be mentioned/described in detail in the wiki.

All the best, Nikos

---

### Post by GeneralSunTzu on 2009-07-26
Then maybe you would please care to:
a. name the exact sequence of steps you do to, for instance, drag a folder from the desktop into the trash and;
b. copy here your /etc/hal/fdi/policy/x11-synaptics-bcm5974.fdi file, unless it is absolutely identical to the one in the wiki.
Thank you. This should allow me to locate my possible mistake.
I made sure that in X11 xorg.conf dooes not contain anything related to the trackpad, and for the rest I followed closely the wiki (remouve mouseemu, install pommed, etc.).
Given that we have exactly the same MBP, there must be a difference that explains the different behaviours.

[As to a., if I click on a folder, without releasing it, and then move any number of fingers it won't do much except, now that I put exactly the same file as in the wiki, maybe with three fingers (am not sure whether with three or two fingers].

---

### Post by Nikos.Alexandris on 2009-07-26
> **GeneralSunTzu said:**
> Then maybe you would please care to:
a. name the exact sequence of steps you do to, for instance, drag a folder from the desktop into the trash and;

[As to a., if I click on a folder, without releasing it, and then move any number of fingers it won't do much except, now that I put exactly the same file as in the wiki, maybe with three fingers (am not sure whether with three or two fingers].

Sure! ( I moved your PS here since it's related directly with point a. ) The first one is simple: drag-n-drop using *one* finger == tap-tap-hold on icon/file (that is: **don't release after the second tap**), then drag, then release somewhere.


> b. copy here your /etc/hal/fdi/policy/x11-synaptics-bcm5974.fdi file, unless it is absolutely identical to the one in the wiki.

It is a _bit_ different. Here you go:
```
cat 11-x11-synaptics.fdi
```
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.touchpad">
   <match key="info.product" contains="bcm5974">
   <merge key="appledevice" type="bool">true</merge>
   </match>
  
   <match key="appledevice" bool="true">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.FingerLow" type="string">100</merge>
        <merge key="input.x11_options.FingerHigh" type="string">200</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>

        <merge key="input.x11_options.HorizScrollDelta" type="string">40</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">40</merge>

        <merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>

        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">25</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">250</merge>
   </match>
  </match>
 </device>
</deviceinfo>
```

> Thank you. This should allow me to locate my possible mistake.
I made sure that in X11 xorg.conf dooes not contain anything related to the trackpad, and for the rest I followed closely the wiki (remouve mouseemu, install pommed, etc.).

As far as i know, pommed is not "valid" for our machines. You probably should remove it. Not 100% sure though :-?

> Given that we have exactly the same MBP, there must be a difference that explains the different behaviours.


Right, could you please, if you have the time, go through "my" list and check if something that does not work for me works for you?

Kindest regards, Nikos

---

### Post by Nikos.Alexandris on 2009-07-28
Great... I've fixed some important issues by using TwinView and (re-)installing latest pulseaudio stuff from [[COLOR="RoyalBlue"]http://webupd8.blogspot.com/2009/05/how-to-install-latest-pulseaudio-0915.html[/COLOR]]("http://webupd8.blogspot.com/2009/05/how-to-install-latest-pulseaudio-0915.html").:guitar:

---

### Post by ercoppa on 2009-07-29
Nikos.Alexandris, the reboot works for you?

---

### Post by Nikos.Alexandris on 2009-07-29
> **ercoppa said:**
> Nikos.Alexandris, the reboot works for you?

> YES!!! :D I didn't even try it since I was used to it not working :D

Great!!

Well... what can I say? **It does not work again!!!** It worked... more than one or two times.

ercoppa, I remember now, I have passed an option and this is:
**vga=773** to have a higher resolution @boot process.

---

### Post by ercoppa on 2009-07-30
> YES!!!  I didn't even try it since I was used to it not working
What kernel? Do you pass some option by menu.lst?

---

### Post by Nikos.Alexandris on 2009-07-30
> **ercoppa said:**
> What kernel? Do you pass some option by menu.lst?

```
uname -a
Linux vertical 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 x86_64 GNU/Linux
```

[s]No options changed. Same as before.[/s] Yes, check post #8.

---

### Post by Nikos.Alexandris on 2009-07-31
Just a(nother) crazy update:

 * The system rebooted successfully one more time and that was it. Every attempt to reboot again was, as usual, freezing the system at the very last step.

 * I managed to break Pulse Audio... it's so easy :-). I wanted to install festival and I messed it up. I removed every pulse* package, installed them again from ubuntu repositories, upgraded to the latest pulse-packages provided by the PPA indicated in the first post, followed the wiki (for MBP5,1 - Jaunty) and I have sound again.

I wonder if it makes sense that owners of the same models that have things working would post here or in another thread their settings.

Regards, Nikos

---

### Post by swarup on 2009-08-01
Nikos,
You mention that the ambient light sensor does not work for the display backlight in MBP 5,1. I have a MBP 5,2 and am having the problem that the ambient light sensor takes over control of the settings, and keeps the screen quite dim. The manual control F2 does work to make the screen as bright as I wish, but that setting only holds for 10-15 seconds, and then the auto-adjust kicks in and makes the screen dim again. Is there a way to turn off the auto-adjust?
Thanks,
Swarup

---

### Post by Nikos.Alexandris on 2009-08-01
> **swarup said:**
> Nikos,
You mention that the ambient light sensor does not work for the display backlight in MBP 5,1. I have a MBP 5,2 and am having the problem that the ambient light sensor takes over control of the settings, and keeps the screen quite dim. The manual control F2 does work to make the screen as bright as I wish, but that setting only holds for 10-15 seconds, and then the auto-adjust kicks in and makes the screen dim again. Is there a way to turn off the auto-adjust?
Thanks,
Swarup

I think you are looking for the following: [s]**System > Preferences > General > Use ambient light to adjust LCD brightness**[/s].

**System > Preferences > [COLOR="Blue"]Power Management[/COLOR] > General > Use ambient light to adjust LCD brightness**. Just uncheck it.

AFAIK from reading threads and launchpad reports, it's a matter of correctly scaling what the sensors reads (because the sensor exists and works).

Regards, Nikos

---

### Post by swarup on 2009-08-01
> **Nikos.Alexandris said:**
> I think you are looking for the following: **System > Preferences > General > Use ambient light to adjust LCD brightness**. Just uncheck it.

In Jaunty, I don't see any "General" within the Preferences menu. I tried looking in Preferences -> Display, but on my computer (17" MBP), that brings up the NVIDIA manager window, which has no options I can see for what you speak of. Can you give me some further sense of where I should look?

---

### Post by Nikos.Alexandris on 2009-08-01
> **swarup said:**
> In Jaunty, I don't see any "General" within the Preferences menu. I tried looking in Preferences -> Display, but on my computer (17" MBP), that brings up the NVIDIA manager window, which has no options I can see for what you speak of. Can you give me some further sense of where I should look?

Ohh!!! My bad. Sorry, i did not realise... it is as follows: **System > Preferences > [COLOR="Blue"]Power Management[/COLOR] > General (tab) > Uncheck the respective option**.

If this is not there... then what can I say!?

---

### Post by swarup on 2009-08-03
> **Nikos.Alexandris said:**
> it is as follows: **System > Preferences > [COLOR="Blue"]Power Management[/COLOR] > General (tab) > Uncheck the respective option**.

Wow, great-- now the problem is solved. I just needed to be able to control the screen brightness myself. 

Now, I have one last big problem: the trackpad. I use the computer mostly for typing text, and I type a lot. And I love the MBP keyboard and its easy touch. But the very serious problem is this: if during typing I allow my palms to rest on the laptop as one ordinarily does, then inevitably the palms will brush lightly occasionally on the trackpad in the course of typing. After all, the trackpad is so big it cannot be avoided. And any time that happens, the cursor where I'm typing, will jump to another part of the page and my typed letters start appearing somewhere else on the page than where I want them.

I've had this computer for a week now, and for this week I've had to type everything with my wrists up in the air, palms off the computer. It's the only way I can type and not ever touch the trackpad.

I called apple and asked how it works in OSX, and they said that even if your palms touch the trackpad while you type in OSX, the cursor will not jump elsewhere. Only the "arrow" will be moved elsewhere, but the cursor which marks your typing will remain where you want it. Is there some way this same facility can be arranged in Jaunty? 

This is one very critical matter for me-- if it cannot be fixed, I may just have to return the computer to apple (for business purchases, one has a 14-day window for returning with no restocking fee). And otherwise I like the computer very much.

---

### Post by Nikos.Alexandris on 2009-08-03
> **swarup said:**
> Wow, great-- now the problem is solved. I just needed to be able to control the screen brightness myself. 

Now, I have one last big problem: the trackpad.

Install *gsynaptic* from the repositories. Then **System** > **Preferences** > **Touchpad** (or similar) > In the **General** tab *uncheck* **Enable Touchpad**.

That's all. Maybe there can be a shortcut defined for that, not sure.

---

### Post by swarup on 2009-08-03
> **Nikos.Alexandris said:**
> Install *gsynaptic* from the repositories. Then **System** > **Preferences** > **Touchpad** (or similar) > In the **General** tab *uncheck* **Enable Touchpad**.

I just tried it--and it completely turned the trackpad off so I couldn't use it as all. That wouldn't do-- without the trackpad I can't do anything, can't maneuver in the computer. I need the trackpad to be *on*, but not doing what I described above when I type. I have used ubuntu with many laptops, and nothing like this ever happened with any other laptop while the trackpad was turned on and working.

---

### Post by ercoppa on 2009-08-03
Install syndaemon (read [here]("https://help.ubuntu.com/community/MacBook2-1/Jaunty#Disable Touchpad While Typing")). It resolves this problem for me.

Greets, ercoppa.

---

### Post by Nikos.Alexandris on 2009-08-03
> **swarup said:**
> I just tried it--and it completely turned the trackpad off so I couldn't use it as all. That wouldn't do-- without the trackpad I can't do anything, can't maneuver in the computer. I need the trackpad to be *on*, but not doing what I described above when I type. I have used ubuntu with many laptops, and nothing like this ever happened with any other laptop while the trackpad was turned on and working.

swarup, sorry for the "wrong" reply then. What you describe happens also to me sometimes. I'll have a look at ercoppa's suggestion and update the firs post of the thread.

(
My aim is to collect finally _only_ problems and update the wiki at some point.
)

---

### Post by Nikos.Alexandris on 2009-08-03
> **ercoppa said:**
> Install syndaemon (read [here]("https://help.ubuntu.com/community/MacBook2-1/Jaunty#Disable Touchpad While Typing")). It resolves this problem for me.

Greets, ercoppa.

WoW! This page (about MacBook2-1/Jaunty) is one of the most complete I've seen. Great work ;-)

I'll try out syndaemon and feed-back this thread only in case of success.

---

### Post by Nikos.Alexandris on 2009-08-03
> **Nikos.Alexandris said:**
> WoW! This page (about MacBook2-1/Jaunty) is one of the most complete I've seen. Great work ;-)

I'll try out *syndaemon* and feed-back this thread only in case of success.

Well, *syndaemon* does not play nice for me. It's like it implements an undo very frequently which is very annoying. I'll remove it for now and check back later to see if I misconfigured something.

---

### Post by swarup on 2009-08-03
> **ercoppa said:**
> Install syndaemon (read [here]("https://help.ubuntu.com/community/MacBook2-1/Jaunty#Disable Touchpad While Typing")). It resolves this problem for me.

Wow-- I am so excited to know someone else has experienced the same problem, and that there is a solution. :)

I went to the site you referenced, and did the first step of going to System &#9656; Preferences &#9656; Startup Applications and adding a new startup program configured with the following command: syndaemon -d -t -K. Then the next step is to execute a command in the terminal window, which I did with the following result:

```
:~$ echo -e '#!/bin/sh\nsyndaemon -d -t -K' | tee -a ~/.kde/Autostart/syndaemon
tee: /home/swarup/.kde/Autostart/syndaemon: No such file or directory
#!/bin/sh
syndaemon -d -t -K
```

So I went to Synaptic Package Manager to see if there is a package named "Syndaemon" which I need to download. But when I search on it, it just shows me the Synaptics Touchpad Driver, which is already installed. So what do I need to do to get the above terminal window command to work?

---

### Post by Nikos.Alexandris on 2009-08-03
> **swarup said:**
> Wow-- I am so excited to know someone else has experienced the same problem, and that there is a solution. :)

I went to the site you referenced, and did the first step of going to System &#9656; Preferences &#9656; Startup Applications and adding a new startup program configured with the following command: syndaemon -d -t -K. Then the next step is to execute a command in the terminal window, which I did with the following result:

```
:~$ echo -e '#!/bin/sh\nsyndaemon -d -t -K' | tee -a ~/.kde/Autostart/syndaemon
tee: /home/swarup/.kde/Autostart/syndaemon: No such file or directory
#!/bin/sh
syndaemon -d -t -K
```


The above code is _only_ for Kubuntu. If you run Ubuntu then you just need to log-out and log-in. Or execute

```
syndaemon -d -t -K
``` or in case of errors ```
syndaemon -d -t -K -S
```

---

### Post by swarup on 2009-08-03
I see, thanks Nikos. I'm at work now-- will try what you've told me when I get home.
Swarup

---

### Post by swarup on 2009-08-04
Ok, today I installed syndaemon and have been typing extensively with it running. I find that it has solved the vast majority of the problem. I can type with my hands resting on the computer now, and the cursor doesn't go flying all over the place. There were only a few scattered occasions on which it moved the cursor somewhere else when it shouldn't have. Otherwise, for 98% of the time I'd say that for me, this particular problem has been solved. 

So that makes two huge solutions which I've been fortunate to find on this thread: (1) how to turn off the screen auto-adjust; and (2) how to make the trackpad stable for typing.

What I think may be the last major hurdle for me with this computer is that the left side where the left hand rests while typing, gets quite warm-- bordering on hot. And is uncomfortable. I see on the MBP 5-1,5-2/Jaunty [wiki]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty") that by configuring the computer to run with the chipset graphicchip (Nvidia 9400), 

> Batterylife seems to improve from 1:40 to 3:20 and the laptop is 10° cooler. 

To achieve this, it says, one has to get the laptop to boot in efi-mode, by installing either elilo or grub2. By the looks of the elilo install description, it seems difficult to do. Also, there is the described drawback that "cpufreq renders system instable". And the grub2 install instructions are written out in only a very general (rather than step-by-step) way. Is it worth doing this conversion over to run with the chipset graphicchip (Nvidia 9400)? Will the left side of the laptop (where my left hand rests as I type) be cooler? If so, it may be worth it to me to do the install.

---

### Post by swarup on 2009-08-05
Do you find that the MBP runs quite a bit hotter with Jaunty than it does with OSX? I do. I did the install of the fan and temp management from the wiki, but I don't know if it is running properly and if it is running, it doesn't seem to do much. Any thoughts on this point?

---

### Post by Nikos.Alexandris on 2009-08-05
> **swarup said:**
> Do you find that the MBP runs quite a bit hotter with Jaunty than it does with OSX? I do. I did the install of the fan and temp management from the wiki, but I don't know if it is running properly and if it is running, it doesn't seem to do much. Any thoughts on this point?

This has been discussed extensively. It is hotter but it is, IMHO, ok (=the machine is not going to fire-up :-p).

Of course it would be perfect to get grub-efi working without problems. We (simple users) have to support the dev's by testing(or tasting) what they are baking :-). I believe, from what I read on the net (forum, launchpad, etc.) that we are close to a good solution.

Nikos

---

### Post by Nikos.Alexandris on 2009-08-06
[s]Does anybody else epxerience kernel panic with kernel 2.6.28-15-generic / Jaunty 64-bit?

I work now with the previous kernel 2.6.28-14-generic.[/s] [COLOR="Blue"]solved, check post # 38.[/COLOR] Probably I had done something wrong while playing with grub2.

---

### Post by alexmurray on 2009-08-06
Can you post the backtrace from the kernel panic? I've been running -15 fine so far for the past day or so under EFI.

---

### Post by Nikos.Alexandris on 2009-08-06
> **alexmurray said:**
> Can you post the backtrace from the kernel panic? I've been running -15 fine so far for the past day or so under EFI.

I can't find anywhere the unsuccessful log (in **/var/log/kern.log** and **/var/log/kern.log.0** I see only successful boots using the -14 kernel). Where can I find the "bad" log?

Anyhow, booting in text mode the system freezes at the 3rd ~ 4th second with a message like (writing from my memory) *kernel panic - cannot sync VFS - cannot mount root on unknown block(0,0)*.

Does this help at all?

---

### Post by alexmurray on 2009-08-06
I wonder if you're not using the correct initrd image for the new kernel? Can you check that a new one has been created (should happen when the -15 kernel is installed) and that grub is using this new initrd?

---

### Post by Nikos.Alexandris on 2009-08-06
> **alexmurray said:**
> I wonder if you're not using the correct initrd image for the new kernel? Can you check that a new one has been created (should happen when the -15 kernel is installed) and that grub is using this new initrd?

alex,

a lot of this stuff is new field for me. Could you please help me more (of course I am searching help files and the web) to understand where I can find the "new" initrd? It's just a file? Well, ok I am looking for it... hopefully I find it quickly.

P.S. For Your Interest, I installed and removed another kernel (the -rt one) just to be sure that grub2-update work(-ed)s fine. Here the result of [s]installing[/s]/purging the -rt kernel:

```
sudo apt-get purge linux-image-2.6.28-3-rt

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.28-3-rt*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 112MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 359978 files and directories currently installed.)
Removing linux-image-2.6.28-3-rt ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
rmdir: failed to remove `/lib/modules/2.6.28-3-rt/updates/dkms': No such file or directory
rmdir: failed to remove `/lib/modules/2.6.28-3-rt/updates': No such file or directory
run-parts: executing /etc/kernel/prerm.d/last-good-boot
Running postrm hook script /usr/sbin/update-grub.
Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Mac OS X on /dev/sda2
  Mac OS X is not yet supported by update-grub.
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.28-3-rt ...
Running postrm hook script /usr/sbin/update-grub.
Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Mac OS X on /dev/sda2
  Mac OS X is not yet supported by update-grub.
done
```

---

### Post by Nikos.Alexandris on 2009-08-06
> **alexmurray said:**
> I wonder if you're not using the correct initrd image for the new kernel? Can you check that a new one has been created (should happen when the -15 kernel is installed) and that grub is using this new initrd?

That the new is there: yes, I think it's there.

```
locate initrd | grep -v home | grep -v share | grep -v src

/initrd.img
/initrd.img.old
/boot/initrd.img-2.6.28-14-generic
/boot/initrd.img-2.6.28-15-generic
/lib/modules/2.6.28-14-generic/initrd
/lib/modules/2.6.28-14-generic/initrd/vesafb.ko
/lib/modules/2.6.28-15-generic/initrd
/lib/modules/2.6.28-15-generic/initrd/vesafb.ko
/usr/lib/e2initrd_helper
```


That the new one is being used: not sure :-?

---

### Post by Nikos.Alexandris on 2009-08-06
> **Nikos.Alexandris said:**
> alex,

...

```
sudo apt-get purge linux-image-2.6.28-3-rt

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.28-3-rt*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 112MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 359978 files and directories currently installed.)
Removing linux-image-2.6.28-3-rt ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
rmdir: failed to remove `/lib/modules/2.6.28-3-rt/updates/dkms': No such file or directory
rmdir: failed to remove `/lib/modules/2.6.28-3-rt/updates': No such file or directory
run-parts: executing /etc/kernel/prerm.d/last-good-boot
Running postrm hook script /usr/sbin/update-grub.
Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Mac OS X on /dev/sda2
  Mac OS X is not yet supported by update-grub.
done
[B]The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
[/B]Purging configuration files for linux-image-2.6.28-3-rt ...
Running postrm hook script /usr/sbin/update-grub.
Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Mac OS X on /dev/sda2
  Mac OS X is not yet supported by update-grub.
done
```

So, if the above bolded lines are the problem, how do I re-run grub???

---

### Post by GeneralSunTzu on 2009-08-07
Kal'hmera Nike,

haven't gone through your list (which meanwhile changed) yet. 
I apologise - I will.
Using your trackpad config file worked, but obviously you were reproducing your own Mac OS X settings, whereas I do not wish to use the trackpad tap for clicking (I can click explicitly), but only the two- three- and four-fingers sweep.
The configurability of the trackpad with an obscure and not very well documented text file (gsynaptics) is not great...
I think that once your list is more or less complete, it could either be added to the wiki or made a sticky here.

---

### Post by Nikos.Alexandris on 2009-08-07
> **GeneralSunTzu said:**
> Kal'hmera Nike,

haven't gone through your list (which meanwhile changed) yet. 
I apologise - I will.
Using your trackpad config file worked, but obviously you were reproducing your own Mac OS X settings, whereas I do not wish to use the trackpad tap for clicking (I can click explicitly), but only the two- three- and four-fingers sweep.
The configurability of the trackpad with an obscure and not very well documented text file (gsynaptics) is not great...
I think that once your list is more or less complete, it could either be added to the wiki or made a sticky here.

&#922;&#945;&#955;&#951;&#956;&#941;&#961;&#945; GeneralSunTzu :-)

I took the liberty to modify some comment which I have put in the first post of this thread under your name. Let me know if something is "wrong".

---

### Post by Nikos.Alexandris on 2009-08-07
> **Nikos.Alexandris said:**
> ...
So, if the above bolded lines are the problem, how do I re-run grub???

Nevermind, while working with the -14 image, I've done the following

```
sudo apt-get purge linux-image-2.6.28-15-generic
```

followed by

```
sudo apt-get install linux-image-2.6.28-15-generic linux-restricted-modules-2.6.28-15-generic linux-restricted-modules-generic linux-generic
```

and the problem is solved :-)

---

### Post by theskunk on 2009-08-07
Hi, 

Just stubled upon this, and I'm trying to actually get both Ubuntu Jaunty to work as well as Fedora 11. My primary usability complaint is that I'm unable to get click and drag to work. If I do it on the desktop itself, it seems to right click, and since i cannot move the mouse it ends up creating a new folder.

I'm using the file posted for the synaptics.fdi file, but I'm not sure what else needs to be done or tested -- Does this file need to be manually loaded somewhere or just putting it in place plus a reboot cause it to take effect?

I'm open to trying just about anything at this point :) 

Thanks!

---

### Post by theskunk on 2009-08-07
Edit: (to above post)

I've found this bug:
[https://bugs.edge.launchpad.net/mactel-support/+bug/356317](https://bugs.edge.launchpad.net/mactel-support/+bug/356317)

and have applied the associated test .deb package, which seems to correct a lot, except for when you press the button down, it and then place your finger on the trackpad to begin dragging, it seems to fly across the screen depending on where you actually touched. 

Can anybody else confirm this?

---

### Post by GeneralSunTzu on 2009-08-07
> **theskunk said:**
> Edit: (to above post)

I've found this bug:
[https://bugs.edge.launchpad.net/mactel-support/+bug/356317](https://bugs.edge.launchpad.net/mactel-support/+bug/356317)

and have applied the associated test .deb package, which seems to correct a lot, except for when you press the button down, it and then place your finger on the trackpad to begin dragging, it seems to fly across the screen depending on where you actually touched. 

Can anybody else confirm this?

Finally, thanks to you, using this patch makes it so that click and drag works as it should (i.e. you click and drag the blasted object).
Meanwhile I have lost the right-click, using Nikos' configuration. Will have to understand it again experimentally, given that synaptic "documentation" is close to unintelligible...
Perhaps we ought to feed all the valuable info of this thread into the 5,1 MBP Wiki...

---

### Post by inphektion on 2009-08-07
Weird, I'm P. Dunbar in launchpad and I could've sworn when I redid my machine I updaed the wiki with everything I did to get it all working.  I could've sworn bcm5974 was the one in the mactel ppa.  It seems just 1.13 is there.  

Anyone know why 1.14 never got put in the ppa?

---

### Post by Nikos.Alexandris on 2009-08-09
> **GeneralSunTzu said:**
> ...
Meanwhile I have lost the right-click, using Nikos' configuration. Will have to understand it again experimentally, given that synaptic "documentation" is close to unintelligible...
Perhaps we ought to feed all the valuable info of this thread into the 5,1 MBP Wiki...

Weird... !? How can we compare 1:1 our settings to see if all match. I might have done extra stuff in the past which I don't remember now (and at somepoint I lost lots of my tomboy notes).

This thread might be useful after all. It's better to move sooner or later the collected info in the wiki. Editing the first post is kind of a monologue (not very constructive).

---

### Post by swarup on 2009-08-10
How about the matter of connectivity-- eSATA and Firewire800. I don't know whether these may already have been solved, but it would be really nice to be able to hook up an external HDD with high transfer rates. 

1. eSATA: I purchased a (DYNEX brand) 2-port eSATA II ExpressCard Adapter. But upon plugging it into the MBP, there was no recognition of the card itself. And when I hooked up an eSATA external HDD to the adapter, again no recognition. Has anyone had success with eSATA connectivity for the MBP in Jaunty?

2. Firewire800: I purchased a (DYNEX brand) firewire800 cable with firewire400 (6-pin) adaptor, and plugged in my FW400 external HDD to it via the MBP FW800 port. The external HDD's FAT32 partition mounted, and everything in it opens smoothly. But the same external HDD's ext3 partition, while it does mount, only folders on the partition can be opened. No files will open. Has anyone gotten success using the MBP's FW800 port with Jaunty? 

Thanks,
Swarup

---

### Post by inphektion on 2009-08-10
One issue I have left that didn't see mentioned is the keyboard and screen backlight following any rules based on ambient light sensor.  
My keyboard backlight is always on and I'd prefer if it only came on in low light conditions like it does in mac osx.

---

### Post by Nikos.Alexandris on 2009-08-10
> **swarup said:**
> ...
2. Firewire800: I purchased a (DYNEX brand) firewire800 cable with firewire400 (6-pin) adaptor, and plugged in my FW400 external HDD to it via the MBP FW800 port. The external HDD's FAT32 partition mounted, and everything in it opens smoothly. But the same external HDD's ext3 partition, while it does mount, only folders on the partition can be opened. No files will open. Has anyone gotten success using the MBP's FW800 port with Jaunty?

Zero problems using a LaCie d2 Quadra (1TB) hard disk with FW800 (via the MBP's firewire of course). Additional info: 3 ext3 partitions and 1 XFS.

---

### Post by Nikos.Alexandris on 2009-08-10
> **inphektion said:**
> One issue I have left that didn't see mentioned is the keyboard and screen backlight following any rules based on ambient light sensor.  
My keyboard backlight is always on and I'd prefer if it only came on in low light conditions like it does in mac osx.

There is this bug-report: [[COLOR="Blue"]https://bugs.launchpad.net/ubuntu/+source/hal/+bug/285815[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/285815")

Is this working effectively for someone?

---

### Post by swarup on 2009-08-10
> **Nikos.Alexandris said:**
> Zero problems using a LaCie d2 Quadra (1TB) hard disk with FW800 (via the MBP's firewire of course). Additional info: 3 ext3 partitions and 1 XFS.

Great news. My guess is that the problem I faced, then, stems not from the FW800 connection itself but from the way the adaptor I bought transmitted the message from the external FW400 drive to the FW800 port.

I'll most likely purchase a large external HDD which itself has a FW800 connector, similar to the one you use.

Has anyone gotten an external eSATA HDD to work with Ubuntu on the MBP, i.e. via the ExpressCard slot? Such a connection would, of course, be much faster than the FW800. (eSATA has a data transfer rate of 3GB/sec.)

---

### Post by Nikos.Alexandris on 2009-08-22
I have "new" issues:

[LIST]
[*] Using twinview introduced a new problem: **window decoration/ borders are missing and are (re-)activated only when I turn on the effects (compiz)**. Is there a work-around for this? I would like to note that *using compiz* seems to "force" better GPU cooling. The average temperature of the discrete Nvidia 9600 is lower (**~70, 71** degrees) than when working without the effects (=compiz) enabled (**~74, 75** degrees).


[*] Can't share internet through an ad-hoc wireless connection
[/LIST]

---

### Post by ercoppa on 2009-08-27
On Archlinux with 2.6.30 kernel and:
```
reboot=pci
```
at kernel's line in menu.lst, the restart/reboot works without problems :P

So on Jaunty doesn't work, maybe with Koarmic (I hope).

Greets, ercoppa.

---

### Post by Nikos.Alexandris on 2009-09-09
> **ercoppa said:**
> On Archlinux with 2.6.30 kernel and:
```
reboot=pci
```
at kernel's line in menu.lst, the restart/reboot works without problems :P

So on Jaunty doesn't work, maybe with Koarmic (I hope).

Greets, ercoppa.

Unfortunately the .30 kernel won't make it to Karmic! Or could it be that it will?

---

### Post by amd-64 on 2009-09-09
> **Nikos.Alexandris said:**
> I have "new" issues:

[LIST]
[*] Using twinview introduced a new problem: **window decoration/ borders are missing and are (re-)activated only when I turn on the effects (compiz)**. Is there a work-around for this? I would like to note that *using compiz* seems to "force" better GPU cooling. The average temperature of the discrete Nvidia 9600 is lower (**~70, 71** degrees) than when working without the effects (=compiz) enabled (**~74, 75** degrees).
[*] Can't share internet through an ad-hoc wireless connection
[/LIST]



70-75C is too hot for me. 

My 5,3 with Nvidia 9600 does rarely go above 60C, most of the time 50-55C. I am running fancontrol from this thread [http://ubuntuforums.org/showthread.php?t=1102465](http://ubuntuforums.org/showthread.php?t=1102465) 

If you do not want to run a script, you could set your min fan speed to 3000 rpm instead of 2000 rpm.

---

### Post by Nikos.Alexandris on 2009-09-09
> **amd-64 said:**
> 70-75C is too hot for me. 

My 5,3 with Nvidia 9600 does rarely go above 60C, most of the time 50-55C. I am running fancontrol from this thread [http://ubuntuforums.org/showthread.php?t=1102465](http://ubuntuforums.org/showthread.php?t=1102465) 

If you do not want to run a script, you could set your min fan speed to 3000 rpm instead of 2000 rpm.

...rarely above 60C!

OK, you convinced me :-). I'll give'm a try.

---

### Post by Nikos.Alexandris on 2009-09-09
> **Nikos.Alexandris said:**
> ...rarely above 60C!

OK, you convinced me :-). I'll give'm a try.

Maybe I'll have to give it some time. I just executed the script as root (did not install it) but it doesn't really do much (yet?). Also, my fans always jump-up when I do intensive stuff. Let's see...

[s]+ a question: how can one "cleanly" uninstall it?[/s] question moved in the respective thread.

---

### Post by Nikos.Alexandris on 2009-09-18
> **Nikos.Alexandris said:**
> Maybe I'll have to give it some time. I just executed the script as root (did not install it) but it doesn't really do much (yet?). Also, my fans always jump-up when I do intensive stuff. Let's see...

[s]+ a question: how can one "cleanly" uninstall it?[/s] question moved in the respective thread.

Folks, the fancontrol script is worth its name. The temperature is mostly between 62 ~ 66 and sometimes below 60! Yet, I still feel the machine is a bit louder than it should be.

---

### Post by alexmurray on 2009-09-18
> **Nikos.Alexandris said:**
> Folks, the fancontrol script is worth its name. The temperature is mostly between 62 ~ 66 and sometimes below 60! Yet, I still feel the machine is a bit louder than it should be.
You should really try karmic on your MBP5,1- my machine is definitely cooler with it, and is usually under 50C, WITHOUT fancontrol script.

---

### Post by amd-64 on 2009-09-18
> **alexmurray said:**
> You should really try karmic on your MBP5,1- my machine is definitely cooler with it, and is usually under 50C, WITHOUT fancontrol script.

Lots of questions for you. Do you use grub2 EFI bootloader. Are you able to use the 9400 graphics. Any drawbacks. What is the battery life, anywhere near the OS X  

Thanks in advance.

---

### Post by alexmurray on 2009-09-19
I dont generally use efi, but it works for me (see the efi booting thread) and I can use the 9400M under efi. But generally I just use legacy boot with the 9600MGT. I get about 2 hrs 15 mins battery life with legacy boot, and maybe only about 10 minutes longer with efi boot and the 9400M. Linux still doesn't have the power saving ability of OSX (but if you think about it, Linux is more generic since it supports infinitely many more computers than just Mac's which is all OSX has to support, so its no real suprise OSX has better battery life - not to mention that Apple get to design the hardware and OS together to optimise battery life etc, but Linux does not get this chance).

---

### Post by Nikos.Alexandris on 2009-09-19
> **alexmurray said:**
> You should really try karmic on your MBP5,1- my machine is definitely cooler with it, and is usually under 50C, WITHOUT fancontrol script.

Maybe I will :-). How stable is it?

---

### Post by Nikos.Alexandris on 2009-09-19
> **alexmurray said:**
> I dont generally use efi, but it works for me (see the efi booting thread) and I can use the 9400M under efi. But generally I just use legacy boot with the 9600MGT. I get about 2 hrs 15 mins battery life with legacy boot, and maybe only about 10 minutes longer with efi boot and the 9400M. Linux still doesn't have the power saving ability of OSX (but if you think about it, Linux is more generic since it supports infinitely many more computers than just Mac's which is all OSX has to support, so its no real suprise OSX has better battery life - not to mention that Apple get to design the hardware and OS together to optimise battery life etc, but Linux does not get this chance).

Many of the things you describe are true. Yet, it is true that ubuntu-linux still needs to go green, disable/deactivate easily/automatically devices that are not used (e.g. bluetooth, wireless) and more. I am convinced that a reasonable average of battery life is achievable. Then again, I am not a developer.

---

### Post by Nikos.Alexandris on 2009-09-19
> **amd-64 said:**
> Lots of questions for you. Do you use grub2 EFI bootloader. Are you able to use the 9400 graphics. Any drawbacks. What is the battery life, anywhere near the OS X  

Thanks in advance.

I also tried a couple of times efi booting. But the lack of accelerated graphics and, mainly, the lack of brightness regulation (display/ keyboard) is a stopper for me. I am not testing any further till the 30 kernel jumps-in the game.

---

### Post by amd-64 on 2009-09-19
> **Nikos.Alexandris said:**
> I also tried a couple of times efi booting. But the lack of accelerated graphics and, mainly, the lack of brightness regulation (display/ keyboard) is a stopper for me. I am not testing any further till the 30 kernel jumps-in the game.



From the release notes of Karmic alpha 6 which came out Sept 17

"Alpha 6 includes the 2.6.31-9.29 kernel based on 2.6.31-rc8."

I tried to run the live cd, but for some reason did not get past grub. Kernel not found or something.

---

### Post by Nikos.Alexandris on 2009-09-20
> **amd-64 said:**
> From the release notes of Karmic alpha 6 which came out Sept 17

"Alpha 6 includes the 2.6.31-9.29 kernel based on 2.6.31-rc8."

I tried to run the live cd, but for some reason did not get past grub. Kernel not found or something.

I've ran succesfully Karmic Alpha 6. Looks better but can't tell much from the live-CD.

**@alexmurray**, is it really ok to install Karmic now? I don't want to play with my machine since it's my workhorse.

Thanks!

---

### Post by alexmurray on 2009-09-20
@Nikos.Alexandris - so far Karmic has been great for me, although I suggest you read some of the posts in the Karmic Testing forum as others have had some problems along the way due to the developmental nature of Karmic - although if this is your main machine and you NEED it to be STABLE, perhaps wait until Karmic is released just to be sure, but if you can handle a few hours / days of downtime to fix things if they break, then go for it :)

---

