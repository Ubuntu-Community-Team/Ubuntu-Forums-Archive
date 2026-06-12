---
title: "Mp3...?"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by kozak on 2005-12-21
I have just finished installing Ubuntu5.10 Linux.
Everything is going fine so far.
First question though.

When I try to play my burned cd's, it says it can't play or something.
Any ideas ?
Also, what would be a good p2p program that works with this operating system ?
Thanks.

---

### Post by Iandefor on 2005-12-21
GTK-Gnutella is a good program. Also, try Nicotine. What's the exact text of the error message? It could be a wide variety of things, and the information you gave simply isn't enough to be able to work out what the problem is.

---

### Post by kozak on 2005-12-21
Okay,

So I browse the cd in my cd rom.
I click on a song.
It says the following in a box that pops up. :

Totem could not play 'file:///media/cdrom1/101-nirvana-heartbreaker_(live_1987_first_nirvana_show)-rns.mp3'.
There were no decoders found to handle the stream.
You might need to install the corresponding plug ins.


Thing is, I don't know what plug ins to install.
I am very new to this linux ubuntu thing.
It's my first day! lol.

Do you know a link where I can get gnutella ?

---

### Post by jbmalone on 2005-12-21
You don't have the updated package to play mp3s.  Do a google search for "playing mp3s in ubuntu" and there should be lots of tutorials.

---

### Post by kozak on 2005-12-21
It appears that I do not know what I am doing.

---

### Post by jbmalone on 2005-12-21
[http://debian.tu-bs.de/mplayer/ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/w32codecs_20050412-0.0_i386.deb](http://debian.tu-bs.de/mplayer/ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/w32codecs_20050412-0.0_i386.deb)

I think I got support through the w32 codecs.

---

### Post by kozak on 2005-12-21
Thanks.
I'll give that a try.
I am a total newb all over again!

---

### Post by Sutekh on 2005-12-21
I would suggest you check out [Automatix]("http://ubuntuforums.org/showthread.php?t=66563")

It can install the necessary codec for mp3 playing, along with a host of other applications.  It is pretty dead easy to use.

---

### Post by kozak on 2005-12-21
Is there any tutorials on how to install things ?
Whats the "terminal" ?
:confused:

---

### Post by Sutekh on 2005-12-21
The terminal can be found in the Applications Menu (top left) under Accessories.

It is a command line interface, similar to using something like DOS.

What are you trying to install?  The w32codecs.deb or Automatix?

I'd really suggest going for Automatix.

---

### Post by kingsidy on 2005-12-21
like suteck suggested, try installing Automatix and use it to install the necessary codecs. I think that you need to install the lame library which i think handles mp3s. at the terminal do: apt-get install lame

---

### Post by jbmalone on 2005-12-21
Automatix is amazing.  Thank you for that link!

---

### Post by Sutekh on 2005-12-21
To install Automatix is very easy

If you've found the terminal, you will need to type these two commands
```
wget http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb
sudo dpkg -i automatix-ubuntu_4.0-1_i386.deb
```
This will download and install the Automatix Package.  

It should install it to the Applications menu under System Tools.  Once you open it, you will be given the choice of programs you'd like to install.  

You can always come back and install more, so only choose the ones you need at the moment.  You need option (24), which obviously you wouldn't install if you lived in the US, would you? ;) 

Once (24) is installed you should be up and running.

As for a good tutorial or two; I'd highly recommend these

[Terminal for Beginners - by Kyral]("http://ubuntuforums.org/showthread.php?t=73885")

and

[Installing Software in Ubuntu - by aysiu]("http://www.psychocats.net/linux/installingsoftware.php")

---

### Post by kozak on 2005-12-21
kozak@S0106000ea6e06f1e:~$ wget [http://beerorkid.com/automatix/automatix](http://beerorkid.com/automatix/automatix) -ubuntu_4.0-1_i386.deb suso dpkg -i automatix-ubuntu_4.0-1_i386.deb
wget: invalid option -- u
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
kozak@S0106000ea6e06f1e:~$



Did I do it wrong, I think so.

By the way, I'd like to thank you all very much for your help/input.

---

### Post by jbmalone on 2005-12-21
You need to copy the first line in first and then hit enter, and then paste the second line in and hit enter.  It'll ask you for your password, put it in and then hit enter.  Also, it should be sudo no suso.

---

### Post by kozak on 2005-12-21
Thanks for pointing that out.

I got this now...

[B]kozak@S0106000ea6e06f1e:~$ wget [http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb)
--22:21:32--  [http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb)
           => `automatix-ubuntu_4.0-1_i386.deb'
Resolving beerorkid.com... 205.196.218.206
Connecting to beerorkid.com|205.196.218.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33,180 (32K) [text/plain]

100%[====================================>] 33,180        48.45K/s

22:21:33 (48.36 KB/s) - `automatix-ubuntu_4.0-1_i386.deb' saved [33180/33180]

kozak@S0106000ea6e06f1e:~$ supo dpkg -i automatix-ubuntu_4.01_i386.deb
bash: supo: command not found
kozak@S0106000ea6e06f1e:~$

---

### Post by jbmalone on 2005-12-21
You typed supo not sudo.  Supo isn't a corrent command.

---

### Post by kozak on 2005-12-21
Okay..

kozak@S0106000ea6e06f1e:~$ sudo dpkg -i automatix-ubuntu_4.0-1_i386.deb
Password:


But, It won't let me type my password...

---

### Post by jbmalone on 2005-12-21
Yeah, you won't see the password being inputed.  Just type it and hit enter.

---

### Post by Iandefor on 2005-12-21
In the password box, under Linux (to be specific, *any* POSIX-Compliant operating system, but that's a little out of your depth for the moment), if you type a letter, it doesn't show a little asterisk to indicate you've typed something in. This is just another security measure.

---

### Post by kozak on 2005-12-21
Okay, and my password would be the same password I enter to log on right ?

---

### Post by kozak on 2005-12-21
Now I am here...

Selecting previously deselected package automatix.
(Reading database ... 59101 files and directories currently installed.)
Unpacking automatix (from automatix-ubuntu_4.0-1_i386.deb) ...
Setting up automatix (4.0-1) ...
kozak@S0106000ea6e06f1e:~$

---

### Post by kozak on 2005-12-21
I went to Applications -> System Tools -> Automatix

Now it is doing a bunch of stuff.

---

### Post by kozak on 2005-12-21
I think I am off and rolling.
I hope so.
I am probobly the biggest ubuntu noob!
Thank you all very much for your help.
I really appreciate it.

---

### Post by kozak on 2005-12-21
Is there any way to get my digital camera to work with this ?
The install cd is for Windows..

---

### Post by jbmalone on 2005-12-21
Well, it kind of depends on what type of camera you have, but I can go ahead and tell you that the easiest way to get it working is to go buy a card reader and do it that way.  I have a Canon SD500 and there was no way I could get it to work, I went to Wal-Mart, bought a ten buck SD reader and everything is perfect.

---

