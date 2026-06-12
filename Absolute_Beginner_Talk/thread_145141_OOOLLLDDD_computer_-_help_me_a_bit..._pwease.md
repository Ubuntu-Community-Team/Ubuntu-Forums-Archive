---
title: "OOOLLLDDD computer - help me a bit... pwease?"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2006-03-15
OK... So today this counsoler guy at school gave me this reeeal old laptop. It's got Windows 2000 installed in it, but really, I don't want to bother with it - seeing how it's SO FREAKIN SLOW. This computer is just right for Ubuntu 64-bit, though.

But the thing is, I can't get the boot CD to run with it. I tried looking through the menus when I press F2 at the begining and all I got was this:

[b]Standard CMOS Setup
Advanced CMOS Setup
Power Management Setup
Peripheral Setup

Change User Password
Change Supervisor Password

Auto Configuration with Defaults

Save Settings and Exit
Exit Without Saving[/b]

...So... I take a gander in the Standard CMOS Setup, nothing about booting.

I go to Advanced CMOS and find:

**BootUp Sequence** - It says A:,C:...?
[b]Plug and Play Awar O/S
NumLock (at BOOT)
Keyboard Auto-repeat Rate
Keyboard Auto-repeat Delay
Password Check[/b]

---

### Post by Aine on 2006-03-15
What happens when you hit F12 on boot?

---

### Post by SZF2001 on 2006-03-15
...Nothing...

But when Windows started booting it said for some options press F8 (kinda just noticed this). It goes on to say:

[b]Safe Mode
Safe Mode with Networking
Safe Mode with Command Prompt

Enable Boot Logging
Enable VGA Mode
Last Known Good Configuration
Directory Services Restore Mode (Windows 2000 domain controllers only)
Debugging Mode

Boot Normally[/b]

Interesting, eh.

---

### Post by FizDev on 2006-03-15
[QUOTE=SZF2001]
**BootUp Sequence** - It says A:,C:...?
[/QUOTE]

Is there something about a D: or a E: (well the letter representing you cd drive under windows)? Put it at the beginning, or at least before the C:, that way, it should boot the cdrom first instead of your harddrive.

---

### Post by SZF2001 on 2006-03-15
OK, so I put A: in first.

It's wierd though... I let it run, I can tell the CD is read because of the noise it makes... Does the boot up, shows this NEC screen than starts all over again.

---

### Post by woedend on 2006-03-15
fizdev has it. boot sequence goes through the drives in that order.  if it says A C then it tries a floppy first, the boots from hard drive.  You need to find out the drive letter of the cd rom(from windows).  90% of the time it'll be D:\, although ive seen E and Q before.  Just add that after or instead of A, but before C

---

### Post by patrick87 on 2006-03-15
finally.. a topic im good with.. lol


um.. with windows 2000, i BELIEVE the command is F11 not F12.. and it can quite possibly be F2..

Honestly..i thought it was F12 myself. Please check and see if AS SOON AS IT SHOWS SUMTHING ON THE SCREEN.. if it says something about that. Unfortunately on some machines, such as my AMD 2000+'s system, to enter that area u must hit the F11 button in like... 2 seconds or it boots up to the OS. 

As i think about this more.... the bios sound like they need flashed (updated) Most current bios will not say boot to A: C: E:   etc.. and give that order.. it usually will identify exactly what each item is.

hope this might help a little.. its kinda hard when i dont have 2000 to look at right here lol  used to though :D

---

### Post by SZF2001 on 2006-03-15
[QUOTE=woedend]fizdev has it. boot sequence goes through the drives in that order.  if it says A C then it tries a floppy first, the boots from hard drive.  You need to find out the drive letter of the cd rom(from windows).  90% of the time it'll be D:\, although ive seen E and Q before.  Just add that after or instead of A, but before C[/QUOTE]
I can't just *change* it to read D:/, though... The only options I have are A: and C:.

This computer was all funky wired up to a network... God, man, I need to find the old techie or something to get rid of all that crap.

---

### Post by jam'ez on 2006-03-15
hmmm makes me wonder. is the cd drive working fine? go into windows and have alook if it is responding ok etc...
otherwise you should be able to cirle arround what drive to boot off, or select what order yourself!

---

### Post by SZF2001 on 2006-03-15
Hm...

I THINK it's working, not sure - I can see the lights flashing and when I put a CD it I can hear it reading it... I took it out and put it back in just to make sure, I'll check again now.

But anyway - I can't really log onto Windows, since this comp. was configured into a network and I need to get through to the tree where all of our names and stuff are.

---

### Post by SZF2001 on 2006-03-15
Sorry to double post, but I just thought of something.

I can take the hard drive out of my laptop in a snap. Real easy.

So I'm thinking... Maybe... Could I put that hard drive into my computer, run the Ubuntu boot up on the computer, put it on the laptop hard drive (wiping out Windows in the process), put the hard drive back into the hard drive and give it a try?

---

### Post by patrick87 on 2006-03-15
reading all of this now.. your best bet is probably to go to the guy who gave it to you.

He can atleast probably help get the network situtation outta the way. 

as for the cd drive, sounds like its not working to me.. a cd drive can spin and not work lol its a matter of if the ribbon cable is correctly seated, is it set to a slave of the harddrive or is it a master on its own cable...  things like that.

---

### Post by SZF2001 on 2006-03-15
Well, it's kida... an odd setup. I mean, the CD drive can be taken in and out like a snap, and you can put a floppy drive in it's place. It's... Old, like I've said.

---

### Post by Bagnaj97 on 2006-03-15
Maybe it was a mistake when you wrote the post, but with an old machine ubuntu 64bit will not work. Download the standard x86 version and try that.

---

### Post by SZF2001 on 2006-03-15
Isn't there only two kinds though? I have both the CDs - One says, "Version 5.10 for your PC" and the other says, "Version 5.10 for your 64-bit PC"... So... they both wouldn't work anyway?

---

### Post by patrick87 on 2006-03-15
of course not.. 64 bit version is for a 64 bit processor.. such as the AMD 64 

if this is a really old laptop... then its not going to be 64 bit ...lol not even close :P 64 bit technology is relatively new to the computer community, as it hasnt been around   THAT many years. If you processor is a pentium II or a low pentium III then u just want the x86  which is intel 32 bit processors..namely all of them im pretty sure..

---

### Post by twowheeler on 2006-03-15
I have an old computer that won't boot from the CD too.  The solution is to create a bootable GRUB floppy disk, boot from that, and use it to load up the CD.  There are lots of articles on this out there if you google for it.

There is also this: [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

---

### Post by SZF2001 on 2006-03-15
Ooooooh K patrick. Sorry... Didn't really realise what I was talking about.

And thanks twowheeler, I think I just might do that.

---

### Post by Ozitraveller on 2006-03-15
This might be useful to you!


[COLOR="Red"]SUCCESS - Breezy loaded on external USB drive ![/COLOR]
[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

[COLOR="Red"]Installing Debian Sarge from a USB memory stick (USB key)
[/COLOR][http://d-i.pascal.at/](http://d-i.pascal.at/)

---

### Post by SZF2001 on 2006-03-15
That would be awesome - except the comp. doesn't have USB. Thanks though...

So I made a GRUB floppy. Now... I checked it out, but I gotta know - how exactly am I going to do this? I have to switch out my floppy drive for the CD drive to work... Does it just install a boot thing or something?

---

### Post by jam'ez on 2006-03-16
you need to make the boot sequence so that it has A drive first (A drive is normally Floppy)
if the CD-Rom drive is working then you should be fine to install.
The thing u need to do is to get the x86 install. download it from here: [http://www.ubuntu.com/download](http://www.ubuntu.com/download)
make sure you download the pc x86, the 64bit WONT work on your pc as it is an old pc. then burn it to a CD-r
but i still think that your CD ROM drive isnt working. it can spin all it likes, but it may not read anything!!!

good luck

---

### Post by _simon_ on 2006-03-16
From what I'm reading you shouldn't need to change anything.

You already have the sequence right A: C:

A: in this case is whatever is in the bay i.e. floppy OR CD

So it sounds as though the drive is faulty. Either that or the cd you are using isn't actually bootable....

As has been said already, just because it makes a noise doesn't mean it works - that just means it has power.

---

### Post by Mustard on 2006-03-16
I've only been casually reading over this thread, so this might be unrelated, but have a look at this link..

[https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

---

### Post by MJSOnline on 2006-03-16
Hi there.  Have you had any joy in fixing this boot problem yet? M

---

### Post by jam'ez on 2006-03-16
yeah any luck so far if you are arround....

---

