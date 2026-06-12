---
title: "Getting a Linksys WMP54GS to work with ndiswrapper"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Wudugast on 2008-03-24
I'm working with a fresh install of Gutsy on a computer with no current internet connection. I'm trying to remedy this situation by enabling wireless, but I'm not having any luck. The networking tools that come with Gutsy don't work, so I've installed ndiswrapper.

If I'm not mistaken, ndiswrapper is supposed to be able to load Windows drivers from the wireless card's installation CD, but after following the instructions (which weren't very clear to me, by the way) it says the driver is invalid. What do I do now?

Here's what I get when I check it: 

> jade@jade-desktop:~$ ndiswrapper -l
wmp54gs : invalid driver!

I'm trying to install a linksys wireless-g pci adapter. It's model number is WMP54GS and the CD I'm using is version 1.4. 

I don't really know the right questions to ask about getting this working. 

I'm wondering if there's another driver out there I should use, or if I should just give up, or if there's anything I can do with the networking tools that were included with the Gutsy installation.

The default networking application seems to work in that it detects wireless capability, but it doesn't list any of the wireless networks in the area, let alone the one I want to log into. Trying to add a network works, but I still cannot connect to anything. My windows laptop can pick everything up just fine, so I think the computer isn't recognizing the card.

Where do I go from here?


***
Also, I've noticed that some people have "thanks" in their posts in an area by their names. I don't use forums very often. How do I thank the people who have helped me?  ...and is this a recent feature, or did I overlook it before?
***
I have looked at other posts regarding the WMP54GS before posting this thread, but none of them seem to be quite like the problem I'm having. I don't know much about the ins and outs of networking, so maybe that's not true...  but I don't really understand where some of those threads are going. Please provide any helpful links and explanations if you can't solve the problem outright. I know the answer's out there somewhere.
***

---

### Post by ichbinesderelch on 2008-03-24
i think the thing you do wrong is that you installed the wrong file with ndiswrapper, there is always the *.inf and the *.sys, i can't remember which one to take of them but one of them should give you a correct installation! and than it should work, i'm using almost the same card with ndiswrapper!

edit: you gotta take the .inf file

---

### Post by Wudugast on 2008-03-24
Okay. If it has already taken the wrong file, how do I get rid of it? Do I just find it, delete it, and tell ndiswrapper to take the .inf file, or do I have to reinstall everything?

---

### Post by ichbinesderelch on 2008-03-24
just do a ndiswrapper -r *.sys{removes wrong one= and than ndiswrapper -i *.inf file, thats it!

---

