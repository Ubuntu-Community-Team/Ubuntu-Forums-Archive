---
title: "A few questions before switching"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by bubbadawg on 2006-02-17
Hello All ---

I am completely new to Linux having just started playing around with it over the last week. After trying several different Live CDs (Knoppix, SuSE, Ubuntu, Kubuntu) I think I am ready to take the plunge and install Ubuntu on my laptop. Ubuntu seemed to run the best on my laptop detecting all of the hardware and I didn't really have any issues with it.  Thus my decision.

With that said, I still have some hesitations. For example, I am somewhat intimated by the amount of command line coding. I have spent a decent amount of time on these forums, but can't seem to find a tutorial/reference to the different commands and their functionality, etc. For example, what is "SUDO"? It's probably just that I am not looking in the right place. Can someone point me in the right direction? Any insight or guidance is greatly appreciated.

Thanks for any and all replies.

---

### Post by aggiechemist on 2006-02-17
First, don't be too scared. I agree that the command line seems wierd at first, mostly because my background is in Windows and that never makes any use of the command line anymore. But once you get used to it, it can be easy and a lot faster than trying to do things through GUI.

When I got started, I really liked this guide. It taught me all the basics of the command line and I still go back to it for a reference now that I am using linux daily:
[http://linux-newbie.dotsrc.org/](http://linux-newbie.dotsrc.org/)

Finally, about sudo. In linux, there are two big groups of users: average and super users. Average users aren't allowed to install software, move important settings, etc. Super users can do whatever they want. This makes the system safer against things like hacking, and also prevents breaking the computer. The way Ubuntu works is to (almost) always make you log in as an average user. If you want to do something important (like add a new program) you use the command sudo to give yourself temporary superuser power. The command actually translates (I think) as Super User DO. Oh yeah, and the name for the super user is almost always root but that is a minor point.

Hope this helps, welcome to Ubuntu.

---

### Post by Iowan on 2006-02-17
Everything you wanted to know?[http://www.linuxdevcenter.com/linux/cmd/]("http://www.linuxdevcenter.com/linux/cmd/")This is more of a reference than a how-to.  There is also (usually) a **man** page for commands - fi type **man sudo** for the syntax of the sudo command - although sometimes the structure doesn't really tell you how to use it...

---

### Post by Rumor on 2006-02-17
Here's a couple fairly good resources for learning the command line:

A very basic step-by-step guide: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

An extensive list of commands with explanations of each: [http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

---

### Post by bubbadawg on 2006-02-17
Thanks for all of the (quick) replies and kind assistance. I am really **impressed** with the users on this board and their extreme willingness to help out.

Thanks again.

---

### Post by TrendyDark on 2006-02-17
If you ever need help with anything, posting here at this forum will most likely yield an answer. 

Oh, and just to let you know. The amount of time you'll be spending using the command line really depends on what you're going to be using the computer for. For example, when I have a fresh install of Ubuntu, I spend maybe the next hour or so in command line, installing drivers for my wireless card, video card, etc. After that is all done, I don't really touch the command line, except to check for updates.

---

