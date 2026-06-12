---
title: "Internet from Command Line"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by cactaur on 2006-08-22
After this recent incident, I was wondering, is it possible to browse the web using just the command line? Luckily, I had a dual-boot system with Windows, but for other people, would it be possible to run firefox or any other browser to for example get to the Ubuntu forums?

---

### Post by Dr. Nick on 2006-08-22
Thier are a few command line web borwsers, lynx comes to mind for me. I am sure thier are others aswell

---

### Post by Brunellus on 2006-08-22
firefox and graphical browsers will not be possible, since they depend on the xwindows system.  Text-mode browsers like lynx and links2 will be possible...but they only support text.  No pictures, not even much in the way of formatting.

It is possible to do nearly everything from the commandline;  it simply requires a recognition that things in a textmode universe are not what you expect from living with X or other windowing systems....

---

### Post by Klaidas on 2006-08-22
Well, lynx is the one I'd prefer.
It's stone-age, but what else to do when your're stuck at commandline and need internet?
hint: have a livecd by hand :)

---

### Post by Brunellus on 2006-08-22
with lynx you can party like it's 1989.

Maybe the Great X Blackout of '06 would be a good time to revive gopherspace for ubuntu users.

---

### Post by Ragazzo on 2006-08-22
> **Brunellus said:**
> firefox and graphical browsers will not be possible, since they depend on the xwindows system.  Text-mode browsers like lynx and links2 will be possible...but they only support text.  No pictures, not even much in the way of formatting.

Links2 has a graphics mode: "links2 -g -mode 1024x768x16M".

---

### Post by Brunellus on 2006-08-22
> **Ragazzo said:**
> Links2 has a graphics mode: "links2 -g -mode 1024x768x16M".
...which depends on the xserver.  OP was inquiring whether browsers could be launched from the command line only.

---

### Post by gThree on 2006-08-22
Check out w3m too ... a bit better than lynx IMO.

---

### Post by calx on 2006-08-22
I like elinks for text mode browsing.

Check out rtorrent for command line bittorrent fun, and bitchx of course.

---

### Post by Ragazzo on 2006-08-22
> **Brunellus said:**
> ...which depends on the xserver.  OP was inquiring whether browsers could be launched from the command line only.

From Wikipedia: "The graphical mode works even on Unix systems without X or any other window environment, using either SVGALib or the framebuffer of the system's graphics card."

---

### Post by cactaur on 2006-08-22
Cool, I'm sure this'll be really helpful in case of another emergency.

---

### Post by Cephus on 2006-08-23
Just such an emergency occured today with the bad upgrade for the xserver.  The GUI was broken, and I'm still a complete novice at the Linux command line.  Using a Windows machine at work to scan for the fix in the Ubuntu forums, I made the mental note to install Lynx on my machine as soon as it was back up and running.

If I had Lynx this morning, the broken GUI would have been only a temporary annoyance.  Having to leave my machine "broken" this AM and search for the answer on my Windows machine at work left me in a panic till I saw the fix was actually pretty simple.

It's definately time to at least become more acquainted with the command prompt, though.  With essentially seven virtual machines to play with... :p

---

### Post by nanotube on 2006-08-23
> **calx said:**
> I like elinks for text mode browsing.


i second that. elinks is good at preserving the general page layout, unlike lynx

---

### Post by 3rdalbum on 2006-08-23
You can definately run Links2 from the terminal; it even renders images straight to the framebuffer. There's a package that you can apt-get, which allows you to use the mouse in console programs... I think it's either "twin" or "gpm". Anyway, you can use that in Links2.

Pity it brings down my computer when it quits... oh well, that's the price of being a "text-pistol"!

---

### Post by drtvasudevan on 2006-08-23
twin and links2.
the gpm is a general purpose mouse interface. nothing to do with browser?
downloaded and installed.
for i too will be lost with just cli!

---

### Post by derred on 2006-08-23
lynx and elynx are the best command line browsers that I know of(think about them as firefox with no pictures or mouse). You can also use mutt for email(as an alternative to evolution or thunderbird or even, dare I say it on a linux forum ... Outlook!!!).

As I understand it you want to have access to the internet in the case something goes wrong. A live cd is the easyest way to do that, usually giving you a graphical interface. I would recomend Ubuntu's live cds or for lower end systems DSL(it doesn't have all the bells and whistles but it does have firefox)

Let's hope you will never need to use them, but I would recommend installing them now with synaptic rather than later with apt :D

---

### Post by mssever on 2006-08-23
This may be slightly off-topic, but while we're talking about text-mode, it would be a good idea to invest some time learning to work from the command line. It's a steep learning curve, but once you've learned, you'll probably discover that it's the fastest way to do many things. And, if you're ever in a situation without X, you won't be lost.

---

### Post by Brunellus on 2006-08-23
> **3rdalbum said:**
> You can definately run Links2 from the terminal; it even renders images straight to the framebuffer. There's a package that you can apt-get, which allows you to use the mouse in console programs... I think it's either "twin" or "gpm". Anyway, you can use that in Links2.

Pity it brings down my computer when it quits... oh well, that's the price of being a "text-pistol"!
I note that I've had permissions issues running links2 -g from the command line;  I've only been able to start it up successfully with root privileges (not good, eh).

---

