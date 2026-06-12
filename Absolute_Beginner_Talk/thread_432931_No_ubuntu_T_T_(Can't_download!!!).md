---
title: "No ubuntu T_T (Can't download!!!)"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by -Soul_Reaper- on 2007-05-04
I went to Ubuntu.com, went to download, tried at least 5 mirriors, NONE WORKED! The all give me a 'not found' message:( :confused: 
Ps. I did the steps right, checked the proper things and all...

Is m$ foiling my attempt to go open source?

---

### Post by laidback on 2007-05-04
Shame, needless to say I've always managed to get access when needed, that's a great help isn't it. Can you get a copy of the install CD via another route?  Try:-

[http://www.linux-man.co.uk/shop/](http://www.linux-man.co.uk/shop/)

I have no connection with Andy, who's shop it is, but he has always been prompt and provides what seems to me to be a good service. 

It's definitely worth the effort and wait.

---

### Post by Seisen on 2007-05-04
Try this mirror it just worked for me.
[http://us.releases.ubuntu.com/7.04/]("http://us.releases.ubuntu.com/7.04/")

---

### Post by -Soul_Reaper- on 2007-05-04
> **Seisen said:**
> Try this mirror it just worked for me.
[http://us.releases.ubuntu.com/7.04/]("http://us.releases.ubuntu.com/7.04/")

Thanks, it is downloading as i type this. :D
One question though, is there any free 3D modeling tools for Ubuntu, that and a c++ compiler/writer thing?
I was wanting to get into both of those, and was going to download M$'s free version, but i would rather get one that can be used on Ubuntu.

---

### Post by Tomosaur on 2007-05-04
> **-Soul_Reaper- said:**
> Thanks, it is downloading as i type this. :D
One question though, is there any free 3D modeling tools for Ubuntu, that and a c++ compiler/writer thing?
I was wanting to get into both of those, and was going to download M$'s free version, but i would rather get one that can be used on Ubuntu.

You bet :)

Blender is the most popular open-source 3d modeller out there. There was even a film made with it, check here: [http://www.elephantsdream.org/](http://www.elephantsdream.org/)

As for compilers, after you've installed ubuntu, open up Synaptic Package Manager and install the build-essential package. To do it via the command line, open up the terminal and type:
```

sudo aptitude install build-essential

```

You will be asked for your password, it's the same one you use to log on to the machine. You won't see it being typed, so be sure to spell it correctly!

build-essential installs much of the absolutely necessary stuff, but for IDEs, text editors, compilers for other languages etc, either use Synaptic and look through the development categories, or type:
```

apt-cache search <search term>

```

in the terminal. Search term could be something like 'python':
```

apt-cache search python

```

It will give you a list of packages which match that term. Synaptic gives you a more flexible search function though.

---

### Post by -Soul_Reaper- on 2007-05-04
Wow, the art on that movie looks good. Thanks a bunch, that is definately gonna me more reason to get Ubuntu.

 But can i use it if i am runnning off of a 'live' disc?

---

