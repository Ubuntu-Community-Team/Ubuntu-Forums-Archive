---
title: "Cannot get Ndiswrapper installed in Feisty Fawn"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Fenrirwulf on 2007-04-08
I tried to install using Synaptic and then when I try to run ndiswrapper -l to see the drivers I get a message saying that no version of ndiswrapper can be found. I uninstalled them and then installed version 1.41. 

fenrirwulf@Fenris:~/Desktop/ndiswrapper-1.41$ sudo make
make -C driver
make[1]: Entering directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/driver'
make -C /lib/modules/2.6.20-14-generic/build SUBDIRS=/home/fenrirwulf/Desktop/ndiswrapper-1.41/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-14-generic'
make[1]: Leaving directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/driver'
make -C utils
make[1]: Entering directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/utils'
fenrirwulf@Fenris:~/Desktop/ndiswrapper-1.41$ sudo make install
make -C driver install
make[1]: Entering directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/driver'
make -C /lib/modules/2.6.20-14-generic/build SUBDIRS=/home/fenrirwulf/Desktop/ndiswrapper-1.41/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-14-generic'
echo /lib/modules/2.6.20-14-generic/misc
/lib/modules/2.6.20-14-generic/misc
mkdir -p /lib/modules/2.6.20-14-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-14-generic/misc
/sbin/depmod -a 2.6.20-14-generic -b /
make[1]: Leaving directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/driver'
make -C utils install
make[1]: Entering directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
fenrirwulf@Fenris:~/Desktop/ndiswrapper-1.41$ ndiswrapper -l
ls: /etc/ndiswrapper: No such file or directory
fenrirwulf@Fenris:~/Desktop/ndiswrapper-1.41$

 
I'm not sure what to do now. Any help would be appreciated. I am a Linux newb and only have a little experience with Freespire prior to this. Thanks!

---

### Post by Kobalt on 2007-04-09
You need to install windows drivers using ndiswrapper with this command : 
```
ndiswrapper -i /path-to-file.inf
```
before using this command
```
ndiswrapper -l
```

Some help about installing/using ndiswrapper : [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Bachstelze on 2007-04-09
If you built ndiswrapper from ource, *make* will only build it (and you don't need to be root for that) but *make install* will install it and you need to be roort for that .

---

### Post by Fenrirwulf on 2007-04-09
> **Kobalt said:**
> You need to install windows drivers using ndiswrapper with this command : 
```
ndiswrapper -i /path-to-file.inf
```
before using this command
```
ndiswrapper -l
```

Some help about installing/using ndiswrapper : [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Yeah but it's saying that Ndiswrapper isn't even installed yet, so it's kind of difficult to install the windows drivers until then... LOL. I'm sure I am missing something probably very easy, but being so new to this OS, I just really don't know the command lines that well. 

And I wasn't sure I need to be using root to install it but I think I had gotten some error before and that's why I tried to like that. I'll give it another go tomorrow cuz I have school after work tonight. Thanks.

---

### Post by Big Dave on 2007-04-09
If you can't get ndiswrapper to work properly, you can also install it using Automatix2 (which will also install many other things along with ndiswrapper).

You can download a .deb file of automatix2 and install it using gdebi (just double-click on the file to start) from their website at:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Bachstelze on 2007-04-09
As I told you, *make* only compiled ndiswrapper but didn't install it. To instal it, do

```
sudo make install
```

And please, please, please *don't* use Automatix !

---

### Post by Fenrirwulf on 2007-04-09
I believe I did also do "make install", but failed to put the text from that in the log. I followed most of the instructions from the ndiswrapper site(as much as I could understand anyway). The site says to:
"Go to the source-directory and run 'make distclean' and 'make'. As root, run 'make install'. This should compile and install both the kernel module and the userspace utilities" .

I did both of those and it said ndiswrapper was not installed. I did those commands several times in fact but must have missed running make install the last time when I posted the results. Sorry about that. I will try it again and if I get the same results I will post the whole thing next time. :oops:

---

### Post by Bachstelze on 2007-04-09
That's very weird, I did the same thing just yesterday and after running *make install*, ndiswarpper was there. Maybe you need to rn in with *sudo*, try :

```
sudo which ndiswrapper
```

---

### Post by richbarna on 2007-04-09
> **Fenrirwulf said:**
> I believe I did also do "make install", but failed to put the text from that in the log. I followed most of the instructions from the ndiswrapper site(as much as I could understand anyway). The site says to:
"Go to the source-directory and run 'make distclean' and 'make'. As root, run 'make install'. This should compile and install both the kernel module and the userspace utilities" .

I did both of those and it said ndiswrapper was not installed. I did those commands several times in fact but must have missed running make install the last time when I posted the results. Sorry about that. I will try it again and if I get the same results I will post the whole thing next time. :oops:

As Big Dave said, if you can't install it manually, try Automatix2. It's better than not having ndiswrapper at all. 

Just for reference I have just tested Automatix2 on Feisty and everything installed as smooth as silk. For second reference I tested Automatix on Breezy, Dapper and Edgy too. I personally had no problems.

Remember though that Automatix isn't officially supported by ubuntuforums, and if you need support it is better to post on the Automatix forums.

|
|
v

---

### Post by oilchangeguy on 2007-04-09
just what is it that you are trying to install? maybe there's a better way.

---

### Post by Fenrirwulf on 2007-04-09
Ndiswrapper. I've been having trouble getting it installed manually and through Synaptic. I will try again tomorrow because I have class tonight after being at work all day so I won't have time to try it again tonight. I'll keep you posted.

---

### Post by Big Dave on 2007-04-09
> **oilchangeguy said:**
> maybe there's a better way.

As richbarna and myself have both posted, use Automatix!! :)

---

### Post by Fenrirwulf on 2007-04-09
There seems to be mixed feelings about this Automatix.... I may just give it a try if I can't get the traditional way to work. I assume it's like Synaptic, Apt-get and Freespire's CNR?

---

### Post by richbarna on 2007-04-09
> **Fenrirwulf said:**
> There seems to be mixed feelings about this Automatix.... I may just give it a try if I can't get the traditional way to work. I assume it's like Synaptic, Apt-get and Freespire's CNR?

Go the traditional route first, then if it doesn't work, try Automatix. You can follow the link in my sig, but give it a day or two. Due to overwhelming demand, the server got maxed out but should be online again shortly.

---

### Post by PriceChild on 2007-04-09
From ubotu on irc> automatix is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to install a fresh copy of Ubuntu.

I strongly advise you follow official ubuntu documentation and learn to do things yourself properly.

---

### Post by Fenrirwulf on 2007-04-11
I give up. I tried it through the normal channels and through automatix and neither way seems to be working for me. Even though I am getting an error saying no version of ndiswrapper is installed I was able to install the drivers, sort of. It came up with an error about not being able to write to some directory and then when I ran ndiswrapper -l it showed the driver but it said it was invalid. I tried to remove the driver but it would say it didn't exist. When I did this about a month ago in Freespire it was quite a bit different. I eventually got it working with other people helping me but this time it doesn't seem to be doing what it's supposed to. I am going to wipe the partition and start from scratch and try the 64 bit version this time and see what happens. Thanks for the help thus far.

---

### Post by Fenrirwulf on 2007-04-11
Ok, after 2 re-installs of the OS I now find that I am an idiot...the hard way. I completely forgot that all commands are case sensitive! DOH!!! After I loaded the 64 bit version I then found that the 32 bit drivers loaded but failed to work for my Netgear card and Netgear doesn't have any 64 bit drivers for this card. I re-installed the 32 bit version and then was able to get it loaded and finally connected to my router. Woot!! Anyway, the most confusing thing was that when I installed Freespire and did the "ndiswrapper -l" command, several drivers showed up. In Ubuntu it said there were none. That was what really confused me. I guess every distro has it's own drivers already listed. Oh well... live and learn.  :p

---

