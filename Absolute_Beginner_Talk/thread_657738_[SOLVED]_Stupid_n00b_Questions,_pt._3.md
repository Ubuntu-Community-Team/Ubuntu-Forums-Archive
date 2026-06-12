---
title: "[SOLVED] Stupid n00b Questions, pt. 3"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by ZOOstation on 2008-01-03
I should've asked this question first. How can I check if everything in Ubuntu installed properly? Or if my install CD was some kind of broken, or anything of the sort?

The real problem: My computer seems to overheat and shutdown frequently [(this thread)]("http://ubuntuforums.org/showthread.php?t=655809") but it never did that on Windows unless you were literally clogging the fans with something. This seems backwards to me -- Linux is supposed to use so little resources you could practically run it on an etch-a-sketch.

I refuse to accept that this is simply an overheating problem isolated from anything else. Something is overworking my laptop and I'm desperate to find out what.

---

### Post by ryanVickers on 2008-01-03
eh, if you wanna run it on an etch-a-scetch, you better use DSL ;)

but in the mean time, I would install some hardware monitors* for the panel to monitor CPU temperature, and if you wnat to check the CD for defects, boot it, but go "check CD for defects" or whatever that option is :p

"hardware-monitor" to be exact, - add it to the panel - at the bottom of the "add to panel" list window thing ... :p
you may also need libsensors3 and lm-sensors

---

### Post by dwhitney67 on 2008-01-03
Try to monitor the processes that are running on your system.  Gnome has an application called 'System Monitor' (gnome-system-monitor).  Alternatively, you can run the 'top' application from the command line.

IMO, if you are able to boot into your system, I would bet that everything (that came from the CD or from synaptic) is installed ok.

If your system is indeed overheating, then it definitely is a hardware issue.  Are you by chance over-clocking your CPU(s)?

---

### Post by ryanVickers on 2008-01-03
and you said it rarely does it in windows... it shouldn't do it ever... lol theres defiantly something wrong with your hardware - fans not good enough, components running to fast, etc....

---

### Post by metalpancake on 2008-01-03
You can also try Gkrellm (type it into add/remove) It can tell you more info than system monitior, like your cpu temp, etc. If you install it there will be no icon, so you have to type Gkrellm into the terminal to open it.

---

### Post by ZOOstation on 2008-01-03
> **dwhitney67 said:**
> Are you by chance over-clocking your CPU(s)?

I don't know what that means, but it's more than likely. What would I do about it?

---

### Post by ryanVickers on 2008-01-04
> **ZOOstation said:**
> I don't know what that means, but it's more than likely. What would I do about it?

well computers don't just come like that - it's an option you have to change in the bios to make your CPUs run faster, but also hotter and it can damage them

---

### Post by Paqman on 2008-01-04
> **ZOOstation said:**
> I don't know what that means, but it's more than likely. What would I do about it?

You'd know if you were overclocking, because you'd have to have done it deliberately. Overclocking is running the CPU a bit hotter than its default settings. It gives more speed, but can reduce stability.

Back to basics with your overheating problem: have you checked in your BIOS for fan control settings? Is the fan set at a constant speed or is it set to be controlled by the OS?

---

### Post by ZOOstation on 2008-01-04
> **Paqman said:**
> Back to basics with your overheating problem: have you checked in your BIOS for fan control settings? Is the fan set at a constant speed or is it set to be controlled by the OS?

I have not checked because, once again, I don't know how. How? And which of those options would I prefer?

---

### Post by Linuxratty on 2008-01-04
> **ZOOstation said:**
> I have not checked because, once again, I don't know how. How? And which of those options would I prefer?

An easy way to check how hot your system is running and if your system fan works is to leave it on an hour,then reboot...When it starts up you can read how hot it is and the fan speeds, as that shows up as it boots up..
 Another simple way to see if the fans are running is take a flashlight and look...
 I had a similar problem with a motherboard that gradually would run hotter and hotter and shut down at times...Finally it just went one night...

---

### Post by Paqman on 2008-01-04
> **ZOOstation said:**
> I have not checked because, once again, I don't know how. How? And which of those options would I prefer?

No problem. When your machine first boots a message like "press DEL to enter setup" will flash up. The exact button will depend on the machine, but usually it's DEL/F2 or similar.

That'll open up a screen a bit like [this](http://tbn0.google.com/images?q=tbn:SuXdD04KGHXAlM:http://content.answers.com/main/content/wp/en/d/dd/Phoenix_-_AwardBIOS_CMOS_Setup_Utility.jpg), or something similar. BIOS is sort of like an operating system built into your motherboard. In there somewhere will be options for controlling a lot of your hardware, including your fans. Go and see what they're set to, and what options you've got.

You can't use the mouse in BIOS, the control options will be listed at the bottom of the screen. Don't save any changes when you exit, for now.

---

### Post by ZOOstation on 2008-01-04
I didn't see any options in the BIOS concerning my fans. I did see a couple about booting my "Floppy Diskette Drive," which I'm pretty sure my computer doesn't have. Does it matter that it thinks it has one?

Poking around with a flashlight, and holding my hands over the vents, it seems one of my fans is working well, one is working not so well, and the third is not working at all. I feel stupid to say this possibility just hadn't occurred to me. Is it possible something in the software isn't activating them, or do I need to send this to a professional who can crack it open and fix the fans themselves.

---

### Post by Paqman on 2008-01-04
Sorry to be a pain, but are you *sure* there was nothing in your BIOS about fans? It should be in there somewhere. Any idea what flavour BIOS it is?

---

### Post by Tyke91 on 2008-01-04
test to see if all your fans are working in windows, then check to see if they are running in linux. 

if both are the same, it's purely an issue of the fans themselves or the BIOS, if windows is better than ubuntu, then it's the problem of the OS.

in the mean time... bring an icepack with you and your computer? :)

---

### Post by ZOOstation on 2008-01-04
For future reference, Windows is gone. Windows was erased when I installed Ubuntu.

---

### Post by ZOOstation on 2008-01-04
Paqman -- my BIOS is called "Phoenix cME FirstBIOS Pro Setup Utility" and I assume it came standard with the laptop (HP Pavilion zd8000). I have a feeling I used it once or twice back when I was on Windows, but couldn't tell you anything for sure.

---

### Post by MasterAlone on 2008-01-04
As far as fan control goes in the bios, on laptops it often isn't there because it is handled by temp sensors in a laptop but it is in the bios of a desktop.

Some laptops have a stepping system on their fans which means that when a certain temp is reached, the first fan kicks in, if it isn't enough to take care of the heat then the second fan kicks in and so on.  Other laptops kick them all in at once, cool it quickly and then kick off.

Either way, if one isn't working it is putting a bigger load on the other two.  I would suspect that with one not working, one not working up to par and one working that you have had one fan fail, one is starting to fail and the other one is trying to do all the work.

Just like the power supply built into a desktop, the dc converter you use to plug into 110 and run the laptop can also fail and not let enough power through to operate everything including the fans.

IMHO, you should check your power supply first or have it professionally done and if it is up to snuff, then you probably have a problem with fans failing.

---

### Post by ZOOstation on 2008-01-04
Pretty sure the power supply is okay. I guess I'll bring it to the shop for fan maintenance then.

Further suggestions are still welcome.

---

### Post by ryanVickers on 2008-01-05
just thought of something - if it's a laptop, where are you keeping it? are you blocking any heat/fan areas?  are you covering the keyboard? ;)

---

### Post by malcolmx82 on 2008-01-13
> "hardware-monitor" to be exact, - add it to the panel - at the bottom of the "add to panel" list window thing ...
you may also need libsensors3 and lm-sensors

hi...
i've got a problem of overheating and i'd like to monitor it...
i added the hardware monitor applet but i cannot change the settings as far as temperature is concerned because it says there are no sensors detected...what shall i do?

---

### Post by ZOOstation on 2008-01-25
Just got my computer back from the mysterious computer repair people. They replaced the fans and it works better than ever now! So I guess it was hardware all along? Whatever. Case closed.

---

