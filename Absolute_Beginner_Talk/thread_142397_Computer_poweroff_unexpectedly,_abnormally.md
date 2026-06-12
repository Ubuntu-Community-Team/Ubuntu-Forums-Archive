---
title: "Computer poweroff unexpectedly, abnormally"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by AtinLango on 2006-03-10
I have never experienced this in Ubuntu.

Supposing, for some reason, my computer powers off unexpectedly in the course of my using Ubuntu, with several mount points open, including non-linux partitions like fat32, ntfs. Wouldn't the end result be disastrous.

When I compare with windows, it appears safer for the computer to go off while working in windows because atleast windows will not mount other OS's partitions. Therefore, it can fairly well manage its own partitions in case of eventuality.

Does anybody have an experience with Ubuntu (or Linux generally) box powering off?

---

### Post by John.Michael.Kane on 2006-03-10
I have turned my machine off while having ubuntu running, and when turned back on it went through the file system check, and loaded the gdm, and all was good to go. now i dont sugest that everyone can do this, and get away with it as i did it to test the os. however from the one time i did i can say the data stayed the same. this may not be true for all, and it depends on how the system is turned off..

---

### Post by pbaehr on 2006-03-10
You mention windows. Do you have a dual boot system?

If you do, try running the computer in Windows for a few hours and see if it happens there as well.

It sounds to me like your computer is overheating. Have you made any significant hardware changes recently? Are you running especially intense software when it occurs? Do you live in an oven?

Overheating is always my first guess when a computer shuts off randomly and unexpectedly. Then again, I've been wrong before...

Edit: I just noticed you're using a laptop which makes it less likely you've made hardware changes. Make sure all the appropriate fans are running and not blocked by a blanket or something. (My laptop always used to overheat when I used it in bed)

While I'm editing...has this always been a problem with Ubuntu or is it all of a sudden not working right?

---

### Post by AtinLango on 2006-03-10
[QUOTE=pbaehr]You mention windows. Do you have a dual boot system?

If you do, try running the computer in Windows for a few hours and see if it happens there as well.

It sounds to me like your computer is overheating. Have you made any significant hardware changes recently? Are you running especially intense software when it occurs? Do you live in an oven?
[/QUOTE]

No. No. My computer is perfect - it is not powering off at all. If you read my original thread, I am just saying supposing a computer does so. This is purely for brainstorming so that we can get to know better.

SD-Plissken, you turned off your computer to test the OS. My question to you is, did you also have other non-linux partitions mounted at that particular time? Because to me, that's where the likely risk is.

---

### Post by az on 2006-03-10
Just because something is mounted does not mean you are writing to it.

I would not be worried.  This does not seem to me to be something that imposes a greater risk.

Anyway, you are not forced to mount any partition if you don't want to.  You just can.


Similarily, you can mount ext3 partitions in windows by running software for that (explore2fs).

---

### Post by John.Michael.Kane on 2006-03-10
@AtinLango No other Os installed. just linux, now xp does have a feture that if it is shut down abnormaly it do go through a filesystem check. I would think that if your dual booting, and one os crashes all you would have to do is boot in to each os, and let them run their system checks ect, and all should be fine. this is only a guess as at this time i'm only using one os, cant check this theory out.

---

### Post by pbaehr on 2006-03-10
> If you read my original thread, I am just saying supposing a computer does so. This is purely for brainstorming so that we can get to know better.

Oops. Totally misread it. Glad to hear your computer's working like it should, though. ;)

---

### Post by AtinLango on 2006-03-10
You know, I was compelled to start this thread partly because I am using a laptop and our power supply is a bit erratic these days. So I end up working on the battery to near depletion.

Anyway because of lack of time, I have not yet figured out how to set the laptop to hibernate or shutdown (for e.g.) when battery level reaches bare minimum. This, to me, potentially put me at a risk of not noticing that battery power is over and as a result the laptop going off when I am working with various mount points open.

It is good to hear that it is not as risky as I had feared. Of course this is not to encourage anyone to be complacent with safety measures.

---

### Post by bcmiller on 2006-08-13
> **pbaehr said:**
> You mention windows. Do you have a dual boot system?

If you do, try running the computer in Windows for a few hours and see if it happens there as well.

It sounds to me like your computer is overheating. Have you made any significant hardware changes recently? Are you running especially intense software when it occurs? Do you live in an oven?

Overheating is always my first guess when a computer shuts off randomly and unexpectedly. Then again, I've been wrong before...

Edit: I just noticed you're using a laptop which makes it less likely you've made hardware changes. Make sure all the appropriate fans are running and not blocked by a blanket or something. (My laptop always used to overheat when I used it in bed)

While I'm editing...has this always been a problem with Ubuntu or is it all of a sudden not working right?

I know this is an old post but...

My computer will power off randomly when I am in linux.  It never does this when I am in windows xp (dual boot)

it is a shuttle pc and it might be clogged with dust or something so I'll clean it out and see if that helps but it's odd that is only happens in linux.  It happened a lot when I used PC Linux OS and now it happened 2 times today in Ubuntu Dapper.

Has anyone ever heard of this?

btw... about the original topic

I have powered this cpu down on purpose and unexpectedly many many times with Ubuntu running and mounting my XP partition and an external Fat32 partition and it starts back up with nothing loss or corrupted.

---

