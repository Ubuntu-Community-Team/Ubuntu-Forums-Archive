---
title: "[SOLVED] Reformat /boot"
date: 2008-05-29
forum: Arch and derivatives
---

### Post by Dr Small on 2008-05-29
I have GRUB on a floppy all backed up, and I want to remove or reformat /boot so when the system boots, it will say there is no operating system, instead of taking me to a GRUB prompt.

What is the safest way to do this?

I plan to just open gParted and reformat /dev/sda1. Will that accomplish what I want to do ?

Dr Small

---

### Post by meierfra. on 2008-05-29
> it will say there is no operating system, 

Why?

Anyway, if you deleted the boot folder, or say just the grub folder, you  will get a grub error (Probably Error 22)

"No  operating system" would be a message from the bios. To get this you would have to delete the Grub code from the MBR.  For example you could write zeroes  to the first 440 bytes of the hard drive. (In this case it would not matter whether you still have your grub folder)

Some bios actually will report this error if none of your primary partitions have a boot flag.   That can be easily achieved with "gparted" or "cfdisk".

---

### Post by Dr Small on 2008-05-30
Well here's the thing. I do have /boot/grub renamed to /boot/grub_bak, and it used to give me an error on Ubuntu, but now with it, it takes me to a grub prompt where I enter commands to boot it, rather that simply giving me an error.

---

### Post by meierfra. on 2008-05-30
Are you just try playing around to learning purposes? (I do that all the time)

> it used to give me an error on Ubuntu, but now with it, 

Did you change anything, which could have caused the different behavior?


>  it takes me to a grub prompt where I enter commands to boot it, rather that simply giving me an error.

This means that grub can still find the stage2 files, but cannot find menu.lst. Doesn't  make much sense, since the stage2 files are also in /boot/grub.   I  had a similar experience once: I replace the stage2 file with the stage2 files from supergrub, but grub still used my old stage2 files. Only after   reinstalling grub, the supergrub stage2 files were used.  So I made up the theory that the grub code in the mbr contains the physical address for the stage2 files. So grub does not  look for the file via the "/boot/grub/stage2" but goes  right to the place on the hard drive, the stage2 files are stored. Renaming  the grub folder does not change the physical location of the stage2 file.  But I did same more experiment which seem to contradict this theory. So I'm not sure what really is going on.

---

### Post by Dr Small on 2008-05-30
Well, it certainly must be using Grub Stage 2 file somehow. I no longer have any 'grub' directory in /boot, as I moved it it my home folder, yet I am still taken to the 'grub>_' prompt at bootup.

So now the question, how would I go about reinstalling GRUB, so I can get this to work right?

I did this back on Ubuntu and never had a slightest problem. Just renamed 'grub' and then it gave me a GRUB File missing error. So I thought it should do similar on Arch. Apparently I have been proven wrong.

Yes, I am tinkering and playing around. Like to try different odd things at times that makes my friends look at me bewilderment :D

Basically, I like to have my system unbootable without the GRUB floppy. Sorta like an extra access key to get the system running, if you bypassed my BIOS bootup password :)

Dr Small

---

### Post by MisfitI38 on 2008-05-30
Here's a reinstall guide for grub in the Arch wiki:
[http://wiki.archlinux.org/index.php/Reinstalling_GRUB](http://wiki.archlinux.org/index.php/Reinstalling_GRUB)

---

### Post by meierfra. on 2008-05-30
> Basically, I like to have my system unbootable without the GRUB floppy.

Writing zeros to the first 440 bytes of the hard drive and removing all boot flags will definitely  do that. (But of course you could still boot your system with all kinds of external media other than a Grub floppy.)

I won't tell you how to write zeros to the MBR. If you can't figure that out by yourself, you shouldn't be doing it.

---

### Post by Dr Small on 2008-05-30
Ok. I found the command (or created it as I went, anyhow):
```
sudo dd if=/dev/zero of=/dev/sda1 bs=446 count=1
```

Didn't do squat, as I was still getting the same stuff after running it, so I reformatted sda1, and now I can't boot!!!!

Just kidding of course. :)
I moved all of the files in /boot over to /kernels and edited my menu.lst around to point to /kernels/vmlinuz sort of stuff, so now it works.

I then just flat out deleted sda1, resized sda2 and moved the remaining space into sda5, as my swap. Now when I reboot without the floppy in, I get:
```
GRUB _
```

(only the underscore blinks very fast :))

I would have rather it not said GRUB, but I guess I can live with it. Thanks for all the help.

Dr Small

---

### Post by meierfra. on 2008-05-30
> Didn't do squat, 

That's because you are doing it wrong.

---

### Post by Dr Small on 2008-05-30
Thanks for the information. Maybe you could explain how I was doing it wrong, so I could learn from my mistakes?

---

### Post by meierfra. on 2008-05-30
You erased that first 446 bytes of the partition /dev/sda1. But I told you to erase the first 440 bytes of the hard drive /dev/sda

---

### Post by Dr Small on 2008-05-30
I tried 440 first, as per your suggestion, and it did the identical same thing. Then in another thread, it said 446, so I tried that. Point is, neither worked.

Anyhow, I thought that was supposed to erase GRUB from the partition. It didn't, and even running the command for the ENTIRE partition didn't work.

Of course then, I couldn't mount it back at bootup, since the filesystem was corrupted. lol. That was another problem I had to fix :D

Dr Small

---

### Post by Dr Small on 2008-05-30
Ah, I see now. You should have applied more emphasis on **sda**. I was continuously trying it for *sda1*. Silly me.

So, if I run:
```
sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
```

It should (in theory) completely eliminate Grub?

Dr Small



Edit:
Curiosity killed the cat, but it never killed me. I went ahead and ran the command anyhow. I got to be adventurous, you know ;)

It solved my problem. Thanks again for your help and support throughout me trying to break my system. It was definitely needed :D

---

### Post by meierfra. on 2008-05-30
> You should have applied more emphasis on sda.

> If you can't figure that out by yourself, you shouldn't be doing it. 

:)

---

### Post by Dr Small on 2008-05-30
> **meierfra. said:**
> :)
Well, it's not like I was going to erase my whole hard drive or anything.... :)

---

### Post by meierfra. on 2008-05-30
> Well, it's not like I was going to erase my whole hard drive or anything...

If you leave out the "count=1"  in the "dd" commmand, it will erase your whole hard drive.

---

### Post by Dr Small on 2008-05-30
Yes. 'dd' is quite self-explanitory as to the effects it will produce. ;)

---

### Post by plamen_todoroff on 2008-10-14
What is the difference between bs=440 and bs=446? Actually this is the first time I see the parameter bs=440 being used. All howtos on the internet about removing Grub state that bs=446 is to be used as a parameter in the dd command.

So, what is the difference between 440 and 446? As 446 is clearing the whole Grub code in the MBR, what exatly is 440 clearing? Part of the boot code?

---

### Post by meierfra. on 2008-10-14
The Grub code ends somewhere around 430.
430-439 is blank (that is zero's)
440-443  contains the disk signature, which is used by Windows.
444-445 is usually blank.
446-511  is the partition table.

These numbers are based at zero. So bs=446 will erase bytes 0-445.

Erasing the disk signature can cause problems, in particular for Vista.

I don't recommend using "dd" to erase grub. There are only very rare circumstances where this is useful.

---

### Post by plamen_todoroff on 2008-10-14
> **meierfra. said:**
> The Grub code ends somewhere around 430.
430-439 is blank (that is zero's)
440-443  contains the disk signature, which is used by Windows.
444-445 is usually blank.
446-511  is the partition table.

These numbers are based at zero. So bs=446 will erase bytes 0-445.

Erasing the disk signature can cause problems, in particular for Vista.

I don't recommend using "dd" to erase grub. There are only very rare circumstances where this is useful.

What does "bootrec.exe /fixmbr" do exactly to each of these parts of the MBR? What exact problems do you mean for Vista if bs=446 is used (disk signature erased)?

---

### Post by meierfra. on 2008-10-14
Bootrec /fixmbr only alters the boot code (bytes 0-439)

For information on the disk signature see

[http://www.multibooters.co.uk/mbr.html]("http://www.multibooters.co.uk/mbr.html")

But my personal experience seems to contradict the article: I have messed around  with my disk signature and it never caused problems  with vista.

---

