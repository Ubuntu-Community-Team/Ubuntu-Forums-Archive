---
title: "A good BitTorrent client?"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by ZelasMetallium on 2006-04-28
I was quite the fan of BitComet on my Windows system and would like to keep my torrents coming on this system but am very unhappy with the basic BitTorrent.

I've heard of Azuerus but it doesn't appear on  my 'Add Applications' list so I have no idea how to install it.  How can I do that and/or what's another program that makes BitTorrent a bit smoother to use?

---

### Post by user1397 on 2006-04-28
I would really recommend azureus, and it's easier to install than you think.  You can use automatix, following this guide: [http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295) ,  and install azureus from there, or you can follow the guide on the wiki: [https://wiki.ubuntu.com/AzureusHowTo?highlight=%28azureus%29](https://wiki.ubuntu.com/AzureusHowTo?highlight=%28azureus%29)

---

### Post by CompShrink on 2006-04-28
Azureus is probably the best all-torrents-in-one-window client for linux. Just go into Synaptic  Package Manager and make sure you have j2re installed before hand, it's needed for Azureus to run, then follow the above.

I recommend against Automatix personally, but that's just my view.

I personally just use BitTornado, but each torrent is still a seperate window, no queueing, but that's fine with me...

---

### Post by user1397 on 2006-04-28
The wiki guide explains how to install the java plugins so don't need to worry about doing that separately.

---

### Post by ZelasMetallium on 2006-04-28
Ubuntu 5.10 (Breezy Badger)

   1.Add universe and multiverse, if they have not already been done. If you do not know how, see AddingRepositoriesHowto

   2. Install the following programs j2re1.4 libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java

$ sudo apt-get install j2re1.4 libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java

   1. Download the following [WWW] [http://ftp.egr.msu.edu/debian/pool/contrib/a/azureus/azureus_2.4.0.2-1_all.deb](http://ftp.egr.msu.edu/debian/pool/contrib/a/azureus/azureus_2.4.0.2-1_all.deb)
   2. Open a terminal and type dpkg -i azureus_2.4.0.2-1_all.deb



I'm to that last step but it says:

"kendra@kendra:~$ dpkg -i azureus_2.4.0.2-1_all.deb
dpkg: requested operation requires superuser privilege"

So I sudo'd it and got:

"kendra@kendra:~$ sudo dpkg -i azureus_2.4.0.2-1_all.deb
dpkg: error processing azureus_2.4.0.2-1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 azureus_2.4.0.2-1_all.deb
kendra@kendra:~$"


Now what?

---

### Post by user1397 on 2006-04-28
you have to first go to the directory where the file is. for example if it's on the desktop, in the terminal you would type cd /home/kendra/Desktop, and then it would look like this: kendra@kendra:~/home/kendra/Desktop$
then you do the sudo dpkg -i azureus_2.4.0.2-1_all.deb command

---

### Post by ZelasMetallium on 2006-04-28
[QUOTE=erik1397]you have to first go to the directory where the file is. for example if it's on the desktop, in the terminal you would type cd /home/kendra/Desktop, and then it would look like this: kendra@kendra:~/home/kendra/Desktop$
then you do the sudo dpkg -i azureus_2.4.0.2-1_all.deb command[/QUOTE]
Sweet, that seems to have worked. :)  Thank you mucho!

Wait a second . . . maybe you can help me again.  I was setting it up and know nothing about ports in Linux.  I got this:

Testing port 21016 ... NAT Error

---

### Post by user1397 on 2006-04-28
[quote=ZelasMetallium]Sweet, that seems to have worked. :)  Thank you mucho![/quote]
You are welcome-o!

---

### Post by N3wtR0ckn13 on 2006-04-29
[QUOTE=ZelasMetallium]I was quite the fan of BitComet on my Windows system and would like to keep my torrents coming on this system but am very unhappy with the basic BitTorrent.

I've heard of Azuerus but it doesn't appear on  my 'Add Applications' list so I have no idea how to install it.  How can I do that and/or what's another program that makes BitTorrent a bit smoother to use?[/QUOTE]

I think azerus is a bad idea compared to utorrent although extremely similar. one of the arguments i've read recently mentions processing power. azerious is way in excess compared to utorrent, but see for yourself. 

[http://gomeler.com/2006/04/23/an-introduction-to-bittorrent-clients/](http://gomeler.com/2006/04/23/an-introduction-to-bittorrent-clients/)

---

### Post by ZelasMetallium on 2006-04-29
[QUOTE=N3wtR0ckn13]I think azerus is a bad idea compared to utorrent although extremely similar. one of the arguments i've read recently mentions processing power. azerious is way in excess compared to utorrent, but see for yourself. 

[http://gomeler.com/2006/04/23/an-introduction-to-bittorrent-clients/](http://gomeler.com/2006/04/23/an-introduction-to-bittorrent-clients/)[/QUOTE]
Umm . . . by posting on the Ubuntu forum I thought it was obvious I meant I need a program for Ubuntu. <_<  It seems uTorrent's Windows only.

---

### Post by CompShrink on 2006-04-29
True but note the one right after uTorrent on that list:
> Transmission does for OS X and Linux what uTorrent does for Windows. The current version of Transmission weighs in at 303KB and is a Universal Binary, meaning those of you running an Intel Mac will be able to utilize all the speed that Yonah can throw at you. Since I haven&#8217;t got a Mac or Linux distro running, I won&#8217;t be able to compare Transmission to Azureus and uTorrent, but I have been told it is a great client. If anyone has any comments on Transmission, do voice your opinion and I will try to compile them here. The installer for Transmission can be found [here]("http://transmission.m0k.org/"), choose between OS X, BeOS and Fedora Core 4.

You can download the Fedora Core 4 package, and then in a terminal:

$ sudo apt-get install alien
$ sudo alien transmission-0.5-2.cru.i386.rpm

Which will give you a deb you can use dpkg on. Like dpkg, make sure you are in the same directory as the rpm file when you do that command.

EDIT: to fix the issue with it not finding libdecrypt.so.5, just make a link:
$ sudo ln -s /usr/lib/libcrypto.so.9.7 /usr/lib/libcrypto.so.5

Then it runs normally, you don't have to recompile it using the instructions following this post. Sorry I didn't notice this earlier.

---

### Post by nchase on 2006-04-30
I've heard that a lot of private tracker sites are banning the use of Transmission. Why is this? And has it been fixed yet?

---

### Post by hito1 on 2006-05-01
[QUOTE=nchase]I've heard that a lot of private tracker sites are banning the use of Transmission. Why is this? And has it been fixed yet?[/QUOTE]


Is this true? Also, is this Transmission really just like utorrent? I don't want to get back to azureus after seeing how much utorrent is great. :)

---

### Post by catlett on 2006-05-01
[QUOTE=CompShrink]True but note the one right after uTorrent on that list:


You can download the Fedora Core 4 package, and then in a terminal:

$ sudo apt-get install alien
$ sudo alien transmission-0.5-2.cru.i386.rpm

Which will give you a deb you can use dpkg on. Like dpkg, make sure you are in the same directory as the rpm file when you do that command.[/QUOTE]
Sorry to go off topic but I ran the install like you described. Everything appeared to be fine. Transmission showed up in the menu, but when I clicked on it, it didn't launch. Has it worked for you? I've heard that sometimes even though rpms get converted to debs they may not work. Did it work for you? Did I miss something?

---

### Post by ba5e on 2006-05-02
[QUOTE=catlett]Sorry to go off topic but I ran the install like you described. Everything appeared to be fine. Transmission showed up in the menu, but when I clicked on it, it didn't launch. Has it worked for you? I've heard that sometimes even though rpms get converted to debs they may not work. Did it work for you? Did I miss something?[/QUOTE]


This happened to me as well....if you run transmission-gtk from terminal you get:

transmission-gtk: error while loading shared libraries: libcrypto.so.5: cannot open shared object file: No such file or directory

so thats the one we need! (dependecy)

---

### Post by ba5e on 2006-05-02
Okay....fixed the problem with help from the Transmission website....

1 enable universe & multiverse in sources.list

2 install (with synaptic or apt):
libssl-dev
libgtk2.0-dev and
jam
(inc. all dependencies)

3 dload latest source code for transmission [http://download.m0k.org/transmission/files/](http://download.m0k.org/transmission/files/)

4 open terminal, unpack, go into dir and type './configure' then type 'jam' (without quotes)

5 you now have a dir 'gtk' and a file (executable) in there called transmission-gtk (this is the only file you need btw)

6 copy this file to /opt (make a dir for it) OR install the deb (like you did) then just copy transmission-gtk to /usr/bin/ (overwite old one) now the link works in the menu.

One thing I can't figure out is that transmission, when opening a torrent does not actuall load the torrent! (is there an add on command for this?) I just manually 'add' it.

---

### Post by catlett on 2006-05-02
I'm stuck too. First, thanks for turning me on to Transmission. I still go into Windows to use Utorrent. I've been using Utorrent since the first release, I love it. (I've actually sent them $50 in $10 increnents over the last year I like it so much)
Anyways, I just got up and running using your update with the dependencies and jam. I downloaded a torrent to the desktop and used "add" in transmission to get it into Transmision.
Right now it isn't doing anything. I don't know if it's lack of seeds, a port issue or that Transmission itself isn't working. I'm going to go and investigate/mess with it and I'll post if I get it to be like Utorrent i.e. open up and load the torrent as soon as you download. Thanks again.

---

### Post by catlett on 2006-05-02
I'm working. Just a seed issue on my first atempt. I tried making Transmission the program to open the download but it didn't work
Meaning when I clicked on "download this torrent" the firefox prompt came up with "save to disk" or "open with". I clicked the drop down box on the open with line, chose "other" and searched to the launcher I made for transmission. Nothing happened. I then downloaded the torrent to desktop and used "add" inside transmission to load it and it is downloading.
I might try and search to the transmission-gtk directly instead of the launcher and see if that makes a difference.

P.S. I used open with and searched not to the launcher but to transmission-gtk. This caused Transmission to launch but the torrent didn't load. ???

P.S.S. How about this one. I went back with Transmission open and with the Firefox download window open. I thought maybe hitting "open" in the firefox download window would cause Transmision to open the torrent and download. Well Bittorrent opened and downloaded it. I wonder if it is a system preference thing. I'm going to see if the system has Bittorrent as it's default bittorrent client and that if I can make Transmision the default will it open and download a torrent automatically.

---

### Post by catlett on 2006-05-02
I found out my problem but got another. I didn't copy over the old transmission-gtk. When I dragged the new one over it said "I don't have permission to write to this folder".
To change the opening application it has to be where the old one is i.e. usr/bin. So it's not working for me but maybe you. Try 2 things. Scroll to usr/bin/transmission in firefox or go to a torent file and hit properties<open with. Then add usr/bin/transmission and that will be the default app and it will load and download when the file is downloaded or opened.
Well it's time for me to learn more about permissions, thanks again for the turn on to transmission.

---

### Post by nanotube on 2006-05-02
[QUOTE=catlett]
Well it's time for me to learn more about permissions, thanks again for the turn on to transmission.[/QUOTE]
here is a good link to teach you about permissions:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by ba5e on 2006-05-03
[QUOTE=catlett]
Well it's time for me to learn more about permissions, thanks again for the turn on to transmission.[/QUOTE]


try this (in dir that the NEW transmission-gtk is in):

```
sudo cp transmission-gtk /urs/bin/
```

NOTE! this will overwrite without warning any file with the same name!

---

### Post by nanotube on 2006-05-03
[QUOTE=ba5e]try this (in dir that the NEW transmission-gtk is in):

```
sudo cp transmission-gtk /urs/bin /
```

NOTE! this will overwrite without warning any file with the same name![/QUOTE]
you have an extra space in there. it's supposed to be
```
sudo cp transmission-gtk /urs/bin/
```

---

### Post by ba5e on 2006-05-03
[QUOTE=nanotube]you have an extra space in there. it's supposed to be
```
sudo cp transmission-gtk /urs/bin/
```[/QUOTE]


Thanks!! have edited it to show correctly :)

---

### Post by nanotube on 2006-05-03
[QUOTE=ba5e]Thanks!! have edited it to show correctly :)[/QUOTE]
hehe, you had to go and make my post obsolete, did you? :)

---

### Post by catlett on 2006-05-03
Thank You. (both)

---

### Post by ba5e on 2006-05-08
[QUOTE=nanotube]hehe, you had to go and make my post obsolete, did you? :)[/QUOTE]


God we must be totally retarded, it should be:

```
sudo cp transmission-gtk /usr/bin/
```

and NOT sudo cp transmission-gtk /urs/bin/ !!!

---

### Post by CompShrink on 2006-05-08
To fix the issue with it not finding libdecrypt.so.5, just make a link:
$ sudo ln -s /usr/lib/libcrypto.so.9.7 /usr/lib/libcrypto.so.5

Then it runs normally, you don't have to recompile it using the instructions following this post. Sorry I didn't notice this earlier.

I edited my initial post to point this out.

---

### Post by nanotube on 2006-05-08
[QUOTE=ba5e]God we must be totally retarded, it should be:

```
sudo cp transmission-gtk /usr/bin/
```

and NOT sudo cp transmission-gtk /urs/bin/ !!![/QUOTE]
hahaha yea... dude, i totally didn't see that. :)

---

### Post by ectoidly on 2008-01-27
Hey all...
I'm new at Mac and need some guidance :)
I was using Azerius and it sucked, so a buddy turned me onto Transmission, which I dloaded and installed.  Im on leapord, by the way.  i open the transmission gui fine, but when I try to dload a torrent firefox gives the message " ...associated helper application does not exits. change it in your preferences."
but i don't see where to associate it in firefox or transmission.
Any thoughts, ideas, suggestions?

Thanks guys
-EC

---

### Post by Ub1476 on 2008-01-27
Hm, you know this is a Linux Ubuntu forum, right?

But well, I haven't use Mac before, but it's probably some settings for file accosiations in the OS X control panel, or maybe you can right click on the torrent file>Preferences>Open with.. 

But, you would be better of in a Mac forum!:)

---

### Post by motion parallax on 2008-01-27
If the original question on this thread is still up I'd have to say I'm enjoying KTorrent.  There are some downsides, but I've never downloaded at the kind of speed that KTorrent has given me.  Avg for weak torrent files is between 20kps and 50kps, but I've had several files coming in at 200kps, and one file at over 1000kps.  

Azureus never gave me that kind of speed on Windows.  

But I've only used Linux for a few days, so maybe I need to get some more experience :)

---

### Post by ectoidly on 2008-01-28
AAaaa...gotcha...
Thanks for the redirect though
-E

---

### Post by newbeeman on 2008-01-28
Not sure if I'm missing something here. 

The original poster liked Utorrent, but never got onto thinking about Utorrent with Wine. That's what I use, works a treat.

I also use Deluge, just as an after thought, both work fine since I found out about port forwarding.

---

