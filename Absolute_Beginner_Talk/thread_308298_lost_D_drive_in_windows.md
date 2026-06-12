---
title: "lost D: drive in windows"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by spar on 2006-11-27
Hi! First post here.

I installed ubuntu on a spare slave drive on my machine.  Now when I switch out the slave back to my original hard drive it wont let me boot into windows (because the OS choosing screen wont come up.)  I hope this makes since. ;) 

What should I do?

Thanks for replies, and happy hollidays.

---

### Post by Tarvok on 2006-11-27
Well, when you say "switch out," do you mean you physically remove one drive and attach the other? What's your setup, here? How are you switching between them?

---

### Post by jdong on 2006-11-27
GRUB must've installed itself to the MBR (Master Boot Record) on C:\. Now, you need to change that back to a windows MBR. The procedure to do this depends on what version of Windows you're running.

Which version of Windows is installed on C:?

---

### Post by Tarvok on 2006-11-27
Well, restoring the Windows MBR is one way to do it, but another (better, imo) way is to keep both hard drives attached, and edit grub's configuration file to include Windows. I can help with this, if I know which drive is which, and what is meant by "switching out."

---

### Post by jdong on 2006-11-27
> **Tarvok said:**
> Well, restoring the Windows MBR is one way to do it, but another (better, imo) way is to keep both hard drives attached, and edit grub's configuration file to include Windows. I can help with this, if I know which drive is which, and what is meant by "switching out."
I think what he's saying is that he has one spare HD slot in his system, where he swaps between a Ubuntu installed drive and some other hard drive. In which case, he either needs GRUB on his C:\ drive (which is a bit of work) or needs to instruct the Ubuntu installer to install grub to the slave drive and keep its paws off the Windows drive.

---

### Post by spar on 2006-11-27
yes, i physically changed out the drive.

let me try this more clearly.  i had 2 hard drives C and D.  C has windows, D has mp3s, videos, ect.

i thought i'd keep all the stuff on D in tact by switching out the D hard drive with a spare one I had lieing around.

so i installed on the junker hard drive, and now i can't switch back.


i think Tarvok might have the right idea.

---

### Post by spar on 2006-11-27
> **jdong said:**
> I think what he's saying is that he has one spare HD slot in his system, where he swaps between a Ubuntu installed drive and some other hard drive. In which case, he either needs GRUB on his C:\ drive (which is a bit of work) or needs to instruct the Ubuntu installer to install grub to the slave drive and keep its paws off the Windows drive.


well so does C:\ drive have something on it that makes it look for GRUB on D: ?

---

### Post by Tarvok on 2006-11-27
Well, it looks like when you installed Ubuntu, it stuck grub in the master boot record, which is what it's supposed to do, normally. So, when you turn your computer on, the MBR points to where grub is installed on your Ubuntu drive. When it can't find it, it gets very confused, and quits working.

One way to fix this is dependent on what version of Windows you're running. If its XP, you can stick your Windows CD into the drive, boot to it, and there's a command you can run in restore mode that will fix your mbr. Actually, I think it might be a simple as "fixmbr", but I'm not sure.

Now I'm getting the idea that you would rather put that other drive with all your media on it back (understandable). So, before I go and google up the wrong answer, which Windows is on your primary drive (hda, in Linux speak)?

BTW, if you've got enough space in your comp, you could hook all three up. ;)

---

### Post by spar on 2006-11-27
thank you for your reply tavok.

i wish i could hook up all 3.  they are all ide hard drives and i can only have 2 hooked up.  i think my motherboard supports 2 ide, and 4 ata drives.

and yes you are correct i have windows xp profesional service pack 2 (for whats its worth:p )

---

### Post by spar on 2006-11-27
google turned up this:

> Repairs the master boot record of the boot disk. The fixmbr command is only available when you are using the Recovery Console

fixmbr [device_name]

Parameter

device_name

The device (drive) on which you want to write a new master boot record. The name can be obtained from the output of the map command. An example of a device name is:

\Device\HardDisk0.

Example

The following example writes a new master boot record to the device specified:

fixmbr \Device\HardDisk0

so should i run it on "harddisk0"?

---

### Post by jdong on 2006-11-27
Yes, run fixmbr on C: and at least Windows will boot.

Then we need to think of some sane way for you to do your hot-swapping Linux configuration.

Does your BIOS have a boot menu that allows you to press a key to bring up a list of disks to boot from?

If so, you can install GRUB on the Ubuntu drive's MBR, and use your BIOS boot menu key to select the Ubuntu drive.

---

### Post by Tarvok on 2006-11-27
That looks right to me. I've never done that before. However, even "harddisk0" may not be necessary, according to [this thread]("http://www.techzonez.com/forums/showthread.php?t=3975").

Let me know how it turns out. I may have to do the same on my parents' computer, in the near future.

---

### Post by spar on 2006-11-28
great success! (borat voice)

got my old drive to work. i used that link you suplied Tarvok.  thank you too jdong.

i think i'm going to get an extra hard drive so i can keep playing with ubuntu. its my first go at linux. :mrgreen:

---

