---
title: "Ubuntu blues on a Mac mini Intel"
date: 2006-08-16
forum: Apple PPC Users
---

### Post by tactus on 2006-08-16
Hi friends.

I Installed 6.06 during the weekend using the [bin-false]("http://bin-false.org/?p=17") tutorial. I have OS X and Ubuntu installed, dual booting with rEfit. Even Compiz is running, but the system is **unstable**. I let it on for say 24 hours, and then it just stops responding, forcing me to do a hard reboot. Then I get errors like "Buffer I/O error on device sda#, logical block ######" and issues with mounting my hda. Resetting PRAM seems to solve the issue, but only for another 24'ish hours.

What in the world is going on, I don't have to reinstall I hope? [-o<

---

### Post by packhater on 2006-08-16
Hey, I'm trying to do the same thing you did but I think I'm stuck at the lilo part!

Can you give me some advice and commands to use to get lilo install right?  :)

Thanks!!!

---

### Post by tactus on 2006-08-16
Sorry, I haven't used Linux much, I just followed the instructions and it worked mostly the way in the "recipe" for me. Except there was one place I needed to type "sudo su" or google up a missing repository package.

Never mind my original post for now, I think I'll give Debian a shoot instead. If that doesn't work either - I might try Dapper again or call Apple care?.. 8-[

---

### Post by hajk on 2006-08-16
> **tactus said:**
> Hi friends.

I Installed 6.06 during the weekend using the [bin-false]("http://bin-false.org/?p=17") tutorial. I have OS X and Ubuntu installed, dual booting with rEfit. Even Compiz is running, but the system is **unstable**. I let it on for say 24 hours, and then it just stops responding, forcing me to do a hard reboot. Then I get errors like "Buffer I/O error on device sda#, logical block ######" and issues with mounting my hda. Resetting PRAM seems to solve the issue, but only for another 24'ish hours.

What in the world is going on, I don't have to reinstall I hope? [-o<

I don't think that your problems originate with Ubuntu Linux, looks more like a bad HD to me... I had similar messages on my 4-year old ThinkPad before it finally gave up the ghost. The install recipe you followed worked fine on my new MacBook, it couldn't lead to those error messages even if you had missed something. :cry:

---

### Post by tactus on 2006-08-17
Yes, it sounds bad. However the S.M.A.R.T status is reported as *verified* in disk utility and I got Debian Etch beta 3 installed yesterday. If it runs stable now, then I might be safe. I think the new Mactels pseudo bios could trigger unknown bugs in a not fully tested setup (like IO issues), but it could also just be a faulty disk... *Holding my breath* :-&

---

### Post by hajk on 2006-08-17
There's a new version of Boot Camp, just out -- may be it solves the GRUB issue so that you don't need the LILO work-around.

---

### Post by 3rdalbum on 2006-08-17
I know this question sounds stupid, but how long does the computer stay up without Compiz?

---

### Post by tactus on 2006-08-19
> **3rdalbum said:**
> I know this question sounds stupid, but how long does the computer stay up without Compiz?

Hi. You know what I've realized, this is what I've found to respect and admire about the Ubuntu community. There is no stupid question, only stupid answers. :)

I didn't try to failseek the Ubuntu installation much, but I've been running Debian Etch nonstop for two days and 15 hours now without problems. It's possible it was just a borked installation. I wonder if it started after playing with Automatix, but that's just a wild quess. :-k

[Update]

For those who might stumble into this thread for whatever reason, Ubuntu 6.10 Edgy is running like a champ on this machine. The 2.6.17.x kernel gives me suspend and sleep and things looks solid. Back to Ubuntu again. :-({|=

---

