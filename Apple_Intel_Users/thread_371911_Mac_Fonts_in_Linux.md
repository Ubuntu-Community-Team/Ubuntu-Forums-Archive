---
title: "Mac Fonts in Linux"
date: 2007-02-27
forum: Apple Intel Users
---

### Post by patchkov on 2007-02-27
Hi guys,

Generally, I always used to dislike the way how linux display fonts. From very early beginnings this really disrupted me and I always struggled to make them look much better. All in all, I always achieved what I wanted.

These days it happened I am a working with Mac, however at home, beloved Ubuntu. It happened that Mac is a very good system, however, as many of us agree, still lacks a lot of things (same as linux). However one thing is great, it is font rendering.

Yes, I managed to make my Ubuntu fonts looks exactly the same as those under Mac. They look nice, crispy, readable, just perfect. Two screenshots of some web-pages do not show any difference. Looking at fonts rendering, almost no difference.

The only difference are fonts itself. They render fine, but the font packages from system to system are not exactly the same as we know. It happened that Mac uses high quality fonts, which are very nice, and what I want to do is to port them to linux.

However, porting is not an easy task. When one goes to /Library/Fonts he will find many different packages, like .dfont and quite a lot of other stuff. Here is my question, **how to copy Mac fonts and make them readable in format recognizable by Linux machine?**

I found some web-pages talking about it, but they mostly relate to the old OS9 System which is definitely not what I want to achieve :)

Many thanks and I hope somebody could help me.
Krystian

---

### Post by patchkov on 2007-02-28
Come on guys(!), nobody knows how to do it?

I just want to copy fonts from my Mac to Ubuntu, that's all.

---

### Post by cendant on 2007-02-28
Just copy them

Put Truetype fonts in your home folder in ~/.fonts and enjoy

---

### Post by cocoia on 2007-02-28
To simplify this process, simply install FontXplorer on the Mac and you can easily select all system fonts and export them in a .zip.

---

### Post by das_syndrom on 2007-02-28
Hi!

The program you're looking for is called "fondu"

Just copy the .dfont files to a temp-directory
Convert them to *.ttf-files with fondu.
Put the *.ttf files in /usr/share/fonts/truetype/macfonts

Enjoy

Andi

---

### Post by patchkov on 2007-03-01
Thanks guys, probably tomorrow I'll test it and will post results.
K

---

### Post by dpny on 2007-03-01
I posted this in a thread on fonts in the PPC forum:
[i]. . . I also followed [this](http://www.isolationism.com/2006-12-27/font-rendering-on-linux/) excellent link to much improve the font rendering on my Ubuntu install. I just copied the .fonts.conf file he includes in totality.

If you really want some of the OS X .dfonts on your machine, and have access to an OS X machine, there is a way. There is an X11 font editor for OS X called [FontForge](http://fontforge.sourceforge.net/) which will take any font and convert it to any other font. I have used it to turn Lucida Grande (one of OS X's .dfonts) and some other OS X fonts into notmal Truetype fonts and use them on my Ubuntu machine. They look great.[/i]

The OS X system fonts--.dfont--are Truetyupe fonts with all non-OS X readable info stripped out, so they can only be read by OS X. The program I linked to above will convert them to normal Truetype. I took some of my OS X fonts over to my Linux machine.

---

