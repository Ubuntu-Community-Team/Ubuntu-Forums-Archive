---
title: "Why Ubuntu Why?  (won't boot)  Please help!?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Phen0m24 on 2006-08-11
Hello all -

I took my laptop on vacation, and had XP Home and Ubuntu on it.  Well, while I was there, for whatever reason Ubuntu locked up hard.  I don't know what caused it, maybe I was impatient about waiting to see if it would resolve itself, but it was fubared.

I held down the power button, and then when I went to reboot I got nada.  Grub wouldn't load, I couldn't get XP to load either.

Well, I needed the laptop and fortunately had my Live DVD with me, so I reinstalled Ubuntu and that was the only resident on the HD.

fast forward to today

My wife is looking at HUGE .jpg files on a CD and somehow the system locks up.  I wait for like 5 minutes - nothing happens.  I hard shut down and then attempt to reboot.

I've been staring at the following prompt for half an hour now:

grub>

What the heck do I do, and why doesn't the kernel load?  Why would one system lock-up render the system completely screwed up all of a sudden?  Frustrated and confused.

Any help would be appreciated - I swear if I have to reinstall this again I'm going to scream and then scream again.

Thanks

Glenn

---

### Post by arjun.shankar on 2006-08-11
for now:

type this when you see the grub prompt, "grub > ":

**root (hd0,n)**

hd0 = the zeroth hard drive.

'n' represents the partition number for "/boot" (if you have a seperate /boot partition), or for "/" (if you have no /boot partition.

The 'n' starts from 0. (so second partition is marked 1, and so on)

Hit enter.

Now:

Again at the grub prompt:

**configfile /grub/menu.lst**

if you have a seperate boot partition, or

**configfile /boot/grub/menu.lst**

if you dont.

---

### Post by Phen0m24 on 2006-08-11
typing root (hd0,n) resulted in

Error 11: Unrecognized device string

---

### Post by Phen0m24 on 2006-08-11
typing configfile /boot/grub/menu.lst yielded some numbers in brackets and then I'm brought to:

GNU GRUB version 0.97 (639K lower / 523072K upper memory)

[Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a device/filename.]

---

### Post by arjun.shankar on 2006-08-11
it's not (hd0,n)
For example if you have a /boot partition, and it is the very first partition:

root (hd0,0)

Or if you dont have a /boot, and your "/" is... say the second partition, give:

root (hd0,1)

I am arjun.shankar on yahoo, and arjunsha on gmail. Catch me there if you can. It will be faster.

---

### Post by Phen0m24 on 2006-08-11
> **arjun.shankar said:**
> it's not (hd0,n)
For example if you have a /boot partition, and it is the very first partition:

root (hd0,0)

Or if you dont have a /boot, and your "/" is... say the second partition, give:

root (hd0,1)

Sorry, my mistake.  I typed root (hd0,0) and got

Filesystem type is ext2fs, partition type 0x83.

I also tried root (hd0,1) and got

Filesystem type unknown, partition type 0x5

---

### Post by arjun.shankar on 2006-08-11
Good! now...

Did you make a '/boot' partition?

And use (hd0,0)

---

### Post by Phen0m24 on 2006-08-11
sadly, typing both of those now results in

Cannot mount selected partition


Am I screwed?

(mumbles and grumbles)

Wait, I went back to the original of hd0.0 and then did it.

Seriously, it looks like the matrix is scrolling on my screen right now.

It says savedefault after like a million numbers flashed across the screen.

HOLY TOLEDO it came on.

---

### Post by arjun.shankar on 2006-08-11
No!
Simply reboot!

---

### Post by arjun.shankar on 2006-08-11
And, you havent told me yet. Did you make a /boot partition?

---

### Post by Phen0m24 on 2006-08-11
Hi arjun - the Ubuntu logo came up but now there is but a blinking cursor on the top left of the screen.

(sorry about the IM situation, I don't have any IM programs installed on my PC - only on the laptop which I'm working on)

---

### Post by Phen0m24 on 2006-08-11
The last time I installed Ubuntu I didn't create any partitions - / was my whole free space.

Unless you mean right now - I told you what I typed..

It is still displaying a blinking cursor in the top left of the screen.

---

### Post by arjun.shankar on 2006-08-11
Thats weird! I'm sort of ill-equipped to handle this. Why don't you reboot and see what happens? You will probably have to give the root and configfile commands again.

EDIT:

No, you didn't make one just now.

Try rebooting, and giving those two commands again:

root (hd0,0)
configfile /boot/grub/menu.lst

---

### Post by Phen0m24 on 2006-08-11
Hi arjun - I did exactly that.  But then I come to the grub> prompt again.

I entered both of those commands as listed.

root (hd0,0)

Then configfile /boot/grub/menu.lst

I'm staring at the grub prompt again.

](*,) 

Thanks for your help though.

---

### Post by arjun.shankar on 2006-08-11
you don't see error messages when you give these commands?

---

### Post by arjun.shankar on 2006-08-11
Hey!
Try this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Maybe it will work.

---

### Post by Phen0m24 on 2006-08-11
Here go:

Right now I see grub>

I type next to it:  root (hd0,0) and hit enter

It replies "Filesystem type is ext2fs, partition type 0x83)

I then type (next to the grub prompt)

configfile /boot/grub/menu.lst

I hit enter and now the hard drive is making scratching noises.

Lovely.

But then I come back tot he grub prompt.

Oh heck with it.  forgive me as I am going to yell quasi-obscenities at my laptop.

---

### Post by arjun.shankar on 2006-08-11
PhenOm24, try that link and see. If it doesn't work, we can give up and wait for someone else to help us out.

---

### Post by Phen0m24 on 2006-08-11
I don't have my Live DVD.  I gave it to my brother-in-law in Canada.  So rather than wait for the download, I think I'll just put XP back on.  

Thank you very much for trying though - I appreciate it.

---

### Post by arjun.shankar on 2006-08-11
well... interested in getting atleast XP to boot? ;)
It will require a _little_ experimenting, unless you remember the partition number.

EDIT:

Here is what you need to do:

1. boot
2. at the grub prompt:

rootnoverify (hd0,2)
chainloader +1

if that doesnt work, try (hd0,3), (hd0,4) and so on. One of them will work.

---

### Post by Phen0m24 on 2006-08-11
Arjun.  Hold on.  Wait.

Ready?

I only had Ubuntu on the laptop.  

Literally, I fished out my XP Home install CD, rebooted and hit the BIOS menu.  I selected to boot first from the optical drive.

I currently have my Windows XP cd IN THE DRIVE.




KNOWING that I can't install Windows without the power cable, I plug the power cable in, hold down the power button - waiting for the ever familiar Windows logo, wipe HD, all that crap.








All of a sudden Ubuntu boots up with no problems -  **with the power cord plugged in?**






](*,)    :confused:    :mad:    :???:    :-?    :-|

---

### Post by arjun.shankar on 2006-08-11
...

---

### Post by arjun.shankar on 2006-08-11
I'm speechless. It's fine now?

---

### Post by arjun.shankar on 2006-08-11
In any case, this is too weird for me to handle right now. It's 6 in the morning in India. Been up all night.. I need some sleep. Hope it stays fine now. Don't hate me, but I also hope your XP CD burns up inside the drive or something ;). Ubuntu still rocks!
Have fun!

---

### Post by Phen0m24 on 2006-08-11
Hey listen - I get cranky sometimes with Dell and HP folks that try to help me in India.  But you sat there and tried to help me and man I REALLY APPRECIATE IT.

Thanks for your effort.

Maybe that's one bug that can be "easily" solved?  Plug in power cable?

Seriously, THANKS AGAIN.  Much appreciated.

---

### Post by arjun.shankar on 2006-08-11
Thats fine. It was a fun hour!

Good night! (or morning? I'm confused!)

---

### Post by Phen0m24 on 2006-08-11
Hey go get some sleep!!!!

Thanks again.  Really.

---

### Post by Phen0m24 on 2006-08-11
Now that my laptop is functioning again, I'm trying to figure out the cause of this situation.

Before the lockup, my wife told me that there were only a few minutes of power left on the machine, but I told her that was impossible as the laptop had been plugged in all night and the bar in the power part of the top bar was GREEN.  But I recall how I had basically run down a battery before and had those messages pop-up, but then I would always A) plug the laptop in and B) close those dopey messages, where they would be replaced with "Your computer will be fully charged in x minutes"

I don't think she closed the little error message popup that only gave the machine several minutes left.  Even though it wasn't true, I'm wondering if that was the cause of the lockup and resulting boot issue?  Like it HAD to have the power connected because it thought it was toast?

Very odd.  But glad it's working.

---

### Post by arjun.shankar on 2006-08-12
Ah!

I remember when Dapper was Alpha (been running it since Flight 4), I had this weird problem where:

1. I would hibernate when the battery is about to die.
2. Charge to full while to notebook is off.
3. Boot after it's fully charged, to find the battery applet showing my battery to be empty.
4. At the same time /proc/acpi/battery/BAT0/state would show it to be full.

I filed that as a bug report.

As far as I remember, it was closed, and I never had that trouble again (after a few upgrades ofcourse).  Let me check up on what happened to it...

---

### Post by drtvasudevan on 2006-08-12
so what happened?
the battery was already dead or your men are already dead?
;-)))))

---

