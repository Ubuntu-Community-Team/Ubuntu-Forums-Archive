---
title: "Playing MP3 Files over the Network?"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by Blacktree on 2006-03-26
Hi everyone. I'm a Linux n00b. And naturally, I need help. ;)

I'm looking for an app that can play files that are on another computer, via the network. You see, I have Ubuntu installed on my personal machine. But all my MP3 files are on the file/web server.

I tried this with Totem, XMMS (with mp321 plug-in), and gnomp3, but none of them would let me browse the network for files to play. I also tried browsing the network in Nautilus, right-clicking an MP3 file, and choosing "open with...". But that was unsuccessful as well.

Thoughts? Opinions?

BTW, I'd also like to say that as a long-time WinDoze user and first-time Linux user, Ubuntu is pretty freakin cool. :cool:

---

### Post by nickj6282 on 2006-03-26
This works great for me in my apartment. What kind of file server do you have? Is it a Windows machine? If so you should mount the samba share to a directory on your local machine and then try to play the files.

Also, MP3 isn't possible with a default Ubuntu installation. Getting mp3's working on Ubuntu requires a little effort before it will work. Your problem may not be a network one at all.

---

### Post by Blacktree on 2006-03-26
The server runs on WinXP.

Hmm... mounting the network share. I'll try that. (I'm still not used to telling the OS to "mount" stuff ;) )

BTW, I was able to play MP3s from a local folder using XMMS with the mp321 plug-in. So MP3 player functionality isn't an issue.

Thanks for the help.

PS -- Could you recommend a media player app?

---

### Post by IYY on 2006-03-26
You can't play files if you're just browsing the samba network. You'll need to mount the drive. You need to use smbmount to mount at some mount point.

Read the manual: **man smbmount**

---

### Post by Blacktree on 2006-03-26
[QUOTE=IYY] Read the manual: **man smbmount**[/QUOTE]
Manual not found? Command not found? :confused: 

Maybe it's time to re-install Ubuntu...  ](*,)

---

### Post by nickj6282 on 2006-03-26
No need to do somethhing so drastic! You just need to install the samba client packages.

```
sudo apt-get install smbclient
sudo apt-get install smbfs
```

Then you can try mounting the Windows share

```
mount -t smbfs //servername/sharename /path/to/mount -o username=windows_username,password=windows_password
```

Also, if you want to mount this share on boot every time, just append this line to your /etc/fstab file:

```
//servername/sharename /path/to/mount smbfs username=windows_username,password=windows_password,umask=022 0 0
```

Good luck!

---

### Post by GMachine_24 on 2006-03-26
Hi:

Ok, I'm here to put my two cents in.

There is a simple and rather elegant solution to your problem - it is a free, open source program called "SlimServer" and is available from [www.slimdevices.com](www.slimdevices.com)  .
It is compatible with Linux, OS X and Windows (a different version for each).

The program will catalogue all your .mp3 files (it also works with .wma, ogg, and other formats) and stream them to any other computer you choose. You will be listening to streaming mp3 files in no time.

SlimServer allows you to access your music via a Web browser from any other computer on your network and play the music with "SoftSqueeze" - which is a Slim Devices free software music player - or with almost any other program that plays .mp3 files (Winamp, etc.)  You can play by CD, artist, pick one song at a time to add to your play list - the possibilities are almost endless.

I have SlimServer installed on a server running Fedora FC4 and I listen to my music (about 9,000 songs) from any computer in my house. You can also connect remotely (i.e. from basically anywhere on the Net) if you open the right ports in your firewall, etc. I don't do this - but my brother does. He listens to music stored on his home computer in the lab where he works - and trust me he is a security freak so I assume it must be safe.

Oh, yeah, and it's simple to install and run and you don't need to have a server to use it.

---

### Post by Blacktree on 2006-03-26
Nick, you rock! I can now listen to MP3 files from the server. :cool:

But the command line almost had me ripping out my hair. Manually adding all my MP3 files to the playlist should be fun & exciting, too. ](*,)

GMachine, that looks interesting. I'll have to try it out. Thanks.

---

### Post by GMachine_24 on 2006-03-26
Please do. It's easier than falling out of a tree.

Good luck!!

---

### Post by nickj6282 on 2006-03-26
I've never tried the slimserver but I hear good things about it. Personally I use Jinzora ([http://www.jinzora.org/](http://www.jinzora.org/)) which requires a webserver (apache or IIS), PHP, and MySQL. I had an old crappy machine with 128mb of RAM laying around so I put in an 80GB HDD, ripped all my MP3s to it over the network, then set it up with Apache, MySQL, PHP and Jinzora. Now I can listen to my mp3s using winamp/xmms over the network using my web browser, or I can listen to them from work/school etc. over the internet.

My $0.02 ;)

---

### Post by Jose Catre-Vandis on 2006-03-28
Thanks for the help with network playing for mp3s and for the pointer to Slim Server

---

### Post by IDipSkoalMint on 2006-03-28
"Quod Libet" is a program in which I downloaded using the "Add Applications" GUI and using my mounted Windows partition, was able to play all my .mp3 files just like in iTunes (only issue was my .m4a files, but I'll work on converting them within the next few days). Just saw people were having problems getting .mp3 files to work. It's only one real step to get it installed, it deals none with the command line (only GUI) and is aesthetically similar to iTunes (to those of you who like that).

---

### Post by lost.sync on 2006-03-31
@nick: 

thanks man.

it never ceases to amazme me how any problem i have with ubuntu, i don't usually even have to ask.  some guy like you's already answered my question for someone else.  

for real, thanks.  my linux system only has 8 gigs of storage.  yes, 8.  so i'm not too keen on putting mp3s on it.  this is one of the most useful solutions i've found to any problem in a long time.

---

### Post by hugmenot on 2006-03-31
[QUOTE=IDipSkoalMint](only issue was my .m4a files, but I'll work on converting them within the next few days).[/QUOTE]


You really don't have to. QL supports MP4 playing and tagging perfectly.
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=7834&d=1143803002[/IMG]

---

### Post by nickj6282 on 2006-03-31
Ok, an update for those interested. I set up Slimserver on my SuSE fileserver and it's pretty sweet. I can listen to my MP3 files from any network or internet connected machine. It even has an option to downsample your music to a lower  bitrate for slow network/internet connections. If anyone out there is interested in installing and trying it, just let me know and I'll be happy to post an installation guide and dispense some pointers.

-Nick

---

### Post by ivan.virtuale on 2006-05-13
[QUOTE=GMachine_24]Hi:

Ok, I'm here to put my two cents in.

There is a simple and rather elegant solution to your problem - it is a free, open source program called "SlimServer" and is available from [www.slimdevices.com](www.slimdevices.com)  .
It is compatible with Linux, OS X and Windows (a different version for each).

The program will catalogue all your .mp3 files (it also works with .wma, ogg, and other formats) and stream them to any other computer you choose. You will be listening to streaming mp3 files in no time.

SlimServer allows you to access your music via a Web browser from any other computer on your network and play the music with "SoftSqueeze" - which is a Slim Devices free software music player - or with almost any other program that plays .mp3 files (Winamp, etc.)  You can play by CD, artist, pick one song at a time to add to your play list - the possibilities are almost endless.

I have SlimServer installed on a server running Fedora FC4 and I listen to my music (about 9,000 songs) from any computer in my house. You can also connect remotely (i.e. from basically anywhere on the Net) if you open the right ports in your firewall, etc. I don't do this - but my brother does. He listens to music stored on his home computer in the lab where he works - and trust me he is a security freak so I assume it must be safe.

Oh, yeah, and it's simple to install and run and you don't need to have a server to use it.[/QUOTE]


Hi, but how can you use slimserver without the hardware?](*,) 
Ivan

---

### Post by Horizon on 2006-06-03
[QUOTE=ivan.virtuale]Hi, but how can you use slimserver without the hardware?](*,) 
Ivan[/QUOTE]
I haven't tried it yet but I looked around the website...it's a little confusing at first glance but for anyone who's reading this. You can download it from here: [http://www.slimdevices.com/su_downloads.html](http://www.slimdevices.com/su_downloads.html)
And the instructions for linux and how to use it are here:
[http://wiki.slimdevices.com/index.cgi?SlimServer](http://wiki.slimdevices.com/index.cgi?SlimServer)

---

### Post by fenton06 on 2006-06-14
Ok, so I managed to get my directoey mounted, but is there any way I can change the permissions so I can add/delete files at will?  I think i need to use chmod, but have no idea how to use it.

---

### Post by Derspankster on 2006-12-07
OK, add me to the list. I was able to play mp3's over my network before I upgraded to edgy with Movie Player. Now, I can't. I mounted the share, can see all folders, can copy folders to my desktop and play them but cannot stream from the network location using Movie Player. The player finds the file, starts buffering, then pauses and never plays the file. I think it has something to do with permissions but something has changed with Edgy. I just can't seem to figure out what. I haven't been able to find a solution as yet browsing this forum but I'm sure there is an answer. Any one able to help?

---

### Post by BabyUbuntu on 2006-12-07
Setting up sox (12.17.9-1) ...
Setting up slimserver (6.2.1-3) ...
Adding system user `slimserver' with uid 112...
Adding new user `slimserver' (112) with group `nogroup'.
Not creating home directory `/usr/share/slimserver'.
Downloading firmware images.
svn: REPORT request failed on '/repos/slim/!svn/vcc/default'
svn: REPORT of '/repos/slim/!svn/vcc/default': 400 Bad Request ([http://svn.slimdevices.com](http://svn.slimdevices.com))
Failed to download firmware.
dpkg: error processing slimserver (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 slimserver
E: Sub-process /usr/bin/dpkg returned an error code (1)
babyubuntu@babyubuntu:~$


i dont know why it happened to me.. any solutions?

---

### Post by lemonsCC on 2006-12-07
> **nickj6282 said:**
> No need to do somethhing so drastic! You just need to install the samba client packages.


OMG!?  I just burnt my town to the ground because samba is acting funny.  I could have just installed it?

:mrgreen: \\:D/ \\:D/ :mrgreen:

---

### Post by victorbrca on 2006-12-07
My Ubuntu worked with no problem. All I had to do was install all mp3 packs from wiki, browse to Network Servers, find my other XP PC and everything was working. I could even see the "smb" on the folders.... I could also access my FreeNAS server and it's files.

  If anyone is still interested on a media server, take a look at _[www.orb.com](www.orb.com)_. You install a small software server on a PC that broadcasts information that you can them retrieve from your account on their site. You can even share your media (music, video, pics, TV if you have card, even files).

  We used to watch the last world cup at work!!!!

  My opinion is to use v1.0


Vic.

---

### Post by Derspankster on 2006-12-08
Yeah, my Ubuntu streamed network media when I was still running Dapper. Clean install of Edgy and I've lost that functionality. From what I've read, I'm not alone. If someone has a working smb.conf for Edgy that they'd like to share, I'd be very grateful.

---

### Post by tommytom on 2006-12-08
> **Blacktree said:**
> 

PS -- Could you recommend a media player app?

Now i don't know if it will suit your needs regarding streaming files etc but i think Amarok well it.....rocks!! :roll: (groan)  anyway thats my tuppence added. Enjoy!

EDIT- Sorry folks i'm about a year behind here and can't figure out if i can remove this post. :oops:

---

