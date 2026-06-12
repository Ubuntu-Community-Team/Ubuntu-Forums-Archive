---
title: "Cannot run Live CD"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by richie42 on 2007-07-10
When I do the live CD and restart the PC, it is good, but when I try to install UBUNTU, is says this



[201.252000] Buffer I/O error on device fd0, logical block 0
[239.356000] Buffer I/O error on device fd0, logical block 0

---

### Post by davidjmayo on 2007-07-10
Depends on the spec of your PC (how much RAM? You need more for the install)

download and try the alternate CD which is text based and so uses less resources

---

### Post by st0nes on 2007-07-10
This looks like a disk error -- do you have another OS & can you boot to it?

---

### Post by richie42 on 2007-07-10
> **st0nes said:**
> This looks like a disk error -- do you have another OS & can you boot to it?

huh?



I got the UBUNTU disk in the mail.

---

### Post by st0nes on 2007-07-10
Sorry, my question was ambiguous: I don't mean the liveCD, I mean your hard drive.  Is that working with another OS?

---

### Post by richie42 on 2007-07-10
> **st0nes said:**
> Sorry, my question was ambiguous: I don't mean the liveCD, I mean your hard drive.  Is that working with another OS?

No, it only has Windows XP.

---

### Post by st0nes on 2007-07-10
OK, if it works with XP then I'm wrong about it being a hard drive failure.

---

### Post by Seisen on 2007-07-10
Here this will help.

[https://answers.launchpad.net/ubuntu/+question/7697]("https://answers.launchpad.net/ubuntu/+question/7697")

---

### Post by richie42 on 2007-07-10
> **Seisen said:**
> Here this will help.

[https://answers.launchpad.net/ubuntu/+question/7697]("https://answers.launchpad.net/ubuntu/+question/7697")

I have **_NO CLUE _**what that means at all.

---

### Post by fastpakr on 2007-07-10
Which part do you not understand?  In the thread, the responder asks some pretty specific questions about the users's system config, has him run a command to test, then determines based on the result that the error is not an indication of a show stopping problem.

---

### Post by Seisen on 2007-07-10
Type this in the command line

```
lsmod | grep floppy
```
then post what is says then we will go from there.

---

### Post by richie42 on 2007-07-10
> **fastpakr said:**
> Which part do you not understand?  In the thread, the responder asks some pretty specific questions about the users's system config, has him run a command to test, then determines based on the result that the error is not an indication of a show stopping problem.

I don't undersrtand what the guy said to do

---

### Post by fastpakr on 2007-07-10
If you want help, you've GOT to be more specific.  He asked the user to run a command.  Do you not understand how to use the terminal, or exactly what to type in, or what?

---

### Post by Seisen on 2007-07-10
To open up the terminal go to Applications>Accessories>Terminal then post the command I gave you previously.

---

### Post by richie42 on 2007-07-10
ok, it is working fine with the text based installer

---

