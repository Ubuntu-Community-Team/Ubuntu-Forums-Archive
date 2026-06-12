---
title: "Keyboard Stops Working"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by notoriouslyKEN on 2006-11-26
I am using Ubuntu Edgy on an IBM Thinkpad r32 (laptop).  I have been using it successfully for more than a month and prior to that I was using dapper for 6+ months.  The other day I turned on the laptop and it wouldn't let me log-in.  As a matter of fact, I could not type anything at all.  I can hit Caps Lock and the Caps Light will light up.  I can even adjust the brightness of the screen with the keyboard.  However, I can not type anything in the User Name box.  I booted into the recovery and could type in the terminal part.  I tried to run "startx" and it worked fine.  However when it loaded up, the keyboard would stop functioning and I can't type again.  I tried to run Device Manager to see if it is listed, but Device Manager will show starting at the taskbar and then close and never open.  Same thing happens with Firefox/Konquerer.  I was able to open the Process Manager, but didn't see anything unusual (not like I'd really know, I am not that good at troubleshooting Linux).  Any suggestions?

---

### Post by LLRNR on 2006-11-26
Just a quick thought: did you install Beryl & xgl/aiglx recently? If not, I can't think of anything else that might be wrong...

---

### Post by notoriouslyKEN on 2006-11-26
> **LLRNR said:**
> Just a quick thought: did you install Beryl & xgl/aiglx recently? If not, I can't think of anything else that might be wrong...

I don't even know what those are, so I would assume not.  The last things I installed were rdesktop and some video codecs so I could play WMV files.

---

### Post by corefile on 2006-11-30
I have the same problem, but its not a laptop, it happens  on a brand new edgy install, after I do the first update, reboot and then I can't login cause the keyboard stops working.

---

### Post by LLRNR on 2006-11-30
> **corefile said:**
> I have the same problem, but its not a laptop, it happens  on a brand new edgy install, after I do the first update, reboot and then I can't login cause the keyboard stops working.

Since this happens after the first update, I assume that initially (i.e. right after the fresh install you did) it worked ok. Does the keyboard stop responding completely? Can you hit Ctrl+Alt+F1 (and Ctrl+Alt+F7 to go back to the GUI) ?

LLRNR

---

### Post by adibudeen on 2006-12-04
I have the same problem on a different architecture: Apple iBook G4.

I have beryl installed but not using it.

It just happened about an hour ago, so I decided to search for a solution.  It freezes the keyboard, but I can still enable caps lock (just like the poster above) and can hit F12 and get a menu (F12 is used as the right click on ppc).

I thought that it might be a pbbuttons bug because of that.  The keyboard apparently still works, but nothing fixes it.  Strangely, if I exit X and try to restart it, it will freeze and only give me an "X" for a mouse cursor.  Invariably, I end up hard rebooting.

This did not occur with Dapper.  I'm not sure if it happened with the latest Edgy update.

---

### Post by adibudeen on 2006-12-04
By the way, I cannot switch with Ctrl+Alt+F1 (or F2, etc.)

---

### Post by rfdeshon on 2007-01-17
I am having this same problem on a Lenovo 3000 C100. It happens at random, it will sometimes run for few days without happening but it always seems to come back and happen again. No programs will launch, no keystrokes seem to be recognized by the OS and it will not poweroff if I press the power button thus I have to hard reset. I am running Edgy as well. I have aiglx enabled and beryl installed, though it happens sometimes when i am running beryl and sometimes when i am not (I have beryl set up as a session so i can switch back and forth easily). I wish I could give you more information than this, but I'm not really sure where to try and grab information from after hard reseting like this.

---

### Post by Ozor Mox on 2007-03-18
I've had this same thing happen once or twice on my Dell Latitude D600 running Edgy. The last time it happened, I was running

```
gksudo nautilus
```

When the system asked me for my password, I couldn't put it in. I cancelled the operation and found I couldn't type in anything. I also couldn't use Ctrl-Alt-F1 or Ctrl-Alt-Backspace to reset the X server. Even the caps lock and num lock keys wouldn't switch their lights on and off on the keyboard display, as though it has been unplugged (it's a laptop keyboard though!)

In addition to those effects, I also couldn't launch any applications or administrative tools except Firefox (starting application...) would appear and then disappear and nothing would start, and clicking the shutdown button would do nothing at all. I had to restart by holding down the power button. After a reboot, everything was back to normal.

Is this a strange bug of some kind?

---

### Post by adibudeen on 2007-03-19
It seems to be most common on laptops, so it makes me wonder if there is something running on the laptops that is causing this problem.

I finally had to switch back to Mac OS X as the main operating system on this iBook G4 because I use it for work (company owned) and can't have it randomly freezing (not to mention Ubuntu dropping official support for PPC).  And I am the type who tries to avoid proprietary software at all costs.  All of my PCs (including a laptop and a home theater system) run Edgy at home, but none of them have this problem.

Has anyone tried a different distro (like debian or fedora) to see if this is Ubuntu-specific?

---

### Post by klato on 2007-03-24
I have this same problem.  I have a "Sleep" function button on my laptop, when I tried it out, the screen dimmed.  I moved the mouse, screen came back on, but I couldn't type in anything (no caps, no ctrl-alt-backspace, nothing).  Had to do a damn hard reboot.

---

### Post by Goliath! on 2007-05-11
I have this problem on a Dell D610 laptop.  I had Edgy running fine, then I upgraded to Feisty.  That ran great for a couple of weeks.  Then one day I booted up the laptop and I couldn't log in because the keyboard wouldn't work.  I could hold down the power button to reboot.  I could move the mouse just fine.  But no other keys had any affect whatsoever.

I discovered a way around the problem.  I use the mouse to click Options on the login screen and click Suspend.  I let the machine go to suspend mode, then press the power button to bring it back.  Then my keyboard is fine.

It happens every single time I turn the laptop on now.  So my boot-up sequence is: start the machine, put it to Standby, bring it back, and then log in.

Several times when I clicked Standby nothing happened.  Nothing at all.  I had to select Hibernate to get the screen to go dark, and then I woke up the laptop and everything was fine.

THis is a short-term work-around of course.  But it will due until some one finds a real fix.

---

### Post by Goliath! on 2007-05-12
I seem to have solved this problem, although I don't know how.

I opened Update Manager and saw there was an update for eLinks text browser.  I installed that, even though I don't use eLinks.  This may have had something or nothing to do with the fix.

Then I noticed that if I just let the computer sit at the login prompt for about 3 minutes, the keyboard would start working again.

Now when I boot my machine I only have to wait for about 5 seconds or so and the keyboard works.

Still not entirely fixed, but the worst of the symptoms went away.  If I could say that about getting old, I'd be a happy man :) 

And Ubuntu is STILL way way better than Windows.  Kind of like how getting old is way better than getting dead I guess :lolflag:

---

### Post by tehtrk on 2007-06-26
I am having a similar problem with my compaq C300. Sometimes when I suspend mouse will work but not the keyboard. This has not always been the case, as it never did this on my "test install" of feisty. I have since reinstalled and stuck to minimal software installation and light system modification, as I am using feisty as a primary OS now. 

If your keyboard is working after 5 minutes that tells me that our answer lies in the logs. I am going to try to replicate this behavior and I will post my findings here soon.

---

### Post by tehtrk on 2007-06-26
FYI neither my mouse nor my keyboard work after a suspend/resume. This is from my kern.log I would suggest that you check yours for this as well (I just used the gnome sysem log viewer)

I have highlighted the suspected errors in red for you all to see.

```
Jun 26 10:56:08 miracle kernel: [ 2423.088000] system 00:04: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.088000] pnp 00:05: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.088000] system 00:06: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.088000] i8042 kbd 00:07: resuming
[COLOR="Red"]Jun 26 10:56:08 miracle kernel: [ 2423.088000] pnp: Device 00:07 does not support activation.[/COLOR]
Jun 26 10:56:08 miracle kernel: [ 2423.088000] i8042 aux 00:08: resuming
[COLOR="Red"]Jun 26 10:56:08 miracle kernel: [ 2423.088000] pnp: Device 00:08 does not support activation.[/COLOR]
Jun 26 10:56:08 miracle kernel: [ 2423.088000] pnp 00:09: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.088000] platform pcspkr: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.088000] pci_express 0000:00:1c.0:pcie00: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.088000] pci_express 0000:00:1c.0:pcie02: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.088000] pci_express 0000:00:1c.1:pcie00: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.088000] pci_express 0000:00:1c.1:pcie02: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.088000] pci_express 0000:00:1c.2:pcie00: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.088000] pci_express 0000:00:1c.2:pcie02: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.088000] serial8250 serial8250: resuming
[COLOR="Red"]Jun 26 10:56:08 miracle kernel: [ 2423.088000] i8042 i8042: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.088000] i8042: failed to resume active multiplexor, mouse won't work.[/COLOR]
Jun 26 10:56:08 miracle kernel: [ 2423.092000] atkbd serio0: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.296000] platform eisa.0: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.296000] serio serio1: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.296000] serio serio2: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.296000] serio serio3: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.296000] psmouse serio4: resuming
Jun 26 10:56:08 miracle kernel: [ 2423.296000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Jun 26 10:56:08 miracle kernel: [ 2423.316000] platform vesafb.0: resuming
```

Also I found this: [https://wiki.ubuntu.com/DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend")

Still reading it though I think it probably holds the key

---

