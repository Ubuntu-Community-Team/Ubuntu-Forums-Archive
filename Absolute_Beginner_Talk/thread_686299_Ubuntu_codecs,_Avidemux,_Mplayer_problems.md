---
title: "Ubuntu codecs, Avidemux, Mplayer problems"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by siretfel on 2008-02-03
Hi all,

I'd like to start with some issues I have with Ubuntu gutsy and avi playing.

1. I use mostly VLC player to view avi files. Recently I downloaded Mplayer to try it. Whilst VLC plays almost everything so far and without problems Mplayer does not. I only managed to play an avi file last night and that was only one time. The second time I couldn't play it and so far it doesn't open avi files. Also the rewind option doesn't work in Mplayer.Which players do you guys use?

2. In windows we know that there are codec packs like Klite full, which is installed in my windows partition and everything works fine. In ubuntu are there any codec packs which i MUST install in order to view avi files? I understand (and correct me if i'm wrong) that VLC has embeded codecs and can play avi. In order to play avi with other player like mplayer do i need to download codecs?

3. I read that avidemux is equivalent to virtualdub. I must say that so far i cannot make it work. I try to embed permanent subtitles in avi files that with virtualdub everything works perfect, but avidemux ALWAYS causes me problems. What program do you use?

4. I try to open subtitles to play with my avi files like in VLC and they don't display correctly in my native language. Furthermore i want to ask this: I want to open the subs in a program like vobsub to see them. In windows they are displayed correctly (the characters i mean). In ubuntu the language seems ....souahili hahaha. I cannot view the subs correctly in text editor or ANY other program. Not even in openoffice word. Is there anything i can do to view them correctly? And why don't they display correctly in VLC although I CAN READ DOCUMENTS IN MY LANGUAGE AND SIMPLE TEXT FILES!!?

Thanks in advance

---

### Post by hhhhhx on 2008-02-03
1 - try xine
2 - get automatix, then install ubuntu restricted extras.
3 -  dunno what your talking about
4 - will try to get back to you on that one

---

### Post by jan quark on 2008-02-03
dont get automatix

it will cause heavy compatibility issues

---

### Post by siretfel on 2008-02-03
> **jan quark said:**
> dont get automatix

it will cause heavy compatibility issues

Oh man....just got it....damn it!!!
:confused:

---

### Post by hhhhhx on 2008-02-03
> **jan quark said:**
> dont get automatix

it will cause heavy compatibility issues
seriously, i've never had any :confused:

---

### Post by zvacet on 2008-02-03
> seriously, i've never had any

I see so many posts here where people try to clean mess produced by Automatix.That doesn´t mean that you shouldn´t use it.It is your comp and you make all decisions.In other hand lot of people say they have no problems using it.

>  get automatix, then install ubuntu restricted extras.

Why do you want to make it complicate when it can be very simple?Just

```
sudo apt-get install ubuntu-restricted-extras
```

```
gsudo /etc/apt/sources.list
```

add this line 

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

Save and close the file.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
```

After this go to the synaptic and in search box type w32(or64 if you use 64 bit version)codecs and install them.I use Mplayer with no problems.

---

### Post by jan quark on 2008-02-03
have read this :) ?
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by zvacet on 2008-02-03
@ **jan quark**

If you asked me,yes I did.I don´t use it and I don´t recommend anyone else to do it.But that is all I can do.I can not stop anyone who want it to use.Other thing against Automatix (from my point of view) is that without it you start to learn how linux works,because you have to learn how to download,install....

---

