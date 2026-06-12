---
title: "HELP!!! Ubuntu 7.10 upgrade..."
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by aj5string on 2007-10-19
Hi...

I started the Upgrade to 7.10 today.  Started it downloading/doing its thing - told my girlfriend that under no circumstnaces should she turn the computer off.

When i got back it was off (guess who that was!), and now ubuntu wont boot.

There are some extra entrys on the grub screen, so i guess its half way through?

What can i do to get ubuntu back!?!

Alex.

---

### Post by Sef on 2007-10-19
Do you have an older version of Ubuntu or another distro?

---

### Post by aj5string on 2007-10-19
An older version of ubuntu.

I was upgrading from 7.04 to 7.10 i think.

I just went to the update manager and did it that way...

Alex.

---

### Post by Hospadar on 2007-10-19
you might try using a livecd and see if you can log in as your old user and run the update that way.  Otherwise, I would try and use the livecd to back up your data and do a fresh install.

---

### Post by aj5string on 2007-10-19
How would i go about that?

Boot off of the livecd?  I'm not sure how i'd go about logging in, or getting my data and doing a fresh install?

Alex.

---

### Post by roderikk on 2007-10-19
Are you still able to login to grub using the 'recovery mode'? (it should give that as an option behind each line, if the first doesn't work try the following kernel).

Otherwise go there and when you arrive at the command prompt just type:

aptitude update
aptitude dist-upgrade

(Sudo not necessary as you enter as root).

Hopefully that helps.

---

### Post by aj5string on 2007-10-19
Thats worked!

It found an error and told me what to run, and im back in now!

Alex.

---

