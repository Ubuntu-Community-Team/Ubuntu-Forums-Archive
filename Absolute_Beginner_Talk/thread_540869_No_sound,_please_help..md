---
title: "No sound, please help."
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Andre_3608 on 2007-09-02
Impressed with the demonstration DVD?  Determined to escape Big Bad Bill's yoke?  Downloaded the package?  Impressed with the plethora of faciltiies for the office, the internet, cameras, videos?

But then you turn on the sound:  and realise that, unless you are a competent programmer, Ubuntu is for the deaf.  For the tyro, largely dependent on an "out of the box" compatibility, Ubuntu makes absolutely no provision, provides absolutely no drivers,something that advertisements choose to omit.  Nor is it possible for a novice to download such from the internet - even instructions for installing and extracting from tar.gz files confuse and contradict.  No radio, no CDs to listen to while you work.

**removed**

---

### Post by chrome307 on 2007-09-02
Is that correct?

I don't recall on any of Windows based PC's being provided with instructions on how to extract zipped files (both Ubuntu + Windows have inbuilt archive managers) or how to install files either.

I think with any change you should be prepared for a **'learning curve'** - forums like these are a great help ( to me ) and having some reading material for reference are a benefit.

---

### Post by scxtt on 2007-09-02
> **Andre_3608 said:**
> Impressed with the demonstration DVD?  Determined to escape Big Bad Bill's yoke?  Downloaded the package?  Impressed with the plethora of faciltiies for the office, the internet, cameras, videos?

But then you turn on the sound:  and realise that, unless you are a competent programmer, Ubuntu is for the deaf.  For the tyro, largely dependent on an "out of the box" compatibility, Ubuntu makes absolutely no provision, provides absolutely no drivers,something that advertisements choose to omit.  Nor is it possible for a novice to download such from the internet - even instructions for installing and extracting from tar.gz files confuse and contradict.  No radio, no CDs to listen to while you work.

*removed* cause Artificial Intelligence removed it from the original :)and your point is?  doesn't seem to be getting sound working . . .

how about the obligatory **lspci**?

---

### Post by Jimmyfj on 2007-09-02
A rather poetic way of throwing the towel to the ring :) 

In my 15 years on the Windows platform I've never come across a Windows version that did not require drivers for a sound card, nor have I seen any version released with a solid instruction on how to unzip files, install programs or even read the hieroglyph error codes Windows are "pleased" to throw at its users.

Maybe if you took the time and asked for help we'd help you make your sound work for you. For that we need some basic information about your system: CPU, the brand of you graphics card, network card, sound card. Then we could point you toward a solution. I list the hardware just to remind you that IF you experience further issues you'll know what to put in your next tread.

And by the way, welcome to our community.

---

### Post by Perfect Storm on 2007-09-02
Just reconstructed the title and thread.

Andre_3608, if you want help, please do it in good manner. People tend to avoid helping people that flame/troll/insult/attention seeking. You catch more flies with honey than vinegar ;)


Lets keep this thread to supporting

---

### Post by s26c.sayan on 2007-09-02
> **Andre_3608 said:**
> Impressed with the demonstration DVD?  Determined to escape Big Bad Bill's yoke?  Downloaded the package?  Impressed with the plethora of faciltiies for the office, the internet, cameras, videos?

But then you turn on the sound:  and realise that, unless you are a competent programmer, Ubuntu is for the deaf.  For the tyro, largely dependent on an "out of the box" compatibility, Ubuntu makes absolutely no provision, provides absolutely no drivers,something that advertisements choose to omit.  Nor is it possible for a novice to download such from the internet - even instructions for installing and extracting from tar.gz files confuse and contradict.  No radio, no CDs to listen to while you work.

**removed**

Well, long ago when I had M$ on my machine, I had to reinstall it once. I found out to my utter dismay that I had no sound on it! I had to call upon the person who configured the system for me (I was a n00b those days!) who installed me the required drivers and I had to pay for them again!!

On the contrary, when I installed Ubuntu on the same system,  sound worked right out of the box!!

So, I'd suggest you NOT to generalize based on your personal expereiences and refrain from saying things like "Ubuntu is for the deaf"!

Rather, post your hardware details, etc. ....I'm sure people will be glad to help you!

---

### Post by Mumbutu on 2007-09-05
> **Jimmyfj said:**
> A rather poetic way of throwing the towel to the ring :) 

In my 15 years on the Windows platform I've never come across a Windows version that did not require drivers for a sound card, nor have I seen any version released with a solid instruction on how to unzip files, install programs or even read the hieroglyph error codes Windows are "pleased" to throw at its users.

Maybe if you took the time and asked for help we'd help you make your sound work for you. For that we need some basic information about your system: CPU, the brand of you graphics card, network card, sound card. Then we could point you toward a solution. I list the hardware just to remind you that IF you experience further issues you'll know what to put in your next tread.

And by the way, welcome to our community.

I like your answer very much.
In my case I posted "no sound" 3 days ago and I followed what you suggested, kindly requesting help, giving the system information, and waiting. I am still waiting for help because the only answer I got did not help that much.

Let's see if somebody, including you, can help me find a solution for which I'll be very grateful, of course.

I am new to Linux.
WindowsXP is on the primary drive and the sound is not an issue.
Linux is on the slave drive (the second HD which is totally devoted to Ubuntu).
Installation went fine.
I got access to the Internet.
I got the printer set up correctly. The printer is a network printer through a D-Link DP-301U USB print server and it serves 3 computers.
But no sound, nothing coming out of the DVD and CD even if it's show it's playing.
Master is set up properly.
The sound card is SBLive!Value-EMU10K1 and it is reconized by Ubuntu.
According to the only answer I got, lspci, lsmod, and sudo/etc/init.d/alsound restart && dmesg | tail,"all is set up and should work as you've said" which is not a helpful reply to solve the issue.

I need, as long as it is possible, a step by step modus operandi.

Thanks for your attention

---

### Post by scxtt on 2007-09-05
mumbuntu --

are you sure there isn't a "hidden" volume set to zero? - fire up **alsamixer** in a terminal and check them all out ...

you may have answered that ? w/ "Master is set up properly" - just want to be sure.

---

### Post by Mumbutu on 2007-09-05
> **scxtt said:**
> mumbuntu --

are you sure there isn't a "hidden" volume set to zero? - fire up **alsamixer** in a terminal and check them all out ...

you may have answered that ? w/ "Master is set up properly" - just want to be sure.

I did. One thing: tone shows MM while the rest looks OK.

---

### Post by Mumbutu on 2007-09-05
> **scxtt said:**
> mumbuntu --

are you sure there isn't a "hidden" volume set to zero? - fire up **alsamixer** in a terminal and check them all out ...

you may have answered that ? w/ "Master is set up properly" - just want to be sure.

Hi again,
In my reply to your post I forgot to point out that I performed a "lspci -v".
I got a list of : " Capabilities: <access denied>" including for the Ethernet controller, the serial controller, the input device controller (Creative Labs SB Live !)

---

### Post by scxtt on 2007-09-05
i don't have that card, so i can't get too detailed - did you try hitting up on "tone" and hitting the "m" key to unmute it - can't hurt ...

do a **sudo lspci -v** to remove the "<access denied>" output ...

---

### Post by ayenack on 2007-09-05
If you have on-board sound as well as a PCI sound card disable the on-board in BIOS. This often works. This card should work. Also do the simple things make sure the card is properly seated if you're using a desktop.

---

### Post by Mumbutu on 2007-09-05
> **ayenack said:**
> If you have on-board sound as well as a PCI sound card disable the on-board in BIOS. This often works. This card should work. Also do the simple things make sure the card is properly seated if you're using a desktop.


I also did that and dod not find an on-board sound. The Pci sound card works well under WindowsXP.

---

