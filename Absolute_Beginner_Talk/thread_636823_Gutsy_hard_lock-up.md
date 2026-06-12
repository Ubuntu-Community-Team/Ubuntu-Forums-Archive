---
title: "Gutsy hard lock-up"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Poohbuntu on 2007-12-10
I've read that one of the great advantages of running Linux over Window$ is that Linux is more stable.  One author went so far as to say that Linux never crashes.  I am running Kubuntu Gutsy Gibbon and fresh from install it locks up on me, hard, maybe three times a day.  I have not noticed any pattern of use that triggers the lock-up.

So what's the deal?  What does it take to lock up Linux?  **How should a noob like me start troubleshooting?**  My goal is to eventually achieve Penguinista status and be a knowledgeable Linux user, but at the moment I am a total noob.  I was really hoping that by going with Ubuntu I'd be able to have Linux running on my machine with ease, allowing me to learn Linux by using it, rather than learn it by troubleshooting immediately after install.  I guess I was naive on that one.

Any help would be welcome.

---

### Post by meborc on 2007-12-10
lock up in what way? the screen freezes? are you still able to press ctrl+alt+F2 to get to the command line?

the system freezes usually come either from overheating, or from wrong display drivers. what graphic card do you have? and how did you install the drivers for it (the method)

linux is as stable as you make it :) it depends on the hardware and the person behind the keyboard... don't worry, if you stick to it, you will get there :D

---

### Post by philinux on 2007-12-10
Whats your system specs.

Are you running compiz or any other eye candy. If so disable it and see if thats it.

Look in /usr/var/message.log  - good place to start trouble shooting.

Some hardware mixes cause problems for any OS.

---

### Post by meborc on 2007-12-10
just by accident stumbled on this [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/157650](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/157650) ... please check your error logs to see if you have the same problem

---

### Post by Poohbuntu on 2007-12-10
Many thanks to meborc and philinux for passing on good info.  I think what I'd like to do here is write up a basic troubleshooting text for noobs like me who have decided to try their own troubleshooting.  If something like this already exists, please just point me to it and I will work from that instead of clogging this forum with questions.  :)

If there is no existing guide for this. please offer corrections to the following text:

**Troubleshooting Hard Lock-up of OS for Total Noobs**

1.  At lock-up, determine the extent of system seizure.  Will Ctrl-Alt-Backspace log you out?  Will Ctrl-Alt-F2 open a virtual terminal?  Can you still move the mouse pointer?

2.  What components comprise your hardware configuration?  What chipset, motherboard, graphics card, audio card, networking hardware, USB hardware, or other extrnal peripheral must Linux manage for you?

3.  Have you confirmed that the driver installed for your graphics card is the appropriate one?  What was your method of installing this driver?

4.  Can you rule out temperature as a culprit?  How hot is your CPU, your video card, or other components at the moment of lock-up?

5.  Is Linux able to use the swap partition?  Open a terminal window and enter the command "free" to view memory usage by the system.

6.  Have you read through your message log?  Check /usr/var/message.log to see if there are error messages that coincide with the timing of the system lock-up.

7.  If you are unable to resolve computer lock-ups using this approach, compile the information you collected above and post it to ubuntuforums.org.

---

### Post by Poohbuntu on 2007-12-10
As an update:  while I was drafting the previous post, my system locked up on me.  Fortunately for me, my draft post had been saved and was retrieved the next time I opened Firefox.

So, to document the lock-up:
06:42 the kernel found an AGP 3.0 compliant device, then twice tried to put that device into "8x mode," then started to load R300 Microcode, at which point the system froze.

At the time, I had Firefox (with just 4 tabs open) KSystemlog, and Konsole running simultaneously.  I was able to move the mouse pointer on the screen but not click on anything.  The mouse pointer image was stuck as the "grab" icon, since the system locked just as I was using the mouse to grab my Konsole terminal and drag it across the screen.  The system did not respond to Alt-Tab, Ctrl-Alt-F2, or Ctrl-Alt-Backspace.  I then pressed the reset button on the front of my computer.

Upon reboot, I opened System Settings and reduced eye candy, changed the video card setting from "ATI Radeon (flgrx)" to "ATI All-in-Wonder PRO," and confirmed that the network manager showed that all was fine with my ethernet card.

I'd write more, but I'm running late for work now and must run out the door.  I'll add more when I get home.

---

### Post by philinux on 2007-12-11
Never hit the power off button, well only if the below still dont reboot it.

With you're pinckies hold down the ALT and SysRq buttons then press in turn  [FONT="Courier New"]**R E I S U B**[/FONT]

This will unmount all drives and shutdown the system properly. I know its a bit off a finger dance but its worth it.

---

### Post by jaybombalous on 2007-12-11
sounds like a video problem to me, I bet you are using ATI right?

AGP is video and r300 sounds like a video chipset. :)


as stated before, make sure things are cooling ok first and foremost. I have seen people wrack their brains for weeks until they finally tried the vacuum cleaner and a can of air which solved there problem outright and forever.

---

### Post by jaybombalous on 2007-12-11
BTW, ATI is proprietary hardware and software. Linux is not the problem... Don't blame the author because u chose to use something that isn't officially supported.

try using 'envy' to install the video drivers.

---

### Post by Poohbuntu on 2007-12-12
Jaybombolous, I agree with your assertion that my ATI video card is making life hard for me.  Coincidentally, it is also having problems - the (proprietary) fan on it is dying and I would rather replace it with a friendlier card than invest in an overpriced replacement fan.  As for the failing fan resulting in unacceptably high temperatures, I doubt that's the issue.  The air inside my box is downright cool - the aluminum box itself is cold to the touch.  I live in a poorly-heated apartment in the northern hemisphere, so it gets pretty chilly on the floor (which is where I keep my box); I have some massive fans venting the oversized case, so airflow is excellent.

If the video card should fail, how is it that I often still can move the mouse pointer around the screen?

Anyhow, I'm still having problems with occasional hard lock-ups.  They don't seem as common now as they were before, but they still happen.  I am not running ANY eye candy.  Compiz is not even installed.  

I'm not familiar with "envy" as a way to install video drivers, but if I can figure it out I'll give that a try.

---

### Post by philinux on 2007-12-12
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Vadi on 2007-12-12
Are you using ndiswrapper for your wireless?

---

### Post by Poohbuntu on 2007-12-12
After the latest hard lock-up, I rebooted, went to Albert Milone's web page (which I had to access via proxy because that server is blocked here in China), installed Envy, and used Envy to install a driver for my video card.  Envy properly identified my video card, so that was reassuring.  Upon reboot, Ubuntu popped up a warning message to make sure I understood that ATI's drivers are proprietary and so Ubuntu developers don't work with them, meaning that I'm dependent on ATI to get the details right on this.  Given my lack of faith in ATI as a company, this does not bode well.  But it is as expected, so I enabled the driver and... so far so good.

Looking over the messages.log, what seems a little glitchy is that the time stamp on the log entries is not in perfect sequence.  

21:38:24 - my system was restarted.
21:38:27 - my video card was initialized.
21:38:28 - "Failure registering capabilities with primary security module" followed by a few lines about putting my video card into 8x mode.
Then there was this entry I don't understand:
21:38:28 xubuntu dhcdbd: Started up.
Followed by the anomaly:
Dec 12 21:38:26 xubuntu kernel: [   47.522573] Bluetooth: Core ver 2.11
Dec 12 21:38:26 xubuntu kernel: [   47.522698] NET: Registered protocol family 31
Dec 12 21:38:26 xubuntu kernel: [   47.522701] Bluetooth: HCI device and connection manager initialized
Dec 12 21:38:26 xubuntu kernel: [   47.522704] Bluetooth: HCI socket layer initialized
Dec 12 21:38:26 xubuntu kernel: [   47.534318] Bluetooth: L2CAP ver 2.8
Dec 12 21:38:26 xubuntu kernel: [   47.534323] Bluetooth: L2CAP socket layer initialized
Dec 12 21:38:26 xubuntu kernel: [   47.570402] Bluetooth: RFCOMM socket layer initialized
Dec 12 21:38:26 xubuntu kernel: [   47.570517] Bluetooth: RFCOMM TTY layer initialized
Dec 12 21:38:26 xubuntu kernel: [   47.570521] Bluetooth: RFCOMM ver 1.8
Dec 12 21:38:26 xubuntu kernel: [   47.672313] [drm] Setting GART location based on new memory map
Dec 12 21:38:26 xubuntu kernel: [   47.672323] [drm] Loading R300 Microcode
Dec 12 21:38:26 xubuntu kernel: [   47.672360] [drm] writeback test succeeded in 1 usecs

Please note that the anomalous log entries indicate that they took place 2 seconds before the entries above them.  After these events, the system locked up.  I had just tried to open a terminal window to install Envy and the screen froze.  As per usual, I could still move the mouse pointer, but clicking was nonresponsive.  Ctrl-Alt-F2 had no effect, nor did Ctrl-Alt-Backspace.  I held down Alt-SysRq and tapped the "r" key and within a second or maybe a second-and-a-half it cut power to the entire system.  Is that what is supposed to happen?  It seemed awfully abrupt, and did not allow me enough time to tap out the E I S U B sequence.

I'll post again after the next lock-up.  I'm cautiously optimistic that the video card driver was the problem and that using ATI's driver will "fix" the problem - at least until I can fix ATI by ditching the card.  Any recommendations for a video card that is Linux-friendly?  :)

---

### Post by dward526 on 2007-12-12
> **jaybombalous said:**
> sounds like a video problem to me, I bet you are using ATI right?

AGP is video and r300 sounds like a video chipset. :)


as stated before, make sure things are cooling ok first and foremost. I have seen people wrack their brains for weeks until they finally tried the vacuum cleaner and a can of air which solved there problem outright and forever.

Agree totally with this one!  Maybe it is my Electronics Tech background, but I am thinking it may be Hardware on this one, Check to see it your cooler and vents are clean.

If it was something to do with xorg (the GUI), it would fail more consistently.

Keep us posted

---

### Post by Poohbuntu on 2007-12-12
Oh, and to respond to Vadi, I am NOT running ndiswrapper.

As for dward526, when it locked-up last time, I opened my case while the system was still on and checked temperature levels (not with a thermometer, just wafting my fingers around).  All fans were blowing, filters were clear, the box itself was cool inside, and the air blowing off the video card was barely warm.  Keep in mind that at no point have I tried to do anything graphically intensive yet.  No reason why my card should be overheating at all.  

Of course, the card may have issues unrelated to heat.  I've had an unhappy relationship with it for five years now (it is an ATI All-in-Wonder 9700 Pro) and this may end up simply being my excuse to finally ditch the pig and get a new card for my box.  The latest annoyance is that the fan is gradually grinding itself to death.  It makes a lot of noise - but it's still blowing and I can still manually adjust the fan RPMs.  Not long for this world now...

---

### Post by dward526 on 2007-12-13
Ok, so it is not a heat issue. :)  I think it may still be your card though, which you are inclined to blame as well.  

If it is increasing in noise the fan bearings are going, and it may be time to ditch it.

---

