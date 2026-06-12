---
title: "Moving around the terminal"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by don cole on 2006-03-11
OK I read the terminal tutor. I know how to go down a directory, up a directory, cd .., cd /, pwd and ls.

What I would like to know is: how do I get to hda1,hda5,etc..?

Thank you 
Don Cole

---

### Post by kaamos on 2006-03-11
If you want to go to hda1
```
mount | grep hda1
```
And then look up the mountpoint
/dev/hda1 on **/mnt/hda1** type ntfs (ro,nls=utf8,uid=1000,gid=1000)

Just use cd to get to the mountpoint (cd /mnt/hda1)

---

### Post by don cole on 2006-03-11
How do you get that vertical slash after mount.

Don Cole

---

### Post by bluevoodoo1 on 2006-03-11
shift \ should hopefully work!

---

### Post by cotcot on 2006-03-11
[QUOTE=don cole]How do you get that vertical slash after mount.

Don Cole[/QUOTE]

Alt Gr 1 (Alt Gr is right of the space bar; | is together with & and 1 on the 1 button) : only problem could be that you have querty and I am writing about azerty)

---

### Post by kaamos on 2006-03-11
And it is not needed really. You could just type "mount" and look up the correct partition.

---

### Post by don cole on 2006-03-12
I typed: mount grep hda5.

And got 'must be in root directory to do this'

I typed: cd /
mount grep hda5


And got 'must be in root directory to do this'

I want to run in terminal scanModem which is in hda5.

Don Cole

---

### Post by xmastree on 2006-03-12
Just type **mount** and you'll be rewarded with a list of what's mounted and where.
So, for mine I get, among other things, this line:
```
/dev/hda1 on /mnt/windisk type ntfs (rw,umask=0222)
``` which tells me that /dev/hda1 (my windows disk) is mounted at /mnt/windisk 
To get there from a terminal I would type **cd /mnt/windisk** (remember the space after cd)

---

### Post by soonindallas on 2006-03-12
the | is the 'pipe'

omitting it makes the command meaningless.

where it is depends on your keyboard layout.

for me: french kbd it is right-alt+6

the symbol on my key is more like a vertical dashed line, not ! though

---

### Post by bluevoodoo1 on 2006-03-12
[QUOTE=soonindallas]the symbol on my key is more like a vertical dashed line, not ! though[/QUOTE]

Good description, I couldn't think of a way to describe it earlier. It's like that on the us keyboards too.

---

### Post by steveneddy on 2006-03-12
I just want more beans.

:neutral:

---

### Post by xmastree on 2006-03-12
[QUOTE=bluevoodoo1]It's like that on the us keyboards too.[/QUOTE]Not on all of them. I have an old uk keyboard, and the pipe is above the \ between the ctrl and alt on the lower left. That's shown as a dashed line.
On the new (us) logitech I'm using it's a solid line,top right, between the backspace and =, still above the \ but in the opposite corner. :confused:

---

### Post by bluevoodoo1 on 2006-03-12
[QUOTE=xmastree]Not on all of them. I have an old uk keyboard, and the pipe is above the \ between the ctrl and alt on the lower left. That's shown as a dashed line.
On the new (us) logitech I'm using it's a solid line,top right, between the backspace and =, still above the \ but in the opposite corner. :confused:[/QUOTE]

Wow that is odd. So there's no real standard pipe then??

---

### Post by xmastree on 2006-03-12
[QUOTE=bluevoodoo1]Wow that is odd. So there's no real standard pipe then??[/QUOTE]Well this is the first one I've seen where it's not a broken line. This is also the newest one, maybe the fashion is changing. After all, it appears as a solid line when typed | (although that may depend on the font), so it makes sense to have a solid line on the keyboard too.

---

### Post by steveneddy on 2006-04-30
More beans? One post at a time. :D

---

