---
title: "Can't compile anything"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Michaelg14 on 2008-02-25
I don't know what I did but I can't compile anything.  I get:

checking for C compiler default output file name... 
configure: error: C compiler cannot create executables

What am I missing?

Mike

---

### Post by owbizi on 2008-02-25
Well, I can only ask that: do you have g++ installed?

---

### Post by PhoenixP3K on 2008-02-25
```

mylogin@MYPC:~$ ./ configure
mylogin@MYPC:~$ make
```

Isn't that what is needed? I usually prefer getting packages and install what ever I need.

---

### Post by taurus on 2008-02-25
You need to install the build-essential package first before you plan to build anything from source.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Michaelg14 on 2008-02-25
That definitely helped, I have gotten to:

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check

I also, at this point have failed my sanity check.

---

### Post by taurus on 2008-02-25
What are you trying to compile anyway?

---

### Post by SOULRiDER on 2008-02-25
> **taurus said:**
> What are you trying to compile anyway?

+1, its possible that theres already a Deb package built.

---

### Post by Crafty Kisses on 2008-02-25
Get build-essentials, and that should solve your problems.

---

### Post by Michaelg14 on 2008-02-25
All I am trying to do is update a little panel app.  Why is it such a freakin hassle?

Now I am getting:

checking for pygtk-codegen-2.0... no
configure: error: could not find pygtk-codegen-2.0 script

---

### Post by Michaelg14 on 2008-02-25
I have finally gotten it in and working.  I only had to install 100 megabytes or so of support files.  Thanks to everyone for the help.

---

### Post by eigenstil on 2008-04-04
> **Michaelg14 said:**
> I have finally gotten it in and working.  I only had to install 100 megabytes or so of support files.  Thanks to everyone for the help.
hey there! what exactly did you install? i mean, wich were the 100 MB. i got the same problem when i try to install the "music applet". i would appreciate it, if you can telll me, which packages i have to install. i searched for "pygtk-codegen-2.0" in synaptic, but i didnt find it.:confused:

thx

---

### Post by JebusWankel on 2008-04-07
BUMP

I am also trying to install music-applet-2.3.0 and am in the same boat as eigenstil.

It found be nice for the answer to be on the forums for our progeny. The great thing about open source is it means people don't have to do the same work over again. Sorry for the mini-rant.

---

### Post by Joeb454 on 2008-04-07
If you have to compile from source, then you'll need to open a terminal and run ```
sudo aptitude install build-essential
```

So make sure you have that installed :)

---

### Post by DariusS on 2008-04-07
i think the main problem is dependencies, wherein you should read the documentation of the package you're trying to install...

---

### Post by JebusWankel on 2008-04-07
Seems like pygtk-codegen-2.0 is somewhere in the package python-gtk2-dev which is a big package, lots of dependencies but easily handled by synaptic. It got me to the next step when running ./configure, now it just tells me the packages i need. I think I got it from here. Thanks everyone.

---

### Post by Joeb454 on 2008-04-08
That's the case with compiling from source.

You need to find the dependencies and what package they're in :)

I always find it helps to have 2 terminal's open: 1 for ./configure, and the other to install the dependencies :)

---

### Post by kpkeerthi on 2008-04-08
You can have the build dependencies (source packages) automatically installed with the below command
```
sudo apt-get build-dep <package-name>
```

If you need the dependent source packages for compiling rhythmbox, it would be
```
sudo apt-get build-dep rhythmbox
```

---

### Post by Joeb454 on 2008-04-08
I'd imagine that the above would only work for packages that are already in the repo's though wouldn't it?

I could be wrong, but it just seems like that to me :)

---

### Post by kpkeerthi on 2008-04-08
Yeah its an easy way to install the build dependencies if you are just looking to compile a latest version of something that is in the repo but not the latest.

---

