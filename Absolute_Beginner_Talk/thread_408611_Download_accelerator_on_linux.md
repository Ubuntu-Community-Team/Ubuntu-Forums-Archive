---
title: "Download accelerator on linux"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by ggaaron on 2007-04-13
Is there any download accelerator for linux? I can't find one - I'm not searching for a manager, but for a program that starts multiple threads when downloading one file, thus downloading it faster. I think aget can be used for this, but I can't make it show me how much of the file was already transfered, and how fast it is downloading.

Thanks in advance.

Aaron

---

### Post by happy-and-lost on 2007-04-13
It's a bit unreliable sometimes, but the DownTheMall! Firefox extension is the only download accelerator I've managed to find.

---

### Post by emrextreme on 2007-04-13
Kget is also a choice.

---

### Post by ggaaron on 2007-04-14
But isn't Kget only a manager with no speedup?

---

### Post by Malta paul on 2007-04-14
I use Firefox pug- in 'DownThemAll'   from [www.mozilla.com/en-us/firefox/customize](www.mozilla.com/en-us/firefox/customize). :D

---

### Post by ggaaron on 2007-04-14
DownThemAll seems to work, thanks=)

---

### Post by brazzmonkey on 2007-04-27
indeed, kget is a download manager, not a download accelerator

---

### Post by Buffalo Soldier on 2007-04-27
My personal choice is axel. Description from synaptic:
> **_A light download accelerator - Console version_**

This program tries to accelerate the downloading process by using multiple connections for one file. Starting from version 0.97, the program can use multiple mirrors for one download as well. The program tries to be as light as possible (25-30k in binary form), so it might be useful as a wget clone on byte-critical systems.

Installation:```
sudo apt-get install axel
```

Example 1 - Without any extra option:```
axel www.example.com/example_song.ogg
```

Example 2 - Download using 1 thread only (some site block multiple connection):```
axel -n 1www.example.com/example_song.ogg
```

Example 3 - Queue download using **&&**:```
axel www.example.com/example_song1.ogg && axel www.example.com/example_song2.ogg && axel www.example.com/example_song3.ogg
```

Example 4 - Specify output:```
axel www.example.com/example_song.ogg -o newtitle.ogg
```

Example 5 - Alternative progress bar:```
axel -a www.example.com/example_song.ogg
```

---

### Post by go_beep_yourself on 2007-10-29
[http://budlite.blogspot.com/2007/08/using-download-accelerator-with-apt-get.html](http://budlite.blogspot.com/2007/08/using-download-accelerator-with-apt-get.html)

---

### Post by erginemr on 2007-10-29
You may use the wxDownloadFast, which uses multi-threading:
[http://dfast.sourceforge.net/](http://dfast.sourceforge.net/)

Also the getdeb.net site has a copy:
[http://www.getdeb.net/app.php?name=wxdownload%20fast](http://www.getdeb.net/app.php?name=wxdownload%20fast)

It has multi-threading and scheduling capacities. And it is "fast".

---

### Post by mysticmatrix on 2007-10-29
Downloader for X(found in add/remove) also worked for me

---

### Post by go_beep_yourself on 2007-10-29
> **erginemr said:**
> You may use the wxDownloadFast, which uses multi-threading:
[http://dfast.sourceforge.net/](http://dfast.sourceforge.net/)

Also the getdeb.net site has a copy:
[http://www.getdeb.net/app.php?name=wxdownload%20fast](http://www.getdeb.net/app.php?name=wxdownload%20fast)

It has multi-threading and scheduling capacities. And it is "fast".

Can it integrate with Firefox or be used with flashgot?

---

### Post by erginemr on 2007-10-29
> **go_beep_yourself said:**
> Can it integrate with Firefox or be used with flashgot?

Yes, it can, via Flashgot. Flashgot web site reports wxDownload Fast as compatible with their plugin. (I ain't using it.)

---

### Post by go_beep_yourself on 2007-10-29
I tried wxDownloader, but it continuously crashes :( That is probably because it is made for Feisty and earlier version of Ubuntu. Has anyone got it working good in 7.10 Ubuntu Gusty Gibbon without crashing often and other bugs or is this just a buggy program? :confused:

---

### Post by mysticmatrix on 2007-10-30
> **go_beep_yourself said:**
> I tried wxDownloader, but it continuously crashes :( That is probably because it is made for Feisty and earlier version of Ubuntu. Has anyone got it working good in 7.10 Ubuntu Gusty Gibbon without crashing often and other bugs or is this just a buggy program? :confused:

It crashed for me too under feisty. Downloader for X is best option(recommended by flashgot)

---

### Post by Crafty Kisses on 2007-10-30
> **happy-and-lost said:**
> It's a bit unreliable sometimes, but the DownTheMall! Firefox extension is the only download accelerator I've managed to find.

That one is ** VERY** unreliable. :(

---

### Post by erginemr on 2007-10-30
> **go_beep_yourself said:**
> I tried wxDownloader, but it continuously crashes :( That is probably because it is made for Feisty and earlier version of Ubuntu. Has anyone got it working good in 7.10 Ubuntu Gusty Gibbon without crashing often and other bugs or is this just a buggy program? :confused:

Try the Edgy version given in the download section of their web page:
[http://dfast.sourceforge.net/](http://dfast.sourceforge.net/)

I am using it under Gutsy without any issues.

---

### Post by go_beep_yourself on 2007-10-30
> **erginemr said:**
> Try the Edgy version given in the download section of their web page:
[http://dfast.sourceforge.net/](http://dfast.sourceforge.net/)

I am using it under Gutsy without any issues.

The 64 bit version is unavailable, so I am using the same one you are using (32 bit version) in 64 bit Gutsy, and I haven't had any issues yet. Thanks for the suggestion. :popcorn:

---

### Post by erginemr on 2007-10-30
> **go_beep_yourself said:**
> The 64 bit version is unavailable, so I am using the same one you are using (32 bit version) in 64 bit Gutsy, and I haven't had any issues yet. Thanks for the suggestion. :popcorn:

You are welcome. Take care... :)

---

