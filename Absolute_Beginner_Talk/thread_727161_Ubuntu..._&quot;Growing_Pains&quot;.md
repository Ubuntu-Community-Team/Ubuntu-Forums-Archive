---
title: "Ubuntu... &quot;Growing Pains&quot;?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Scapie on 2008-03-17
I am a total newbie to Linux, however I have been toying with the idea of going open source for a few months now (I now use OOo, Firefox, Thunderbird, Scribus, GIMP, Inkscape, etc. on my Windows XP installation.)

When my friend asked me to burn an Ubuntu CD for him, I decided to make two copies and try it for myself. I really enjoyed the Ubuntu experience, and so I bought an external hard drive and used the "casper-rw" tutorial to, in effect, install Ubuntu. I had it configured nicely, but I ran into some problems.

[LIST=1]
[*]The sound from my Toshiba Satellite is very, very quiet. I have checked all volume controls (including "alsamixer" which has **NO** Master volume control, and PCM turned up to 100%). This really annoyed me, so I compiled the latest drivers (Intel HDA HD7 or something of the sort) and installed them (following a tutorial). This did not change anything.
[*]I then tried to install Java for Runescape. I love Runescape, have been playing it for a year now, and am a Member, so I wish to be able to use my account to its best on whatever computer. When I tried to install Sun's Java 6, Ubuntu crashed with the screensaver loaded. This really annoyed me, so I rebooted and reinstalled the packages - I now get something like "Sub-process installation script returned error". I tried again with IcedTea and Java 5 - to no avail.
[*]And now, I was just browsing the internet on Ubuntu, and it crashed again with a locked screen (mouse pointer arrow still moved, but no buttons anywhere did anything on the otherwise black screen). And again, with Gnome showing and Firefox running, it crashed with the Hand pointer moving but no buttons doing anything.
[/LIST]

Could some more experienced people tell me exactly what I need to do. I, however, will not be able to be persuaded to dual-boot, as I am hoping to soon upgrade XP to Vista - from what I gather, this is the depths of Hell for Linux users. I really enjoyed my short time with Ubuntu, but if I have no success, I am likely to move onto Fedora, which (thankfully) has IcedTea preinstalled.

Thank you in advance,
Scapie.

---

### Post by ajgreeny on 2008-03-17
> 1. The sound from my Toshiba Satellite is very, very quiet. I have checked all volume controls (including "alsamixer" which has NO Master volume control, and PCM turned up to 100%). This really annoyed me, so I compiled the latest drivers (Intel HDA HD7 or something of the sort) and installed them (following a tutorial). This did not change anything.Have you double clicked the volume control icon in the panel and added the **Master Volume**?  I'm surprised it isn't there by default as it usually is, but it's worth a try.

  >  3. And now, I was just browsing the internet on Ubuntu, and it crashed again with a locked screen (mouse pointer arrow still moved, but no buttons anywhere did anything on the otherwise black screen). And again, with Gnome showing and Firefox running, it crashed with the Hand pointer moving but no buttons doing anything.This may nothelp but try disabling ipv6 in FF by typing about:config in the address bar and in the filter look for ipv6.  If the resulting line of configuration ends in false, double click it to change to true and see if it helps.  If that isn't your problem, I'm afraid I can't help with any other suggestions.

---

### Post by The Cog on 2008-03-17
Alsamixer certainly should have a master control, on the left hand end. Try scrolling left/right with the arrow keys - there may be more controls than fit on one screen.

---

### Post by sayakb on 2008-03-17
Point 1. Agree with ajgreeny
Open the ALSA Mixer and goto Edit->Preferences. Make sure you have Master checked.

---

### Post by vexorian on 2008-03-17
It crashed during the installation of Java 6 or during the installation of the game?

After installing Sun's Java, always make sure to uninstall any other Java that could be remain.


In a terminal type java -version to verify Sun's java is in use by default.
```
vx@ubuntuvx:~$ java -version
java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Client VM (build 1.5.0_11-b03, mixed mode, sharing)

```

---

### Post by Scapie on 2008-03-18
I apologise if my problems seemed unclear. I hope to rectify this below.

[LIST=1]
[*]"Alsamixer" does show an entry for Master, but there is no control for it whatsoever. I can mute it, but not change the volume. I read somewhere that Ubuntu has a limit volume limit in the Alsa packages in the repository, but I have no idea how to disable this. I am certain that every possible volume control in the GUI mixer is enabled and turned to max, but I would like clarification on this situation.
[*]The Java problems were during the install of Java (Runescape being a web-based game, sorry if there was any confusion), and I did use Synaptic to remove any previously installed Java packages. An interesting thing is, even when using the complete removal (or whatever it's called - writing this in Windows, unfortunately), installing the same packages caused the error "Sub-process install script returned error" or something of the sort. The error is always with *-bin packages from the Java VM.
[*]I will try disabling the IPv6 setting in Firefox's config. I will post my results here when I get round to it. Unfortunately, my GCSE coursework is calling, and I must answer it. :(
[/LIST]

---

### Post by billgoldberg on 2008-03-18
> **Scapie said:**
> I apologise if my problems seemed unclear. I hope to rectify this below.

[LIST=1]
[*]"Alsamixer" does show an entry for Master, but there is no control for it whatsoever. I can mute it, but not change the volume. I read somewhere that Ubuntu has a limit volume limit in the Alsa packages in the repository, but I have no idea how to disable this. I am certain that every possible volume control in the GUI mixer is enabled and turned to max, but I would like clarification on this situation.
[*]The Java problems were during the install of Java (Runescape being a web-based game, sorry if there was any confusion), and I did use Synaptic to remove any previously installed Java packages. An interesting thing is, even when using the complete removal (or whatever it's called - writing this in Windows, unfortunately), installing the same packages caused the error "Sub-process install script returned error" or something of the sort. The error is always with *-bin packages from the Java VM.
[*]I will try disabling the IPv6 setting in Firefox's config. I will post my results here when I get round to it. Unfortunately, my GCSE coursework is calling, and I must answer it. :(
[/LIST]

1. install "gnome alsamixer", it will be under "applications -> sound and video"
2. don't know
3. flash tends to crash on ubuntu and takes firefox with it. Set you terminal to a shortcut (like f12) in system -> preferences- > keyboard shortcuts and in a terminal type

pkill firefox

Firefox will be gone.

---

### Post by Jerry N on 2008-03-18
> **Scapie said:**
> 
 I, however, will not be able to be persuaded to dual-boot, as I am hoping to soon upgrade XP to Vista - from what I gather, this is the depths of Hell for Linux users. 

Just out of curiosity, what benefits do you expect from "upgrading" from XP to Vista?  

Jerry

---

### Post by Scapie on 2008-03-18
> Just out of curiosity, what benefits do you expect from "upgrading" from XP to Vista?  

Jerry

I'm not particularly expecting any benefits. It's mainly because A) my XP system is cluttered, and B) I need Windows to run particular programs (they don't run under Wine).

> 1. install "gnome alsamixer", it will be under "applications -> sound and video"
2. don't know
3. flash tends to crash on ubuntu and takes firefox with it. Set you terminal to a shortcut (like f12) in system -> preferences- > keyboard shortcuts and in a terminal type

pkill firefox

Firefox will be gone.

Nothing would respond at all with the system. Only the mouse pointer moved, it couldn't "interact" with anything, so I think assigning a keyboard shortcut to "pkill firefox" unlikely to work. Plus, I have the sound mixer in "Applications > Sound and Video" and I have enabled everything, so installing the "gnome-alsamixer" package probably won't do anything. Thanks for the suggestions, anyway.

---

### Post by Xiong Chiamiov on 2008-03-18
[QUOTE=Scapie;4533551. I, however, will not be able to be persuaded to dual-boot, as I am hoping to soon upgrade XP to Vista - from what I gather, this is the depths of Hell for Linux users.[/QUOTE]
If you mean that we would die before "upgrading", well then, yes ;).  However, my roommate is dual-booting Vista and Kubuntu on his lappy just fine (and soon we're going to try adding OSX).

Flash in Linux most certainly causes problems for many people.  I had many problems until I switched from Firefox to Swiftweasel (which shouldn't make any difference).  I avoid GNOME whenever I can, but I know that in KDE, when flash freezes my browser, KDE is still responsive, and I can kill processes by attempting to x them (which will give me a "this window isn't responding" box).  You can also try Kazehakase or Opera if you don't need the extensibility of Firefox.

---

### Post by Scapie on 2008-03-19
I may try KDE when I get home tonight. Luckily, it's the end of the term at school, so I can fiddle around with Ubuntu as much as I want to.

Quick question: Does Gnash interpret SWF files exactly the same as Flash?

Cheers.

---

### Post by Scapie on 2008-03-22
Ok, the results are in:

I have succesfully installed KDE, and though it hasn't had chance to show it's promised features, I like the environment. I have a feeling that the screensavers also have a hand in crashing GNOME, so they're disabled for now.

When trying to install the Java VM, this is my exact message (same errors for all 3 major Java products, just happen to have used the sun-java6 VM's errors)
"E: sun-java6-bin: subprocess post-installation script returned error exit status 127
E: sun-java6-plugin: dependency problems - leaving unconfigured
E: sun-java6-jre: dependency problems - leaving unconfigured"
Does anyone have any ideas?

With sound, I admit, I was wrong (being a Linux newbie it's to be expected) - GNOME ALSA mixer is a completely different application - but it still didn't resolve my problem. I also tried to install PulseAudio... nothing happened (hoping to learn more about this soon)

---

