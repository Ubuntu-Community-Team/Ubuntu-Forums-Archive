---
title: "Lock-up Tips"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Andavane on 2007-07-21
Greetings.
Are there any good tips on how to proceed when the system locks up? (Apart from switching off the power)

And/or anything to do when the mouse freezes, so one can move the pointer with the keyboard?

I'm afraid I still automatically go for ctr-alt-del.

I feel that using Windows and pointing and clicking tends to cause freezes.
Command lines are much more stable, more 'direct'

I have already put the "force quit" command into the bottom bar.

Regards

John

[color=blue]PC: IBM Think-Centre A-50 : 40 Gb

Hard Drive 0) Windows XP-Pro (NTFS), partitioned (my data folder on a FAT32 partition)
Hard Drive 1) Ubuntu 7.0.4 “Feisty Fawn”, : 110 Gb (ext3)[/color]

---

### Post by rax_m on 2007-07-21
I read a good article somewhere on the use of Alt-SysReq-Key combinations that you can use if your system is not responding. I couldn't find the article, but the table below gives a summary of the commands. 

I'm sure someone more knowledgeable can comment on the merits of each.. 

Table 1: Magic emergency key combinations with <Alt><SysReq><key>. Taken from  /usr/src/linux/Documentation/sysrq.txt (in the doc package of the Linux source code distribution).
<key> 	Action
'r' 	Turns off keyboard raw mode and sets it to XLATE.
'k' 	Kills all programs on the current virtual console.
'b' 	Will immediately reboot the system without syncing or unmounting your disks.
'o' 	Will shut your system off via APM (if configured and supported).
's' 	Will attempt to sync all mounted filesystems.
'u' 	Will attempt to remount all mounted filesystems read-only.
'p' 	Will dump the current registers and flags to your console.
't' 	Will dump a list of current tasks and their information to your console.
'm' 	Will dump current memory info to your console.
'0'-'9' 	Sets the console log level, controlling which kernel messages will be printed to your console. ('0', for example would make it so that only emergency messages like PANICs or OOPSes would make it to your console.)
'e' 	Send a SIGTERM to all processes, except for init.
'i' 	Send a SIGKILL to all processes, except for init.
'l' 	Send a SIGKILL to all processes, INCLUDING init. (Your system will be non-functional after this.)

---

### Post by Mornedhel on 2007-07-21
Ctrl Alt Backspace kills your X server (if it is not completely frozen, that is, if you can still press keys and it has some effect). Then you only have to log back in (no reboot).

---

### Post by davidjmayo on 2007-07-21
For mouse freezes

try in order:

1  esc
2 [ctrl]+[alt]+[printscreen/sys request]
3 unplug mouse, wait a bit, replug mouse
4 [ctrl]+[alt]+[backspace] 

as said by Mornedhel number 4 will kill the X session but no reboot needed

---

