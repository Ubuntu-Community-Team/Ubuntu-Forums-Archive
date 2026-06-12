---
title: "BitTornado, Azureus won't start"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by maxuser on 2008-01-18
I just started using linux a couple of days ago (Ubuntu 7.10) and I'm having problems starting up some programs. I installed Azureus and VLC thru synaptic and it seemed to install without problems. Then I went to Applications -> Internet -> Azureus and nothing happened. No errors, nothing. Same thing for VLC. I uninstalled and tried it again but the same thing happened. I tried BitTornado and same thing happened. When I click on these programs absolutely nothing happens. What am I doing wrong?

Then I installed Deluge and MPlayer and they worked fine. I reinstalled VLC for the last time and it still didn't work.

---

### Post by alan tait on 2008-01-18
Exactly the same here, since this morning. Could there be a problem with this morning's updates? Azureus simply doesn't start, even after uninstall/reinstall and nothing for other torrent apps either.

---

### Post by hyper_ch on 2008-01-18
azureus needs java. Is that also installed?

I prefer a command line torrent client called:   rtorrent
Can be simply controlled through a ssh connection from everywhere.

---

### Post by alan tait on 2008-01-18
Incidentally, Maxuser, Deluge still doesn't work for me, but Transmission is running fine as I  write.

---

### Post by adileader on 2008-01-18
I have the same problem with Azureus...It worked fine on windows:lolflag:

---

### Post by dustman on 2008-01-18
try running those programs from a terminal. If they don't start, it should output an error of some kind. Running the programs from the terminal offers you the possibility to see that error/errors ;).
I don't use Azureus, but the command should be like this: ```
azureus
```
And as for VLC, just run from the terminal: ```
vlc
```
As hyper_ch said, to run azureus you need JAVA (a java runtime environment to be more exact). That can be installed by inputing in a terminal: ```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
Try to see if the installation was successful (with the output of the command):```

dustman@dustman-laptop:~$[COLOR="Red"] java -version[/COLOR]
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

```

Cheers!

Radu

---

### Post by alan tait on 2008-01-18
this is what I get:

The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 477 error_code 11 request_code 145 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by maxuser on 2008-01-18
I got the same error as Alan.

---

### Post by hyper_ch on 2008-01-18
how much ram have you got?

---

### Post by maxuser on 2008-01-18
I guess this is the same problem people on the other threads are having, something to do with the update. I thought I was making a stupid newbie mistake...

---

### Post by psychok7 on 2008-01-18
yeah. me 2.. i think it is due to this morning updates.. i am triying now to see if the vuze azures works.

---

### Post by jdong on 2008-01-18
Hi everyone, it is the morning updates.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

Security team and archive administrators are aware and currently discussing this problem, and will soon pull the update (in a matter of minutes) from the archive servers.

For now, just sit tight until there's an update on the situation. I don't advise people to try to roll back to old versions of packages or otherwise home-brew fixes unless you want to risk making a mistake doing this and screwing up things even more.

As far as this fix, it's a security fix taken directly from the X.org team and several distros have chosen to adopt this patch. Upstream has been notified regarding this situation too.

---

### Post by psychok7 on 2008-01-18
yeah, the other azureus(not from synaptic) also doesnt work.. i just didnt get one thing, when will they give us the fix for this??today?

---

### Post by hyper_ch on 2008-01-18
They will give you the fix once it's been fixed and recompiled and put into the repos ;)

---

### Post by poisonkiller on 2008-01-18
Another bug caused by xorg-core: opera's big red O disappears from bottom panel. :D

Maybe this is somehow connected, but when I install Crossover, I can't find it in Applications. How can I put it there, 'cause at the moment I can't uninstall anything without removing Crossover itself.

---

### Post by alan tait on 2008-01-18
At the risk of appearing a complete idiot, what's the best way of finding out things like disk size/free space, and RAM and so on? :?

---

### Post by psychok7 on 2008-01-18
> **alan tait said:**
> At the risk of appearing a complete idiot, what's the best way of finding out things like disk size/free space, and RAM and so on? :?

you got a thing called system monitor on system/administration. give it a try

---

### Post by hyper_ch on 2008-01-18
or for disk space usage:

```

df -l

```

and for memory:

```

free -m

```

---

### Post by dustman on 2008-01-18
well, the tomorrow updates will fix today's bugs ;) . i also use System Monitor from : System->Administration. It's also a great tool to kill the trouble making processes.

P.S. i installed the updates today, and my VLC works fine.

---

### Post by bmagyarkuti on 2008-01-18
As a temporary solution, you can downgrade your xorg-core package to the previous one:

Just
```
sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8
```
and restart your x-server (if you don't know how to, restart your computer).

It's also important that you don't install any updates to x-server today. Doing so will restore the wrong package.

---

### Post by vigyani on 2008-01-20
Today after update Azureus works fine.

regards
Vig

---

### Post by dustman on 2008-01-20
> **vigyani said:**
> Today after update Azureus works fine.

regards
Vig

then this thread should be marked as SOLVED ;)

Cheers!

---

