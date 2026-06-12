---
title: "Twonky Music server setup"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by chrism7 on 2006-01-08
Hi all, 
I'm new to linux and I'm having difficulties setting up Twonkymusic server.  I've had the Windows version running properly on my old Windows setup to stream to a Netgear MP101, but can't get the linux working on Ubuntu.  I have version 2.7.5 and it runs to create the config files.  I can manually edit the .ini file, but can't open the html file (firefox says can't connect to localhost:9000 - I assume this is due to the ports being closed?  How do I open the relevant ports?  I've tried using Firestarter but my lack of knowledge shows through!).  Then when I try and run musicserver I get a "Segmentation fault", with no other info.  Any ideas what I need to do to fix this, or what might be casuing it?

Thanks,
Chris

---

### Post by chrism7 on 2006-01-08
Anyone with any ideas?  Or is this in the wrong forum?
Chris

---

### Post by chrism7 on 2006-01-09
I'm going to give this one more bump.  Anyone who has this working on Ubuntu - what do I need to check?

---

### Post by uglysmurf on 2006-05-08
Hey chrism7 -- I've been trying to track down the TwonkyMusic server with no luck...can't find a link to anything but the TwonkyMedia trial on their site...can you point me to where you found it?

If I have any luck getting it working hopefully I can help you out

---

### Post by jkopp on 2007-02-20
I have Twony working, but performance is less then desirable.  To get mine working I simply extracted the files into a directory I named TwonkyVision in 'usr/local/TwonkyVision'  There are a number of files extracted to the folder: 

username@yourdomain:/usr/local/TwonkyVision$ ls
lame             RevisionHistory                  twonkyvision-config1.html
licence-de.rtf   twonkymedia.db                   twonkyvision-config.html
licence-en.rtf   twonkymedia.sh                   twonkyvision-musicserver.ini
Linux-HowTo.txt  twonkymusic
radio.m3u    

You will need to edit the ini file to fit your server configuration.  The most important thing to ensure is that twonky has at least read access to your music directory.  Then you can start the server:

username@yourdomain: /usr/local/TwonkyVision$ sudo ./twonkymedia.sh start
Password:
Starting /usr/local/TwonkyVision/twonkymusic ... TwonkyMusic Version 3.1

This should do it.  You should be able to access the config through the [http://you.local.ip:9000](http://you.local.ip:9000).  I am sure there is a way to add this service to init.d, but I have not done so yet.  I just start the service when I need it.

This is what worked for me to get it running, although I wont promise that this will work for everyone.  I currently have problems with the server parsing my music directory.  When I play music from a directory and skip through files the server breaks and I am forced to restart.  The windows cient worked well for me, but the linux client left me wanting more support.

Good Luck

---

### Post by tjkolev on 2007-07-28
Hello!

I downloaded the TwonkyMusic from here: [http://www.twonkyvision.de/Download/TwonkyMusic/index.html](http://www.twonkyvision.de/Download/TwonkyMusic/index.html)

It all installed fine, but I am at my wit's ends why it won't run. Here's what my setup looks like.

```

ls -l /etc/init.d/twonkyserver
-rwxr-xr-x 1 root root 4120 2007-07-23 22:41 /etc/init.d/twonkyserver

ls -ld /usr/local/TwonkyVision
drwxr-xr-x 4 root root 4096 2007-07-22 12:59 /usr/local/TwonkyVision

ls -l /usr/local/TwonkyVision
total 428
-rw-r--r-- 1 root root    311 2007-07-22 12:59 install.log
-rw-r--r-- 1 root root  16104 2007-04-04 06:21 licence-en.rtf
-r--r--r-- 1 root root   2763 2006-08-11 10:06 Linux-HowTo.txt
drwxr-xr-x 2 root root    106 2007-04-11 10:39 plugins
-rw-r--r-- 1 root root    421 2004-10-31 11:57 radio.m3u
drwxr-xr-x 2 root root   4096 2007-04-11 10:39 resources
-rw-r--r-- 1 root root  28238 2007-04-11 05:01 RevisionHistory
-rw-r--r-- 1 root root    422 2007-04-11 10:39 twonkymedia-default.ini
-rwxr-xr-x 1 root root   3946 2007-07-22 12:59 twonkymedia.sh
-rwxr-xr-x 1 root root   4300 2007-04-11 10:32 twonkymusic
-rwxr-xr-x 1 root root 352276 2007-04-11 10:32 twonkymusicserver
-rw-r--r-- 1 root root     29 2007-07-22 12:59 twonkyvision-musicserver.ini

```

The script in init.d tries to run twonkymusic from the above directory. But it fails. I try to start it manually and it fails with the same error

```

/usr/local/TwonkyVision/twonkymusic
-bash: /usr/local/TwonkyVision/twonkymusic: No such file or directory

```

Same thing with sudo:

```

sudo /usr/local/TwonkyVision/twonkymusic
sudo: unable to execute /usr/local/TwonkyVision/twonkymusic: No such file or directory

```

What is going on here? ](*,) The file is there. Is bash giving me the wrong error back? Perhaps it is corrupted or something?

Thank you!
tjk

---

### Post by RayFig on 2007-11-27
I was getting this same problem about "No such file or directory" even though I knew it was right there.

It turned out that on my 64 bit machine, Twonky needed 32 bit support. Or something. 

Anyway, this fixed it:

 ```
sudo apt-get install ia32-libs
```

Now it works fine for a while, an hour or so, then the MP101 player just stops in the middle of a song and after about ten seconds, skips to the next song.

I'm still trying to track that down. . .

-Ray

---

### Post by rotsa on 2007-12-07
RayFig:

I think your problems with the MP101 not playing more than 10 seconds and then skipping does not have to do with Twonky.
I guess you use your Netgear MP101 wireless?
Frankly - the wireless capabilities on that one is useless...
There is a hardware mod you can do to make it a little bit better (search on google, there is also a group on Yahoogroups with some useful information - I did it and it helped a bit but was still not good enough).
My advise is simply to use it wired.

Good luck!
rotsa

---

### Post by RayFig on 2007-12-20
I have one MP101 wired and one not and I agree, the wired one is much less trouble.

I was trying to move my Twonky server from Windows to Ubuntu 7.10 but kept having the freeze after playing a few songs. It would not happen with Twonky 4.1 on Windows or with Tonkyy 4.4 from Ubuntu to a laptop with On2Share UPnP Windows Media Plugin. I would also get the freeze using MediaTomb on Ubuntu serving to the MP101.

So it seemed to be some combination of Ubuntu on AMD64 and the MP101 and possibly the Twonky 4.1 to 4.4 upgrade. 

So I gave up moving my music server to the MythTV backed machine.

But now I just got a kernel update and some other updates and am trying again. I llistened for about 40 minutes with no freeze, but I need to test it for hours to be sure.

-Ray

---

### Post by hyper_ch on 2007-12-20
If you just want to setup a streaming audio server I use gnump3d... very simple to setup:

[http://www.howtoforge.com/share_your_music_with_gnump3d](http://www.howtoforge.com/share_your_music_with_gnump3d) (it might even be in the repositories)

---

