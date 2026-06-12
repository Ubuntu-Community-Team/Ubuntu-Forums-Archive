---
title: "Speech-Dispatcher package broke?"
date: 2007-03-22
forum: Assistive Technology &amp; Accessibility
---

### Post by sedition on 2007-03-22
First off, the preliminaries:

I'm running Edgy i386 with all standard installed repos open and active plus medibuntu. Sounds works.

Background:

I have a friend who is blind and he wants to try Ubuntu. He's fed up with XP and JAWS (a windows screen reader). I plan to, once I get this working, create a custom distro on a live CD that he can take for a test drive based upon the command line install and certain accessibility packages (specifically TTS ones), as well as a few others (browser, email, mud client, etc.). I figure that he'd be more efficient in a text only environment once he gets the hang of it (he's a pretty bright guy and a swift learner).

The problem:

In my standard install from the live cd, I tried out festival ```
(SayText "I'm working.")
``` and it works fine. I pulled down speech-dispatcher and tried it out ```
spd-say "I'm working."
``` and got no love. I checked the config file and eveything looked kosher. I checked the log file and noticed that when calling the config file, the referenced path had double slashes right before the config file, e.g (mind you, this is from memory and I've been taking cold medicine):
```
/etc/speech-dispatcher/modules//speechd.conf
```
Is this a package compilation issue? I seem to recall while playing around with this on Debian (before my total Ubuntu transition :) ) a while back that I had a similar issue and when I compiled speech-dispatcher from source, there was a an option specifically for Debian systems that may or may not have taken care of this issue.

Being the guy I am, I tried to take the path of least resistance (not recompiling speech-dispatcher) and pulled down espeak, tested it, edited the speechd.conf file appropriately and still no sound from speech-dispatcher. Tried it with flite and no dice there as well.

Short of trying to recompile speech-dispatcher from source, anyone have a similar problem or a solution? I can post more specific error messages and my conf files once I get home from work today. I'd really like to use ubuntu for this as it's quite possibly the best and most user-friendly distro I've tried. The forums here have been an veritable plethora of helpful information and I think that apt would make the learning curve a lot shorter that using Oralux or pkg_install via FreeBSD.


Thanks in advance,
-sed

---

### Post by sedition on 2007-03-22
Update:
So I got home installed espeak and compiled Speech-Dispatcher from source. It works perfectly fine. Set up everything the same on another computer, but using the package instead and it doesn't work. After comparison, here's what I found: the compiled version put the program's modules and clients folder along with the speechd.conf file at ```
/usr/local/etc/speech-dispatcher/speechd.conf

``` in the package it drops everything at ```
/etc/speech-dispatcher/speechd.conf

``` using the computer with the working version, I installed kernel-patch-speakup and reboot to command line. After login I ran:
```
sudo modprobe speakup_sftsyn
sudo speech-dispatcher
sudo speechd-up

``` and started getting data! Everything was being read, but...

New Issue:
The system falls into some kind of loop where the damn thing won't shut up. It continually says, "Playing wave '/tmp/espeak.wav' ; signed 16 bit Little Endian, Rate 22050 Hz, Mono." This will continue until you reboot, or ```
sudo killall speechd-up
``` Anyone ever run into this?

Yet Another update:
I followed the same process with the second machine (compiling speech-dispatcher from source, etc.) and everything works like a champ: speakup, speech-dispatcher, speechd-up and espeak.

---

