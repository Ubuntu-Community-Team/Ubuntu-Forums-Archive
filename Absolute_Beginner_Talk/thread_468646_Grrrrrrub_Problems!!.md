---
title: "Grrrrrrub Problems!!"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by simoneale on 2007-06-09
I've got XP Home and Ubuntu v7.04 dual booting (Separate Drives), and I had to re-write my Grub so Windows was first in the list (Default) with a 5 second count down so the Wife wouldn't moan!...

All was working well till last week (Saturday Morning) when, After leaving the PC in Linux downloading for me, The Wife Re-Booted (I showed her how as she's a Windows Fan!) so she could work on her College coursework!...

She came storming into the bedroom claiming I'd 'Broken the Computer' and 'It's only going into that Umbungo Thing!'... I had a look and the Grub had been re-written so if went: 
                             Linux Ubuntu...
                             Linux Ubuntu... (Recovery)
                             Linux Ubuntu...
                             Linux Ubuntu... (Recovery)

Instead of:
                             Windows XP Home
                             Linux Ubuntu...
                             Linux Ubuntu... (Recovery)

It doesn't even have Windows as an option!!!  :confused: 

After a bit of Surfing I found how to edit it back (which ain't easy when your being nagged!!). I also saved a copy of this Re-Edited Grub 'just in case!!'

Now this morning... Guess What!.. its done it again!... Thank God I saved a backup of what I wanted!!!...

Anyone know why/how the Grub edits its self... I had done an 'update' thinngy... not sure what was updated... would this have done it!?!...

I don't want the wife to find it doing that again!, otherwise I'll have to go back to 100% Windows... and I don't want to do that!!  :( 

Cheers
Sim.

---

### Post by AAM on 2007-06-09
I can't do Grub counselling, but I can do marriage counselling

---

### Post by AAM on 2007-06-09
I have had the same problems before. She now has a computer which I refuse to touch. It collects viruses and trojans and hardly works, but that's OK ... NMP!

A cheap P3 (~IGHz) will do you just fine with Ubuntu and KTWOYB!

---

### Post by confused57 on 2007-06-09
You should probably have your Window's entry placed just above the line ###BEGIN AUTOMATIC KERNELS LIST...this way a kernel update won't affect the Window's entry.  
You definitely don't want to place the Window's entry between the ###BEGIN AUTOMATIC...  and the ###END DEBIAN AUTOMATIC KERNELS LIST.

Here's how I have my system set up:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by Inxsible on 2007-06-09
That's because you are placing the Windows entry between these lines.
```
### BEGIN AUTOMAGIC KERNELS LIST
```
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

Anything you place between these lines WILL be over-written on the next kernel update. If you wan Windows to be the default and place it on top , then you have to place that entry before the BEGIN AUTOMAGIC KERNELS LIST line.

Place this before it, and things should work after that
```
title		 Microsoft Windows XP Home
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

You might want to change the root (hd0,0) line to point to the drive where you have your Windows installed.

---

### Post by AAM on 2007-06-09
how about that! Grub counselling ... still need the other?

lol

---

