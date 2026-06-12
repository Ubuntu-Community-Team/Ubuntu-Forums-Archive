---
title: "17&quot; Powerbook G4 and R300 graphics drivers."
date: 2016-08-31
forum: Apple Hardware Users
---

### Post by claniraq on 2016-08-31
[FONT=verdana]I've been trying to get lubuntu 16.04 installed on my old Powerbook with little success. I originally started with 12.04 as when I used the 16.04 live cd the computer would boot to a black screen after showing the lubuntu splash for a short time. 
Under 12.04 everything worked flawlessly with a little tinkering, and I was even able to get the multimedia and brightness keys working as well as the keyboard backlight.

 I then decided to upgrade to 14.10 or 14.04 (I can't remember exactly) as I needed a newer version of the kernel for some of the applications I was intending to use. Upon upgrading to 14.xx the video looked like it was being forced down to a lower bit depth with everything taking on a very weird psychedelic look and none of the GUI elements functioning correctly. I did some research and found out there was some kind of bug in the graphics drivers, and as I was unable to figure out how to fix it, I decided to simply upgrade to version 16.04 of lubuntu via tty and command line as none of the GUI was functioning.

Upon completing the update to 16.04, the graphics driver problem has only gotten worse. Now regardless of any yaboot paramters I use, sometimes the system will boot and then the graphics driver(?) will crash causing a black screen. I know the system is still running however, as if I enter tty, login, and su reboot the computer does in fact restart. Sometimes the system will boot to desktop without crashing, and if I am fast enough I can enter tty and have access to the computer, however 8/10 times the driver will crash as the lubuntu splash screen and loading bar come up.

I did some research, as well as looked into what was happening as linux boots and I get a few different messages. 

During boot, I get a message along the lines of:

RADEON (some kind of memory address?) invalid rom content
RADEON unable to get BIOS (?)

I'm not exactly sure as to what it says as it appears very quickly and I'm not familiar enough with Linux to debug any better. 
Whenever I am able to get to the desktop, if I attempt to run : exec firefox : I get errors that look like this:

[/FONT][FONT=verdana]  libGL error: failed to load driver: r300
  libGL error: Try again with LIBGL_DEBUG=verbose for more details.
  libGL error: failed to load driver: swrast
  libGL error: Try again with LIBGL_DEBUG=verbose for more details.

Now unfortunately I again don't know enough about linux to effectively debug this but I did some google searching and I came up with this thread:

[https://bugs.freedesktop.org/show_bug.cgi?id=71789](https://bugs.freedesktop.org/show_bug.cgi?id=71789)

I most definitely don't know what to do with any of this information as I am still a relative Linux noob, and I wasn't able to find any information on anyone having a similar problem other than that link which unfortunately contains to much arcane Linux magic
for me to effectively parse. 

If anybody has any ideas or any suggestions as to how to get more information and nail down the problem I am all ears! 
[/FONT]

---

### Post by rican-linux on 2016-09-01
This is a known bug that is resolved in mesa 12.0. This version of mesa is 16.10.

---

### Post by claniraq on 2016-09-01
Is there any way I could go about updating?

So I tried a live usb of the PPC 16.10 daily build but the problem persists. I see the lubuntu splash screen, it loads for a short while, and then the display driver crashes (?) and the screen goes black

---

### Post by rican-linux on 2016-09-02
at the second yaboot prompt on the live usb enter this

```
live radeon.agpmode=-1
```

You get into the live enviorment. Then when you install create  a seperate /boot partition as ext2 (or else yaboot will not load the kernel). Then when you are done reboot and enter this in the second yaboot prompt.

```
Linux radeon.agpmode=-1
```

Then you should be able to login.

Finally edit you /etc/yaboot.conf file like so

```
image=/vmlinux
	label=Linux
	read-only
	initrd=/initrd.img
	append="quiet splash radeon.agpmode=-1"

image=/vmlinux.old
	label=old
	read-only
	initrd=/initrd.img.old
	append="quiet splash radeon.agpmode=-1"

```

Save you changes and load them by running this command *sudo ybin -v*. Then you should be good to go!

---

### Post by claniraq on 2016-09-02
First of all I'd like to thank you for your help!
However I tried to boot the live USB using the yaboot parameters you gave (as well as all of the ones listed in the PPC FAQ and then some more video related ones that I found) and unfortunately the blue lubuntu splash screen is still as far as it gets.
After sitting at that screen for a while, the video goes black (at the same time the keyboard lights up, I don't know if it's trying to load some kind of driver?)

I tried sacrificing my existing lubuntu install and reformatted the entire drive with my OSX 10.4 DVD in case that would help, as well as downloading the most recent daily build and trying to create another live USB but still no dice.

In my previous (very limited) experience with Linux, there has always been more information displayed on boot. Is there a way to get the live USB to boot in CLI or text mode so I can try and diagnose exactly where and what is causing it to fail?

---

### Post by luigiburdo on 2016-09-02
Hi Herminio,
you are on 16.10? umm there i have issue with drm or Xorg on X5000 ...  video is not working any more on xorg.
screen is blinking and i see just the pointer . Same bug is present on Sam 460 but look like the X1000 isnt effected. 
I dont know if on G4/G5 this issue is present too. 
My Quad is with 15.10 and i will not move from here now ... i have a really great deskop experience with 15.10 and 4650 hd
tomorrow a video will come ;-)

---

### Post by rican-linux on 2016-09-02
My PowerBook G4 is on Lubuntu 16.10 so far the experience has been ok. With 16.10 there was the move to webkit2gtk which has issues on PowerPC. Hopefully these will be fixed soon.

Herminio

---

### Post by claniraq on 2016-09-07
So am I just SOL trying to get lubuntu working on this Powerbook?

---

### Post by rican-linux on 2016-09-09
I do not see why it will not work. I have ran Lubuntu 16.04 and 16.10 on my PowerBook with no problems.

---

### Post by ernsteiswuerfel on 2016-09-10
@[claniraq]("https://ubuntuforums.org/member.php?u=2042738"):
You could try again when Kernel 4.8 hits the 16.10 daily iso. I did a mainline build of 4.8-rc4 and noticed that it boots now into my r300-machines (PowerMac G5 7,3 + PowerBook G4 5,6) without freezing the desktop and without needing additional boot-parameters.

---

### Post by claniraq on 2016-09-12
I tried the latest daily build of lubuntu today but now I get even less of a result even after trying all of the video modes I could think of. The live USB gets to the splash-screen and loads for a while, then throws me the black screen as usual but now I don't even have the keyboard backlight. I'm assuming that the build I used still doesn't contain the 4.8 kernel as I have a Powerbook G4 5,6 as well (if memory serves) I'm guessing that doing my own mainline build is a little above my pay grade, but is there anywhere I should be looking to see when the 4.8 Kernel hits the daily iso?

Could the problem be that I am trying to boot off of a USB? I don't see why it would be and I am hesitant to waste DVDs but I am a relative linux newbie so I don't entirely understand how the system loads, especially on these old macs that were never designed to USB boot in the first place.

---

### Post by ernsteiswuerfel on 2016-09-12
> **claniraq said:**
> I'm guessing that doing my own mainline build is a little above my pay grade, but is there anywhere I should be looking to see when the 4.8 Kernel hits the daily iso?
Sure. Just check the manifest what's on the daily iso found on [http://cdimage.ubuntu.com/lubuntu/daily-live/current/yakkety-desktop-powerpc.manifest](http://cdimage.ubuntu.com/lubuntu/daily-live/current/yakkety-desktop-powerpc.manifest) and have a look for "linux-image". ;)

Kernel 4.8 is not released yet, its 'release candidate 6' ATM. We will have to wait until 4.8.0 is released + several days for the Ubuntu Team to build an incorporate a 4.8 mainline kernel in the ppc isos.

Don't know much about USB-booting on the PPC-Macs. I use DVD-rewriteables, they work fine on all of my PPC-Macs and it takes really A LOT of writes until they cease to work.

---

### Post by claniraq on 2016-09-12
Thank you! I'll keep an eye on the manifests. 
I don't mind waiting, this powerbook isn't exactly my main computer, but I hate just having it collect dust.
I might try using a DVD, the main reason I've been trying USB booting is because the DVD drive in my tower was busted, but I found an older one I might be able to use the other day.

---

