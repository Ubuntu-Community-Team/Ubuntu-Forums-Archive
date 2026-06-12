---
title: "Laptop battery 238760 hours 35 minutes remaining!"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by DaraJava on 2007-12-01
The estimation for my battery is way off:

[IMG]http://i218.photobucket.com/albums/cc189/DaraJava/Screenshot-5.png[/IMG]

I dont know why this happens. I don't really mind too much that this is happening (It *is* pretty cool to show other people :lolflag: ) But I'm just wondering why it happens. Any help would be appreciated, thanks,

DaraJava


P.S This is not a prank or anything.

---

### Post by red_Marvin on 2007-12-01
I'm taking a wild guess here, but it might be that it checks the current battery drain speed and then estimates the remaining time based on a *linear* discharge rate, but in reality the rate is very slow in the beginning and then speeding up.

---

### Post by DaraJava on 2007-12-01
It used to be OK though. Just recently it started going like that. Also, sometimes the estimated battery life goes to the millions of hours as it discharges further, not just the hundreds of thousands. It doesn't seem to make sense. 

Oh, and when I use

```

sudo acpi -V

```

It gives me an accurate reading:

```

     Battery 1: discharging, 49%, 03:02:53 remaining
     Thermal 1: ok, 43.0 degrees C
  AC Adapter 1: off-line

```

---

### Post by Paulmd on 2007-12-02
> **DaraJava said:**
> It used to be OK though. Just recently it started going like that. Also, sometimes the estimated battery life goes to the millions of hours as it discharges further, not just the hundreds of thousands. It doesn't seem to make sense. 

Oh, and when I use

```

sudo acpi -V

```

It gives me an accurate reading:

```

     Battery 1: discharging, 49%, 03:02:53 remaining
     Thermal 1: ok, 43.0 degrees C
  AC Adapter 1: off-line

```


Either:

A) Your battery is bad
B) The Battery Controller is bad
C) There is something wrong with the applet. 

If you have access to a different battery, try that. If you get reasonable readings, you have a bad battery.

Since it used to work fine,  I bet the applet is OK.

If you DO have a bad battery or battery controller, this is more than an amusing glitch. It is potentially very bad for the laptop. It's better to run with NO battery than a bad battery.

---

### Post by PointyWombat on 2007-12-02
because acpi shows correct information, I suspect the applet is at fault.

---

### Post by PointyWombat on 2007-12-02
Hmm.. maybe it is the battery, read this FAQ for the applet itself..

[http://live.gnome.org/GnomePowerManager/FAQ#head-48610fc676fa0bbd056b4eb3d60c1dfdc646125b](http://live.gnome.org/GnomePowerManager/FAQ#head-48610fc676fa0bbd056b4eb3d60c1dfdc646125b)

---

### Post by DaraJava on 2007-12-02
No, no. It's not the battery thankfully. I just tried it on a windowze machine. It gave an accurate reading. Whew! Also, I have another problem that could be related: my brightness on my laptop dimmed one day and the setting for brightness just disappeared. :confused: Haven't a clue how to fix this either. It could be related to the battery thing.

Thanks a million for all your help, this is such a great community.

---

### Post by DaraJava on 2007-12-02
Something weird just happened. I tried the other laptop battery in my laptop and it gave an accurate reading as well. I was expecting it to give me thousands of hours like it does for my battery. So the applet must not be at fault. I find it strange that my battery got a correct reading on the other laptop. Is my battery wrong? It's very hard to tell...

---

### Post by steveneddy on 2007-12-02
That must be a hydrogen cell battery. I need one of those for my lappie. 

:razz:

---

### Post by markp1989 on 2007-12-02
i would love to have that kind of power in my laptop lol

---

### Post by DaraJava on 2007-12-02
You can get them on the black market. Quite cheap too if you know the right people. :)

---

### Post by Paulmd on 2007-12-02
> **DaraJava said:**
> Something weird just happened. I tried the other laptop battery in my laptop and it gave an accurate reading as well. I was expecting it to give me thousands of hours like it does for my battery. So the applet must not be at fault. I find it strange that my battery got a correct reading on the other laptop. Is my battery wrong? It's very hard to tell...

You can try updating the BIOS, maybe it's a firmware bug with certain motels of battery under some circumstances.

---

### Post by DaraJava on 2007-12-03
> You can try updating the BIOS, maybe it's a firmware bug with certain motels of battery under some circumstances.

How would I go about in doing that? Would it involve modifying the hardware? My computer is brand new so I dont think the BIOS is out of date or anything.

---

### Post by quandary on 2007-12-03
> **DaraJava said:**
> How would I go about in doing that? Would it involve modifying the hardware? My computer is brand new so I dont think the BIOS is out of date or anything.

No, the BIOS itself is software, not hardware. You couldn't just update it, if it was otherwise...

But i strongly advise you not to update your BIOS. The chances that you do irreparable harm to your computer are far greater than the chances that you might get an accurate battery reading.

Besides, if the BIOS was incorrect, it would also be incorrect for windows, and probably for both accumulators, 
And that's not the case.

So, don't update your BIOS.

---

### Post by LowSky on 2007-12-03
use you computer a few time on just battery and let it drain til it dies

the applet needs to get used to the battery's regular cycle

---

### Post by DaraJava on 2007-12-03
> How would I go about in doing that? Would it involve modifying the hardware? My computer is brand new so I dont think the BIOS is out of date or anything.
No, the BIOS itself is software, not hardware. You couldn't just update it, if it was otherwise...

But i strongly advise you not to update your BIOS. The chances that you do irreparable harm to your computer are far greater than the chances that you might get an accurate battery reading.

Besides, if the BIOS was incorrect, it would also be incorrect for windows, and probably for both accumulators,
And that's not the case.

So, don't update your BIOS.

Ok i won't update my BIOS. Thanks. :)

> 
Use you computer a few time on just battery and let it drain til it dies

the applet needs to get used to the battery's regular cycle

It used to know my battery's regular cycle and give me an accurate reading. is there any way it could "forget"? But of course I'll try your suggestion. :) Thanks.

---

### Post by Paulmd on 2007-12-04
> **quandary said:**
> No, the BIOS itself is software, not hardware. You couldn't just update it, if it was otherwise...

That's wrong. The bios is firmware, that can be reprogrammed. It is an EEPROM. So yes, it IS hardware. But it is rewritable with software!

The method for updating a BIOS depends on the make and model of your machine. But there are 2 main ways: a program that is loaded onto a bootable floppy disk or CD, and WinPhlash. which is a program that runs in Windows. Sometimes there are programs that run in Windoes, to CREATE a bootable floppy.

> **quandary said:**
> 
But i strongly advise you not to update your BIOS. The chances that you do irreparable harm to your computer are far greater than the chances that you might get an accurate battery reading.


I have, as a pc technician literally updated hundreds of BIOSes, I have not once "bricked" a machine. There are safeguards, modern flash utilities will only allow a bios to be used that is compatible with the machine. Dell, Sony, HP, Compaq for sure use this method.  A lot of people are paranoid about this. It's an order of magnitude safer in a laptop, because the chances of losing power in the middle of the operation (which is what the paranoia is about) is much mitigated by the fact that the laptop has a battery.

Also, the harm is not irreparable. The factory can pull the old eeprom and replace it. So can others who specialize in this repair.

> **quandary said:**
>  Besides, if the BIOS was incorrect, it would also be incorrect for windows, and probably for both accumulators, 
And that's not the case.

So, don't update your BIOS.


That's not necessarily true.  It appears as if there at least 2 methods of getting the estimated battery life. If there is a glitch in one method, it may not be the one used by Windows.

Of course, you could just assume you have a bad battery, to be on the safe side.

---

### Post by DaraJava on 2007-12-04
I think it must be a bad battery because I tried a different battery in this laptop and it gave me a correct result. And your different methods idea makes sense as to why my battery got an accurate result on windows. 

I'll give the battery back to Dull and see what happens. If it returns with no success I will update my BIOS. 

Thank you for being so helpful.

P.S. Over the last few weeks my screen has dimmed. Could that be due to BIOS?

---

### Post by Paulmd on 2007-12-05
> **DaraJava said:**
> I think it must be a bad battery because I tried a different battery in this laptop and it gave me a correct result. And your different methods idea makes sense as to why my battery got an accurate result on windows. 

I'll give the battery back to Dull and see what happens. If it returns with no success I will update my BIOS. 

Thank you for being so helpful.

P.S. Over the last few weeks my screen has dimmed. Could that be due to BIOS?


Check here for updates:

[http://support.dell.com/](http://support.dell.com/)

Dell machines are one of the easiest to update BIOSes on. Dell has been known to warranty bios updates, (which is not universal among OEMs). Basically if you used their program to update the bios and it fails.... you can still send the thing back to Dell.

The PS...

It could be a power issue. Many machines run their screens dimmer on battery-only than on ac-only. On many dell machines, there is a setting in the bios to control this behavior. There is a chance that the 2 issues could be related. Not a high chance, but a chance.

(IIRC, to get into the bios of a dell machine, press f2 before the OS loads)


The other thing to do is to look for brightness/contrast sliders and controls. 

fn+arrow keys is a common one. But so is fn+some other function key

You got any other issues?

---

### Post by DaraJava on 2007-12-05
> Check here for updates:

[http://support.dell.com/](http://support.dell.com/)

Dell machines are one of the easiest to update BIOSes on. Dell has been known to warranty bios updates, (which is not universal among OEMs). Basically if you used their program to update the bios and it fails.... you can still send the thing back to Dell.

The PS...

It could be a power issue. Many machines run their screens dimmer on battery-only than on ac-only. On many dell machines, there is a setting in the bios to control this behavior. There is a chance that the 2 issues could be related. Not a high chance, but a chance.

(IIRC, to get into the bios of a dell machine, press f2 before the OS loads)


The other thing to do is to look for brightness/contrast sliders and controls.

fn+arrow keys is a common one. But so is fn+some other function key

You got any other issues?

Yeah the thing is that Fn + up/down used to work for the brightness settings and I'm assuming that the power slider used to work but it doesnt work now it has a sun icon and a little "mute" icon on it kinda the same as what happens when I mute the sound.

When I plug the AC adapter into my laptop the brightness doesn't change at all either. 

I'll look in the BIOS and see what I can find. Thank you.

---

### Post by Paulmd on 2007-12-05
> **DaraJava said:**
> Yeah the thing is that Fn + up/down used to work for the brightness settings and I'm assuming that the power slider used to work but it doesnt work now it has a sun icon and a little "mute" icon on it kinda the same as what happens when I mute the sound.

When I plug the AC adapter into my laptop the brightness doesn't change at all either. 

I'll look in the BIOS and see what I can find. Thank you.

Did you get one of those Dells with Ubuntu Pre-loaded?

If you did... I think I might send the entire machine back.

---

### Post by DaraJava on 2007-12-05
Nope. Vista pre-installed.

---

### Post by quandary on 2007-12-05
> **Paulmd said:**
> 
That's wrong. The bios is firmware, that can be reprogrammed. It is an EEPROM. So yes, it IS hardware. But it is rewritable with software!

Thanks for the correction. I know it's EEPROM. 
The point is, you also need a magnetic head to rewrite software on the HD.
So in the end, firmware is nothing else but software, so it doesn't really make sense to differentiate, because there isn't any conceptual difference. The only practical difference is, that if you trash your BIOS, you need special equipment or help from outside to rewrite it (which is what i call irreparable harm...  because getting a technician for some hours can be more expensive than just buy a new computer. perhaps i should call it 'total' damage instead of 'irreparable').

> 
The BIOS is firmware.... So yes, it IS hardware.

hmmm, is this just me, or does this sound like a contradiction?

> 
I have, as a pc technician literally updated hundreds of BIOSes, I have not once "bricked" a machine. There are safeguards, modern flash utilities will only allow a bios to be used that is compatible with the machine. Dell, Sony, HP, Compaq for sure use this method.  A lot of people are paranoid about this. It's an order of magnitude safer in a laptop, because the chances of losing power in the middle of the operation (which is what the paranoia is about) is much mitigated by the fact that the laptop has a battery.

OK, i agree with that. But the point is, you are a PC technician, and this is the 'absolute beginner' forum. 
So if he now goes and just updates his BIOS with a BIOS for the wrong machine, he has 'total' damage... And you can also get a corrupted download, if you don't CRC/MD5 check it. Again--> absolute beginner forum. 

> 
That's not necessarily true.  It appears as if there at least 2 methods of getting the estimated battery life. If there is a glitch in one method, it may not be the one used by Windows.

Of course, you could just assume you have a bad battery, to be on the safe side.

As you said, not necessarily, yes, but it's likely. 
And the last thing is exactly what I assume...

Besides, if you know the approximate maximum lifetime, and percent remaining shows ok, then why risking to damage your BIOS?

---

### Post by DaraJava on 2007-12-05
Oh no! You're fighting! :lolflag:

---

### Post by quandary on 2007-12-05
> **DaraJava said:**
> Oh no! You're fighting! :lolflag:

:lolflag:

But i'm staying nice ;-)

---

### Post by Paulmd on 2007-12-06
> **DaraJava said:**
> Oh no! You're fighting! :lolflag:

This isn't fighting. Fighting is where we insult each other. This is just a disagreement, on a perennial point of contention in tech circles.

---

### Post by Paulmd on 2007-12-06
> **quandary said:**
> Thanks for the correction. I know it's EEPROM. 
The point is, you also need a magnetic head to rewrite software on the HD.


On a hard drive, yes. EEPROMs are a different animal. Most commonly, they are written with a special device. But some, like the bios chips, are reprogrammable in-situ. Anyway, not a magnetic process. Nor is it on the hard drive. (there are eeproms on hard drive PCBs, but that's an entirely different discussion) 

> **quandary said:**
> 
So in the end, firmware is nothing else but software, so it doesn't really make sense to differentiate, because there isn't any conceptual difference. The only practical difference is, that if you trash your BIOS, you need special equipment or help from outside to rewrite it (which is what i call irreparable harm...  because getting a technician for some hours can be more expensive than just buy a new computer. perhaps i should call it 'total' damage instead of 'irreparable').

hmmm, is this just me, or does this sound like a contradiction?


While it's true that some repairs are non economical. But this is a class of repairs that everybody seems to think is non-economical, but turns out, on average to be way cheaper than replacing the machine.  So are broken DC jacks, which lots of small shops won't touch, but is one of MY specialties. 

Firmware is in a different class than software. Firmware is part of the piece of hardware itself. and may- or may not be rewritable. Usually stored on eproms, or eeproms, but again, not always. Most CD burners, for example have firmware that can be rewritten with an updating program. While most other devices like ethernet cards have firmware that cannot be changed short of desoldering the eprom and replacing it manually.

> **quandary said:**
> 
OK, i agree with that. But the point is, you are a PC technician, and this is the 'absolute beginner' forum. 
So if he now goes and just updates his BIOS with a BIOS for the wrong machine, he has 'total' damage... And you can also get a corrupted download, if you don't CRC/MD5 check it. Again--> absolute beginner forum. 


On a dell machine, which he has, it's one of several safeguards in the process.

First, the program checks that the CRC is correct.  Then It checks that the machine type is correct. On a laptop, it even checks that a battery is in the machine and reasonably charged. AND that it's plugged in to AC power. It also checks that the bios revision that you are updating to is higher than the one currently installed. The very last safeguard, is that a bios update rarely writes over the boot block portion of the bios. What that means, in practical terms is that even if everything else goes wrong, you can STILL boot to a floppy disk and re-flash. On a dell, it just isn't possible to update with a bios intended for a different dell, or different machine entirely.  


Other brands have similar safeguards,  in modern machines it is very difficult to accidentally update a machine with a bios not written for it (difficult, even to mis-flash on purpose). By modern I mean Pentium 2s, and higher. Even on earlier machines than that, mis-flashing is frequently  guarded against by the flashing utility itself.

Part of the reason there is so much disagreement on this issue is that different manufacturers have different policies on bios updates. MSI, for example has the Live Update program which treats bios updates like dental hygiene, to be done regularly, whilst other manufacturers are downright paranoid. At least one motherboard manufacturer practically encourages it.(DFI LANparty ) They actually shipped an eeprom puller with every motherboard, on the theory that you could send you eeprom back to the factory for warranty replacement.


> **quandary said:**
> 
As you said, not necessarily, yes, but it's likely. 
And the last thing is exactly what I assume...

Besides, if you know the approximate maximum lifetime, and percent remaining shows ok, then why risking to damage your BIOS?

A bad battery can slowly kill a machine. It's way bad. Because it usually finishes the deed once after the machine is well out of warranty, because people don't pick up on the little symptoms, and blame it on an OS glitch. I happen to know that Dell warranties bios updates, done with their tools, which are downloadable from their website. So in the unlikely event it DOES go wrong... he's covered. If it makes no difference, we assume its the battery, and return the battery, while it's under warranty, no permanent harm done to the machine. If it fixes the problem, Great!. But if ignored entirely, and the battery kills machine 2 years from now. He's not covered. A bit Machiavellian... but you asked. :)

---

### Post by DaraJava on 2007-12-06
> **Paulmd said:**
> This isn't fighting. Fighting is where we insult each other. This is just a disagreement, on a perennial point of contention in tech circles.

Yeah I know I was only joking. I just sent Dell an e-mail telling them what the story is.

---

### Post by DaraJava on 2007-12-06
Oh and the amount of hours seems to be getting lower. For example it is a 69% power now and its giving me 80,000 hours remaining. It used to be in the couple of hundred hours. Could it be slowly fixing itself?

---

### Post by DaraJava on 2007-12-07
OK. Dell responded and said to upgrade the BIOS. I downloaded the .exe from the Dell website and it wont open with WINE. I rang them up and they told me that they are working on an upgrade to work with Linux machines. 

Is there any way to make the executable file that I downloaded work or is there any other way to upgrade my BIOS? (I'm sorry Quandary but if Dell say to upgrade my BIOS then I think it's pretty safe because if I do brick my machine I'm pretty much covered by Dell.)

---

### Post by Paulmd on 2007-12-07
> **DaraJava said:**
> OK. Dell responded and said to upgrade the BIOS. I downloaded the .exe from the Dell website and it wont open with WINE. I rang them up and they told me that they are working on an upgrade to work with Linux machines. 

Is there any way to make the executable file that I downloaded work or is there any other way to upgrade my BIOS? (I'm sorry Quandary but if Dell say to upgrade my BIOS then I think it's pretty safe because if I do brick my machine I'm pretty much covered by Dell.)

What's the model # of the machine, so I can do more detailed checking?

Some of their exe programs just create a floppy disk, you can run them on a Windows machine, create the disk, and then insert it at boot time.

Others, more recent ones, are a winflash-hybrid, where the program copies the new bios to a specific region of memory (i think it's separate from the RAM, but I'm not all THAT sure), reboots your computer, and the program then runs at POST time. That kind, you need a Windows machine to run. There's a workaround. But it really is a WORKaround (you pull the hdd, install windows on a 2nd hdd, run the flash program, put back the linux hdd). 

I really think it's a bad idea to run a bios update program in WINE. You gotta run those on the platform they were intended for.

Dell has historically been pretty good about providing multiple options. I can do a bit of digging on this one, IF I have the model number. I can get you a definitive answer.

---

### Post by DaraJava on 2007-12-09
It's a Vostro 1000. I'm not sure if that's the model number but I'm not sure where to find it if it's not. lol

Thanks a million Paulmd.

---

### Post by Paulmd on 2007-12-09
> **DaraJava said:**
> It's a Vostro 1000. I'm not sure if that's the model number but I'm not sure where to find it if it's not. lol



Thanks a million Paulmd.

That model number will be just fine. The following directions pre-suppose that you have a floppy drive. And Access to a Windows machine with a floppy. You will not be updating the BIOS on THAT machine, just creating a boot floppy. (just to calm down whoever may be the owner of the Windows machine :)  )

IN windows:

Download THIS file: (WinVOST261.exe)

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R165211&SystemID=VOS_N_1000&servicetag=&os=BIOSA&osl=en&deviceid=15246&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=222387#3DOS](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R165211&SystemID=VOS_N_1000&servicetag=&os=BIOSA&osl=en&deviceid=15246&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=222387#3DOS)

Create a bootable DOS floppy disk.

[http://www.bootdisk.com/](http://www.bootdisk.com/)


[COLOR="Red"]Edit: Select the file that says "Driverless diskette for BIOS flashing

Run the program.
[/COLOR]

After the disk is created, copy the WinVOST261.exe to the floppy disk.

Verify that the file is there.

Insert the disk into your laptop, turn on the machine. It should then boot from the floppy disk.

When DOS is booted, type: WinVOST261 at the command prompt.

Follow the directions. Do not turn off or reboot the machine until prompted (Or you get a message that says that the bios update has been completed). Don't panic if the machine restarts on it's own (that's pretty normal). 

If you don't have a access to a Windows machine with a floppy, I should be able to create a disk image for you and post it on my website (direct link only), to be reproduced onto a floppy using dd.

If you don't have a floppy drive on your machine, it becomes more complicated, you will need to create a bootable CD, with the file on it. Some Windows based CD writing programs such as Nero have this functionality. Maybe you can con Dell into sending you a premade CD, (or  CD ISO if you have a burner).

I'm sure this is do-able in linux as well, It's just I haven't had to do it myself yet, And don't want to give you directions to a place I haven't been. Not on that topic anyway. :)

---

### Post by DaraJava on 2007-12-10
Thank you Paulmd. I do not have a floppy drive in my laptop and I dont know exactly what file to download from Bootdisk.com (I'm a bit of a n00B in this area.) 

I think I could do what you're saying on cd if I know what file to download. Thank you so much for your kindness and great answer,

DaraJava

---

### Post by Paulmd on 2007-12-11
> **DaraJava said:**
> Thank you Paulmd. I do not have a floppy drive in my laptop and I dont know exactly what file to download from Bootdisk.com (I'm a bit of a n00B in this area.) 

I think I could do what you're saying on cd if I know what file to download. Thank you so much for your kindness and great answer,

DaraJava

I will create a ISO image for you to burn onto a CD. Since you have no floppy drive, the bootdisk.com stuff is moot. 

I probably won't have the time to do this till Saturday.

---

### Post by DaraJava on 2007-12-12
Paulmd, you are a saint! Thank you so much. 

I heard a quote on this forum: "The true measure of a man is how he treats someone who can do him absolutely no good". You measure up very well! :lolflag:

Thanks again,

DaraJava

---

### Post by Paulmd on 2007-12-14
> **DaraJava said:**
> Paulmd, you are a saint! Thank you so much. 

I heard a quote on this forum: "The true measure of a man is how he treats someone who can do him absolutely no good". You measure up very well! :lolflag:

Thanks again,

DaraJava

You are very much welcome!

The ISO file is here.

[http://www.efn.org/~paulmd/Vostro1000.iso](http://www.efn.org/~paulmd/Vostro1000.iso)

This is a direct link, and it is the only way to get to that file.

step 0) save the file to disk.

Step 1) Burn it to a cd as an image. 
2) insert cd into computer (it looks like there is nothing on the CD, that's just fine, in this case!)

3) reboot the computer with the cd in the drive
4) you should be taken to a dos prompt
5) type dir (to see the name of the phlash program (it should be called phlash1~.exe... but just to be sure)
6) type phlash1~ 
6a) press enter
7) Sit back, arms crossed, and do nothing until prompted.

8) when the process is complete, remove the cd from the drive. You may have to enter the bios program and load default settings. and set the date and time.



Note: I cannot actually run this all the way through on my own computer, as it (correctly) tells me that the bios image is not for my computer. So at least that safeguard is still in place.

So this is for a Vostro 1000 ONLY.

If it doesn't LET you flash the bios. Give up, call Dell, make them do it. 


PS: just in case, print out the email from dell that said to flash the bios ;)

There were several obsticles to overcome, to create this image.

1) the Winvost621.exe program is too large to fit on a floppy.The advice on Dell's own website is wrong.

2) provided you get it on to a DOS bootable cd, Winvost621.exe cannot be run in DOS mode. (again, contrary to what dell's support website says)

3) to extract the image I and to run the program in windows mode, which extracted the winphlash program and the bios image. 

4) I had do find phlash16, the dos-mode version of winphlash. 

5) I found my usual bios flashing floppy from bootdisk.com, and copied phlash16 and the bios image to it.

6) rename flashabl.rom to bios.wph to make phlash16 happy.

7) used nero to create a bootable cd with a boot image from the floppy

8) tested the cd.

9) had nero create an image (stupid nero doesn't create isos)
10) find a program to convert nero's nrg to iso.
11) burn iso
12) test cd, again


All in all... Dell really should have actually provided a utility that can be run in dos mode.

---

### Post by DaraJava on 2007-12-16
It didn't work. My battery still shows a ridiculous reading and my screen is still dim. My laptop must be at fault. I'm going to send it back to Dell. The BIOS is 2.5.2 now. Is this correct? Did I upgrade properly? 

Also, my main user, dara, is weird. It's like it's in safe mode. There is no top or bottom panel and there are loads of error messages before it starts up. It takes about 5 mins to start up. Another user, tina, however, works fine. 

Thanks for your help,
Dara.

---

### Post by Paulmd on 2007-12-17
> **DaraJava said:**
> It didn't work. My battery still shows a ridiculous reading and my screen is still dim. My laptop must be at fault. I'm going to send it back to Dell. The BIOS is 2.5.2 now. Is this correct? Did I upgrade properly? 

Also, my main user, dara, is weird. It's like it's in safe mode. There is no top or bottom panel and there are loads of error messages before it starts up. It takes about 5 mins to start up. Another user, tina, however, works fine. 

Thanks for your help,
Dara.

What version was it before? 

The correct version should be 2.6.1. (A04)

You may want to burn the Dell Diagnostics ISO, to a cd, and run it through its paces.

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R153320&SystemID=VOS_N_1000&servicetag=&os=WLH&osl=en&deviceid=3841&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=2&libid=13&fileid=204528](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R153320&SystemID=VOS_N_1000&servicetag=&os=WLH&osl=en&deviceid=3841&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=2&libid=13&fileid=204528)


Or you can, justifiably, give up and send it back.

---

### Post by DaraJava on 2007-12-18
I think I might just give it back. Thanks for all your help.

---

