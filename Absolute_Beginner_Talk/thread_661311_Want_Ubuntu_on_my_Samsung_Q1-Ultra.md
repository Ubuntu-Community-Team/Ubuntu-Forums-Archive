---
title: "Want Ubuntu on my Samsung Q1-Ultra"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Offbeatmammal on 2008-01-07
Bored of waiting for a LiveUSB of Moblin so I can try Linux on my UMPC I decided (I'm a total newbie with Linux) to use Wubi to install 7.04 and see how it goes.

Intalls great, no complaints there, starts up fine and everything works okay.

My problems are a bunch of subtle little things that, as a Windows user, I'm used to Device Manager just fixing for me ;) Hopefully there's a one click smart utility so I don't have to go into things that scare me (command prompts, anything that starts sudo or vi!)

- Touchscreen calibration is off... apart from at the exact center the cursor never matches the stylus (makes it a little hard to use)
- Screen on the Q1U is bigger than 800x600 ... but that's the largest I'm offered
- Battery life is terrible! It's pretty bad under Vista and I assumed (hoped) it would be better with Ubuntu ... if anything it's worse!
- WiFi doesn't seem to work reliably. Wired it works fine, but unwired it quite often fails to find my base station, and even when it does it's not very good at connecting me to the outside world!

Once I can get these four little things fixed I'll be in a much better position to play and see what I think of Linux (is it as easy to use for the basic stuff I do every day as Vista, is it better on my UMPC) ... hopefully someone here can help out :)

---

### Post by A_Lyle on 2008-01-08
Hi Offbeatmammal

I'm planning on trying 7.10 (Gutsy Gibbon) on my Q1U. I've previously tried the beta of UME from a live USB, but AFAIK you can't install it alongside Windows the way you can the full version of Ubuntu, and I'm not ready to give up so much functionality just yet.

Do you have the Q1U (split keyboard, screen 1024 x 600) or the old Q1 (no keyboard, 800 x 480)? The reason I ask is that battery life for the Q1U is much better than the Q1 - I get 3.5-4 hours from the standard battery and 7-8 from the extended one (it came bundled with my Q1U, probably because Samsung took a severe pasting over the battery life of the Q1). Hearing you describe the battery life as terrible makes me think you have the older device.

Anyway, if I come across any easy fixes, I'll let you know!

---

### Post by Offbeatmammal on 2008-01-08
Mine is the newer on - strange split keyboard (actually prefer the one on my Wizard phone!) and the higher screen res.

I suspect the battery issues I'm seeing with 7.04 installed via Wubi is the lack of optimizations/specific drivers, which is why I'm hoping there's a "UMPC Pack" or something similar I can click and install ;)

Like you, I need dual boot to Vista - Ubuntu is just an experiment at the moment :)

---

### Post by A_Lyle on 2008-01-15
The problems you're getting maybe down to 7.04, or wubi - I just did a full install of Gutsy alongside XP Tablet and the screen resolution was perfect without any fiddling. Touchscreen is pretty good too, and WiFi works, though at the moment only on manual configuration, not roaming :(

It meant getting my hands dirty with command-line stuff, but if you're feeling brave, the full step-by-step instructions are here:

[http://www.annelyle.com/geek/q1u_ubuntu.php](http://www.annelyle.com/geek/q1u_ubuntu.php)

Have fun!

---

### Post by stream303 on 2008-01-29
Thanks to your excellent instructions for the Q1U, I now have a **fully operational Q1 (non-ultra)** working with on-screen keyboard.  Thanks to you and the other forum members I'm a happy camper with some fiddling specific to my model.

I took the easy way out with the Q1 by using an external usb keyboard and usb cd-player for initial installation.  I used the "alternate" text-based install iso of Gutsy to get it installed initially, and after reboot, just plugged in the mouse.  So far so good.

The catch-22 is that the input device changes after you calibrate things and then pull your devices out depending on the pen only.  So while I had the keyboard and mouse hooked up, the device was seen as /dev/input/event6, but when you pull everything out, the device is really **/dev/input/event2**.  Thus once things were calibrated, I changed the edits in /etc/X11/xorg.conf to reflect event2.  All other names were used as per your example.  The key for everyday usage is to make sure that you boot with nothing attached, and only plug devices into usb ports afterwards should you want to.

For the **on-screen keyboard**, I used the "onboard" keyboard in Gutsy and just told gdm to fire it up.  Thanks to forum members I found that I needed to edit **/etc/gdm/Init/Default** and put the exec line between fi and exit 0:
```
fi
exec onboard &
exit 0
```

To get this keyboard at the password / username login prompt, you have to **enable assistive technologies:**

System > preferences > universal access > assistive technology > (make sure that BOTH "enable assistive technology" AND "password dialogs as normal windows" are checked) > accessibility > mobility > change to Onboard.  Be sure to check "run at start"

Also crucial was to **change the fancy gnome login window to a "plain" window** in system > administration > login window> local > style change to plain.

If anyone has trouble calibrating, here is what mine looks like for a standard Q1 (non-ultra) in xorg.conf:

```

Section     "InputDevice"
                Driver "evtouch"
                Identifier              "eGalax Touchscreen"
                Option                 "Device"     "/dev/input/event2"
                Option                 "DeviceName"     "touchscreen"
                Option                 "MinX"     "79"
                Option                 "MinY"     "3907"
                Option                 "MaxX"     "3986"
                Option                 "MaxY"     "147"
                Option                 "SwapY"   "1"
                Option                 "ReportingMode"   "Raw"
                Option                 "SendCoreEvents"
EndSection

```

About the only thing left for me to fix is that it doesn't seem to perform a full shutdown, and I have to manually turn the system off at a dark screen.  Until then, I gotta' pay attention. :)

I'm so happy that I got this thing working well with ubuntu thanks to your excellent guide and other forum member tips.  I even wiped the original OS off, and somehow feel better. :)  Thanks again!

---

### Post by nielinjie on 2008-02-25
Do your 4d navigation buttons work?

---

### Post by kpgalligan on 2008-02-29
I did this last night.  It works pretty well.  I got the touchscreen to work, and for the most part, everything is good.  Its much better than Vista, and I work on linux all day, so at this point I'm more at home there anyway.

However.  A couple issues. The arrow keys.  I would LOVE to have these.  They don't work.  I think this is a known issue.  If the Q1 is being used as a test platform for the new mobile ubuntu distro, I have to imagine this works somewhere.  Any thoughts on where to look?

Also, when not plugged in, it does something weird.  It dims, which is normal.  Happened in Vista also.  However, if you don't touch it for like 30 seconds, then touch it again, it briefly flashes at full brightness, then goes back to dim.  Anybody else see this?  Its weird.

Also wondering some generals.  Any way to do Home, End, Page Up/Down?  Stuff like that?  Not really an ubuntu question.

Thanks in advance

---

### Post by kpgalligan on 2008-02-29
Some progress.  The bright flash issue is easy to deal with.  If you go into Administration > Power Settings (something like that.  Not looking at it right now), there's a checkbox for going dim or some such.  Just uncheck that.  The screen is already dim, so this is somewhat redundant.

I bumped up the brightness in general, and was running some constant CPU stuff, and it predictably sucked the juice right out, but it was reasonable.

Going to try to the mobile build this weekend (hopefully).  I bet the buttons work.  Now just need to figure out how to get that stuff in the standard ubuntu build.  The mobile thing looks like its for severely restricted hardware.  The Q1 is pretty beefy, relatively.  Full ubuntu runs fine for me.  As an example, I opened eclipse, which is a beast of a java IDE.  Seemed fine.

---

### Post by nielinjie on 2008-03-03
Dear kpgalligan--
Have you any update on the buttons? I really like to use these buttons to scroll web pages in firefox.

---

### Post by kpgalligan on 2008-03-03
It turns out the arrow button functionality can be done by putting the mouse pointer into "joystick" mode.  On top of the little mouse knob, it says 'Mouse'.  Press that.  You should see a little indicator led at the top change.  Now pressing up, down, left, right acts like the arrow keys.  I'm not sure even if the "arrows" on the right do what we think they do in windows.  It would seem odd if they had two ways of doing that.

I do wish they were assignable.  That would be cool.

I'm able to get by quite well now with the joystick mode and 'onboard'.  Its the on-screen keyboard.  It opens pretty large, but you can make it smaller, and also create a new layout and change all...

font='5'

to...

font='10'

Go to "Accessories > Terminal".  Then type...

onboard &

Pretty sweet.

---

### Post by ulugeyik on 2008-04-30
nice hardy heron live CD boots up fine. Touch screen does not work though. I can click on some buttons but not all, seems like a calibration problem , but I have no idea what one could use to re-calibrate/test it. 

Before I go about downloading modules and following the detailed instructions, I am wondering if anyone used hardy heron release version on it yet?

---

### Post by Offbeatmammal on 2008-04-30
given the apparent lack of progress on the Mobile Ubuntu version that was going to target the Q1U and similar I'm not sure it's worth the effort... if it worked I suspect it would be a supported platform

I'd love someone to prove me wrong though, and point me to a Wubi-installer of a mobile build optimized for Samsugn Q1U ....

---

### Post by ulugeyik on 2008-07-14
Ubuntu-mobile works reasonably ok on Samsung Q1 Ultra. It has got a bunch of bugs here and there and I think it needs more polishing and more documentation. There does not seem to be large/active enough of a community yet though, my questions generally get quite broad replies so far.

Turgut

---

### Post by kpgalligan on 2008-07-14
Here's a question.  I downloaded the image for install, and put it on a USB key.  When it boots up, it says it'll erase the entire disk.  I'd like to install the mobile version on another partition and keep my current ubuntu install.  Does the install give the option to do that?

---

### Post by ulugeyik on 2008-07-14
I could not find one. In fact, I accidentally installed it and wiped off the Win XP -- I do not regret it.

---

### Post by kpgalligan on 2008-07-14
> **ulugeyik said:**
> I could not find one. In fact, I accidentally installed it and wiped off the Win XP -- I do not regret it.

Hmm.  I'd like to figure that out.  I have a lot of stuff on the ubuntu drive I'd rather not lose.  I'm surprised there's no option to do that.

---

### Post by kpgalligan on 2008-07-16
Well.  I upgraded to 8.04, which blew out my touchscreen.  I had been using 7.10 for a while and was pretty happy with it.  So, I figured I'd try the mobile edition.  It dumped windows and ubuntu.  However, the mobile edition is a little clunky, and certain things were conspicuously absent (like "Connect to server" in the file system.  I'm sure you can do it the hard way, but why dig?).  So I installed 8.04 again.  Some touch screen worked in a weird way, but not really.  Can't find the process again.  Any thoughts?

---

### Post by cj2003 on 2008-07-17
Another article about it here: [Running Ubuntu on the Samsung Q1U UMPC]("http://ubuntu-news.net/modules/news/article.php?storyid=3919")

---

### Post by ulugeyik on 2008-07-17
Yes, out of the box, hardy heron does not get the touch screen right. that is why I went with the mobile edition -- also because I have the SD drive version which is small ~30Gb. 

Mobile edition is lacking in a bunch of aspects that surprised me -- there is no "shutdown" option in the GUI, openoffice does not appear as an editor in GUI, you can't access regular menus except those touch buttons, GUI file browser is quite incapable like you state, there is no GUI to move things around, arrange the icons, add new ones.  None of these would have bothered me if it were a regular computer since I am more used to using the command line anyway and do not use GUIs much. But on this gadget with an unusable keyboard, I have to use GUIs.

On the other hand, wireless , touch screen etc work fine out of the box. I am going to stick with UME and fix some things myself and wait for others to come up in releases. I am reporting bugs in bugzilla etc. I would like to help the community development of this release as much as I can.

Right now, my biggest problem is that it does not "suspend/resume" even "hibernate/resume" works intermittently.

---

### Post by kpgalligan on 2008-07-17
> **ulugeyik said:**
> Right now, my biggest problem is that it does not "suspend/resume" even "hibernate/resume" works intermittently.

Forgot about that.  That was frustrating.

I think its a great effort overall.  I should be putting my effort into helping the community as well.  I guess I really just wanted a few things working right away that are deal killers, and they weren't.  I'll have to see what I can do with that.

---

### Post by ulugeyik on 2008-07-17
All solutions I see on internet talk about "uswsusp" which does not exist in the repositories for the mobile edition.

Turgut

---

### Post by Jayhawk on 2008-07-17
I've alternately installed both UME and Hardy on my Q1U and find both lacking for this linux noob in various ways. The lacks are mentioned in passing here in this thread and in various other forums as well. I like the full hardware functionality found in UME, but have made better progress at BT DUN over my 700p in Hardy.

Is it theoretically possible to copy various files from UME to a Hardy installation so as to enable the touchscreen and 4-way navigator on the righthand side of the keyboard? If so, has someone done it? If not, I suppose it would be much of the /lib/ directory, /etc/x11/xorg-samsungq1ultra.conf, and several other files from the UME installation I'm still ignorant of. The touchscreen parameters seem to be described in the xorg*.conf file I mentioned and while I don't see specific mention of the 4-way navigator, it certainly works in UME.

My Q1U is simply a web browser for me right now so I'd be happy to be an experimenter for anyone with more knowledge as to what files and/or directories to cut and paste from a UME installation to Hardy.

---

### Post by kpgalligan on 2008-07-17
Didn't know the 4-way worked like that in UME.  You can use the arrows by clicking "Mouse" on the left, then the joystick acts like the arrow keys instead of a mouse pointer.  The 4-way on the right only does a couple things.  When you hold "Dial Key", up and down do  brightness, and left/right does volume.

I'd be happy with touchscreen.  I got that to work on 7.10, but 8.04 blew that out, and I don't know how to get it working again.  The screen does get a touch event, but its always the same position, somewhere int he middle of the screen (regardless of where you touch).  It seems like a simple config thing, but I don't know where to set it.

---

### Post by ulugeyik on 2008-07-18
Jayhawk, I believe your question is bit too specific for us to expect an answer on this forum -- it does not look like UME developers are reading here -- but the IRC channel and the mailing list might be able to do that. I have seen same request on various blogs and other posts with no clear path to take care of.

On UME, the fourway arrows act like cursors for me when using various applications. I wish I can use the "menu", "udf", "vol-","vol+" and other buttons too.

---

