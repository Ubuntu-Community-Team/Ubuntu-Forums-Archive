---
title: "Finding an installed .deb program"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by joel1a on 2007-03-22
I installed Ubuntu a few weeks ago and quikly found the easy and friendly use very pleasing.  Through the forums and web searching I have found how to get my Graphics card to work,  install codecs and much more.  Now to make the complete switch over from Windows I need two things...  One is I have a Creative Zen vision M and need it to play nice...  I found that I need the libmtp-0.1.4...  Found it but can't compile it, and don't know where it should go.  Problem for another post I guess. 

I also record a Internet radio show and found a program that looks like it will do nicely (Internet DJ Console, [http://www.onlymeok.nildram.co.uk/](http://www.onlymeok.nildram.co.uk/) ) found a .rpm package figured out how to change it to a .deb with Alien.  Ran it and it worked. (made sure that dependences were installed)   But I don't know where it went!  Can anyone help?  Also how do I launch it...  I can find a tutorial to make a short cut I'm sure :)

---

### Post by tipsqueal on 2007-03-22
Try the command whereis. Just type "whereis" then the name of the program.

---

### Post by scxtt on 2007-03-22
you should be able to install libmtp from the repos (w/ **universe** repository enabled): **sudo aptitude install libmtp2**:
```
[font=courier]:> aptitude search libmtp
Password:
p   libmtp-dev                                          - Implementation of Microsoft's MTP
p   libmtp2                                             - Implementation of Microsoft's MTP[/font]
```

---

### Post by joel1a on 2007-03-22
"whereis" isn't turning up anything typed in idjc, and Internet DJ Console.   and the libmtp isn't there... I believe that I have all the repositories turned on. 

 Brain...  Frying...  Must...  get...  to... Mountain Dew!!!

---

### Post by scxtt on 2007-03-23
as long as you have:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

you should be able to see libmtp2 just like i do ...

---

### Post by joel1a on 2007-03-23
ahh,  I think that is the problem...  How do I add that.  I have ver. 6.06 do I have to up grade?

Can I do that with the source.list?

---

### Post by scxtt on 2007-03-24
yes, that'll go in sources.list ... just change "edgy" to "dapper" ...

**nano /etc/apt/sources.list**
add (or just remove a #) for the entry: deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
**ctrl-o** (to save)
**ctrl-x** (to exit)
**sudo aptitude update** (to "load" the new repo)
**sudo aptitude search libmtp2** (now you should see it)

---

