---
title: "Help for a REAL begginer please."
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by TheSeb on 2008-02-15
Hi,
First of all... thank you all for helping by responding so quickly. Sadly, even here on absolute beginner talk, I have trouble understanding much of the advice you give me.

for example, phrases such as:

> It should be in a .xpm.gz file format.
Download it and copy it to /boot/grub/

```

Code:

sudo cp imagename /boot/grub/
```

now edit /boot/grub/menu.lst with your favorite editor
and near the top add a line like this
splashimage = (hd0,1)/boot/grub/usplash.xpm.gz

I know questions such as "how do I get to boot/grub" or "where the heck do I input the code" ... or "what is an editor for .lst files" seem beyond basic and might not be answered here.

Therefore... is there some ubuntu-bible-book or on-line resource that actually takes you step by step from the most basic stuff... without killing you with stuff you don't understand right off the bat.

Sorry if this sounds negative, I really appreciate that you guys are here - even if I don't understand you :)

---

### Post by kpkeerthi on 2008-02-15
To know your way around in Ubuntu spend some time reading [ubuntu guide]("http://help.ubuntu.com"). 
Then [Linux Commands]("www.linuxcommand.org") for some command line stuffs.
And then, read the links in my signature to know what can be done/customized in ubuntu.

---

### Post by finer recliner on 2008-02-15
you input those commands in a terminal.

where is the terminal?

answer:
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)


check out the other help pages on that site. i found them very useful as a newbie too

---

### Post by TheSeb on 2008-02-15
Thanks,

What about books? Are there any good ones... or any to stay away from?

I would really like some resources with 
1. A lot of tutorials
2. Tons of pictures
3. 1+2 together

I learn best when I do stuff ...

---

### Post by drummingpariah on 2008-02-15
As far as books go, they tend to be outdated by the time they get published.  Ubuntu changes fairly rapidly, and online resources tend to keep up with that best.  The Ubuntu wiki is an excellent resource, but the forum tends to be better.  We're willing to answer whatever questions, no matter how basic they might be, right here.

---

### Post by Technophobia on 2008-02-15
I guess you could say thousands of pictures for every article.

[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

---

### Post by seventhc on 2008-02-15
I understand your confusion and don't worry about it, but what is the original problem?
I'd rather start clean rather than looking at commands you were told to do. ;)

---

### Post by TheSeb on 2008-02-15
> **seventhc said:**
> I understand your confusion and don't worry about it, but what is the original problem?
I'd rather start clean rather than looking at commands you were told to do. ;)

The above sample was just an example from some threads I looked at (or started) ... and although they were on topic.. I do not understand them enough to use the knowledge to my advantage...

ex threads are:
[http://ubuntuforums.org/showthread.php?t=697247](http://ubuntuforums.org/showthread.php?t=697247)
[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

---

### Post by kpkeerthi on 2008-02-15
[Practical Guide to Linux Commands, Editors & Shell]("http://www.amazon.com/Practical-Guide-Commands-Editors-Programming/dp/B000P28VO0/ref=sr_1_1?ie=UTF8&s=books&qid=1203059174&sr=1-1") 
[How Linux Works - What every super user should know]("http://www.oreilly.com/catalog/1593270356/")
- My favorites. I enjoyed reading those books. They teach you the **fundamentals** and are worth buying. The basics never change irrespective of the distro you may be using.

---

### Post by seventhc on 2008-02-15
Looks to me like you want a dual boot.
Haven't read both threads, but I read a few posts from both.
So dual boot is what you want?
You have windows installed now?

---

### Post by Ex-windows on 2008-02-15
> **TheSeb said:**
> Thanks,

What about books? Are there any good ones... or any to stay away from?

I would really like some resources with 
1. A lot of tutorials
2. Tons of pictures
3. 1+2 together

I learn best when I do stuff ...
There is The Official Ubunt Handbook and another called Ubuntu Hacks. Both areat (should be) Barnels & Nobles Both are Very Easy 2 read.

---

### Post by Scut_Farkus on 2008-02-15
Hey!

I can finally help someone!  :)

I've really been enjoying this book by Rickford Grant.  You can get it on Amazon.com for about $20.00 or so.  Mine came with an Ubuntu disk (Dapper Drake), but I believe there's a 2nd edition that has Fiesty Fawn support.  Anyway, the book is called _Ubuntu Linux for Non-Geeks:  A pain-free, Project-Based, Get-Things-Done Guidebook_

The reviews on Amazon will do a better job of describing the book than I can here.  Please remember that depending on the version of Ubuntu you're using (I apologize if you mentioned it earlier) there might be some changes and/or differences in the projects the author spells out for you.  The basics will be the same, though.  What are repositories?  Why do I need them?  How do I add new ones?, etc.  He'll guide you through all of that in an easy to read and understand format.

Enjoy!

---

### Post by erginemr on 2008-02-15
I suggest you to read these easy to follow tutorials:

1. Ubuntu Desktop Guide:
[https://help.ubuntu.com/ubuntu/desktopguide/en_GB/](https://help.ubuntu.com/ubuntu/desktopguide/en_GB/)

2. Tuxfiles: (command line guide)
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

3. How to install ANYTHING in Ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by hyper_ch on 2008-02-15
also use a descriptive thread title next time and not a generic "need help"

---

### Post by TheSeb on 2008-02-15
> Looks to me like you want a dual boot.
Haven't read both threads, but I read a few posts from both.
So dual boot is what you want?
You have windows installed now?

Yep, I have VISTA... and I got it to dual boot... but now I would like to modify the boot screen to my liking. 

1. I want to use GRUB, or Gfxboot. Something that doesn't look like DOS, Gfxboot splashes look great!

2. I would also like the compy to skip the bootscreen by default... unless I press a button or something. For example: I want to use Windows: So I press F4 as the computer is starting up... and it takes me to the boot screen. However, if nothing is pressed - the computer goes straight to Ubuntu. Does that make sense?

---

### Post by drummingpariah on 2008-02-15
> **hyper_ch said:**
> also use a descriptive thread title next time and not a generic "need help"

That's probably the best advice one could offer.  Describe the problem as specifically as possible, always.

---

