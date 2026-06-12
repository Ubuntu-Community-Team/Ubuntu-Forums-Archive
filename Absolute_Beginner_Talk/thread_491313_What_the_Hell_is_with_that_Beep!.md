---
title: "What the Hell is with that Beep?!?"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by TheBlackWizard on 2007-07-03
Ok...

My computer is beeping.

Every 3 - 15 seconds, it lets out this freaking annoying beep.

The time seems to be random, not corresponding to any particular thing I am doing.

It is driving me nuts.

I have disabled the system beeps in the Sound part, but it is still doing it.

Any ideas?

---

### Post by Rocket2DMn on 2007-07-03
You can disable the system beep:
System->Preferences->Sound->System beep

---

### Post by TheBlackWizard on 2007-07-03
> **Rocket2DMn said:**
> You can disable the system beep:
System->Preferences->Sound->System beep

Ok, not to be rude, but did you read the post, or just the headline? #-o

---

### Post by Rocket2DMn on 2007-07-03
I read the post, sounds like a system beep (this is a common problem for people).  Do you have a desktop computer with chassis intrusion detection?  If so, this can be disabled in the BIOS.
If it's not either of these, do you have any other idea what it could be?  Have you installed anything new recently?  Added hardware?  Suffered any sort of hardware failure?

---

### Post by rolfen on 2007-07-03
Possible workarounds:
- Get earplugs
- Listen to loud music

---

### Post by Rocket2DMn on 2007-07-03
> **rolfen said:**
> Possible workarounds:
- Get earplugs
- Listen to loud music

That was intelligent and useful... In general we try to solve problems, not cover them up.

---

### Post by kebes on 2007-07-03
Is the beep coming from the speakers or from the built-in PC speaker? If you unplug your speakers, do you still hear it?


It might be the motherboard giving a "high CPU temperature" alarm (or other motherboard warning). Try going into the BIOS for the motherboard, and see what the CPU temperature readout is. Maybe the CPU's cooling isn't working as well as it used to... See if there is an option for temperature alarms, and what they are set to.

There may be other hardware alarms set in the BIOS. Look around and see what options are there.

---

### Post by TheBlackWizard on 2007-07-03
I don't know about "intrusion detection". Never heard of it, would know if I did. 

My computer is a new Acer Aspire 9410z, with dual-boot Vista/Ubuntu.

The only thing that I have changed in the configuration from the inital install is attempting to get a USB headset to work.

I can't remember if it was doing it before that or not... (Just installed Ubuntu last night)

Is there a way to reload all the sound "parts" of the OS, back to the default? Not sure if you call it a module, kernal, process, whatever...

Still new to Linux...

---

### Post by Rocket2DMn on 2007-07-03
Perhaps the motherboard's battery is failing or is not present?
Definitely shouldn't relate to the USB headset.  I suggest having a look in your BIOS to see what hardware problems might result in beeping since that what system beeps tend to be.
Does the computer beep while it's booting up, or JUST when Ubuntu is loaded?  Beeping in Vista?

---

### Post by sab0403 on 2007-07-03
Is that a desktop or a laptop?

If it's a desktop, unplug the speakers. If it's a laptop, plug in some earphones - this is to see if the sound is coming from the speakers or the built-in speaker.

If it's the speakers, it's most likely a setting within Preferences | Sounds. If it comes from the built-in speaker, it could be a temperature/overheating alarm, or some other kind of system alert.

Does the beep come up even if you do nothing? Or when you're working, etc.?

---

### Post by TheBlackWizard on 2007-07-03
It doesn't beep when going into the BIOS at startup, or when using (god forbid) Vista.

I can't tell if it is being generated from the motherboard speaker, or from the audio speakers.

It is a steady volume, regardless of changes to speaker volume, so that tends to make me believe that it is a motherboard speaker generating the sound.

In regards to heat, that is interesting, due to the fact that my processor  fan never seems to come on...

But, on the flip side, my processor isn't working overtime to handle 38 billion extra lines of code...

How do I go into the BIOS to check heat sensor? Is that something done at boot? Or is there another process?

---

### Post by r4ik on 2007-07-03
My guess is CPU you could go and check you're system health in you're bios
Otherwise there is a beep load of codes here,

[http://bioscentral.com/beepcodes/awardbeep.htm](http://bioscentral.com/beepcodes/awardbeep.htm)

Good luck !

---

### Post by TheBlackWizard on 2007-07-03
Let me clarify...

The fan is running, it just isn't kicking into high gear all the time like it did with Vista.

---

### Post by r4ik on 2007-07-03
Escape, F1, F2, F12, or Delete.
during boot ?

---

### Post by sab0403 on 2007-07-03
The sound may be steady because the volume control doesn't actually control the speakers. Does the volume control work for other apps?

I'd go to Preferences | Sounds and set every single system sound (in the second tab) to "no sound". Also I'd leave the system alone and do nothing to it for about a minute or two, and see if the beep comes up then. If it does it's very likely that it's a system thing.

Try adding a Processor monitor to the panel. Right-click on the panel (the one on the top is better since it has open space), then "Add to panel", then go to the "System and Hardware" section and add the "System Monitor" option... that lets you know the ammount of usage of the processor (on the graph) as well as the processor frequency (by hovering your mouse over it). That might shed some light on it.

---

### Post by Raineer on 2007-07-03
> I don't know about "intrusion detection". Never heard of it, would know if I did. 
It's in every BIOS from the last few years.

Your CPU is overheating, check the heatsink's attachement to the CPU, especially on something you bought premade.

edit: Also had this once when an additional power connector to a high-end graphics card wasn't plugged in.  It came up and ran but beeped until I found I left the plug out.  Normally the won't start or will just give a message after booting, not this one :)  But you say you weren't in there so I still think your heatsink is loose.

---

### Post by TheBlackWizard on 2007-07-03
Ok...


So far, we are up to....

Computer:
Acer Aspire 9410z Laptop
Dual-Boot Vista/Ubuntu
1 Gig RAM


It is the motherboard speaker that is beeping.

The beeps are not in any pattern, but instead come randomly every 3 - 15 seconds.

It is not due to overheating. lm_sensors doesn't show a correspondence between temp and beeps.

Only does it when using Ubuntu, not when using Vista or looking through the BIOS.

Any ideas?

---

### Post by Redeyes_Gambit on 2007-07-03
If you don't want to use BIOS to see you CPU temp you could always install the sensors applet package from synaptic, and then add the applet to your gnome-panel.

Just type

```

sudo apt-get install sensors-applet

```

in a terminal, or do a search for sensors-applet in synaptic. Then just right-click on your gnome-panel (the "start bar") and hit "add to panel". Somewhere in the list that pops up you should see "hardware sensors monitor". Just add it to the panel to see what your CPU temp is.

EDIT:

OOPS, never mind. You seem to have gotten lm_sensors to work for you. HTH anyhoo. Is your clock in BIOS losing time per chance? That could be an indication of a waning CMOS battery.

---

### Post by kebes on 2007-07-03
> **TheBlackWizard said:**
> Only does it when using Ubuntu, not when using Vista or looking through the BIOS. Any ideas?

Strange.... Just to confirm: you were using Ubuntu for awhile without the beeping, right? Then it just stared and continues beeping every 3-15 seconds while booted into Ubuntu. Right?

Some other things you could try, to track down the source of the problem:

1. See what modes have beeping and what don't:
a. Boot into Linux in safe mode or command-line only mode. Does the beep still happen?
b. Try booting your Ubuntu, but don't login. Just sit at the "enter your password" GUI prompt. Does the beep ever start?
d. If it's beeping in Ubuntu, and you go "logout" and sit at the login prompt, does it beep?
c. Try booting into a LiveCD (the one you used to install Ubuntu, for instance). Does the beep still happen? 
d. When you tell Ubuntu to shutdown, does the beep happen at all during the shutdown steps? At what point during a shutdown do the beeps stop?

These tests may help to differentiate between a recent hardware change or recent software change causing the beeps.

2. Open a terminal, and run the program "top", which lets you see what's currently running. (There are also GUI-based programs that show you what is running.) See if there is a particular program that always appears to be active when the beep occurs.

3. When is the last time you did software updates? It's possible that this is a bug that has been fixed already and is in the updates. (Or did this problem only start after you applied a recent set of updates?)

---

### Post by TheBlackWizard on 2007-07-10
Ok...

I reloaded Ubuntu from scratch the distro, and did NOT install the 72 updates that are available...

And, I haven't heard the beep....

So, I guess one would have to assume that one of these updates conflicted with something.

Do I need to go piece by piece now?

---

### Post by TheBlackWizard on 2007-07-10
Never mind.

It did it again, on the fresh install of Ubuntu, without the updates downloaded.

To refresh:

Brand new laptop computer.
Doesn't beep while sitting in BIOS or when using Windows Vista.
The beep sounds like Windows did when you held a key down and it would make that rapid repeating error beep.
The beep is singular.
Doesn't beep while sitting in BIOS or when using Windows Vista.
The beeps are random. They occur at random intervals, and do not appear to sync with any actions of the OS or hardware (such as a HD spin-up, etc.)
The frequency of the beeps seems to increase over time. The longer I use Ubuntu, the more frequent the beeping.
There seems to be a wait period before they start, 15-30 minutes.
There are no intense operations taking place, just firefox and terminal windows.
They occur with firefox and/or terminal windows open and/or closed, in all possible combinations.
Temp software (ls_sensors) shows no abnormalities in the CPU heat, or any other type of abnormality. The actual surface temp even "feels" cooler than it does when running Windows Vista.

Please remember, when making suggestions, this ONLY occurs in Ubuntu. I don't think that it is a Motherboard, System Clock battery, or other such issue, as it would occur in Windows as well. 


I am willing to try all the different configurations listed a few posts ago, however, it can be time consuming to wait until the beeps start, and even if I DON'T hear something in one config, it is possible that it just didn't happen yet.

Is there a way to go into the OS, and look at every thing it has done? Some sort of activity log? Something is sending a signal for Ubuntu to beep... How can I find out what it is?

Any ideas, anyone?

---

### Post by kebes on 2007-07-11
It's definitely worth checking all the logs in "/var/log/". Maybe write down the exact time for a few beeps (use the "date" command in a terminal right after the beep) and then check all the log files in /var/log. See if a particular process message or error message always appears right before or after the beep.

I would check "syslog" first. But depending what this is, a message could appear in "messages" or "kern.log" or "daemon.log" or "user.log" (or even one of the other ones!).

---

### Post by avalook on 2007-07-28
> **Redeyes_Gambit said:**
> If you don't want to use BIOS to see you CPU temp you could always install the sensors applet package from synaptic, and then add the applet to your gnome-panel.

Just type

```

sudo apt-get install sensors-applet

```

in a terminal, or do a search for sensors-applet in synaptic. Then just right-click on your gnome-panel (the "start bar") and hit "add to panel". Somewhere in the list that pops up you should see "hardware sensors monitor". Just add it to the panel to see what your CPU temp is.
I installed the sensors-applet as above, but I don't see it listed when I try to put it on the panel and don't know how to start it another way. I'm new at this, so I'm probably missing something obvious.

BTW, I started reading this thread because I was plagued by the beep, too. I suspected it might have something to do with temperature, since my Dell XPS M1210 laptop seemed to be hot, so I went looking for a temperature monitor. In the meantime, I found (in the excess stuff around the house) a laptop stand with 2 built-in fans, which runs off USB. I installed it this morning and have not had a beep since then (over 12 hours). This does suggest that the temp might have been the cause of the beep.

Would still like to get the sensors-applet running, though.

---

### Post by muddatrucker on 2007-08-05
This happens to me too during startup, shut down and when playing flash movies (playing flash games and YouTube vids, to be more specific).  I'm pretty sure it's coming from the built-in speaker.

I have an ASUS A8JR, with Vista and Ubuntu as the OSes.

---

### Post by Rocket2DMn on 2007-08-05
> **muddatrucker said:**
> This happens to me too during startup, shut down and when playing flash movies (playing flash games and YouTube vids, to be more specific).  I'm pretty sure it's coming from the built-in speaker.

I have an ASUS A8JR, with Vista and Ubuntu as the OSes.

Have you gone to System->Preferences->Sound and selected the System Beep tab where you can disable the beep?  This will disable most beeps.  If other beeps appear during startup, check your BIOS, there is often a setting there you can change to turn off the system beep.

---

### Post by muddatrucker on 2007-08-06
> **Rocket2DMn said:**
> Have you gone to System->Preferences->Sound and selected the System Beep tab where you can disable the beep?  This will disable most beeps.  If other beeps appear during startup, check your BIOS, there is often a setting there you can change to turn off the system beep.
Yes, I did.  

After more testing, I found out that it beeps anytime I do something with sound (e.g., playing games, videos, startup, before shutting down, etc.).  Is it possible that it has something to do with my sound card?  If so, how do I find out which one I have and how do I update my drivers?

It also doesn't happen when I'm on Vista.

---

### Post by Rocket2DMn on 2007-08-06
That sounds like a BIOS issue, you should reboot your computer, access the BIOS and disable the system beep.  Most BIOSes have an option for this.

---

### Post by wak_wak on 2007-08-13
At a terminal type:

xset b 0 0 0
and
xset b off

If it's still beeping it may narrow it down to being CPU (as opposed to OS) related.  And then  I believe you'd know to check in BIOS for the solution.

---

