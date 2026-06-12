---
title: "installing .bin"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by bhouncy on 2007-02-11
Hi.. first post... and just migrated to linux from windows. I now have 3% less hair since yesterday. I've dabbled with linux in the past for a very short time using Suse although I still know very little. I am using 6.10 64. OK.. so I eventually got firefox sped up with some ipv6 fudge.. just in time as the monitor was heading out of the window. My problem now is that I can't get realplayer and flash to install (even if I have the right versions).. I keep getting the following...

bhouncy@UTOPIA:~/Desktop$ sudo ./RealPlayer10GOLD.bin
Password:
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory
bhouncy@UTOPIA:~/Desktop$ dir
realplay-10.0.8.805-linux-2.2-libc6-gcc32-i586.bin  thunderbird
RealPlayer10GOLD.bin

I also went to the add/remove program and found both flash and realplayer but I couldn't selcect them to install as the check box was greyed out.

Any ideas?

---

### Post by deadgobby on 2007-02-11
Why not use the real player that is in synaptic? It is the same thing.
Gobby

---

### Post by bhouncy on 2007-02-11
> **deadgobby said:**
> Why not use the real player that is in synaptic? It is the same thing.
Gobby

I've looked in synaptic and can't find realplayer

---

### Post by deadgobby on 2007-02-11
Cool lets get your extra repositories in action. Here is a how to to do it. After you are done. You'll see a bunch more programs in your Synatpic. It is very simple to this.
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)

Gobby

---

### Post by nalioth on 2007-02-11
> **bhouncy said:**
> I've looked in synaptic and can't find realplayer
You'll need dapper-commercial repos for RealPlayer, Opera and some more goodies.  once you get the sources added, search for 'realplay'

---

### Post by bhouncy on 2007-02-11
> **deadgobby said:**
> Cool lets get your extra repositories in action. Here is a how to to do it. After you are done. You'll see a bunch more programs in your Synatpic. It is very simple to this.
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)

I followed the guide and got the following

bhouncy@UTOPIA:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
bhouncy@UTOPIA:~$ gksudo gedit /etc/apt/sources.list

(gedit:13111): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Now I just carried on with the instructions and it did download stuff. But no realplayer or macromedia flash.

---

### Post by nickoli_02 on 2007-02-11
After you add the extra repositories, you need to update apt-get:

```
sudo apt-get update
```

Then you should be able to find the packages you're looking for.

Don't worry about the warnings you got when using gksudo, I believe it's a known issue.

---

### Post by bhouncy on 2007-02-11
> **nalioth said:**
> You'll need dapper-commercial repos for RealPlayer, Opera and some more goodies.  once you get the sources added, search for 'realplay'

I am now going to look up the linux speak dictionary or flush my head down the loo.. xp has killed too many braincells from lack of use ;)

---

### Post by deadgobby on 2007-02-11
> **bhouncy said:**
> I followed the guide and got the following

bhouncy@UTOPIA:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
bhouncy@UTOPIA:~$ gksudo gedit /etc/apt/sources.list

(gedit:13111): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Now I just carried on with the instructions and it did download stuff. But no realplayer or macromedia flash.
 That error is just a bug and you'll be find. You'll get that every time you edit your list. You will be OK. Really you'll be A OK
Gobby

---

### Post by deadgobby on 2007-02-11
OK let s get some fun stuff going then. It will make your Ubie box sing like a bird.
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
 That will install lots of Restricted formats and yes. Real Player and Flash as well. It takes about an hour to do if you select every thing to install. At installing Java. Make sure you use the TAB key to tab to the YES I agree lincess.
Gobby

---

### Post by bhouncy on 2007-02-11
> **deadgobby said:**
> OK let s get some fun stuff going then. It will make your Ubie box sing like a bird.
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
 That will install lots of Restricted formats and yes. Real Player and Flash as well. It takes about an hour to do if you select every thing to install. At installing Java. Make sure you use the TAB key to tab to the YES I agree lincess.
Gobby

ty gobby.. I'll give that a try right now and see where it takes me :)

---

### Post by bhouncy on 2007-02-11
Well now I have realplayer but when playing a stream there was no video or audio although the time was moving but I'll play around with that.

I did manage to get a stream in wmv format to play on VLC but Totem tries to play the file by default but gives an error... is there a way to change the default player in firefox to play wmv files?

Last thing.. still can't get macromedia flash to work and I don't even know if I have it on my machine! I'll keep plugging away.

---

### Post by borisdaniel on 2007-03-30
Am sorry .. can somebody tell me how i can install real player. 
I have downloaded the RealPlayer10GOLD.bin and .rpm both in the desktop.

am having the same trouble / errors following the instruction via terminal yet i get nothing.

---

