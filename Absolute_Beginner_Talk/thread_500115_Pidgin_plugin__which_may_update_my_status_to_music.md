---
title: "Pidgin plugin : which may update my status to music track i am listening"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by cyneuron on 2007-07-13
hello there

i use pidgin, and want my online status to chang according to the music track playing in my music player.

currently i am using Listen Music manager.

is there any plugin available for pidgin ?

by the way, any website having pidgin plugins in general ....

---

### Post by Kingsley on 2007-07-13
Here you go.
[http://sourceforge.net/projects/currenttrack](http://sourceforge.net/projects/currenttrack)

---

### Post by cyneuron on 2007-07-14
isnt there any .deb file available for ubuntu ? i don't wish to compile it as i will have to download lot of compiler tools for this....

---

### Post by alexef on 2007-08-09
> **Kingsley said:**
> Here you go.
[http://sourceforge.net/projects/currenttrack](http://sourceforge.net/projects/currenttrack)

Hi, I'm using Ubuntu 7.04 and I'm trying to build currenttrack 1.2 from source. From ./configure i get ```
checking for PIDGIN... no
configure: error:
*** Pidgin 2.0+ is required to build Currenttrack; please make sure you have the
*** Pidgin development files installed. The latest version of Pidgin is always
*** available at http://pidgin.im/.

```.
I have Pidgin 2.1.0 from getdeb, but I couldn't find a package pidgin-dev.

What should I do?

---

### Post by Radicalation on 2007-08-26
Thought this might help [http://rpmseek.com/rpm-pl/pidgin-dev.html?hl=com&cs=Pidgin:PN:0:0:0:0]("http://rpmseek.com/rpm-pl/pidgin-dev.html?hl=com&cs=Pidgin:PN:0:0:0:0")

---

### Post by happyxix on 2007-09-14
> **Radicalation said:**
> Thought this might help [http://rpmseek.com/rpm-pl/pidgin-dev.html?hl=com&cs=Pidgin:PN:0:0:0:0]("http://rpmseek.com/rpm-pl/pidgin-dev.html?hl=com&cs=Pidgin:PN:0:0:0:0")

It gives dead links. And I still havent figured this out. Anyone help?

---

### Post by splintercellguy on 2007-09-14
Die die die RPM? Building Pidgin from source should take care of the dependency complaint.

---

### Post by l.capriotti on 2007-09-14
I am using musictraker, very effective!

I configured this guy's repository:

[http://www.ansemreport.com/pidgin-backports](http://www.ansemreport.com/pidgin-backports)

as per his instructions, and installed musictraker.
Plain and simple.

Luigi

---

### Post by HokeyFry on 2007-09-27
is there a plugin like this that works with banshee?

---

### Post by mercurysquad on 2007-09-29
Hi guys,
Just compiled a .deb for musictracker. Attached. Have fun!
(this was compiled on gutsy).

---

### Post by Sciroccogti on 2007-10-07
musictracker deb there dont work at all, wont show up as a plugin in pidgin.

---

### Post by gebeleizis on 2007-10-07
It shows up for me. The problems is I can't get it to work.
I am using Audacious and I did the special formating and all the rest but ...nothing.
Too bad for me.

---

### Post by Dread Knight on 2007-10-14
Works excelent! Thanks!

(Note that this is actually a pidgin plugin xD)

---

### Post by motang on 2007-10-18
> **l.capriotti said:**
> I am using musictraker, very effective!

I configured this guy's repository:

[http://www.ansemreport.com/pidgin-backports](http://www.ansemreport.com/pidgin-backports)

as per his instructions, and installed musictraker.
Plain and simple.

Luigi
Wow sweet thanks! :-D

---

### Post by Popoi on 2007-10-22
I installed Musictracker from Debian package I found in Getdeb, the plugin is shown in plugins list of Pidgin but it doesn't work at all. Im'm using Rythmbox and Ubuntu 7.10 amd64.

---

### Post by airtonix on 2007-10-26
why the heck cant this plugin be a simple :  "Display-contents-of-changed-text-file-as-away-msg"
operation, like it is with miranda....on that bloated half witted system over at redmond.

nvm, i see the problem. tunnel vision.

---

### Post by thelost on 2007-12-10
> **airtonix said:**
> why the heck cant this plugin be a simple :  "Display-contents-of-changed-text-file-as-away-msg"
operation, like it is with miranda....on that bloated half witted system over at redmond.

nvm, i see the problem. tunnel vision.

heh, that made me chuckle. I loved Miranda and miss it dearly, pidgin doesn't compare. However, Miranda was anything but simple ;)

---

### Post by z3r0_butterfly on 2008-02-28
Whenever I have a song with a non-english characters as the title, (using this plugin from the dev package uploaded here) pidgin crashes. Any idea why?

---

### Post by Xubus on 2008-03-18
Currently using musictracker 0.4.1 here, is there any way of using the official MSN now playing method?

I've build Pidgin with msnp14 support enabled. Is there any way of simply altering musictracker or is there a plugin that already supports the msnp14 method?

---

### Post by sceo on 2008-05-04
> **gebeleizis said:**
> It shows up for me. The problems is I can't get it to work.
I am using Audacious and I did the special formating and all the rest but ...nothing.
Too bad for me.

I have this same issue.  I downloaded and manually compiled musictracker, it shows up - I configured Audacious appropriately... it just doesn't seem to be automagically changing my status message in any way.

Is there something I need to do?  Put a tag in my available message, or... something?  :confused:

Looking in Pidgin's "Debug Window," I see:
```

(18:52:25) core-musictracker: libaudacious.so 
(18:52:25) core-musictracker: Failed to load library libaudacious.so
(18:52:25) core-musictracker: xmmsctrl not initialized properly
(18:52:25) core-musictracker: libaudacious.so.3 
(18:52:25) core-musictracker: Failed to load library libaudacious.so.3
(18:52:25) core-musictracker: xmmsctrl not initialized properly
(18:52:25) core-musictracker: Getting info failed. Setting empty status.

```

So... how do I gets?  :)

Hmm, apparently it has something to do with DBUS and Audacious 1.4+?
[http://code.google.com/p/musictracker/issues/detail?id=86](http://code.google.com/p/musictracker/issues/detail?id=86)

---

