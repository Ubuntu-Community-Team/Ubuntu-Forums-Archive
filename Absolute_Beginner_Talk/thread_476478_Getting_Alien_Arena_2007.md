---
title: "Getting Alien Arena 2007"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-06-17
Can you give me simple instructions to download and install Alien Arena 2007. 

Thanks.

---

### Post by Lord Illidan on 2007-06-17
```
wget -c http://icculus.org/alienarena/files/alien-arena_6.05-0ubuntu1~feisty1_i386.deb

wget -c http://icculus.org/alienarena/files/alien-arena-data_6.05-0ubuntu1_all.deb 

sudo dpkg -i alien-arena*  
```

---

### Post by aberadam on 2007-06-17
Thanks.  Will that install it all in the right place and get it working?

---

### Post by Lord Illidan on 2007-06-17
Yes. You can delete the .debs afterwards.

---

### Post by JuicedJuice on 2007-06-17
im a noob, how the heck do i launch the game after it's installed via this method? I'm not sure where it installed to or if i'm supposed to launch it in terminal.

---

### Post by ajskhan on 2007-06-17
> **aberadam said:**
> Can you give me simple instructions to download and install Alien Arena 2007. 

Thanks.
digg?

---

### Post by Lord Illidan on 2007-06-17
> **JuicedJuice said:**
> im a noob, how the heck do i launch the game after it's installed via this method? I'm not sure where it installed to or if i'm supposed to launch it in terminal.

I am not using GNOME atm, but on KDE, it added itself to the Games menu, and running alienarena in the terminal also works.

And yes, I got those links from digg :)

---

### Post by ajskhan on 2007-06-17
HAHA - you gotta love it, I would run the game but I dont think my PC can handle it, see sig

---

### Post by skymera on 2007-06-17
my pc can run iti have Intel Intergrated graphics and runs fine, ubtil theres action.

plus i cant changhe settings.

i will try above method laters

---

### Post by JuicedJuice on 2007-06-17
I get no new game icon under Applications > Games and typing alienarena in terminal does nothing. Everything appeared to get installed correctly.

edit: Im running ubuntu 7.04 64bit, gnome. I just download the debian game package. I downloaded these files

[http://icculus.org/alienarena/files/...isty1_i386.deb](http://icculus.org/alienarena/files/...isty1_i386.deb)
[http://icculus.org/alienarena/files/...buntu1_all.deb](http://icculus.org/alienarena/files/...buntu1_all.deb)

and then the installed it by typing "dpkg -i alien-arena-data_6.050ubuntu1_all.deb" and everything appeared to work correctly, but there is no new game icon in the game menu under Applications > Games and typing alienarena in terminal does nothing. How the heck do I launch this game?

---

### Post by k33bz on 2007-06-17
thats funny, i just installed it, and my icon appeared where it is suppose to be

---

### Post by Lord Illidan on 2007-06-17
> **JuicedJuice said:**
> I get no new game icon under Applications > Games and typing alienarena in terminal does nothing. Everything appeared to get installed correctly.

Perhaps you only installed 1 of the .debs? Oh, and sry, it is alien-arena.

Hint, type the first 3 letters of a command, then press TAB for Bash to autocomplete.

---

### Post by aberadam on 2007-06-17
Thanks, yeah, I saw the link on Digg. :)

---

### Post by jjasonj on 2007-07-11
> **Lord Illidan said:**
> ```
wget -c http://icculus.org/alienarena/files/alien-arena_6.05-0ubuntu1~feisty1_i386.deb

wget -c http://icculus.org/alienarena/files/alien-arena-data_6.05-0ubuntu1_all.deb 

sudo dpkg -i alien-arena*  
```

Hi, after putting this in terminal i encountered the problem of alien arena as being for 32bit system ....can anyone help me with trying to get the game for 64 bit??

Thanks in advance\\:D/\\:D/\\:D/

P.s i like the smileys

---

### Post by Nomax on 2007-08-28
> **jjasonj said:**
> Hi, after putting this in terminal i encountered the problem of alien arena as being for 32bit system ....can anyone help me with trying to get the game for 64 bit??

Thanks in advance\\:D/\\:D/\\:D/

P.s i like the smileys

You can get the 64-bit package here: [http://www.getdeb.net/app.php?name=Alien%20Arena%202007](http://www.getdeb.net/app.php?name=Alien%20Arena%202007).

By the way, it's really a great game; very fun to play! \\:D/ (once more for you).

It should be added to Add/Remove! ;)

---

### Post by khughitt on 2007-12-30
In case anyone is interested, there is more information on grabbing the latest alien arena SVN build, and debugging at here. I just started playing myself and really like the game, however I am getting constant crashes running it on Ubuntu 7.10/Compiz.

---

### Post by Joeb454 on 2007-12-30
Turn Compiz off and see if you still get the crashes

---

### Post by khughitt on 2007-12-30
I tried switching to metacity while still on xgl (i.e. **metacity --replace**), but still no luck. What setups do you guys have?

---

