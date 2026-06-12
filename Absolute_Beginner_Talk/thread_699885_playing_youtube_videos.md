---
title: "playing youtube videos"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Quotidian Minutia on 2008-02-17
I am having a lot of trouble getting youtube (and other videos) to play in Firefox.  I've done a lot of hunting around in this forum and other places for solutions, and have tried a number of different things, but still with no luck.  Although I'm a newbie, I can guess that it's a Flash issue, and also has something to do with the fact that my machine is amd64 (never would have bought it if I knew what trouble it would cause!!).  Anyway, the latest thing I've discovered to try is at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)
but when I do the very first thing on the list, I get a warning:

WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  util-linux
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 5632B of archives.
After unpacking 5353kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'

Well, to someone as new as me, that sounds serious!!!  I can't honestly say that I do know what I'm doing, so I didn't proceed.  But I wonder what else I can do?  I could continue following the instructions from that page, but what if I do something I don't know how to undo?? :confused:

I really need some help here.  I've been with Ubuntu for about a week now, and am starting to find it more trouble than it's worth, and yet I don't want to return to the bad old days of windows.  It's these little things that keep making my ubuntu experience frustrating. :(

---

### Post by iansane on 2008-02-17
I don't use gnash. I have 64 bit computer but use 32 bit Ubuntu. I went in Firefox to the adobe flash download page.

[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

 They only gave me linux options for download so the auto detected my system. Downloaded the tar.gz file. Used rightclick and extract here, then in terminal cd to the directory it extracted too and type ./flashplayer-installer  That will install it. No problems

Well I say no problems but apparently it doesn't work right for everyone cause there are a lot of posts about it.

---

### Post by bbukh on 2008-02-17
Since i do not like to use Flash (most of it is used for ads nowadays) I use YouGrabber which can be downloaded from [http://yougrabber.sourceforge.net/](http://yougrabber.sourceforge.net/). To convert .flv file into .mpg use the following script
```

#!/bin/bash
#Converts YouTube .flv into .mpg
#
#Example: script movie.flv movie.mpg

ffmpeg -i $1 -ab 56 -ar 22050 -b 500 -s 320x240 $2

```

Boris

---

### Post by Flyingjester on 2008-02-17
> **iansane said:**
> I don't use gnash. I have 64 bit computer but use 32 bit Ubuntu. I went in Firefox to the adobe flash download page.

[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

 They only gave me linux options for download so the auto detected my system. Downloaded the tar.gz file. Used rightclick and extract here, then in terminal cd to the directory it extracted too and type ./flashplayer-installer  That will install it. No problems

Well I say no problems but apparently it doesn't work right for everyone cause there are a lot of posts about it.

+1

---

### Post by wolfen69 on 2008-02-17
why not just install the 32 bit ubuntu and avoid any headaches? i guarantee you wont notice a difference in speed.

---

### Post by Presto123 on 2008-02-17
> **iansane said:**
> I don't use gnash. I have 64 bit computer but use 32 bit Ubuntu. I went in Firefox to the adobe flash download page.

[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

 They only gave me linux options for download so the auto detected my system. Downloaded the tar.gz file. Used rightclick and extract here, then in terminal cd to the directory it extracted too and type ./flashplayer-installer  That will install it. No problems

Well I say no problems but apparently it doesn't work right for everyone cause there are a lot of posts about it.

+1 as well. If you have any issues, follow the directions listed on the site, and as iansane says, download the tar.gz.

---

### Post by spacefreak86 on 2008-02-17
I got YouTube videos to work using Flash player, but I'm still extremely timid around the terminal. Is there a GUI front end program to download .flv (and convert to .avi or .mpeg) ?

---

