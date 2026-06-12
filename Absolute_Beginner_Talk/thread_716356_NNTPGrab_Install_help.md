---
title: "NNTPGrab Install help"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by frimilden on 2008-03-05
Someone has recommended NNTPGrab to me and being the n00b that I am I am having a tough time installing it. I am using Ubuntu 7.10. Up to now I have been using hellanzb and myhella GUI but while it is a good program it just is not for me, I prefer to have something with a good GUI and many options, so I have been looking for something different. I also use PAN for headers.

I have downloaded the source and while trying to configure I ran across a few things  I needed to install. All went well with that until I get to Glade. I get an error saying "Glade 2.0. (libglade2-devel)" is not installed so I download the .rpm and use alien to convert to .deb and install it, then try to configure again and it still says it is not installed. :confused:  Well I got fed up and removed all of it and am going to try fresh.

Am I going in the wrong direction here? Is there an easier way of getting this running? Any help is appreciated. Or is there another newsreader that will unrar, repair, etc...? As I said I am new to linux and have only been using it for 2 weeks so bear with me please. :lolflag:

Thanks

---

### Post by Liet_Kynes on 2008-03-06
Have you tried installing it from the ubuntu repositories?

---

### Post by frimilden on 2008-03-10
> **Liet_Kynes said:**
> Have you tried installing it from the ubuntu repositories?

Thank you for replying. I have looked in Synaptic and it is not in there. Do I need to add a source or something? Please bear with me as I said I am a complete newbie and am learning.

---

### Post by Liet_Kynes on 2008-03-11
What I meant was install the libglade2-dev from synaptic. And then try installing nntpgrab.

I hope that helps.

---

### Post by frimilden on 2008-04-04
Ok I finally was able to install NNTPGrab after much frustration and a lot of digigng on google. So for anyone interested in how to get it running here ya go:

```

sudo apt-get install build-essential pkg-config \
libsqlite3-dev libsexy-dev \
libgtkspell-dev libgtkhtml3.8-dev \
libglib2.0-dev libdbus-glib-1-dev \
libcurl3-dev libpcre3-dev \
libxslt1-dev libnotify-dev libtool \
automake1.9 autoconf firefox-dev \
gettext

wget http://nntpgrab.signalrunner.com/nntpgrab-0.2.4.tar.bz2

tar -xvjf nntpgrab-0.2.4.tar.bz2

cd nntpgrab-0.2.4

./configure
make
sudo make install
sudo ldconfig
```


:popcorn: Hope this helps others. It really is a decent newsreader with a Grabit feel to it, and has a low ram and CPU usage.

---

