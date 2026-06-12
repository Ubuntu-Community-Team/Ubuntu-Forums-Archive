---
title: "Error while trying to automatic partition w/ silder"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Canadaboy on 2007-08-23
[IMG]http://img503.imageshack.us/img503/4498/screenshot1ql1.png[/IMG]

---

### Post by Canadaboy on 2007-08-23
I am using the slider option because I want to double boot, but I always get an error :S

---

### Post by amneziac on 2007-08-23
well it seems that the problem is resizing ur harddrive, because w/e method of partitioning uve tried to use there has always been an error with resizing the harddrive

---

### Post by Steve1961 on 2007-08-23
Make sure you thoroughly defragment the drive first.  If you still have problems it might be worth resizing from within windows - acronis disk director works well

---

### Post by Canadaboy on 2007-08-23
> **amneziac said:**
> well it seems that the problem is resizing ur harddrive, because w/e method of partitioning uve tried to use there has always been an error with resizing the harddrive

I ran disk defragmenter so I dont know what the problem could be

---

### Post by Steve1961 on 2007-08-23
> **Canadaboy said:**
> I ran disk defragmenter so I dont know what the problem could be

Might be worth giving the alternative CD a try

---

### Post by bren on 2007-08-23
you could try partitioning the drive first

then when you install choose the "manual option" and install to the already freed up space

to partion in advance you can

1) use partition magic or similar in windows
2) use gparted (System-Admin-Gnome Partition Editor) from the desktop booted from the LIVE CD

if you have problems with 2) then post a screenshot of gparted (you take a screenshot by doing Applications -- Accessories - Take Screenshot)

bren

---

### Post by Canadaboy on 2007-08-23
> **Steve1961 said:**
> Make sure you thoroughly defragment the drive first.  If you still have problems it might be worth resizing from within windows - acronis disk director works well

I will try defragmenting again

---

### Post by Canadaboy on 2007-08-23
> **bren said:**
> you could try partitioning the drive first

then when you install choose the "manual option" and install to the already freed up space

to partion in advance you can

1) use partition magic or similar in windows
2) use gparted (System-Admin-Gnome Partition Editor) from the desktop booted from the LIVE CD

if you have problems with 2) then post a screenshot of gparted (you take a screenshot by doing Applications -- Accessories - Take Screenshot)

bren

I tried #1 and I messed up

I tried #2 and got this:

[IMG]http://img524.imageshack.us/img524/1525/screenshotto4.png[/IMG]

---

### Post by bren on 2007-08-23
hi canada boy

that screenshot look fine
will take a while to complete
let us know how it goes

bren

---

### Post by Canadaboy on 2007-08-23
> **bren said:**
> hi canada boy

that screenshot look fine
will take a while to complete
let us know how it goes

bren

You see those red signs? I got an error!

---

### Post by bren on 2007-08-24
ok canada boy

sorry missed the red / fails - sorry

 i have seen some mention on other threads (rumour only) that gparted on LIVE CD is an old version and does not allow all combinations of partion creation. this may be the problem.   you could try one operation at a time.... or....

for latest version of gparted seach and then burn new ISO to cd for GPARTED LIVE CD
this should do any combo of operations you choose..... 

alternatively as other poster said above alternate CD sometimes solves probs of graphics install.

i note from the screenshot that there is a very small parition right at the start of the disc...2.2GB.. this is likely some OEM or recovery type partition by manufacturer.

it is the case (in my case anyway) that it is more dificult for the Ubuntu install when this small starting parition exisits....

so be patient with Ubuntu if you can it is also your OEM setup that may be causing you these problems in what (for many people) is a simple install process.

bren

---

