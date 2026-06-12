---
title: "Locks up during installation."
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by FLAGAL on 2006-10-23
In the past I have always used Windows on my computer. I had never even heard of Linux until recently. Well it sounded so good that I order a copy of it which I tried to install yesterday. It's not the alternate version of 6.06, so I am not given a choice of which mode to install in. I select "Install or Start", it shows a progress bar and under the bar it says "installing essential drivers" and "mounting root file system". To the right of that it says "OK". After about 2 minutes, It switches to another screen where it says that I have an "O/I error on device hdc". I ran the memory test which it said passed, but instantly began running the test again after the first one finished. I am unable to test the CD as it gives the same error message as when I try to do the install.
   Does anyone know if this is a problem with my computer, the disk or am I just not doing something right? I'd appreciate the input. Thanks.

---

### Post by elpuerco on 2006-10-23
Could be hardware related.

But why not try downloading the alternate iso and give that a run.

---

### Post by Bartender on 2006-10-23
Memtest is meant to restart.  It'll run over and over until the pyramids erode away if you let it.  So don't worry about that.  Many people suggest letting it run overnite if you suspect your RAM is getting flaky.
Linux drive identification is different from what you're used to.  "hdc" is probly your optical drive.  Can you take a look at the cables?  Maybe try a different optical drive?

---

### Post by FLAGAL on 2006-10-23
> **elpuerco said:**
> Could be hardware related.

But why not try downloading the alternate iso and give that a run.

Where would I be able to get a copy of the alternate version? I printed out installation instructions a few days ago and didn't realize until I was trying to do the actual install that it was for the alternate version. It gave instructions on doing a dual-boot, which is what I'm wanting to do because I have files being used under Windows 98.

---

### Post by FLAGAL on 2006-10-23
> **Bartender said:**
> Memtest is meant to restart.  It'll run over and over until the pyramids erode away if you let it.  So don't worry about that.  Many people suggest letting it run overnite if you suspect your RAM is getting flaky.
Linux drive identification is different from what you're used to.  "hdc" is probly your optical drive.  Can you take a look at the cables?  Maybe try a different optical drive?
When you say let it run overnight, are you refering to the Memtest? If so, how would this affect the RAM? As far as checking the cables, I usually consider myself computer literate, but only when it comes to using it. With the cables, I just plugged the different cables to each device into the areas labled with their picture on the back of the modem. I just bought the computer _used_ about two weeks ago, so I'm not entirely familiar with it. Again, being a novice when it comes to the different parts of the computer itself, how would I try a different optical drive? I don't know where it's located. Sorry for sounding really dim-witted. Thanks!

---

### Post by Bartender on 2006-10-24
Sorry, been away -
Yeah, I did mean run memtest all nite long.  Memtest puts your RAM memory sticks thru their paces, sending bits of code through them and looking for faults.  One method (if you suspect RAM problems) is to remove all but one stick (that remaining stick should be in the #1 slot on the motherboard) and run memtest for several hours.  If no faults, put in the next piece of RAM and repeat.  Ideally, you should have no memory errors at all.  Don't quote me on this, but if you get one or two errors on a long memtest run you could probly use the stick but you might get sporadic blue screens of death in Windows.  I don't know what Linux does.  I'd guess that Linux soldiers on somehow by repeating the task ;) 
Anyway, that's all memtest does.  It doesn't affect your RAM other than give it a good workout.
I didn't mean to snow you with geek terms.  Since I didn't know if you had a CD or DVD drive or burner, I just used the phrase "optical drive" to indicate the device that spins your CD's.  Your hard drive uses electromagnetism to write and read data, so you could refer to hard drives as electromagnetic storage or  electromagnetic devices.  But most everyone just says "hard drive".
CD and DVD drives use a tiny laser to either create (burn) or read miniscule pits on the disc surface.  Since your CD or DVD drive uses light, not magnetism, the term "optical device" is just an easy way to make sure you know we're talking about your CD/DVD, not your hard drive.
Make any sense?  With that other operating system, your optical drive is probly numbered "D" drive.  In Linux, it's probly "hdc".  If you type 'hdc' into the Search box you'll see lots of other threads.  You might want to check [this]("http://www.ubuntuforums.org/showthread.php?t=254468&highlight=hdc") one.
If it were me (that's my newb qualifying statement) I'd take off the case cover & check the cable that runs from the back of the optical drive to the motherboard to see if it's wiggled loose.  If I couldn't find anything obviously wrong I'd plug in a spare optical drive and see what happened.  You mention buying it used. Maybe the optical drive was failing and that's why they sold it.

---

### Post by FLAGAL on 2006-10-24
I tried installing again last night with no luck. I tried hitting F6 and entering different boot options, but none worked. I either got locked up on the screen with the progress bar, locked on a black screen with "Uncompressing Linux...OK, booting the kernel" with a blinking cursor, same as above but with "Buffer I/O error on device hdc, logical block ## (goes from 0 to 15) or on some of the boot options, it will go to the black screen and a whole bunch of information scrolls down the screen then it stops and says: 
hdc: command error: error=0x50{LastFailedSense=0x05}
ide: failed opcode was: unknown
end_request: I/O error, dev hdc, sector ##  (## changes)
Buffer I/O error on device hdc, logical block ##  (##changes)
hdc: command error: status=0x51{DriverReady SeekComplete Error}
I'm completely lost! Where would the sticks for the RAM be located at in case I do need to try to remove all but one? 
I looked up the definition of I/O on [http://www.computerhope.com](http://www.computerhope.com) and it states that it is the Input/Output which "is software or hardware device designed to send and receive information to and from a computer hardware component". On the same site, I found suggestions for fixing IOS (Input/Output Supervisor) errors:  [http://www.computerhope.com/issues/ch000359.htm](http://www.computerhope.com/issues/ch000359.htm) 
I think I'm going to try that before I take apart the computer and start removing and jiggling pieces.
I also wondered if my problem could be that Ubuntu isn't compatible with my computer. Is that a possiblility?
I ran a System summery Report and it gave some info on my computer. I don't know whether it's good or bad.....
HP Pavilion w/Intel Celeron Processor currently running Win98
IBM PC/AT, 191MB RAM, DirectX version 8.0, Processor: X86family6model6stepping5, 466MHZ, 32-bit File System/Virtual Memory, Available Space: 4111MB of 8038MB (FAT32), 636KB Total Conventional Memory 195032KB Total Extended Memory, Drive Info: (A) 3.5" 1.44M (C) 8231832K Total 4214428K Free (D) CD-Rom Drive, Intel Graphics Driver w/ Mini-VDD.
There was a lot more information that printed out, but I didn't know what information was needed.
SOMEBODY PLEASE HELP ME.  Thanks!

UPDATE: The suggestions to fix the IOS errors didn't work. Downloading the alternate CD so I can see if that fixes the problem.

---

