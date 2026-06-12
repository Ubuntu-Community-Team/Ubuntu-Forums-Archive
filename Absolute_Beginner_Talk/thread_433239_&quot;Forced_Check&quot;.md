---
title: "&quot;Forced Check&quot;?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by gpilkay on 2007-05-04
When I booted today, it said that my hard drive had been mounted 27 times with no check, and it was 'forcing check'.  The screen counted to 100%, and then booted up with no troubles.

I'm just wondering what this was about, and is it normal?  Some sort of disk check or something?

---

### Post by L Campbell on 2007-05-04
> **gpilkay said:**
> When I booted today, it said that my hard drive had been mounted 27 times with no check, and it was 'forcing check'.  The screen counted to 100%, and then booted up with no troubles.

I'm just wondering what this was about, and is it normal?  Some sort of disk check or something?

Yes, this is normal.

---

### Post by gpilkay on 2007-05-04
Thank you!  So, what is it actually doing?

---

### Post by kpkeerthi on 2007-05-04
It checks for any disk errors similar to windows chkdsk

---

### Post by Inxsible on 2007-05-04
I got a Forced Check too, but then it failed saying

fsck exit status 8

What should i do then ?

---

### Post by L Campbell on 2007-05-05
> **Inxsible said:**
> I got a Forced Check too, but then it failed saying

fsck exit status 8

What should i do then ?

I Googled your question and found this:-

[http://ubuntuforums.org/showthread.php?t=291890](http://ubuntuforums.org/showthread.php?t=291890)

Hope this helps you.

---

### Post by mills on 2007-05-05
just out of curiosity, is it normal to have a force check then another a couple of boots later that says it hasn't been checked in 20-25 mounts?

just asking cuz i get that quite a bit

---

### Post by jvc26 on 2007-05-05
Have you multiple drives? I have the issue occasionally that the drives have been mounted different numbers of times (as I have unmounted and remounted etc at times and then now I get one every 25 boots for my main partition and then one a couple of boots later (again every 25) for my other partition.
Il

---

### Post by mills on 2007-05-05
i got just the one hard drive, does cd/dvd rom drive and cd/dvd rw drive count?

---

### Post by elyask87 on 2007-05-05
Search for a little tool called "Bonager", lets you know how many mounts are left until the next scan and force a scan next time you boot.

---

### Post by insane_alien on 2007-05-05
you can turn the force checking off or change the frequency it runs through some file that i forget where it is.

my laptop gets checked every 33-36 boots and i check my desktop everytime it boots(since it only gets rebooted 4 or 5 times a year i figure its fine)

---

### Post by gantengx on 2007-05-05
> **gpilkay said:**
> Thank you!  So, what is it actually doing?

It checks for error like windows chkdsk. The default setting is to check it after 25-30x boot (for ext2/3).

---

### Post by szf on 2007-05-05
Assuming that the format of the disks is the default ext2/ext3, you can adjust the 'forced check' on number of remounts using the tune2fs utility. It's part of the [e2fsprogs]("http://e2fsprogs.sourceforge.net./") tool suite.

---

### Post by teasum on 2007-05-05
Just a thought--couldn't there be a frontend to this that notifies you that upon shutting down that such-and-such partition should be checked upon the next reboot, and asks for approval?  I ask because I have several partitions (Win XP, Dapper, Feisty, /home, /backups), and it always seems to want to force a check when I'm booting up to check my email before class, or to show a student something, and when it's checking my /home partition it takes a while because of all the files there.  

Just a thought.

---

### Post by liljoe76 on 2007-05-05
as noted by post #10
[http://ubuntuforums.org/showthread.php?t=295262&highlight=bonager](http://ubuntuforums.org/showthread.php?t=295262&highlight=bonager)

---

