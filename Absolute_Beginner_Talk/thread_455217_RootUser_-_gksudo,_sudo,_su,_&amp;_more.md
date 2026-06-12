---
title: "Root/User - gksudo, sudo, su, &amp; more?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-05-26
Being a new linux user, I am still somewhat confused by the terminology, how to properly "log in as root", & for that matter, "log out of root"?

Is there a good tutorial on what all these terms mean & how/when to use them, & this is the tricky part; in a language that a recent windows convert can understand?

I read some of the stuff in the wikis, & on forums, etc., but a lot of it is geared towards folks who already have a working knowledge of linux.

I need newbie stuff!

Thanks! :)

---

### Post by Bachstelze on 2007-05-26
You do not login as root in Ubuntu. When you want do to something with root privileges, you use sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

That's really all you'll need to know about it. If you want to know something else, it's better to ask more precise questions.

---

### Post by starcraft.man on 2007-05-26
[Sudo]("https://help.ubuntu.com/community/RootSudo")

[Su]("http://en.wikipedia.org/wiki/Su_%28Unix%29") isn't used in Ubuntu unless you actually enable that, since you don't know it, don't worry about it. 

That should do it, stick to plain sudo, can't go wrong with it :).

Oh and gksudo, is just the proper command for getting a graphical app to launch with sudo power, like gedit or nautilus. Thats it, have fun.

Edit: Arrrr, hymn beat me to it :p

---

### Post by Bachstelze on 2007-05-26
I win :p

---

### Post by starcraft.man on 2007-05-26
> **HymnToLife said:**
> I win :p

*grumbles very loudly so hymn can hear* Next time... next time *stares and then scurries off to another*

---

### Post by discmaster on 2007-05-26
Thanks for the info! 

I was looking to get a deeper understanding of the OS, & really know what all the term. means, as opposed to windows lingo.
And also, some of my very basic newb. questions, such as; file permissions, why do I need to create a "home" partition, & all those newbie related things that you guys understand, but us "babes" don't!

Are the "dummies" books a good source of elementary & _Useful_ info., or would you consider them a waste of $$$?

---

### Post by whatrucrazy on 2007-05-26
hey,
i found it difficult too at first, but you do get the hang of it pretty quickly.  there are intro websites etc out there but really you just have to hope someone is thinking of newbies when they write up a howto, and most people do. if you do have problems just say so, ask "what is it i actually type in, and what does it mean/do".

for eg: if you need to do something as root, ie "adminstrator" in windoze speak (the top user), just type "sudo" befor whatever you need to do. eg: if ineed to change something in the file "xorg.conf" which controls the way my window manager operates, like the possible resolutions my monitor might display or the driver it uses, if i type "nano /etc/X11/xorg.conf"  (nano is just a text editor, i could also use "gedit /etc/X11/xorg.conf" to use the gedit editor, and the /etc/X11/xorg.conf is the file path name, the adress where the file resides), well if i just type that, i can see the file but not change it, as i am not accessing it as a root user. but if i type "sudo nano /etc/X11/xorg.conf" then i can read it and write to it, as i am (for this one command, that of opening the file designted, the xorg.conf) acessing it as root by typing sudo before my command. This works for all commands that require root privledges to execute, so you will see it quite often.
There are other ways of doing this, you can log in as root, but for using an ubuntu system it is so much easier and safer to just use "sudo" and make the single command a root command, otherwise you risk the whole operating system changing in possibly bad ways - logging in as root gives you a lot of power, power to destroy your whole system if you do the wrong thing!

anyway, my point was if you are unsure just ask, most people in this forum will gladly tell you exactly what buttons to hit, what to type, and why you typed that command, just be clear that you need to know explicitly. And from experience i can tell you, pretty soon it will make alot more sense.

good luck!

---

### Post by JerryAtrik on 2007-05-26
As a newbie like you,  I find the "Official Ubuntu Book" very helpful I got it from Amazon .co.uk from the used book section for half the official price .The best £12 I have spent in a long while

---

### Post by starcraft.man on 2007-05-26
> **discmaster said:**
> Thanks for the info! 

I was looking to get a deeper understanding of the OS, & really know what all the term. means, as opposed to windows lingo.
And also, some of my very basic newb. questions, such as; file permissions, why do I need to create a "home" partition, & all those newbie related things that you guys understand, but us "babes" don't!

Are the "dummies" books a good source of elementary & _Useful_ info., or would you consider them a waste of $$$?

[Psychocats]("http://www.psychocats.net/ubuntu/") and [Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") for beginner questions. If their not covered, just ask em here. I don't think people need to pay anything to learn Ubuntu.

Edit: yay, beat Aysiu to post :p.

---

### Post by aysiu on 2007-05-26
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by whatrucrazy on 2007-05-26
hmmmm, does aysiu ever sleep?
hard workers, how are us procrastinator lazies supposed to get some kudos...

:)

---

### Post by starcraft.man on 2007-05-26
> **whatrucrazy said:**
> hmmmm, does aysiu ever sleep?
hard workers, how are us procrastinator lazies supposed to get some kudos...

:)

Hmmm, I don't know about aysiu, but I don't sleep much, I just happen to like being on here learning about linux and helping others often. Helps me learn more about Ubuntu, now off to lunch, while I don't sleep much all this typing and answering sure does make this Zealot HUNGRY!!!

Adios till after I eat.

---

