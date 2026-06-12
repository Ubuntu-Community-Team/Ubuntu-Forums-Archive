---
title: "Defrag"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-09-22
i KNOW EXT3 dosent need to be defragged.

but while i was in LiveCD i gave it a shot, had time too kill.

anyway my home was 6.5% fragmented now it 0.2%
and my startup time is much improved.

not sure if it's in my head but it does seem quicker to load apps.
since their settingd are stored in /Home

i reccomend defragging once in a while.
like every 6 months.

---

### Post by Arwen on 2007-09-22
Can you post how can we do the defragment?I didn't know I could it in ubuntu.Thanx!

---

### Post by skymera on 2007-09-22
its not really needed.

well pop in the liveCD

unmount all drives when its loaded.

update the repos and enable extra repos, restriced etc.

sudo apt-get install defrag

then 

e2defrag /dev/sda6    

that was my command for home.
simple, but not needed really.

---

### Post by nvteighen on 2007-09-22
There's a tool for ext2 that can be used, but I understand it may break ext3 journal.

---

### Post by skymera on 2007-09-22
all i know it was called defrag,
in repos.

welll...i defragged both home and root and working better.

---

### Post by insane_alien on 2007-09-22
yeah thats the ext2 defragger. it is possible for it to hurt your ext3 filesystem. if you run a fsck on the the drive first it will reduce the risk but it will still exist.

somebody made a ext3 defragmentation script i remember but i have no idea where you would find it.

---

### Post by skymera on 2007-09-22
ok i look for that script.
is it on this forum?

tbo im not bothered about ubuntu breaking.
i reinstall, takes 20 mins lol

---

### Post by insane_alien on 2007-09-22
i've no idea. i just remember that it shunts the files around and relies on the inherent properties of the ext3 filesystem to join up the fragmented files. it doesn't work very well if ou have little free space or mega files that take up a few % of the HDD.

---

### Post by Arwen on 2007-09-22
Well I'll have to do it when ubuntu gets really slow but no way I'll try it now,I'm nervous about unmounting drives,everything is ok now and I don't want to mess it up,since it's not needed.Thanx anyway,I may need defragment sometime..

---

### Post by Sef on 2007-09-22
ext3 automatically defrags every 30 boots.

---

### Post by skymera on 2007-09-22
nervous about unmounting?


in LiveCD nothing is usually mounted, nothing is needed.
if you try when its running you cant :P

---

### Post by psusi on 2007-09-27
> **Sef said:**
> ext3 automatically defrags every 30 boots.

No, it does not.  It fscks every 30 boots.  

And the defrag package in Ubuntu now works fine on ext3; it used to just refuse to run so you had to use tune2fs to convert it back to ext2 ( i.e. just disable the journal ).

---

