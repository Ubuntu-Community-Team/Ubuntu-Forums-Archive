---
title: "RealPlayer / Firefox plugin problems"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by Larry Grant on 2006-03-02
I'm having a hard time getting Firefox to use the RealPlayer 10 plugin.  I think I need to change something on the Download Actions options dialog, but I think something is messed up with my Firefox, because that Actions list is completely blank.

As of now, Firefox is using mplayer to play video, and my problem with that, is that it won't go "full screen".  I would like to make it use RealPlayer 10 instead to see if that will give me a full screen option.  I have installed RealPlayer 10 but when I go into "about plugins" on Firefox, it lists RealPlayer 9 with mplayer but nothing about RealPlayer 10.

I'm a bit frustrated by my lack of Linux skills ... I don't know how to uninstall RealPlayer 9 (or anything else for that matter), and I don't know how to point Firefox to RealPlayer 10.

---

### Post by daredevil on 2006-03-02
I have this problem too but i did not install RealPlayer 9 and MPlayer plugin though. Me too looking for a solution. Larry Grant ill notify u if i come across a solution

---

### Post by Larry Grant on 2006-03-02
What about uninstalling Firefox and reinstalling... would that help?

However...

- I don't know how to uninstall stuff, and

- I'm concerned that uninstalling the only browser on my system will mess things up.

---

### Post by Perfect Storm on 2006-03-02
I don't know how you installed the previous realplayer, but you can go to synaptic package manager press the search button and uninstall it through there.

To install realplayer 10 there's sevreal options.
1) check my signature where it says Automatix.

2)
 Onlu works if you are using breezy i386 x86
 ```
sudo gedit /etc/apt/sources.list
```
add:
[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```
sudo apt-get update
sudo apt-get install realplay
```

3) Go here [http://www.real.com/linux?pcode=rn&opage=freeplayer_partner&src=freeplayer_partner](http://www.real.com/linux?pcode=rn&opage=freeplayer_partner&src=freeplayer_partner)
Download it and follow the instruction which can be found on the same site.

---

### Post by daredevil on 2006-03-02
It is only for installing real player (i think) but plug in for firefox did not work for me ???

---

### Post by Larry Grant on 2006-03-02
Anyway, I already installed RealPlayer 10.  The problem is that Firefox is not using it.

---

### Post by Perfect Storm on 2006-03-02
Let me guess you're not using the default FF which comes ubuntu?

---

### Post by Larry Grant on 2006-03-02
Yes, I am using that.  So far, I never installed FF on Ubuntu.

---

### Post by Larry Grant on 2006-03-02
To clarify.. After installing Ubuntu, I used Automatix to install a bunch of multimedia plugins to FF.  Then when I saw that I couldn't get video full screen, I installed RealPlayer 10, but FF doesn't use its plugin.  That's where I stand now.

---

### Post by javyer on 2006-03-03
Hello,

I have the same problem, i got a lot of plugins into my FF ( mplayer, vlc, totem, realplayer, plugger ... etc ).
I havn't found any solutions to select which plugin FF choose by default.

I was testing Gnash plugin last day, and the only solution to force FF to use it insteed of flash, is to remove this one :( .

How FF manage plugins having sames mimes types capabilities ? that is the question. :D

---

