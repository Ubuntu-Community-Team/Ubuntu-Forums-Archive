---
title: "Macbok pro 1.1 with Ubuntu 8.10 Just a couple of questions"
date: 2008-12-20
forum: Apple Hardware Users
---

### Post by mongrel boy on 2008-12-20
Hi everyone, hopefully I'll get some more quality help here again!!
I'm running Ubuntu 8.10 on my Macbook pro 1.1 which I got second hand. The thing that causes the most problems is the fact I'm a total beginner! Although I work in infrastructure, it's more the installation itself than networks so I'm not exactly Mr. I.T.
When I got my macbook pro the hard disk was dying (due to a drop or two!). So I got onto the internet and found out how to replace it and did so. I was proud of myself but I couldn't get a hold of a copy of Mac OS X that would work and because I'm not an expert in the whole computer field I just replaced the hard disk and installed Ubuntu without taking down any details of the macbook system itself!
I know, very silly (but at the time I didn't have a clue).
So now I know it's a macbook pro 1.1 (serial No. A1150)
However I recently installed google Earth and I have a problem with flickering. This leads me to three questions:
1. Can anybody please give me the full technical specs. of my macbook pro? It's a 1.1 but I'd like to know the detailed specs. (in particular graphics card)
2. I saw some info before I installed google Earth that said: 
"NOTE: If you have an ATI graphic card using the proprietary (fglrx) driver,
 please read carefully /usr/share/doc/googleearth/README.Debian before
 reporting any bug.
-----------------------------------------------
Question 3. I kow this confirms my idiocy but how do I read "/usr/share/doc/googleearth/README.Debian???
I've tried searching in synaptic, google and entering it in terminal and I can't find it as a body of text.
Any help would really be appreciated as I need Google Earth to help me with something I'm working on at the moment and the flickering is migrane inducing!!

---

### Post by hyperboloid on 2008-12-20
> **mongrel boy said:**
>  
Question 3. I kow this confirms my idiocy but how do I read "/usr/share/doc/googleearth/README.Debian???
I've tried searching in synaptic, google and entering it in terminal and I can't find it as a body of text.
Any help would really be appreciated as I need Google Earth to help me with something I'm working on at the moment and the flickering is migrane inducing!!

1. Open up a terminal and type 
```
less /usr/share/doc/googleearth/README.Debian
```
which will allow you to look at the contents of the file. This works for ANY text file. Use arrow keys to move up and down in the file, hit "Q" key to quit. Type "man less" for the manual page telling you more than you want to know about the "less" command. Note that ALL commands are similarly documented in the man pages, including the "man" command itself: type "man man" for fun.

2. From Places choose Computer and navigate to the file in the file system. Then double click it to open it up in your default editor. 

I'm sure there are other solutions, too.

---

### Post by mongrel boy on 2008-12-21
O.K things just got worse.

I carried out the "fix" thats in the README. Now, I'm not an expert but I remember it said something about replacing something to do with the flgrx graphic driver wit an older version.

Not only did this not help at all but it's totally swear worded my firefox/compiz.
Now when I open firefox it doesn't have the window border at the top(the bit with the title, min, max and close tools!

This used to happen when I had Hardy and I hated it! ow I have to turn off my compiz effects completely in order for the window box to be there when I run Firefox!!!!!!!

Worse of all saying as I've uninstalled googleEarth I can't seee the README any more.
I've recovered the command line from the "fix" from my terminal

It was:  sudo wget [http://librarian.launchpad.net/7037027/libGL.so.1](http://librarian.launchpad.net/7037027/libGL.so.1) -O libGL.so.1

After running that my firefox started with the problems and google earth wouldnt even respond any more hence the uninstall.

Do you know of any way I can fix this?? It's killing me that after getting everything the way I wanted its all gone pear shaped. Help here would be great. CURSE YOU GOOGLE EARTH!

---

