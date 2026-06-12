---
title: "How To Get Itunes? (Or something just like it)"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2007-11-21
Ok so i have the 32 bit Ubuntu Gusty Gibbon 7.10. And I have and Ipod and I was just wondering, how do i get Itunes? I've heard about Wine? Is that the way to go? I heard that you can only do older versions of Itunes with Wine?Which my Ipods already updated to the 7.4 or Itunes. So if that's not the way to go then tell me what you know.:) (I would like a program very much like Itunes and that works well with Ipods if possible)

---

### Post by angelsguitar on 2007-11-21
There's this program called gtkpod, but i believe it works only for transfering files between the iPod and your computer

---

### Post by RadiationHazard on 2007-11-21
could i get a link to it? or instructions on what to do?

---

### Post by aysiu on 2007-11-21
Read this:
[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

---

### Post by Pres-Gas on 2007-11-21
When you read the article aysiu recommended, I would seriously look into amarok.  It really seems to have all the features of iTunes and more.  I would probably switch to it on my Mac if it ran well on it.

---

### Post by zach12 on 2007-11-21
You can install it(gtkpod) by doing this

[B]1,ctrl alt f1
2,type sudo apt-get install gtkpod(wait a few min)
3,ctrl alt f7
4,open it as you would any program

If you need to uninstall it do this
1,ctrl alt f1
2,type sudo apt-get remove gtkpod(wait a few min)
3,ctrl alt f7

if you don't like it have a look a Virtual box![/B](i use it pm me for help installing it)
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Inxsible on 2007-11-21
Rhythmbox and Songbird are very similar to iTunes in the GUI layout.

Although most of the music players in Linux will be able to connect to iPods (except the new generation, where Apple has added some proprietary locks or something), the above two "feel" a lot like iTunes

---

### Post by RadiationHazard on 2007-11-21
could i get the install on the amarok program please? you make it seem pretty nice. I wanna try it out for myself. :) so if you could just give me a step by step on how to get it up and running...

---

### Post by Inxsible on 2007-11-21
> **RadiationHazard said:**
> could i get the install on the amarok program please? you make it seem pretty nice. I wanna try it out for myself. :) so if you could just give me a step by step on how to get it up and running...Open a terminal and type in```
sudo aptitude install amarok
```

---

### Post by RadiationHazard on 2007-11-21
Media Change: Please insert the disc labeled 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386.


What do i do?

---

### Post by frego on 2007-11-21
Sounds lik you need to insert your install disc or you can change your repositories so that it doesn't look for the install CD, if you'd rather.   

If you'd like to change your repositories to not look for the CD (do this only if you have broadband), go to System->Administration->Software Sources and uncheck the box at the bottom that is next to the CDROM install disk.

Here's a link to the Ultimate Ubuntu Desktop: 
[http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

which guides you through setting up some repositories to be able to get some real useful programs including Amarok and gtkpod which were mentioned earlier in this thread.  If you are not comfortable with the command prompt, just use System->Administration->Synaptic to install the programs listed.

---

### Post by frego on 2007-11-21
PS:  In the world of Ubuntu you really don't generally need to find an "install program" as you do in windows. Basically you use the package manager of Synaptic (at a command line: "apt" or "aptitude") to add and remove any and mostly all programs.  If something isn't available, you likely need to change the repositories (the source(s) of your available installation options).  I would recommend by starting with a good guide like the link I sent you in the above message of mine.

---

### Post by RadiationHazard on 2007-11-22
It's a bad idea. Or atleast it didn't work good for me. It really slows down my computer. can i get some help on how to get this crap off??:confused:

---

### Post by RealG187 on 2007-11-22
I hate iTunes.

Anyways, goto /home/yourusername/.wine/drive_c/Program Files

You can delete it, when does it slow down, just when you run it? Or does it start automatically with the computer?

---

