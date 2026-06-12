---
title: "ftp and website design software???"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by TrevorRS on 2007-06-18
is there an ftp tool built into ubuntu?

also website design software can i run dreamweaver and photoshop on ubuntu?

Cheers

Trevor

---

### Post by the.phantom on 2007-06-18
not a expert but can help some 

1. ftp...well you have firefox right? just download the add-on fireFTP
it is easy and looks/works like the well known ftp programs
or you can use "filezilla"

2. photoshop...well look and you have gimp on your system and works close like it !


3. dreamweaver...well never used it 

but you can use a WYSIWYG nvu
or you can use bluefish a full editor

---

### Post by Pconfig on 2007-06-18
I use filezilla for FTP. If you have universe in you rep, just type

```
sudo apt-get install filezilla
``` in the terminal.

Otherwise add universe to your rep by

```
sudo gedit /etc/apt/sources.list
```

and add

```
deb http://archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty universe
```

to it and type

```
sudo apt-get update
```

for php editing i use gphpedit. Works fine and gives some color to your page. It does't work the same as dreamweaver though as dreamweaver produces it's own html code. Here you have to do everything manually. Didn't try bluefish out though. It's known as a more complete web-editing package.

For photo editing, just use gimp. There's also a tool called 'pixel' wich people seem to like.

Greetings

---

### Post by Jimmyfj on 2007-06-18
Yes there's built in ftp in Nautilus just click Places --> Connect to server

As for the web, there quanta anf bluefish - For picture edit The GIMP 

Dreamweaver? Wouldn't know that but search the forum, there might be something in here about that.

---

### Post by TrevorRS on 2007-06-18
thank you very much 

you really are a helpful bunch :D

Trevor

---

### Post by nine01a on 2007-06-18
If you use Nautilus with it's built-in ftp support, you can use gedit for editing text files. By default, in Feisty, it didn't support saving to ftp but if you add "ftp" to the list of keys with gconf-editor, it can be done (/apps/gedit-2/preferences/editor/save, to be exact). Cheers.

---

### Post by TrevorRS on 2007-06-18
> **nine01a said:**
> If you use Nautilus with it's built-in ftp support, you can use gedit for editing text files. By default, in Feisty, it didn't support saving to ftp but if you add "ftp" to the list of keys with gconf-editor, it can be done (/apps/gedit-2/preferences/editor/save, to be exact). Cheers.

that sounded very helpful but i didnt understnad what u meant by ading it to the list of keys?

Trevor

---

### Post by quercusrobur2002 on 2007-06-18
Try NVU for website design, I installed it and for ages couldn't get my head around how to use it, but then downloaded a couple of webpages I liked the look of and basically 'reverse engineered' them in NVU and found it a very fast learning curve to then put together a reasonable website  (well better looking than my old website at any rate...) very quickly, I basically re-designed my whole site at [www.spiralseed.co.uk](www.spiralseed.co.uk) in a couple of days using completely open source software - Open Office Writer for text, GIMP for graphics including the banner and page heading/link graphics, NVU for site design and FireFTP for uploading! Not bad for free!!!

---

### Post by TrevorRS on 2007-06-18
thanks will give it a go and see what i can come up with

Trevor

---

### Post by TrevorRS on 2007-06-18
right when i go to [http://www.nvu.com/download.php](http://www.nvu.com/download.php)

and click to download nvu this 1 nvu-1.0-pc-linux2.6.10-gnu.tar.bz2

when i have it downloaded how do i install it?

Cheers

---

### Post by the.phantom on 2007-06-19
nvu should be in applications.add/remove?

if you do it that way no problem and it will show up in the app list ;-D

---

### Post by guitodd on 2007-06-19
Quanta Plus and Bluefish are a bit more Dreamweaver like.  I was able to install flash MX and Fireworks MX using WINE.  Not sure about Dreamweaver..  I think the required server type selection keeps the program from loading properly in WINE.

---

### Post by guitodd on 2007-06-19
Oh and... both of these are in add/remove.  Best of luck.

---

### Post by quercusrobur2002 on 2007-06-19
NVU is in the repositories for Dapper Drake, which I'm still using, although apparently the program has now been renamed KompoZer so maybe thats where you'll find it if you are using Feisty fawn?

---

### Post by timmahhny on 2007-07-30
Dreamweaver CS3. Free download for a 30 day trial in Windows, not sure about Ubuntu. I will say that it is tough to learn how to work this thing. I have tried for seven years to learn Dreamweaver and gave up on it. 
 I do the hand coding with textpad. 
 Am looking for some good software in Linux to use. 
 Dreamweaver offers a lot, but for me it was difficult to try and figure things out. I did program some websites with Flash MX, but had help from a book. Flash seemed much easier to learn than Dreamweaver. 
 I am going to try NVU, Bluefish, and a few other programs that I found listed in this post. 
Good luck
Timmahhny

---

### Post by yogo on 2007-07-31
For ftp, I would go with Filezilla, it is the best FTP program I have ever used out od several.

Dreamweaver actually works better for me using Wine in Ubuntu than it does in Windows. The ftp in Windows is slow as can be, never had a clue as  to why so I always used Blumentals software, it is for hand coders, not a wysiwyg, I hate those editors as the code they produce is bloated.

However, the Blumentals WeBuilder 2007 has an OLE Error 80004001 and does not work in Wine. That said, it looks like I will be using Dreamweaver as every one of the Linux apps I hated for their FTP capabilities. I looked at Komposer and uninstalled that quickly, I have Bluefish I will just let that hang around but it is really not up there with Blumentals software.

Here is the page for [WeBuilder]("http://www.blumentals.net/webuilder/"), however all of their software editors have the best FTP integration of any editor out there. It works great if you work on the fly and are editing several files at once in different locations. The program remembers where it opens every file and all you have to do is hit save and it transfers the file to the correct folder on your server.

---

### Post by ramjet_1953 on 2007-07-31
I have found NVU to be a very nice piece of Website design software.

Here is a link to the home page:

[http://www.nvu.com/index.php](http://www.nvu.com/index.php)

There is a deb package available. Just scroll down the download page, until you find it.

Regards,
Roger :cool:

---

### Post by Astronomy_Nick on 2007-09-23
I've been using **Bluefish** since installing Ubuntu and it does a very nice of keeping everything sorted and code-highlighted etc. The only thing that slightly bugs me is the time it takes for a file to be saved online, i.e. uploaded by the ftp. Does anyone knows why this should be? Does it have to re-establish the connection every time? It is the same if I upload after a 10s edit as it is if I have had the page opened for several hours before saving. It can get a bit infuriating and when I used EditPlus2 on XP the upload was almost instantaneous providing it hadn't timed-out.

---

### Post by HermanAB on 2007-09-23
Check your DNS settings.  You probably have a lame DNS as the first one in /etc/resolv.conf.  You can test the DNS response time with 'dig', then put the fastest one at the top of the list.  For maximum speed, you could run a local DNS slave.  Online delays are usually DNS related.

Cheers,

Herman.

---

### Post by Astronomy_Nick on 2007-09-23
Thanks for the reply Herman, however on checking my /etc/resolv.conf file the only DNS server is my wireless router, which responds quickly. In general I don't have any problems with my internet connection, it just seems that Bluefish does not keep the ftp connection open, and everytime I want to upload it has to go through the whole connection/authentication procedure. Perhaps this is simply a more secure way of doing it but it does take away some of the speed of editing websites when you have to wait 20-30s for a page to upload. Does anyone else have this same experience with Bluefish?

---

### Post by RKCole on 2007-09-23
Nvu has actually, in itself, become quite outdated.  The developer of Nvu went on to work on a project called Composer; while I'm looking forward to the release (unknown) of Composer, there is an updated bug-fix release of Nvu--KompoZer.  You can get the latest .deb package of this program [here]("http://www.getdeb.net/app.php?name=Kompozer").  It has a really nice built-in CSS editor as well.

Hope this helps.

Take care.

---

