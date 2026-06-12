---
title: "[SOLVED] Ubuntu Not Booting Up"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by GMada on 2007-12-11
I turned on my PC this morning, chose my Ubuntu partition (I duel boot with XP) like I do every day, but after the orange bar on the Ubuntu logo reached a quarter, a new screen came up with lots of white text, after it stopped, this is what was on the screen:
"hda2 contains a file system with errors, check forced"
It then said something about "Inode 5391022 has illegal block(s)"
"hda2: UNEXPECTED INCONSISTENCY; RUN fsck manually (i.e., without -a or -p options)"
"fsck died with exit status 4"

Then it said something about:
"An automatic file system check (fsck) of the root filesystem failed" And that the file system was now "read-only"
"A maintenance shell will now be started"
"bash: no job control in this shell
bash: groups: command not found"

And then it just stayed there with a command input for me at root. I am a real real mega noob at linux and I have no idea what all that meant, it was like it was in an alien langauge. However, I think hda2 is my D drive (where I store my back up data) and when I was on XP (before I got Ubuntu), my D drive had loads of file system errors, my friend told me it was because my harddrive disk was made by a bad company so I just brought a new one, moved my old files over and that was that.

So, can anyone please help me get Ubuntu working again? I booted up on XP fine, but it didn't detect the D drive error (like it did before in the past with my old D drive), so it worries me to think that hda2 might be my Ubuntu partition, because if it was my D drive, wouldn't have XP tried to fix it like it had done in the past?

Thanks for any help on this matter you can give.

---

### Post by jasmuz on 2007-12-11
Hello.

The message just shows you that your filesystem is corrupt.
In order to fix it, then boot again, and just before the Ubuntu logo press F2, go into recovery mode. This will throw you to the shell with root access.

Now you must check your damaged partition, by typing:

fsck /dev/hda2

Read all the messages it gives you, as it will ask for permision to recover lost chains and make them files.

Take care.

---

### Post by flamelab on 2007-12-11
Do what it says . In GRUB , press esc and then the recovery mode . It should boot in text mode . If it reaches a point where you may put a command , the problem is solved automatically ( that's what I had done once ) . Then enter the command it tells you .

---

### Post by GMada on 2007-12-11
Yes! Thankyou! It worked! It was my Ubuntu partition that had all the errors and I had to clear and fix alot of stuff, but it's now working. Thankyou so much!

---

