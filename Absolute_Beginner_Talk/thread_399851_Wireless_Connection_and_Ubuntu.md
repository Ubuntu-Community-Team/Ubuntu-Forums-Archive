---
title: "Wireless Connection and Ubuntu?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by c-breakdown on 2007-04-02
I was thinking about loading ubuntu onto my laptop so I started it up with the Live CD.  I notice that I don't have any internet connection though.  I'd like to make sure I'll be able to access the internet wirelessly before I go through with the install.  Any advice would be great.

---

### Post by mikewhatever on 2007-04-02
Can you open the terminal (Applications>Accessories>Terminal), type > sudo lshw -C network and post the output. Also, look in System>Administration>Networking. Is there a wireless option?

---

### Post by bcrowell on 2007-04-02
Hi,

Here are some of my own notes on what I had to do to make wifi work:
[http://www.lightandmatter.com/cgi-bin/meki?unix#Unix_Notes,home_network,wifi](http://www.lightandmatter.com/cgi-bin/meki?unix#Unix_Notes,home_network,wifi)

Dunno of any of that is helpful. I never did succeed in getting it to start up the wireless connection automatically every time it booted, so I ended up having to make a script that would do the necessary stuff.

Basically the story seems to be that wifi is not very well integrated into GNOME yet, so you may have to muck around with the command line.

-Ben

---

