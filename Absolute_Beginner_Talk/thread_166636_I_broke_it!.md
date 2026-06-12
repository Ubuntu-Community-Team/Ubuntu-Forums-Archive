---
title: "I broke it!"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by therunnyman on 2006-04-26
I'm writing to you from the failsafe terminal, as I can't boot into GNOME.  Something about ICE authority, and a failure to make a /dev something or other.  I shall try to get the exact error message to you, but, meantime, any ideas?

---

### Post by halfvolle melk on 2006-04-26
What did you do to break it?
Here's a stab in the dark: 'startx'.

---

### Post by garner_nc on 2006-04-26
I've seen this before in a failed IceWM installation. Don't remember how I fixed it though.  The exact error message would be a BIG help.

All the Best,
Doug White

---

### Post by kaaredyret on 2006-04-26
[QUOTE=garner_nc]I've seen this before in a failed IceWM installation. Don't remember how I fixed it though.  The exact error message would be a BIG help.

All the Best,
Doug White[/QUOTE]

No, I don't think you broke anything. It broke itself. Try entering this:

sudo chown loginname .ICEauthority

**loginname** is of course the username you tried to login with.

I have had this problem 10+ times, that I suddenly was not able to login. I would like to see how the Average Joe fixes this problem. Anyway, I hope I could help you.

---

### Post by therunnyman on 2006-04-26
Thanks for helping so quickly, gents!

Um, I tried everything to get a precise copy of the error message here, but I can't, not yet.  What it appears to be getting at is "WARNING: cannot read /home/myusername/.ICEAuthority".  I had a look at that file: it's there, with appropriate permissions (I think), but it's blank.

What else can I give you to go on...um, in shame, I confess to you I shut GNOME down to have a look at a couple of things on my Windows XP disk, then rebooted to GNOME to find that error message.  All is well in grub, menu.lst, and fstab.  Umm, nothing out of the ordinary happened today, and I always monitor the system closely with GKrellM (hardware was 5x5 when I left).

Let me see if I can get more for you.

therunnyman

---

### Post by therunnyman on 2006-04-26
[QUOTE=kaaredyret]No, I don't think you broke anything. It broke itself. Try entering this:

sudo chown loginname .ICEauthority

**loginname** is of course the username you tried to login with.

I have had this problem 10+ times, that I suddenly was not able to login. I would like to see how the Average Joe fixes this problem. Anyway, I hope I could help you.[/QUOTE]


That did it.  Thanks kindly guys!

What on earth happened?  Just a bug?

therunnyman

---

### Post by kaaredyret on 2006-04-26
[QUOTE=therunnyman]That did it. Thanks kindly guys!
What on earth happened? Just a bug?
therunnyman[/QUOTE]

Good! :KS 

**Bug!** I don't know what else to call this 'inconvenience'. It was not your fault, that much I know. Write the solution down on paper, I had to use it many times.

---

### Post by therunnyman on 2006-04-26
[QUOTE=kaaredyret]Good! :KS 

**Bug!** I don't know what else to call this 'inconvenience'. It was not your fault, that much I know. Write the solution down on paper, I had to use it many times.[/QUOTE]

Duly written.  Thanks again, kaaredyret.

therunnyman

---

### Post by ronmarley1 on 2006-04-26
This happened to me one time, and I seem to remember the solution I found mentioning something about K3b causing the problem, but that was a while ago...

---

