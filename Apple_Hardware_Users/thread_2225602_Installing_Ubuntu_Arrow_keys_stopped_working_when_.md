---
title: "Installing Ubuntu: Arrow keys stopped working when I got to the partition page."
date: 2014-05-22
forum: Apple Hardware Users
---

### Post by John_Fuller on 2014-05-22
Hello helpful Ubuntu people who know what they're doing [I don't!]

I want to dual-partition my G4 PPC Man powerbook with ubuntu - so tha I can continue to use Photoshop etc, but have access to the internet via ubuntu.

I chose *ubuntu-12.04-alternate-powerpc* and was doing well with the install process till I got to the partition page [the title had exclamation marks by it...]. The only option available was a guided full install [without partition]. The arrow keys weren't working.

[There wasn't a next button, but 'return' worked.]

My machine:

[COLOR=#000000]1.67 GHz ppc g4 17"[/COLOR]
[COLOR=#000000]1 GB RAM[/COLOR]
[COLOR=#000000]POWERBOOK 5,9[/COLOR]
[COLOR=#000000]And this is what I could find under 'graphics':[/COLOR]
[COLOR=#000000][FONT=Lucida Grande]**ATI Mobility Radeon 9700:**[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Chipset Model:	ATY,RV360M11[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Type:	Display[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Bus:	AGP[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]VRAM (Total):	128 MB[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Vendor:	ATI (0x1002)[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Device ID:	0x4e50[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Revision ID:	0x0000[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]ROM Revision:	113-xxxxx-169[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Displays:[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]**Color LCD:**[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Display Type:	LCD[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Resolution:	1440 x 900 @ 60 Hz[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Depth:	32-bit Color[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Built-In:	Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Core Image:	Supported[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Main Display:	Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Mirror:	Off[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Online:	Yes[/FONT][/COLOR]
[FONT=Lucida Grande][SIZE=2][COLOR=#000000]Quartz Extreme:	Supported[/COLOR][/SIZE][/FONT]

[FONT=Lucida Grande][SIZE=2][COLOR=#000000]I force quitted from the process till I can work this out.[/COLOR][/SIZE][/FONT]

[FONT=Lucida Grande][SIZE=2][COLOR=#000000]Maybe I need a different boot/install command ... or different iso.... who knows?[/COLOR][/SIZE][/FONT]

[FONT=Lucida Grande][SIZE=2][COLOR=#000000]Any help will be [/COLOR][/SIZE][/FONT][FONT=Lucida Grande][COLOR=#000000]greatfull[SIZE=2]y appreciated.

John[/SIZE][/COLOR][/FONT]

---

### Post by este.el.paz on 2014-05-22
> **John_Fuller said:**
> Hello helpful Ubuntu people who know what they're doing [I don't!]

I chose *ubuntu-12.04-alternate-powerpc* and was doing well with the install process till I got to the partition page [the title had exclamation marks by it...]. The only option available was a guided full install [without partition]. The arrow keys weren't working.

[FONT=Lucida Grande][SIZE=2][COLOR=#000000]Maybe I need a different boot/install command ... or different iso.... who knows?[/COLOR][/SIZE][/FONT]
[FONT=Lucida Grande][COLOR=#000000][SIZE=2]John[/SIZE][/COLOR][/FONT]

@John:

It looks like you changed your .iso??  Before you were saying you had the 12.04-desktop-ppc iso and now you are using the alternate?  My advice would be the same, check the md5sum of the iso you are using for this one.  The alternate of course doesn't provide a sample desktop for you to test drive, it just does the install.  As to why it would get you to the partition page and then the arrow keys would stop???  If you went through the process up to that point, choosing your language, choosing your proper keyboard, etc, and everything was working fine . . . it's odd . . . .  It would make more sense if they didn't work at any point . . . .

Anyway, I would check the md5sum number of both of your iso's . . . it ***might**** show you that there is file corruption, which ***might*** explain why you are having these issues . . . .  And, then I would say to first try out the desktop CD/DVD and get it to the live desktop . . . as your first exercise in playing the game of linux . . . .  You would have to figure out if you need some boot parameters like "live video=ofonly" ????  Then, once you've gotten that far, then try the install process . . . which could be done through the liveDVD iso or the alternate . . . .

e.e.p.

---

### Post by John_Fuller on 2014-05-22
Hi este... yes, you're right.When I went to try to find this mysterious md5sum on the page where I clicked the download link for the first iso I used, I realised that that iso was for a desktop. I wondered if that meant I was using the wrong iso, as I'm trying to do this on a powerpc laptop. I posted on the old thread to tell you that but, for some reason, that post didn't get published.


Anyway, it went a lot better - till it got to the partition bit.

I've just checked the md5sum number - according to your instructions on the other thread
[http://ubuntuforums.org/showthread.php?t=2220867&page=5](http://ubuntuforums.org/showthread.php?t=2220867&page=5) and they both match the iso's exactly.

The next thing I'll do is to try to install it again.

J

---

### Post by John_Fuller on 2014-05-22
Here's a satisfying discovery ..... I've found that the keys on the laptop are **faulty**!!  

So, I'm ploughing on again, and hopefully I won't be wasting your time any longer [... although the partition option is still acting up a bit it seems - I'm getting help here with a friend].

:)

---

### Post by este.el.paz on 2014-05-22
> **John_Fuller said:**
> Hi este... I realised that that iso was for a desktop. I wondered if that meant I was using the wrong iso, as I'm trying to do this on a powerpc laptop. I posted on the old thread to tell you that but, for some reason, that post didn't get published.

I've just checked the md5sum number - and they both match the iso's exactly.

The next thing I'll do is to try to install it again.
J

John:

Saw the post about faulty keys . . . and that the md5sum numbers are good . . . I'm just posting to say that the "desktop" iso is not exclusive to desktop computers, it's the iso that provides a GUI "desktop" on computers in general . . . the "live" aspect that lets you test the system **before*** you install it . . . the "alternate" iso is just the installer--you can't test it until after the install.  But, if the md5sum numbers check out there is a better chance that whatever you do will go well . . . or better . . . but if keys or the computer are having issues that may interfere with clean operation or install . . . .  Either way, enjoy the process.

e.e.p.

---

### Post by John_Fuller on 2014-05-24
I carried on with the "alternate" iso, as I was already a long way down that route. The keys are working better now [the powerpc hasn't been used for a long time].

I got 12.04 all loaded up without any further hitches.

When I booted in Ubuntu the whole thing ground to a halt after yellow error messages about wireless appeared - then the laptop turned itself off. This happens every time I boot.

[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]&#8226; Firmware file &#8220;b43/[ucode5.fw]("http://ucode5.fw/")&#8221; not found
&#8226; Firmware file &#8220;b43-open/[ucode5.fw]("http://ucode5.fw/")&#8221; not found
&#8226; and told me to go to this site:
    [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware)
    and download the correct firmware.


[/INDENT]
[/INDENT][/INDENT]
[/INDENT][/INDENT]
[/INDENT]

---

### Post by rsavage on 2014-05-24
Make sure you are connected to mains power.  Batteries of laptops that have not been used much can be dodgy.  

See powerpc known issues page about the b43 firmware bug that some machines with 12.04 suffer from.

---

### Post by este.el.paz on 2014-05-24
> **John_Fuller said:**
> I carried on with the "alternate" iso, as I was already a long way down that route. The keys are working better now [the powerpc hasn't been used for a long time].

I got 12.04 all loaded up without any further hitches.

When I booted in Ubuntu the whole thing ground to a halt after yellow error messages about wireless appeared - then the laptop turned itself off. This happens every time I boot.
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]• Firmware file “b43/[ucode5.fw]("http://ucode5.fw/")” not found
• Firmware file “b43-open/[ucode5.fw]("http://ucode5.fw/")” not found
• and told me to go to this site:
    [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware)
    and download the correct firmware.


[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


@John:

Those error messages are common for laptops, because the b43 or b43-legacy drivers are not included . . . that shouldn't stop the OS from loading, I've seen that message after many installs . . . and it hasn't shut my laptop  or computer down.  One of the "bugs" of 12.04 is it seems to generate a "crash report" every time I log in, don't have the skilz or time to get it to stop; possibly your computer is responding as though it is a "real" crash?  : - ))

Is the laptop connected to an ethernet/hardwired connection during the install?  I'm not in linux right now, but I think there is an "add'l drivers" app that will find and install the video and wifi drivers, of course you have to be able to log in to use it . . . but you should be plugged in until you get that installed.

Couple suggestions . . . like I mentioned before, try to boot the LiveDVD and see if you can get to a desktop . . . it's possible that there is some mechanical problem w/ your computer . . . and, thirdly, check out rsavages "WUBI style install" thread if you don't have ethernet and can't get wifi to work . . . another poster had that problem and he posted that assistance for him.  Or his recent, "How to install w/o burning a CD" from within OSX . . . .

Did you shut the computer down after the install or did you just try to boot the system right after the install?  Some suggestions in the past have been to shut down after the install . . . .  It seems like if you get the "yellow" error codes you are at least getting to the splash window . . . .  You could try to get the "SuperGRUB2" file and burn it to a CD--it's a Boot handler or something, it lets you select the OSs on your computer and will boot them . . . it's small and free . . . might help you . . . .

e.e.p.

---

### Post by John_Fuller on 2014-05-24
Thanks you two...
&#8226; Yes, I did have the laptop plugged in. I searched for the b43 bug on the issues page but haven't located it yet...

&#8226; "..[COLOR=#000000] that shouldn't stop the OS from loading" - That's what my knowledgable friend [who doesn't know Macs] said at the time.
[/COLOR]&#8226; Yes, kit's connected to the ethernet when I installed, and when I boot it.
&#8226; Re [COLOR=#000000]"add'l drivers" - I'll ask my friend [to be known as Brian from now on!] how I can do this.... as well as the live DVD process.
[/COLOR]&#8226; "[COLOR=#000000]check out rsavages "WUBI style install" - this won't apply I think, as I have ethernet [and wifi].[/COLOR] 
&#8226; "[COLOR=#000000]Did you shut the computer down after the install" - yes.
&#8226; I'll look into the [/COLOR][COLOR=#000000]super grub thing and find out how to go about installing it.

Stay tuned!  :)
Thanks.
J[/COLOR]

---

### Post by este.el.paz on 2014-05-24
> **John_Fuller said:**
> Thanks you two...
• Yes, I did have the laptop plugged in. I searched for the b43 bug on the issues page but haven't located it yet...
• "..[COLOR=#000000] that shouldn't stop the OS from loading" - That's what my knowledgable friend [who doesn't know Macs] said at the time.
[/COLOR]• Re [COLOR=#000000]"add'l drivers" - I'll ask my friend [to be known as Brian from now on!] how I can do this.... as well as the live DVD process.
[/COLOR][COLOR=#000000]• I'll look into the [/COLOR][COLOR=#000000]super grub thing and find out how to go about installing it.

J[/COLOR]

John:

OK . . . the "b43 bug" might be mentioned by name in the PPCFAQ, or it might just refer to the fact that the installer isn't "recognizing" the driver and "loading" it, as it might for PC based systems???  If you have ethernet, you don't "need" it to boot the system, or shouldn't.  The "LiveDVD" would just be a test to see if you can get to the desktop using it, and might point out some error in the install process?  If you can get it to boot in "live" then you might try the install again from that CD/DVD and see how it goes.  The install process isn't very long compared to some, so it might be easier to run the install again. . . then, if you can get into the OS, you can worry about the b43 issue later.

And, I guess you **could** install "SuperGRUB2" . . . but, it's a "rescue" boot loader, so I have mine burned to a CD for "rescue" operations . . . or dealing with problems with Yaboot or GRUB . . . like if there is no partition set for Yaboot or it fails to get installed . . . however if you are getting to the "Ubuntu 12.04" splash with the 4 dots underneath . . . and, ***then*** are seeing these b43 errors it might not be a boot issue, and so SG2 will not do anything, however, linux, like life, is a great mystery and sometimes what wasn't working seconds or minutes ago, will suddenly change and . . . will work . . . .  Perhaps if you "love-bomb" your machine and system it will "feel the love" and will work!!!???  :KS  Or, if you get SG2 to boot the system maybe it will "figure it out" and start working . . . that has happened for some of my installs, after a couple cold boots it comes together . . . .

e.e.p.

---

### Post by rsavage on 2014-05-24
> **John_Fuller said:**
> I searched for the b43 bug on the issues page but haven't located it yet...

It's below the big bold writing that says

[h=3]b43 (Airport Extreme) hangs at missing firmware[/h] 
Nobody has mentioned the computer shutting down before though.  Which is why I suggest it could be a hardware problem with the battery or the pmu/pram on your computer (so try resetting them).

---

