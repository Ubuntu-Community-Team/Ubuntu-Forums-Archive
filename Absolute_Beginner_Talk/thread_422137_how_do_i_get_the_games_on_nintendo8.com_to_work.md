---
title: "how do i get the games on nintendo8.com to work"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2007-04-24
how do i get the games on [http://www.nintendo8.com](http://www.nintendo8.com)  to work with ubuntu?

---

### Post by disturbed1 on 2007-04-24
Neat site :)

Install the Java Run Time (sun java jre) it should work fine then.

---

### Post by Fittersman on 2007-04-24
yeah, a friend just showed me it

i have the Sun Java(TM) Runtime Environment (JRE) 5.0 installed in package manager already though. (thats the one you meant right?)

---

### Post by disturbed1 on 2007-04-25
Yep, that's the one.

I cruised through the site and tried a few games. They were all hit or miss, from playing great, not loading, being too slow .....

One thing I found out it is that I had to click on the window, and then hit the control button first, before attempting to play the game.

---

### Post by Fittersman on 2007-04-25
o, well when i been going through the site, none of them work, is there maybe another package that i need too? 

tel me what one you got to work, to see if it works for me too if you would...

---

### Post by 007Bond on 2007-04-25
Reinstall it through Synaptic.

---

### Post by disturbed1 on 2007-04-25
Contra Force played.

---

### Post by Fittersman on 2007-04-25
no luck, tried reinstalling, any other ideas?

---

### Post by Fittersman on 2007-04-25
o, that sucks, that (contra force) wont work for me.

---

### Post by Fittersman on 2007-04-27
i think it might not be using that version of java.

when i right click on the game and click about java (or something) it pops up with a window that contains:

```
Version 1.4.2-02 (build Blackdown-1.4.2-02)
Copyright 2003 Sun Microsystems, Inc. All rights reserved. Use is subject to license terms.
```

if im reading that right, im using version 1.4.2-02, not 5.0 like i have installed (i think that one i said a couple of posts ago is 5.0)

---

### Post by Interestedinthepenguin on 2007-04-27
Do you have 'sun-java5-plugin' or 'j2re1.4-mozilla-plugin' installed?

---

### Post by darkdays on 2007-04-27
If the problem isn't with the plugins, this might do it.

```
sudo update-alternatives --config java
```

...and choose the java-version you want to use.

---

### Post by Fittersman on 2007-04-28
i have tried all of the following options (none worked), unless a restart is required between changes.

```
cleippi@cleippi-desktop:~$ sudo update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-gcj/jre/bin/java
 *       3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
   +    4    /usr/lib/j2se/1.4/bin/java
          5    /usr/lib/j2sdk1.4-sun/bin/java

```

i have both of 'sun-java5-plugin' and 'j2re1.4-mozilla-plugin' installed as well.

---

### Post by Interestedinthepenguin on 2007-04-30
Can you see the game, or do you get a grey box with a red 'x'?

---

### Post by Fittersman on 2007-04-30
> **Interestedinthepenguin said:**
> Can you see the game, or do you get a grey box with a red 'x'?

sometimes it starts as a java cup in the top corner, but it always ends up as the red X after like 2 seconds.

---

### Post by darkdays on 2007-05-01
When I tried it actually took a restart before I got the games to work. I used;
 /usr/lib/jvm/java-6-sun/jre/bin/java

---

### Post by Fittersman on 2007-05-01
> **darkdays said:**
> When I tried it actually took a restart before I got the games to work. I used;
 /usr/lib/jvm/java-6-sun/jre/bin/java

i dont have that option in mine, how do i get that one?

---

### Post by keagan on 2007-05-02
OMG
to who ever said
to do this 

sudo update-alternatives --config java

THEN TAHKNS YOU!
it worked..
ive been up to 4 am trying to get this to work
ily
lol
THANKS :D

---

### Post by darkdays on 2007-05-02
> **Fittersman said:**
> i dont have that option in mine, how do i get that one?

```

sudo apt-get install sun-java6-jre 
```

Should do the trick, don't know if the plugin is included in the jre, in case it isn't this line makes sure you get it also;

```
sudo apt-get install sun-java6-plugin
```

---

### Post by Fittersman on 2007-05-02
didnt work for me, this is what i got:

```
cleippi@cleippi-desktop:~$ sudo apt-get install sun-java6-jre
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-jre

cleippi@cleippi-desktop:~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-plugin

```

---

### Post by darkdays on 2007-05-05
Fittersman:

For me it's in synaptic, I'm running feisty and it either was there from start or was installed with something else as a dependency. What release are you running? Do you have the multiverse-repo enabled?

---

### Post by Fittersman on 2007-05-05
im on edgy (6.10, thats edgy right?) and i have the multiverse repo enabled, is that option only available for the feisty fawn version now then?

---

### Post by Fittersman on 2007-05-07
well, i spent all day yesterday backing up, reinstalling (my windows was broken) my whole system, so i upgraded to feisty fawn while i was at it, and its all good now

---

