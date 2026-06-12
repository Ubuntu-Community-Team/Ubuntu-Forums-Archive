---
title: "Hello I am having some difficulties could someone plz help me?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by haolunli on 2007-12-03
Hey guys I'm thinking of converting by to Ubuntu here are my concerns:

1. Well firstly my laptop's screen is way too bright and I have no idea how to adjust it. I been told before to use terminal but it never works for me. Using windows xp I need the toshiba hotkey install thenIjust push fn-f6/f7.

2. My wireless mouse and keycorad isn't working at all and it worked fine in windows xp.

3. I use many methods but could not install the pugins like flash player dixv player etc...

4. My printer is lexmark 2300 although I have no idea witch model it is and cannot get  it to work on ubuntu. The driver backup is pc only

5. Why is ubuntu free? Who is paying for the site and updates? Is there some way ubuntu makes money?

If you could answer these then I will give ubuntu another go

:guitar::guitar::lolflag:

---

### Post by Don1500 on 2007-12-03
Delete

---

### Post by haolunli on 2007-12-03
> **Don1500 said:**
> Delete


What does that mean?

---

### Post by Don1500 on 2007-12-03
It means I had a long smartA** answer but decided not to send it.

Read the introduction to UBUNTU for most of your answers and your laptop instruction book for others.

---

### Post by khurrum1990 on 2007-12-03
> **haolunli said:**
> Hey guys I'm thinking of converting by to Ubuntu here are my concerns:

1. Well firstly my laptop's screen is way too bright and I have no idea how to adjust it. I been told before to use terminal but it never works for me. Using windows xp I need the toshiba hotkey install thenIjust push fn-f6/f7.

2. My wireless mouse and keycorad isn't working at all and it worked fine in windows xp.

3. I use many methods but could not install the pugins like flash player dixv player etc...

4. My printer is lexmark 2300 although I have no idea witch model it is and cannot get  it to work on ubuntu. The driver backup is pc only

5. Why is ubuntu free? Who is paying for the site and updates? Is there some way ubuntu makes money?

If you could answer these then I will give ubuntu another go

:guitar::guitar::lolflag:

Hi, Ubuntu is a Linux operating system and Linux is part of an open source agreement so its free. Ubuntu developers and other Linux developers have support of big businesses and they also sell paid versions of their software. For ur laptop brightness, I am not sure but if u have a Nvidia vga card then all u have to do is type in terminal "sudo nvidia-xconfig" and configure whatever u want.

Your wireless mouse and key board isn't working because wireless drivers r not installed, u will need to install that using restricted drivers manager or usind NDISWrapper. For different plugins and stuff, go to add/remove programs and on the top right corner choose show all applications. Then on the left bar choose other applications and install ubuntu restricted extras. If u want encrypted dvd play back and windows media support then add the medibuntu repos.

As for ur printer, Lexmark has horrible Linux support so I am not sure whether it works or not but it will be tough setting it up. If u get an Hp printer then it will work perfect as Hp supports Linux. If u didn't know that Ubuntu was actually a Linux operating system then I doubt u know much about computers and trust me u will be way better of with Windows in that case.

Good Luck!

---

### Post by haolunli on 2007-12-03
> **Don1500 said:**
> It means I had a long smartA** answer but decided not to send it.

Read the introduction to UBUNTU for most of your answers and your laptop instruction book for others.


Could you send it anyways I need the info I've serched everywhere

---

### Post by Don1500 on 2007-12-03
All your answers are here:
[http://www.ubuntu.com/](http://www.ubuntu.com/)

---

### Post by haolunli on 2007-12-03
Wow thx for that link too bad i've been on that last time I had ubuntu:popcorn:

---

### Post by Paqman on 2007-12-03
> **haolunli said:**
> 
3. I use many methods but could not install the pugins like flash player dixv player etc...


Best way to get flash: install flashplugin-nonfree. It's also included in ubuntu-restricted-extras, which is a very handy package for media codecs. The VLC media player plays pretty much everything under the sun, too.

---

### Post by haolunli on 2007-12-03
Thx a lot but can I watch utube videos and stream .divx online? 

And could someone plz anyswer my other questions too? :lolflag:](*,):-({|=[-X:-$:---):tongue::-&=

---

### Post by LowSky on 2007-12-03
> **haolunli said:**
> Hey guys I'm thinking of converting by to Ubuntu here are my concerns:

1. Well firstly my laptop's screen is way too bright and I have no idea how to adjust it. I been told before to use terminal but it never works for me. Using windows xp I need the toshiba hotkey install thenIjust push fn-f6/f7.
 right click on one of the panels where there is no application buttons, clcik on add to panel look for brightness icon, then play with settings


> 2. My wireless mouse and keycorad isn't working at all and it worked fine in windows xp.

you need to install the drivers go to system>admin>restricted drivers manager

> 3. I use many methods but could not install the pugins like flash player dixv player etc... im watching divx movies and on youtube all the time

in terminal paste this ```


sudo apt-get ubuntu-restricted-extras
```

> 4. My printer is lexmark 2300 although I have no idea witch model it is and cannot get  it to work on ubuntu. The driver backup is pc onlylexmark doesn't play well with linux, try epson, canon, or my favorite hp

> 5. Why is ubuntu free? Who is paying for the site and updates? Is there some way ubuntu makes money? ubuntu is free, and only makes money on support

If you could answer these then I will give ubuntu another go

:guitar::guitar::lolflag:[/QUOTE]

---

### Post by haolunli on 2007-12-04
Bump

---

### Post by Vadi on 2007-12-04
> **haolunli said:**
> Hey guys I'm thinking of converting by to Ubuntu here are my concerns:

1. Well firstly my laptop's screen is way too bright and I have no idea how to adjust it. I been told before to use terminal but it never works for me. Using windows xp I need the toshiba hotkey install thenIjust push fn-f6/f7.

**Hm, that should work. Because that setting isn't Ubuntu-specific as far as I know.**

2. My wireless mouse and keycorad isn't working at all and it worked fine in windows xp.
**Dunno. When did you try Ubuntu last time? A new one came out in October. (my stuff works ok)**

3. I use many methods but could not install the pugins like flash player dixv player etc...
**sudo apt-get install ubuntu-restricted-extras, and you're all set.**

4. My printer is lexmark 2300 although I have no idea witch model it is and cannot get  it to work on ubuntu. The driver backup is pc only
**Dunno, dont have that printer. Check out ubuntuhcl.org and help.ubuntu.com/community**

5. Why is ubuntu free? Who is paying for the site and updates? Is there some way ubuntu makes money?
**People are donating money for the site. People are also helping code it. And nobody's making money here - this is an OS by people for other people. It's a thing called "open source", Google it. It's damn cool.**

If you could answer these then I will give ubuntu another go

Covered? :)

---

