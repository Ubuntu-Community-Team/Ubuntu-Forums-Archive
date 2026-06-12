---
title: "Ubuntu killed my iBook G4"
date: 2006-06-15
forum: Apple PPC Users
---

### Post by bennyp on 2006-06-15
I just installed Dapper yesterday on my 1.07GHz iBook G4. Today, it will not boot. When I left school, I suspended the machine by closing the lid, then disconnected the power cable, then went home.
When I arrived, I opened the lid, but the screen was blantk. It flashed for a second all white as I opened it, but by the time the lid was o.pen, the screen was totally blank. Not knowing what to do, I hard-rebooted by holding down the power button.

After rebooting, I went to enable my airport extreme card so I could go about my business on my computer. After a few minutes, the screen blanked (but I could see that the screen was still on) and I was again forced to hard reboot. 

After the second reboot, it took even less time for the screen to blank

on the third reboot, the boot menu did not even appear. one second after I press power, the back fan begins turns on and spins HARD, harder than it ever has before. The screen remains blank, and even holding down the power key does nothing.

I feel like I have no more options. Has Ubuntu destroyed my computer?

---

### Post by bruce89 on 2006-06-15
I doubt it, it will be a hardware issue.  Software doesn't have the habit of destoying hardware.

---

### Post by flapane on 2006-06-15
don't you have a macos partition to test it?

---

### Post by bennyp on 2006-06-15
If it's a hardware issue, then why did this only happen the day after I installed new software?

I do have a mac os partition, but, you see - the problem is that the machine does not boot at all. Not into Yaboot, not even into the firmware, as far as I can tell.. as soon as I press power, the fan and hard disk start spinning and that's it....


this sucks!

---

### Post by tidris on 2006-06-15
Are you sure the ibook suspended when you closed the lid? I have read complaints about that in other threads. If the machine didn't really suspend, and since you disconnected the power cable, the battery would have discharged completely during the  night. This might be totally dumb question, but do you still have this problem if the power cable is connected to the ibook?

---

### Post by bennyp on 2006-06-15
The computer did suspend - the light was on at least
but it was not left overnight, and the battery is not just drained. I suspended it not even 2 hours ago, and it's now plugged in. The problem does not go away, and it seems now that I cannot even get it to reboot
THere is no way for me to get the fan to stop spinning, short of pulling out the battery, which i REALLY don't want to do.....

---

### Post by anindya_m on 2006-06-15
Hi,
     Can you try the following thing. While the machine is on see if it will let you insert your Mac OS X cd. If the disc goes in next restart (power button) and this time press and hold down the "C" key. This will cause the system to boot from CD. If it starts up from Mac Os cd the hardware is probably fine.

regards,
Anindya

---

### Post by bennyp on 2006-06-15
THe system doesn't boot even get that far.... the screen does not even turn on...

---

### Post by Slicedbread on 2006-06-15
The screen doesnt turn on and fans are just spinning? Sounds like dead hardware:maybe RAM, Motherboard, or CPU.

---

### Post by Jasper Houtman on 2006-06-15
Did you try removing the battery and booting up without the battery in the Ibook?

Had the same kind of problem with my laptop, and that fixed it.

Put the battery back in later and let it charge completely (laptop switched of, charge only).

Worked fine after that, never had any problems again.

No idea what caused it though.

---

### Post by bennyp on 2006-06-15
no good...

Yes, Ubuntu certainly and absolutely destoyed my iBook... it is now a useless mass of garbage that will require possibly great deals of money to repair.

Thank you all for your help, I will never install linux on apple hardware ever again.

This SUCKS!

---

### Post by Jasper Houtman on 2006-06-15
Your anger and frustration are understandable, but it is highly unlikely linux (ubuntu, etc) is to blame for your system crashing.

First of all linux runs fine on thousents of ibooks, so why haven't they all crashed?

Software cannot destroy hardware, if it could then we would be threatened by computer destroying trojans etc (and there are none)

If and when you turn your Ibook in for repair I am sure they'll find a hardware failure. 

I know we will probably not be able to convince you to try Ubuntu again, but I for one love this OS and hope you'll give it another try.

I wish you the best of luck in getting your Ibook back in working order (hopefully at minimal costs).

---

### Post by anindya_m on 2006-06-15
I agree with Jasper. I have tried linux on powerbooks and it works fine. Just one thing: you mentioned you moved your computer after closing the lid. Are you sure it really did sleep? One (scary) possibility is that it might have been on while you put it in a backpack or some bag, which might cause overheating. I hope that's not the case. I have this worry whenever I carry my laptop, and I double-check every time.

One last check: Can you try the key combination: **apple-option-O-F** immediately after powering it on. This enters the firmware and you should (I hope) get a prompt. It's easy to miss the window so try it a few times.

---

### Post by eidex on 2006-06-15
apple seems to have serious problems with the quality of their products, my first ibook g3 800 died twice (logicboard was dead, i never had linux on it), the ibook i am currently working with (g4, 12000) had to be repaired 3 times in 2 monthes, again logicboard problems, they replaced it twice.

some models (depending on their serial number) have extended warranty because of this, search some apple forums (or on the apple homepage) for more information


anyway, good luck

---

### Post by bennyp on 2006-06-15
My reasons for believing that installing ubuntu were directly related to the downfall of my hardware:
A) if the machine DID overheat because it wasn't suspended, then it's a software problem, as the software failed to suspend tha machine
B) If it's the airport firmware that I loaded that killed the beast, then it's also a software issue

either way less one laptop now, and it happened RIGHT after I installed ubuntu - what else could it be?

Don't get me wrong, I like ubuntu. I wouldn't have installed it otherwise, but it definately killed my laptop.

---

### Post by tidris on 2006-06-15
[QUOTE=bennyp]
 - what else could it be?
[/QUOTE]
Faulty electronic components. Resistors, capacitors, inductors, transistors, LEDs, integrated circuits, lcd screens, hard disks, they are all known to fail unexpectedly. Ask any computer repair person.

---

### Post by Ptero-4 on 2006-06-16
Can you press alt right after turning it on. This bypasses whatever bootloader (crapboot, elilo, OSX BootX, etc) that happens to be in your HD and allows you to put your OSX Cd in the drive and install OSX. Also the fans is b/c the G4 iBooks and G5 iMacs use software based thermal control which is based on propietary drivers not available for Linux, raw Darwin or OS9. The blank screen is obviously X11 misconfiguration. And it can also be a overheated logicboard, those latter iBooks/PowerBooks seem to have lots of logicboard issues. But one thing I tell you out of experience. Linux runs quite good in Apple hardware, in fact Apple hardware is far better at running linux than any cheap x86 PC from wallmart's

---

### Post by ssam on 2006-06-19
have you tried reseting the PRAM and PMU?

[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)
[http://docs.info.apple.com/article.html?artnum=14449](http://docs.info.apple.com/article.html?artnum=14449)

---

### Post by bennyp on 2006-06-19
I took my book to the apple store, and the techs there confirmed that it was the logic board that just gave out. I think the most plausible theory was that the thing over heated.

So rather than spending $1000 to get a new logic board, I'm going to spend about the same and get a macbook.

---

### Post by s_groening on 2006-06-30
I have tried the exact same thing on my iBook G4 12" 1 GHz!!!

...So this guy is not kidding! Ubuntu effectively killed off my otherwise completely stable working machine by introducing the exact same symptoms as described here. As I originally booted the iBook G4 from the Ubuntu cd, the graphics went totally crazy, weird colours and it even made it impossible to turn off the computer. 

Now, the screen goes black on startup and either the fans spin like a G5 in single user mode or it boots Mac OS X (now the only system on it now after changing my hard drive which also did not like the trip to linux land and answered by throwing in some dead sectors to the mixture...) in complete blackness and I am then able to turn it off as normally but It can go as many as 10 attempts to get the screen up and running...

Since this adventure, I have not been able to let the iBook go to sleep, wake it from sleep or even from a black screen caused by the power management....

Please do not tell med this is a hardware problem that has always existed and that  Linux works soooo properly that it is only thanks to Apples many workarounds that Mac OS X happens to have worked flawlessly before and up untill  this day.... I admit software does not have the habit of destroying hardware, but something definately went *terribly wrong* here....

---

### Post by 3rdalbum on 2006-07-01
Software cannot destroy hardware. That is simply irrefutable. Besides, I talked to a guy at an Applecenter near us, and he told me that similar things happen to iMacs (he was surprised it hadn't happened to mine). This was before Ubuntu was ever installed on my computer. I doubt enough people run Linux on G3 iMacs in my hometown for this guy to have seen many cases of Linux-related hardware destruction!

---

### Post by eidex on 2006-07-02
why are you so sure that software can't destroy hardware. eg in dapper the fan control (therm_adt746x) is not installed by default (dont know if that is already patched, i fixed it myself and i bet a lot of users didnt), and overheating can result in damaged hardware...

---

### Post by 3rdalbum on 2006-07-02
[QUOTE=eidex]why are you so sure that software can't destroy hardware. eg in dapper the fan control (therm_adt746x) is not installed by default (dont know if that is already patched, i fixed it myself and i bet a lot of users didnt), and overheating can result in damaged hardware...[/QUOTE]

That would have to be the only example, unless you get into malicious behaviour. (e.g. writing constantly to flash drives until they fail, turning the monitor on and off to destroy the tube... you know, things that viruses might do)

---

### Post by benoitc on 2006-07-02
[QUOTE=3rdalbum]That would have to be the only example, unless you get into malicious behaviour. (e.g. writing constantly to flash drives until they fail, turning the monitor on and off to destroy the tube... you know, things that viruses might do)[/QUOTE]

Off course software can kill hardware. Kernel is playing with hardware, remember ? And X11 drivers call directly hardware even by bypassing the kernel when they need it. So yes software can damage hardware obviously. And this example remember me what happened to my tibook 1ghz with a gentoo install that kill the display. So maybe this bug is coming back ?

---

### Post by LettuceandPickles on 2006-07-03
[QUOTE=bennyp]I took my book to the apple store, and the techs there confirmed that it was the logic board that just gave out. I think the most plausible theory was that the thing over heated.

So rather than spending $1000 to get a new logic board, I'm going to spend about the same and get a macbook.[/QUOTE]

This is certainly false.  

A hardware repair on an Apple portable out of warranty is a structured service and, absent accidental damage, the cost would be less than a third of what is described to get a main logic board replaced. (I've had this done on another machine.)

Hardware fails.  It was ALWAYS working before it failed.  That's how you know it failed.

That said, Apple's hardware is the equal of, and generally better than, any other large manufacturer's hardware.  Period. Apocryphal stories notwithstanding, survey after survey after survey bears this out.

Try this:

Plug the iBook in.

Hold down shift-option-apple-power

Wait for a tone (this may take twenty seconds or so)

Wait ten to fifteen seconds.

Press power.

If you don't boot (or hear the tone) the tech at the Apple Store was probably correct.  The hardware is failed.

Hardware fails.  Eventually, all hardware fails.

Certainly bad power/fan management could overheat the machine, but it's highly unlikely in the timeframe you describe.  HIGHLY unlikely.

As for me, haven't turned my iBook G3 off (suspend?  yes) in more than a week.  As I did with Mac OS I do with Ubuntu; I don't turn it off.

I'm still here.

---

### Post by Peter76 on 2006-07-03
I have an iBook g3 900, where I have just had the motherboard replaced; luckily this was still under apples extended guarantee ( apple video bug ). 
The thing I'm noticing still though, that the iBook runs extremely hot ( you can barely touch it now and again ) under Ubuntu. It then takes forever for the fan to go on. The strange thing is this does not only happen under high load. I'm thinking about installing OSX again to compare if that runs as hot as well. As far as I can remember it didn't, but I want to know for sure. Anybody else having things like this????

---

### Post by Peter76 on 2006-07-03
Ok, did some searching around and found this in the archives:

[http://www.ubuntuforums.org/archive/index.php/t-12388.html](http://www.ubuntuforums.org/archive/index.php/t-12388.html)

My output from hddtemp = 48 degrees; this is hot!!!!
I haven't been doing anything heavy; what is going on here?????

---

### Post by OpenMinded on 2006-07-14
Four all you people having a hard time with your fan, I am having the same problem with two G4 800 Mhz ibooks.
1 i bought like this, one went like that when i changed the display.
This has NOTHING to do with UBUNTU!
This is purely a hardware problem on the Logic board.
I found this :
[http://guides.macrumors.com/Talk:iBook_logic_board](http://guides.macrumors.com/Talk:iBook_logic_board)
.
Must be purely coïncidental that this happened after an Ubuntu boot?
These things just boot any once in a while now, seems 1 goes on when I firmly press around the chips that are cooled.
Can't find any loose contact...
If any1  has a solution, please post !

---

### Post by thyberthpithe on 2006-08-27
> **3rdalbum said:**
> Software cannot destroy hardware. That is simply irrefutable.

Whether or not it is the case here software can most definitely destroy hardware.  I work in embedded device development and we often have to work around issues to protect hardware.  

Yes just running some code on a processor will not directly kill anything but if that code plays with registers in hardware it can.  If you don't believe me I can give you a program that will blow up your monitor.  It will drive it outside of the sync ranges and that will most definitely destroy it.

Screens can be driven at the wrong rates, hard drives can over heat, processors can over heat, software controlled voltage systems can produce incorrect voltages.  For example hard drive DVRs have sophisticated temperature control systems since their drives are used more often than a PC for example.  If that code was buggy it *will* kill the hard drive.  iPods use a software cache because continually driving the hard drive in its small enclosure would destroy it.

If there was a bug and the laptop did not properly suspend it *would* cause the motherboard to over heat and kill it.  So the parent poster is probably correct in that this would not have happened on OS-X purely because Apple will have done *loads* of testing...

---

### Post by bennyp on 2006-08-27
Hey All!

So I got my new MacBook, and am now installing ubuntu into a virtual machine over OS X. I think that's the safest route, as I still believe that it's more than a coincedence that my computer just up and died right after installing ubu. Can I prove it? No. Does it really matter that much? Not for me, anymore.

The logic board definately failed, that's for sure. Two stores (apple and an independant store) verified that and both quoted $1000 for the fix.

I hope everyone else with hardware issues can get them fixed up. Ubuntu's still a pretty good distro, and I still recommend it to anyone wanting to try GNU/Linux. I probably wouldn't recommend it to an iBook owner, though. Cheers.

---

