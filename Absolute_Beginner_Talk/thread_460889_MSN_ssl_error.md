---
title: "MSN ssl error"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by silentjudas on 2007-06-01
ok nothing i have will connect to msn anymore. whats up. i'm confused. one gives me an ssl error, the rest just wont log in! i've tried with serveral account (like 2 or 3) and nothing.....i'm really lost. help please!

---

### Post by seshomaru samma on 2007-06-01
are you using pidgin?
i was using gaim and then compiles pidgin , I ignored a make line error that said 'no ssl support' and the result was no MSN
you can solve it by installing the .deb file from [here]("http://www.mediafire.com/?9dzxhl0z1mj")
you can also try to compile it with ssl support -it's a little complicated. info [here ]("http://developer.pidgin.im/wiki/FAQssl")

if you are not using pidgin , then i don't know....

---

### Post by silentjudas on 2007-06-01
a. i've tried aMSN, which wouldnt let me connect way before this anyways. i;ve tried kmess, same there. gaim, and pidgin (which i compiled myself.) and nothing

---

### Post by Malibu Illusion on 2007-06-01
Issue:

```
sudo apt-get install gnutls-bin
```

Compile Pidgin from source.

After issuing ./configure, you should see a line like this at the end:

> SSL Library/Libraries......... : GnuTLS

This means SSL is enabled and MSN will connect.

Take care.

---

### Post by silentjudas on 2007-06-01
```

silentjudas@QUEENMACHINE:~$ sudo apt-get install gnutls-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnutls-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
so jsut compile AGAIN now?

---

### Post by Malibu Illusion on 2007-06-01
Hmm.

As I said, after running the configuration script, you should see a summary and a confirmation of the SSL libraries that the program will use.  If you see that, you shouldn't have any problems connecting to MSN that are caused by lack of SSL support anyway.

---

### Post by silentjudas on 2007-06-01
alright well i used the .deb and it works, but still wont let me log in. i think m$ is out to get me...my account wont log in that is. but the ssl error is fixed, eh heh

---

### Post by silentjudas on 2007-06-01
ok tell me if this makes sense

i can log onto msn just fine with meebo.com
but nothing on my computer''


anyone?

---

### Post by silentjudas on 2007-06-02
well? do ya know?

---

### Post by MissG on 2007-06-08
> **seshomaru samma said:**
> are you using pidgin?
i was using gaim and then compiles pidgin , I ignored a make line error that said 'no ssl support' and the result was no MSN
you can solve it by installing the .deb file from [here]("http://www.mediafire.com/?9dzxhl0z1mj")
you can also try to compile it with ssl support -it's a little complicated. info [here ]("http://developer.pidgin.im/wiki/FAQssl")

if you are not using pidgin , then i don't know....I'm a newbie, was having this problem, and it resolved by using the debian package mentioned above. I recommend trying it before messing with compiling by hand. (thanks for the link seshomaru)

---

