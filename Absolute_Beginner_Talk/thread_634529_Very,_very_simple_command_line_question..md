---
title: "Very, very simple command line question."
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by ChristDude on 2007-12-07
If you see something like this to be put in the command line...


> sudo apt-get update
sudo apt-get firefox

Would that be all typed in the command line at one time or one command for each line. Sorry, I need these little questions answered, shouldn't be hard at all :D.

---

### Post by monte48lowes on 2007-12-07
one line at a time. unless the line is "wrapped" like in notepad.

Mike

---

### Post by taurus on 2007-12-07
Yip.  Enter each line and hit the Return key.  By the way, if you want to install something, you need to include the install before the app or you would get an error message.

```
sudo apt-get install *app*
```

---

### Post by ChristDude on 2007-12-07
OK, thank you.:guitar:

---

### Post by bigRahn on 2007-12-07
I have the 'sudo apt-get install xxx' down.  That's easy enough to type.
But, I'm curious where I can find the variations on this command?
For instance, at one point a how-to I was following said to do 'sudo aptitude ...'
What's the difference between this and apt-get?

At the end of  'apt-get -h', it lists references.  Where do I find these?
> See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.

---

### Post by Dr Small on 2007-12-07
Try running:
```
man apt-get
```
Or:
```
man aptitude
```

---

### Post by jss on 2007-12-07
You can link two apt commands with the double ampersand, as in sudo apt-get update && apt-get upgrade. The second command will not execute unless the first command is completed properly. sudo apt-get update && sudo apt-get install app would install the chosen app from one command.

---

### Post by betes on 2007-12-07
> **bigRahn said:**
> IFor instance, at one point a how-to I was following said to do 'sudo aptitude ...'
What's the difference between this and apt-get?


Here's a primer on apt-get vs aptitude:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by bigRahn on 2007-12-08
> man apt-get
Doh! I should have figured that one out.

Thanks for the primer link. I'll check it out after I get some coffee.

---

