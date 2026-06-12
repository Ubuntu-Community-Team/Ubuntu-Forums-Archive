---
title: "Backup dvd's"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Hospadar on 2007-08-23
Hi,
Just a quick question about backing up dvds, I want to back up some dvd's I own, and I'm just wondering if I need to do anything more than extract a disk image and write that to a dvd.  I don't need to do any ripping or converting of any sort, I just want to make a copy of the dvd so I don't have to worry about my originals.

Just wanted to ask If anyone has any experience with this before I start burning coasters out of expensive dual-layer dvds.

Thanks,
Luke

---

### Post by wolfen69 on 2007-08-23
K9copy is a good app for that.

---

### Post by andrew.46 on 2007-08-27
Hi,

 I have recently published a walkthough for doing just that:

[http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#dual](http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#dual)

 This walkthough deals with the CLI method of doing it though.

                Andrew

---

### Post by Hallvor on 2007-08-27
K9copy is very easy. It`s a lot like dvdshrink in Windows. (I also think you can run dvdshrink in Wine.)

---

### Post by FNDII on 2007-08-27
Where can i get K9copy?

---

### Post by hyper_ch on 2007-08-27
from the repos.

---

### Post by FNDII on 2007-08-27
can you explain exactly what the repos are? Because I though the repos are the things available through the add/remove feature. 

Is there a way to add more programs  to the add/remove feature? 

Or am I way off?  (most likely this one)

---

### Post by hyper_ch on 2007-08-27
By default not all repos are enabled....


[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Adding_new_programs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Adding_new_programs)

And here a generator:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by FNDII on 2007-08-28
I have looked around and cant find much of a how to for k9copy. I tried a couple things.

made the input device /dev/scd0 and the output /dev/scd1,that didnt work.

I also made the output to ISO and is made a 4.3gig ISO for some reason.

I tried to copy a dvd with K3b and it made a 4.7 gig ISO that when trying to burn I would get a file is to big error.

I have never tried to back up DVD's before not even in windows with DVD shrink or anything. So don't assume any dvd copy knowledge when posting helpplease

---

### Post by indytim on 2007-08-28
Ok, this will be the short explanation of how to backup a dvd with k-9 copy:

1.  Insert dvd into dvd compatible optical (duh).
2.  Launch k9-Copy
3.  Click on the first icon (looks like a file folder), navigate to your correct optical (if you have more than one).
4.  Make sure your output device is set to iso file.
5.  Click the small dvd icon and choose appropriately.
6.  Let dvd-copy do it's thinger.
7. Exit from the app.
8.  Launch k3b and choose dvd iso option.
9.  Select your iso file location etc and burn to iso to dvd.

IndyTim

---

