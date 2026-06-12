---
title: "Where to find Popular Linux Programs to Download"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by forumposters on 2006-07-29
Is there a good site to browse and download programs that are tried and true and have good reviews?

---

### Post by Rumor on 2006-07-29
What sort of programs? There are lots you can download right from your own desktop using Applications > Add|Remove or more through Synaptic at System > Administration > Synaptic Package Manager

For list os programs, there's this thread in the forums: [http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183)

Or this site listing several equivalents: [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by aysiu on 2006-07-29
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) should help.

---

### Post by forumposters on 2006-07-29
Specifically, I'm looking for a program where I can compile c++ programs.  I want to learn c++ and I'd like to find a nice program that might make it easier to learn this programming language.

---

### Post by aysiu on 2006-07-29
Look at the link I linked to before.

---

### Post by forumposters on 2006-07-30
OK, I see that when you go to add/remove there are some things to download for programming.  I didn't realize that it actually downloaded the programs for you.  I thought it was just a place to add them once you downloaded them somewhere else.  Very cool, I love this operating system more and more everytime I learn something like this that makes so much sense.

---

### Post by steve.horsley on 2006-07-30
> **forumposters said:**
> OK, I see that when you go to add/remove there are some things to download for programming.  I didn't realize that it actually downloaded the programs for you.  I thought it was just a place to add them once you downloaded them somewhere else.  Very cool, I love this operating system more and more everytime I learn something like this that makes so much sense.

Yup. It's cool.

Almost by definition, any "popular" programs will be listed there. Very many of the the popular free and open-source programs are there. You will see even more if you enable the multiverse and universe repositories. Aysiu's link is as good as any to see how. 

You will definitely want to install the build-essential package. This is the GNU C++ compiler and associated utilities. You can do this from the command line with these commands:
> sudo aptitude update
sudo aptitude install build-essential

---

