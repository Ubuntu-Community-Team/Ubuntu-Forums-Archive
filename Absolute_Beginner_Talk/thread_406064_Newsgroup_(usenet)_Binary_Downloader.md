---
title: "Newsgroup (usenet) Binary Downloader?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by chrisf79 on 2007-04-10
Greetings,

I used Newsbin on Windows to grab binaries from newsgroups.  What's a good program to do the same on Linux?

Thank you,

Chris Farrugia

---

### Post by picpak on 2007-04-10
I use Pan. You can get the latest version here:

[http://darrenalbers.com/Pan/](http://darrenalbers.com/Pan/)

---

### Post by kspringer on 2007-04-10
I've used PAN and liked it.
It's in the repositories.

Check out [this link]("http://www.newsreaders.com/unix/clients.html") for many different readers.

k

---

### Post by chrisf79 on 2007-04-10
> **picpak said:**
> I use Pan. You can get the latest version here:

[http://darrenalbers.com/Pan/](http://darrenalbers.com/Pan/)

Problem is, Pan is a newsreader.  I'm looking for something to download binaries.

---

### Post by jvc26 on 2007-04-11
Reading here [http://pan.rebelbase.com/](http://pan.rebelbase.com/)
> 
Pan is a Usenet newsreader that's good at both text and binaries. It supports offline reading, scoring and killfiles, yEnc, NZB, and multiserver. 

Doesnt that do what you need it to?
Il

---

### Post by J-me on 2007-04-11
Good thing I done a search I was just about to post this! I found 1 from ur list kspringer that I have tried "KLibido" but it dont have the secure cornection thing to stop isp from tappigng the speeds so it wont work on mine =(

---

### Post by pirothezero on 2007-04-11
sabnzbd:[http://ubuntuforums.org/showthread.php?t=320475&highlight=sabnzbd+on+edgy](http://ubuntuforums.org/showthread.php?t=320475&highlight=sabnzbd+on+edgy)

I used grabit on windows. Moving over to linux I tried out some of the random little gui applications around and I didnt like them at all. Then found hellanzb which is a python nzb engine that works but I would always have intermitent stoppages and random stuff happen. 

Then I found the guide above followed it down on Edgy and haven't looked back since. If you end up trying it out and having issues post on here.

---

### Post by J-me on 2007-04-11
I used grabit it also.

I'm following them instructions pirothezero, it seems to think the files should be in home/username/ when there not so i copied them there also incase they need to be.

also it asked me to edit a file called SABnzbd.ini but when i go to where the download went its there but called SABnzbd.ini.sample so I copied the file and paste it and renamed it to what the tut said 


I get to the very last command which is 

```
./SABnzbd.py -d -f SABnzbd.ini
```

and i get this in my terminal

```
Traceback (most recent call last):
  File "./SABnzbd.py", line 37, in ?
    import cherrypy
ImportError: No module named cherrypy
```

sorry for being such a n00b Im slowly getting there lol =)

---

### Post by Mithrilhall on 2007-04-12
There is always [Hellanzb]("http://www.hellanzb.com/trac/").

Also, [Grabit]("http://www.shemes.com/") works fine under Wine...at least it did when I tried it.

---

