---
title: "Explanation of sudo, su, &amp; gksudo"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by dwiedenfeld on 2007-08-30
Can someone please give me a clear explanation of the differences between sudo, su, and gksu, and gksudo? I've read different threads here and elsewhere in forums and wikis and _Linux for Dummies_, but I still don't understand. (This is why I'm at "Absolute Beginner Talk", of course.) 

I get some of the difference between su and sudo, and I see instructions to use gksudo, but why?

---

### Post by p_quarles on 2007-08-30
Aysiu has a great explanation of gksudo [here]("http://www.psychocats.net/ubuntu/graphicalsudo").

Simply put, though:
su = switch user; if no name is entered, it switches to root
sudo = run a command *as *root, without actually logging in
gksu[/do]=run a command as root in the Gnome GUI. For KDE, it's "kdesu."

---

### Post by jamesstansell on 2007-08-30
su is to switch users.  It can be used to switch to root (although you wouldn't normally do that on ubuntu) but it can also be used to switch to other users.  So, for example, I can switch to my son's account to check something out without having to do a full graphical login to his account.

sudo is for running commands as the super user (root).  Use it when you're running a console application at a command prompt.

gksudo is for running commands as the super user when you're using alt-F2 or setting up a shortcut for a graphical program, since the command needs to interact with GNOME in those cases.  You should use this for graphical programs even if you're typing at a command prompt.

gksu is also for running graphical programs, but can use su instead of sudo.  I don't know much about this yet, and I'd recommend that you concentrate at first on becoming familiar with sudo and gksudo.

Did that help any?  I assumed above that you already know that regular applications should be run as a normal user whereas most administration requires the super user account.

Regards,

-james.
.

---

### Post by zzztownsend on 2007-08-31
thanks for the info chaps

Matt

---

### Post by Steveway on 2007-08-31
You don't need to use gksudo because it is just a symlink to gksu.
Those are the same commands and do the same things.
You spare two letters if you type gksu instead of gksudo and you get the exact same result.

---

### Post by dwiedenfeld on 2007-08-31
> **p_quarles said:**
> 
gksu[/do]=run a command as root in the Gnome GUI. For KDE, it's "kdesu."


Thanks--nice clear explanation, although I still have at least question:

So, when I'm in a terminal window I'm not in Gnome at all? But I can do something that affects Gnome? (OK, now it's obvious that I really am an Absolute Beginner, ?no?) This relates to me response to jamesstansell too.

---

### Post by dwiedenfeld on 2007-08-31
> **jamesstansell said:**
> gksu is also for running graphical programs,

So how do I know if it's a graphical program? If it's a program you're not familiar with, do you just try it one way and see if it works? And if I use sudo when I should use gksudo, or vice versa, what happens?

---

### Post by dwiedenfeld on 2007-08-31
I'm with zzztownsend, too: Thanks for the info, chaps.

---

### Post by jw5801 on 2007-08-31
sudo and gksudo will both work for graphical and non-graphical apps (as far as I'm aware anyway). It's just that running a graphical app using sudo rather than gksu can sometimes mess with file permissions (aysiu's guide as referenced above explains). If you run a command that does something in the command line (ie. only outputs to the terminal you have open) then that's a command line app. Anything that opens another window or displays anything outside your terminal window is a graphical app.

---

### Post by rsambuca on 2007-08-31
> **jw5801 said:**
> sudo and gksudo will both work for graphical and non-graphical apps (as far as I'm aware anyway). It's just that running a graphical app using sudo rather than gksu can sometimes mess with file permissions (aysiu's guide as referenced above explains). 

Then I would say that it really doesn't work!

---

### Post by dwiedenfeld on 2007-08-31
Thanks, jw5801. I'll have to say I'm with rsambuca too. I read aysiu's (very good, very helpful) explanation, and it looks like you can screw things up, but **probably** won't. And it's hard to tell what will and what won't work. So you really just have to know which is the one to use. Unfortunately for us noobs, that's not very easy.

---

### Post by jw5801 on 2007-08-31
That should have read as a "work" in inverted comma's to make more sense. Meaning that the app will run and most usually be fully functional, but there is the potential for bad things to happen. Kinda like if your goal was to get to the bottom of a building: jumping off the roof would "work," but taking the stairs is probably the safer option! :p

---

### Post by p_quarles on 2007-08-31
> **dwiedenfeld said:**
> Thanks, jw5801. I'll have to say I'm with rsambuca too. I read aysiu's (very good, very helpful) explanation, and it looks like you can screw things up, but **probably** won't. And it's hard to tell what will and what won't work. So you really just have to know which is the one to use. Unfortunately for us noobs, that's not very easy.
It actually is pretty easy, you just have to know some basics about the program you want to use (and you really don't want to run an unknown app as root, anyway).

Basically, if the terminal command launches an application that opens a new window of any kind, it's considered a "graphical" application. In other words:
non-graphical app = an application that returns all its output as text, inside the terminal window
graphical app = anything else

Examples of non-graphical apps: netstat, lynx, apt-get, tar, and nano

Examples of similar graphical apps: etherape, firefox, synaptic, fileroller, and gedit.

Play around with those a little bit, and you'll get the idea.

And while it is true that most of the time using "sudo" to run a graphical app won't cause any apparent problems, it's still nothing less than playing Russian roulette with your computer.

---

### Post by p_quarles on 2007-08-31
> **jw5801 said:**
> That should have read as a "work" in inverted comma's to make more sense. Meaning that the app will run and most usually be fully functional, but there is the potential for bad things to happen. Kinda like if your goal was to get to the bottom of a building: jumping off the roof would "work," but taking the stairs is probably the safer option! :p
So you're saying I bought that reusable parachute for nothing?!? Oh snap. :)

Seriously, though, well put.

---

### Post by ts51 on 2007-08-31
using sudo usually works just fine for antying requiring root privelges. .

---

### Post by p_quarles on 2007-08-31
> **ts51 said:**
> using sudo usually works just fine for antying requiring root privelges. .
Yes, and running with scissors usually works just fine for not puncturing your own lungs.

---

### Post by jw5801 on 2007-08-31
[Fun metaphors for using "sudo" with graphical applications!](http://ubuntuforums.org/showthread.php?p=3288599) :D

---

### Post by dwiedenfeld on 2007-08-31
Great info, guys & gals. I actually think I DO understand a bit better which to use, and how to decide whether it's better to run with scissors or jump down the stairs?

---

