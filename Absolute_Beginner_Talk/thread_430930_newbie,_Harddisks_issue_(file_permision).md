---
title: "newbie, Harddisks issue (file permision?)"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by adi-n on 2007-05-02
hey, i'm a newbie so please be easy on me...

first time installing linux and it's not so bad at all :)
i have 2 harddrives, first one had windows xp deleted it all and installed ubuntu, second one is my multimedia hdd with all my movies pictures etc

on the second hdd i cant delete no files like i dont have permision. on the properties the owner seems to be root and not me (adi)


why?

thanks!

---

### Post by Hase on 2007-05-02
Give us an "ls -l" response from the directory in question.  That is, from command line.  If you need further explanation as to what I mean, just ask.

---

### Post by Ianman on 2007-05-02
I am guessing you used the second hard drive in windows as well? Meaning it is NTFS. By default you only have read rights on NTFS partitions. As I understand it though, there should be a way to give yourself write access to NTFS partitions.

Let me know if this is indeed the case, then we will find a solution for ya ;)

---

### Post by adi-n on 2007-05-02
thanks hase but i dont know how... 
lanman you are right thanks! now what can i do?

im starting to miss my old xp :(

---

### Post by taurus on 2007-05-02
If you want to write to ntfs, you need to use ntfs-3g driver.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Ianman on 2007-05-03
> **adi-n said:**
> thanks hase but i dont know how... 
lanman you are right thanks! now what can i do?

im starting to miss my old xp :(

Don't give in! Every new system has a learning curve. Just keep using Ubuntu and you will get the hang of it. Think of all the benefits! (Security, no viruses, no adware).

---

### Post by kelvin spratt on 2007-05-03
both edgy and fiesty can read and write to windows partions but you need to enable them but in add remove programs is easy in fiesty if your not sure or download automatix for either version i personal find the automatix 
version does a better job with permissions you can then drag drop read/write to all windows partitions simple

---

### Post by teddybairs1 on 2007-05-03
I agree, don't give up. those who give up don't learn how to do it, they only learn how to give up more easily.

One idea, if it is possible, is to back up all of your multimedia on DVDs/CDs through a burner and then reformat that drive as an ext3 (native linux), and then reload it with your stuff. This will give you read/write access with no problems.

changing over to Linux of any flavor will require a learning curve and a bit of tolerance for some of the less than user-friendly things we run into. You will eventually learn, and you will eventually come to appreciate the benefits of running Linux in spite of the obstacles which still remain.

Consider, that if you had bought a mac to replace your windows system, you would have had to experience the same learning curve because it too is completely different from Windows. Does this mean OSX is a bad OS? No. Absolutely not. But it is different. So is Ubuntu.

I've had to fight with several things, annoyances, about my laptop and desktop hardware and programs with Ubuntu. Were they insurmountable? No, but I did have to ask here on the forum and do some experimentation and digging on my own. Was it worth it. Absolutely.

There are also good Ubuntu books now available at Barnes and Noble and Borders which should help you out as well.

Keep it up.

---

