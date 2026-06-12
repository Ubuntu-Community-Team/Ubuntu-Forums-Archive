---
title: "New to ubuntu"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Primefalcon on 2008-04-01
I used windows for near on 20 years. I've just installed Ubuntu and am feeling like a complete computer noob here

I have no idea how to run wine or anything else, and I'm desperately trying to find a voice chat tool I can use and work out so I can talk to my parents in Australia (I live in the states)

I'm lost

---

### Post by ghost_ryder35 on 2008-04-01
use Skype [http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)
You will also find [https://help.ubuntu.com/](https://help.ubuntu.com/) very helpful

---

### Post by olskar on 2008-04-01
Hello and welcome! Please ask your questions here and we will try to help you :)

Are you sure you need to run windowssoftware? Often there is good opensourcecounterparts :) If you are sure you can get wine by using add/remove in the programsmenu.

Perhaps skype could work as voicechat? 

[http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)

---

### Post by Bölvaður on 2008-04-01
WINE is pretty advanced topic. But you can always type in the terminal

apt-get install (wine is it not?)

after that you can open exe files with WINE and hope it works without tweaking.


For talking to your parents Skype might be the best thing for you like he said :) cheers

---

### Post by Primefalcon on 2008-04-02
Can skype be used computer to computer free?

Btw wow thanks for all the advice and quick replies.

---

### Post by Patb on 2008-04-02
Yes, Primefalcon.  I use Skype computer to computer (free) all the time.  It works fine.  If you have any problems installing or setting it up, search the forum and if you still need help, post here.  

Cheers, Pat

---

### Post by hyper_ch on 2008-04-02
> **Primefalcon said:**
> I used windows for near on 20 years. I've just installed Ubuntu and am feeling like a complete computer noob here

that's normal, but it'll pass....

------------------------------------------------

Add the medibuntu repos:  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


And then install skype through apt
```

sudo apt-get update && sudo apt-get install skype

```

---

### Post by Primefalcon on 2008-04-02
I went and downloaded and installed Skype no problems, heck its works better than any voice program I've seen before, its beautiful, thanks so much for recommending this! The terminal thing is new to me however and I'm not sure what I'm doing with it

I installed wine using the package manager but every time I try to use an exe file I get the message that I couldn't open it

so I went into the properties and tried to associate it with wine and now I get nothing, I think I've completely messed up with that

---

### Post by nadanil on 2008-04-02
"Becoming friends with the terminal"
-->  [http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338)

Terminal for Beginners (I Liked this one alot)
---> [http://ubuntuforums.org/showthread.php?t=73885&highlight=terminal+anime](http://ubuntuforums.org/showthread.php?t=73885&highlight=terminal+anime)


Good luck to both of us : ), it's frustrating sometimes isn't it, but this too shall also pass.

---

### Post by Crafty Kisses on 2008-04-02
> **Primefalcon said:**
> I used windows for near on 20 years. I've just installed Ubuntu and am feeling like a complete computer noob here

I have no idea how to run wine or anything else, and I'm desperately trying to find a voice chat tool I can use and work out so I can talk to my parents in Australia (I live in the states)

I'm lost

Ekiga has really good VoIP, and Skype has pretty good voice compatibility.

---

### Post by ichi@YUKI on 2008-04-02
This is the code I used to get wine:

sudo apt-get install wine

And this is what I use to get applications for wine (uTorrent for example):

wget [http://download.utorrent.com/1.7.5/utorrent.exe](http://download.utorrent.com/1.7.5/utorrent.exe)

and installing:

wine utorrent.exe

I got it from here: [http://www.howtoubuntu.com/2007/10/21/how-to-install-utorrent-in-ubuntu-with-wine.html](http://www.howtoubuntu.com/2007/10/21/how-to-install-utorrent-in-ubuntu-with-wine.html)

---

### Post by Crafty Kisses on 2008-04-02
> **ichi@YUKI said:**
> This is the code I used to get wine:

sudo apt-get install wine

And this is what I use to get applications for wine (uTorrent for example):

wget [http://download.utorrent.com/1.7.5/utorrent.exe](http://download.utorrent.com/1.7.5/utorrent.exe)

and installing:

wine utorrent.exe

I got it from here: [http://www.howtoubuntu.com/2007/10/21/how-to-install-utorrent-in-ubuntu-with-wine.html](http://www.howtoubuntu.com/2007/10/21/how-to-install-utorrent-in-ubuntu-with-wine.html)

So is your question on how to install this?

---

### Post by Primefalcon on 2008-04-02
thx :-) I'm slowly becoming familiar with this learning how to navigate and such using the terminal having probs installing stuff atm still using ./configure

and get this

```
primefalcon@Blackbeard:~/Desktop/amsn$ ./configure
checking for prefix by checking for wish... /usr/bin/wish
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking tcl build dir... using tcl library in /usr/lib/tcl8.4
checking tk build dir... using tk library in /usr/lib
./configure: line 3482: /usr/lib/tkConfig.sh: No such file or directory
primefalcon@Blackbeard:~/Desktop/amsn$ 
```

I'm kinda happy with getting this far atm since most of my work I can still do since Filezilla and php editors were in the package but sigh I'm trying to work this out so I can install the latest versions of stuff and getting there but... yoh well have to admit, its fun learning all this stuff from scratch again.

going back to reading and keeping and eye here :-) I'd prefer not to trust Microsoft software if I can avoid it, I honestly don't trust them anymore

---

