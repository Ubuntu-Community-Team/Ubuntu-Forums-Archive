---
title: "Ubuntu 6.10 causes even Bios to not start"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by gloomdragon on 2006-11-01
I run an MSI with an AMD MT37. I have windows XP and installed Ubuntu 6.10, my first try at a Linux.
 In retrospect the problem started still with the Live CD but I didn't figure out it was Linux messing up already my machine. 

Basically, after I shutting down (and pressing enter doesn't work but I know that then one is supposed to be able to just power down so I did), when I switch it back on I just get the laptop power buttons lighting up, a bit of noise on the cd-rom even if it's empty and power out. And immediately power on again, light on (screen stays black), bit of noise on the CD-ROM and out again. And it just stays like that until I press the power button long enough to shut it down completely. 
I does this always until I take the battery out and unplug it from the power supply. Then I can restart normally.

Considering the amount of other extremely annoying bugs which I'm not gonna get into here (ok, just for example the lack of access to windows partitions and the discontinuing of the only tool to allow this in the new Gnome), I've decided to just get rid of my Linux partition and swallow my pride and live with Windows with all its faults because at least its for actual normal humans, not programmers like this stuff (and I studied some Unix myself). Sorry, If I sound bitter but 3 days of frustrations with Edgy eft are a bit too m~uch to just keep in.

So my only 2 questions are:

Will this bug have harmed my machine (I just bought this new machine last week so I could get a quick replacement still instead of a month in tech support)

How do I get rid of my ubuntu created partition and turn them back into NTFS so I can use my whole hard drive again? Is a low level format and full reinstall of everything the only way?

Cheers and good luck. Maybe I'll try linux again someday if it gets user friendlier

---

### Post by mattskr on 2006-11-01
What type of laptop is it?

---

### Post by Qrk on 2006-11-01
Without knowing which laptop its hard to say, but I believe some MSI laptops have a bug in their BIOS which prevents them from taking advantage of acpi.

I wish I knew more, I only know that when I was considering purchasing an MSI laptop, I was told to stay away from this issue.

---

### Post by podunk on 2006-11-01
There is nothing any OS can do to your BIOS, if your computer won't boot into BIOS that is a hardware problem. You might want to read your manual and see if there is a user option to clear the CMOS (sorry to do the read the manual thing), if not or if so it doesn't help I'd return it.

About Edgy EFT - in the forums sticky it says in big red letters:
> 
Also note that Edgy 6.10 is considered a development platform for testing new ideas,and technology. Use of this version,and coming versions there after are at your own risk. 
 

I'm an Alpha pre-release user, I shouldn't be trying to use development software until I've developed some myself. :) Once your computer is fixed why don't you give Dapper Drake (6.06 LTS) a try?

You can use the Windows XP disk tools to change your Linux partition back to ntfs very easily.

---

### Post by gloomdragon on 2006-11-01
its an MSI m655. AMD turion mt37 100Gb HDD 1g ram
oh yeah, ATI radeon 256 Mb dedicated and ralink wireless ethernet

---

### Post by JayTee on 2006-11-01
Try installing Dapper instead of Edgy. Dapper is very stable and should work fine on your laptop. No OS should be able to affect your computer's BIOS as you've described. Only a program deliberately written to write to the flash memory of your BIOS would do that and the manufacturer protects that with a key to prevent trojans and viruses from overwriting flash BIOS. If your laptop is new enough, bring it back and get another and then try it with Dapper 6.06 instead.

---

### Post by gloomdragon on 2006-11-01
tried the dapper livecd last week but couldn't get it installed because it gave an IO error with the APICs. I know I could disable them, I did that to try the livecd and it worked fine but since I couldn't figure out if the APICs would be necessry for something I stayed away from doing it permanently. That's why I was happy to see 6.10 not having any issues with that for some reason. At least it didn't complain about it.
Maybe it is all about those ACIPs

I don't think it is hardware I'm afraid. Though I'm no hardware specialist. The Bios seems fine. It just booted fine a bunch of times from Windows while installing some utilities. I saw another thread with someone having a similar prob earlier in september. He tried a bunch of things at the same time and in the end the computer miraculously ressuscitated and worked fine since. One of things he did was to just unplug it from the power. And this seems to have done the trick for me. Except the prob returns when I load ubuntu.
Anyhow, bringing it to the shop tomorrow just in case.

Anyhow, got my HDD back. Cheers for the advice. 

While I'm at it, I think this MSI is actually manufactured in an ASUS plant. My brother uses an ASUS for work that even looks the same in many respects. Would this issue be out for Asus machines as well (in the odd case that I get my money back or something :-) )

Anyhow, thanks and sorry for blowing up earlier

---

### Post by mattskr on 2006-11-01
Some AMD ASUS boards have problems with Linux. It's the APIC problems. Check MSI's website for bios updates if you haven't already because some of the ASUS boards are have BIOS updates listedwhich says "Fixes Linux Compatability Issue"

My board's BIOS has not got an update yet so I boot with the "noapic" option, so far everything works fine. Without that option both Dapper and Edgy, live or installed will crash on booting.

---

### Post by gloomdragon on 2006-11-02
You are probably right. So, no Edgy nor Dapper for my machine because I can't find any patches for the problem on MSI's webpage.
I supppose this will affect Kubuntu too won't it? Or is it just Gnome that will crash?

Thanks

---

### Post by bigken on 2006-11-02
as far as the bois issue goes ie the laptop not booting too the bios is a hardware failure nothing to do with linux its sometimes a checksum error  in which case  you would need to  reset the  cmos  ;)

---

### Post by IMS3 on 2006-11-02
I have a similar problem with Xubuntu 6.10 using a Compaq nx6325.

I first went into the bios before installing XP.

Then installed Xubuntu over the formatted XP drive.

Ever since installing Xubuntu Edgy I can't seem to get into the BIOS.

Everything else in Edgy seems to work fine.

Btw, I have only had the laptop since yesterday.

Doesn't seem to be a hardware issue as it worked the day before when XP was installed.

It also seems to wait a few seconds when switched on showing 2 options,
F9 For BIOS
F10 For something else

Before the screen for choosing the OS comes up.

Any ideas?

---

### Post by bigken on 2006-11-06
F10 might be boot options or to load the restore ghost image ;)

---

### Post by tjeerdsma on 2006-11-06
When I want to run multiple OS's on my laptop, I use Virtual PC from Microjunk. It lets you mess around with any other OS you want without screwing up your XP machine.

---

### Post by IMS3 on 2006-11-08
Got the BIOS working.

The key to use is F10 and has to be pressed repeatedly before GRUB starts to load up.

Just before grub loads, the BIOS is loaded.

It used to load immediately with Windows by pressing the F10 key once.

---

### Post by dannyboy79 on 2006-11-08
it looks like you figured it out but I wanted to inform you that an os installed has NOTHING TO DO WITH THE BIOS. the bios is something that's run even before the os runs so there's no way the os could affect this.

---

