---
title: "Complaint!"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by RockinDolphin on 2007-01-08
I have recently installed Ubuntu on my machine. I was having problems and came to this forum seeking answers. I am in the correct forum, right? ABSOLUTE BEGINNER TALK? 'Cause a lot of the responses to posts that have been made in this forum have been complete gibberish and have me almost pulling my hair out!

The reason I decided to try this distro was because I read a review and someone said that Ubuntu was meant to be as painless an install as possible. Well, that's great! I applaud that notion, but I'm used to GUI based things and all I get from these posts are geek-speak. Someone will give a piece of advice, but I'm looking at it saying, "Huh? Now where am I supposed to put ALL THOSE COMMANDS? The person giving the advice failed to say!

Currently, I'm having problems downloading updates. I've seen where a lot of people are, and it appears to be a goof-up within a command-line. Something about removing "us." from the string. Well, I sure wish I knew where to find that!

I feel I have done pretty good at teaching myself what I have on using a computer, up to this point.  I'm terribly sorry that I find it hard to deal with DOS, let alone another language. It seems to me that that is when personal computing started to take off is when some genius came-up with the graphical interface. It seems to me, however, that Linux, 'Hard-core Linux users', and the development community are still trying to hold-on to this command-line fixation and to heck with people like me who are dependent on GUI's. I've taught myself to manually program CNC machines, which aren't as complicated as programming languages go, but I CAN learn. Thing is, I would like to be able to wade into the shallows before being thrown into the deep end. Can we please remember that this is the Absolute Beginner Forum? Thank you!

---

### Post by kj1h234lkj1234 on 2007-01-08
The file that controls which package repositories are used is /etc/apt/sources.list

You can edit it by typing:

```
gksudo gedit /etc/apt/sources.list
```into the terminal. You can start the terminal from Applications -> Accessories -> Terminal in the top left of your desktop.

Adding .us to the http:// lines in there simply makes your system retrieve the packages from a more local mirror (assuming you live in the USA).

After editing that file, you can download the latest updates through Synaptic (System -> Administration -> Synaptic Package Manager) or by using these 2 commands (from the terminal again):

```
sudo apt-get update
sudo apt-get dist-upgrade
```

A reason most people (myself included) prefer a command-line interface is speed. It's much more efficient to write a simple script to do a task than to do it through a GUI every time, for example.

---

### Post by RockinDolphin on 2007-01-08
Sure. It's all well and good *if you know what to type and where to type it[I]*[/I], but I'm starting fresh into this thing and have a LONG way to go! 

Thank you for the info. I learned about the terminal and used it a couple of times when I ran across something that explained clearly what to do, but this download speed on the updates is killing me!

---

### Post by kj1h234lkj1234 on 2007-01-08
> **RockinDolphin said:**
> Sure. It's all well and good *if you know what to type and where to type it[I]*[/I], but I'm starting fresh into this thing and have a LONG way to go! 

Thank you for the info. I learned about the terminal and used it a couple of times when I ran across something that explained clearly what to do, but this download speed on the updates is killing me!

[http://ubuntuforums.org/showthread.php?p=1983722#post1983722](http://ubuntuforums.org/showthread.php?p=1983722#post1983722)

There's a 99% chance I just posted the solution to your problem. :P

I just did a fresh install and had to disable IPv6 because Firefox was CRAWLING

(On the other hand, I am glad that Firefox 2 is actually usable on Linux. :) It's HORRIBLE on Windows)

---

### Post by RockinDolphin on 2007-01-08
The fix worked, at first. I was getting at least 400Kbs speeds. All I was doing was trying to update the package list in Synaptic, but then it throttled-down to miserable speeds again. I'm wondering if it reverted back to it's original setting. Is there something wrong with the US mirror, then?

---

### Post by xpod on 2007-01-08
Sorry to hear your woes RD......
The fact is that most stuff in Ubuntu can in fact be done with a GUI but when it comes to telling people how to do xyz then a simple command typed into the terminal is usually a lot quicker & easier for all concerned than trying to direct someone through numerous points & clicks via possibly numerous GUI`s..

The fact that you had trouble finding the terminal is enough to show how hard navigating numerous GUI`s can potentially be.
You`ll soon get the hang of things im sure but it just takes a little time & patience during those initial days & weeks....
I wasn`t any programmer or dos expert myself when i came to Ubuntu RD and in fact i had only switched a pc on for the first time a couple of months previously.

I understood less than most but i can assure you that it does all fall into place eventually:D 
Well,mabey not it "all" but certainly enough to get by ok

---

### Post by slimdog360 on 2007-01-08
> **RockinDolphin said:**
> The fix worked, at first. I was getting at least 400Kbs speeds. All I was doing was trying to update the package list in Synaptic, but then it throttled-down to miserable speeds again. I'm wondering if it reverted back to it's original setting. Is there something wrong with the US mirror, then?
Did you make sure you rebooted your computer after doing that ipv6 thing?

---

### Post by STREETURCHINE on 2007-01-08
[QUOTE=kj1h234lkj1234;1983708]The file that controls which package repositories are used is /etc/apt/sources.list

You can edit it by typing:

```
sudo gedit /etc/apt/sources.list
```into the terminal. You can start the terminal from Applications -> Accessories -> Terminal in the top left of your desktop.

it is best to use gksudo when using gedit or any graphical programs

                  gksudo gedit /etc/apt/sources.list

---

### Post by RockinDolphin on 2007-01-08
I haven't done the IPv6 thingy, yet. I just took 'us.' out of the command that tells where to get the updates. When I was just trying to update the package list, I started at 400+Kbs and got throttled down. However, when it came to actually downloading the packages, I was cruising right along at 600+Kbs, which is definitely what I like to see!

---

### Post by kj1h234lkj1234 on 2007-01-08
> **STREETURCHINE said:**
> it is best to use gksudo when using gedit or any graphical programs
```
gksudo gedit /etc/apt/sources.list
```
Ah yea, you're right. I forgot. Sorry. Original post edited. :)

Can't you tell I don't use a GUI for anything? :/

---

### Post by RockinDolphin on 2007-01-08
Next question is: Since I'm using a cable modem through an ethernet card, does the IPv6 thing affect me?

---

### Post by RockinDolphin on 2007-01-08
Huh. I posted a reply, but I must've accidentally put it in the wrong thread...

My next question is: Does the IPv6 thing affect me with a cable modem through an Ethernet card? I have read in posts about IPv6 and DSL modems, so was wondering...

---

### Post by RockinDolphin on 2007-01-08
Well, so far so good! My speeds are kick-*** and I've got the MP3 player going! Hopefully, if all goes well, I'll have this thing all specced-out like I want it when Micro$oft starts screwing people over even more with Vista! Many thanks to all who have helped me!

---

### Post by kj1h234lkj1234 on 2007-01-08
> **RockinDolphin said:**
> Next question is: Since I'm using a cable modem through an ethernet card, does the IPv6 thing affect me?

I know you're all set, but I'll answer anyways.

Currently, 99.999999999999999% of the world uses IPv4. That's addresses that look like this: w.x.y.z

You are one of the users of IPv4, so yes, this does affect you. :) It has to do with the protocol being used, not the physical hardware. 

IPv6 is the newer version of IP, because apparently we're "running out" of IPv4 addresses (thanks to the United States Department of Defense's hogging of half the available addresses).

I won't get into the technical aspects of why having IPv6 enabled will slow your connections down, but it does.

More info:

[http://en.wikipedia.org/wiki/IPv4](http://en.wikipedia.org/wiki/IPv4)

[http://en.wikipedia.org/wiki/IPv6](http://en.wikipedia.org/wiki/IPv6)

---

### Post by RockinDolphin on 2007-01-08
Thanks for that info! I *do[I]*[/I] like to try to understand the 'why' of things.

---

