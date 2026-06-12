---
title: "New and Confused"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-06
Alrite, i have been on these forums for a few days and have gotten alot of help, but at the same time i do not understand most of the help
hahaha
I am quite comfortable with windows, as are most people.
What i need is a walk through on Ubuntu Linux
From installing packages using synaptics and to how the terminal works

I am having trouble with java the most i seem to have downlaoded it but idk how to isntall it
I read install instructions but they are over my head

If anyone can help me out with like a beginners beginners guide to Newest Newbies
It would be much appreciated.

Thanx

---

### Post by wolfmaniac on 2006-07-06
check this 
[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

may be it is useful

---

### Post by lee45 on 2006-07-06
i got nothing on beginners guide, but i did manage to install java and get it working (so i can play online euchre).
I got it working with sudo-apt get install , but i noticed later that its listed under add/remove programs
that one usually works pretty easy, so i'd look there first.
You may have to add repositories with your synaptic package manager.
Hope that helps

---

### Post by aysiu on 2006-07-06
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) isn't a bad place to start.

For Java, try this:
1. Enable extra repositories
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

2. Install Java by pasting this command in the terminal ```
sudo aptitude update && sudo aptitude install j2re1.4-mozilla-plugin
```

---

### Post by IrishGangsta on 2006-07-06
aysiu

I did what u just said there and i guess it went ok
 I received no errors
After i typed that line into the terminal 
Do i have to do anything else?

And does this install java runtime environment?

---

### Post by Frank Golden on 2006-07-06
[QUOTE=IrishGangsta]aysiu

I did what u just said there and i guess it went ok
 I received no errors
After i typed that line into the terminal 
Do i have to do anything else?

And does this install java runtime environment?[/QUOTE]
Hi IrishGangsta, 
   Was in your position about a year ago when I started playing with
Ubuntu. Back then it was Hoary and Breezy. Today I have a very stable
version of Ubuntu 6.06 LTS on my Acer Aspire 5672 lappy along with
XP pro. It was a sometime frustrating, sometime uphill battle.
But with the help of the folks at these forums and Google I am finding
that I understand Linux a lot better. I ain't an expert like aiysu or others
here but I can tell you that if you keep at it you will progress
I eventually plan to ditch XP altogether. 

For more linux info check out 

[http://forums.scotsnewsletter.com/index.php?showforum=14](http://forums.scotsnewsletter.com/index.php?showforum=14)

Great bunch of folks there also.
Hang in there.

---

### Post by IrishGangsta on 2006-07-06
to tell you the truth i was thinking about just giving up on Linux here
I mean i do understand windows but this is crazy

But i mean obviously everyone has trouble starting off but i guess its no reason to quit

Thanx fo the inspiration and that link looks helpful!

---

### Post by Nikusan on 2006-07-06
[QUOTE=IrishGangsta]aysiu

I did what u just said there and i guess it went ok
 I received no errors
After i typed that line into the terminal 
Do i have to do anything else?

And does this install java runtime environment?[/QUOTE]

You might need to type this in a terminal:
```
sudo update-alternatives --config java
```

---

### Post by badlogic on 2006-07-06
go to that link it will show ya alot. Make sure you set up the repository's in the first part of the wiki befor you do anything else.




[http://ubuntuguide.org/wiki/Dapper]("http://ubuntuguide.org/wiki/Dapper")

---

