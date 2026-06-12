---
title: "Uh, compile?"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by erhunter on 2006-04-05
I'm the newest of n00b, so my sob story is this;

I have the distribution of a program I need to run and so I went to the console and tried to configure but the configure program reported that I had no valid compilers on the system or in the system path.

Any advice on this?  make is not found, no gcc, no nothing.

---

### Post by Perfect Storm on 2006-04-05
For basical tools to compile you'll get what you need if you run this command:

```
sudo apt-get install build-essential
```

---

### Post by johnnymac on 2006-04-05
Do this from a terminal...

```

sudo apt-get install build-essential

```

That will get you all the stuff you need.  Also, you may want to check out this wiki:

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

---

### Post by erhunter on 2006-04-05
Thank you thank you.  Ok, next question, where would I get libgc? Better yet, help me fish - how would I search for components such as libgc on my own?

---

### Post by johnnymac on 2006-04-05
I'd use synaptic and use the search that way.  Synaptic is the gui to apt-get and will allow you to search for it.  So if you search for libgc you should get a list of things that match...pretty easy actually.

---

### Post by erhunter on 2006-04-05
Thanks will do.

---

### Post by barebones on 2006-04-05
Also, when your looking a package required to compile, its probabily something that ends in -dev or -devel or something like that (it stands for devlopement). Compiling things became much easier once I figured that out :D

---

### Post by Sutekh on 2006-04-06
I also find this site very useful for searching for packages and easily tracking down dependencies

[Ubuntu Pacakges](http://packages.ubuntu.com/)

---

