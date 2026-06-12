---
title: "A new user with some questions/problems"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by sleepjump on 2006-07-26
hi guys, I recently installed ubuntu on my laptop a few days ago. It's running great, but I have some problems/questions.

1. My biggest problem right now is that it restarts randomly on me. I will be  using a program, then all of a sudden a black screen pops up asking me for my login name which then procedes to restart the computer. this doesnt seem to be happening in a fixed time, which makes me think that i may be hitting a hotkey on my keyboard on accident. I really have no idea on what to do for this.

2. I cannot play wmv videos whatsoever. I've searched many posts on the forums and followed steps but each time I get an error. For example, I installed automatix and when I try installing the audio/video codecs this is the error I get:[IMG]http://img234.imageshack.us/img234/9118/problemlm7.jpg[/IMG]

3. I used a ubuntu install disc, but I am not sure if I need to update to the newer version that is out. If I do need to, I'm not quite sure how to go about doing this.

If anyone could awnser any of my questions or help with my problems that would be awsome, thanks.

---

### Post by SeanHodges on 2006-07-26
Number 1... I'm not sure about, sorry I've never seen that before. If theres any other information you can give about the issue (such as what does the dialog asking for your login name look like?) I'll get back to you if i think of something.

Number 2... If I were you, I'd remove the repository you have saying "deb http://download.gna.org..." whatever - automatix probably added that, look in /etc/apt/sources.list and add a "#" at the beginning of the line to comment it out. Then download and use this:

[http://easyubuntu.freecontrib.org/]("http://easyubuntu.freecontrib.org/")

It should give you the Windows codecs as well as a bunch of others you'll need.

Number 3... Do you know which version of Ubuntu you are using? Breezy? Dapper? The stuff in /etc/apt/sources.list should tell you. If it's Dapper, you're up-to-date, just type the following in a console to make sure the packages are all upgraded to latest version:

```
apt-get update && apt-get upgrade
```

---

### Post by FenrisAbraxas on 2006-07-26
> **SeanHodges said:**
> 
Number 3... Do you know which version of Ubuntu you are using? Breezy? Dapper? The stuff in /etc/apt/sources.list should tell you. If it's Dapper, you're up-to-date, just type the following in a console to make sure the packages are all upgraded to latest version:

```
apt-get update && apt-get upgrade
```

I guess from the screenshot of the xterm he is using Breezy :p

So i would recommend a full system upgrade and for the random restarts try to select from the grub menu the memtest+ check the messages in dmesg and post it here to try to guess the problem.

---

### Post by SeanHodges on 2006-07-26
> **FenrisAbraxas said:**
> I guess from the screenshot of the xterm he is using Breezy :p

So i would recommend a full system upgrade and for the random restarts try to select from the grub menu the memtest+ check the messages in dmesg and post it here to try to guess the problem.

lol can't believe I missed that on his screenshot!

Full system upgrade: [https://help.ubuntu.com/community/DapperUpgrades]("https://help.ubuntu.com/community/DapperUpgrades")

It looks like lot to read, but only a section of it applies to you (i suggest trying "Upgrading with the Update Manager application").

---

### Post by kurniawands on 2006-07-26
:-D :-D :-D  you guys... sean, fenris... hahahahahahaha...

btw, i have no idea for sleeps 1st Q

for 2nd, have you update your source list, sleep ??? :-k (trying to get serious hahahaha) since many sources are no longer serving today...

3rd, what makes you feel not sure ???

---

### Post by jimbren on 2006-07-26
On the restart problem...is your laptop hot to the touch when this happens?  My guess would be that the power management isn't doing something right and your fan isn't kicking on.  Most CPUs will trip themselves and restart when they get too hot, as a means of preventing them from frying themselves.

Does your fan run?

---

### Post by sleepjump on 2006-07-26
thank you everyone for the help. the videos are now playing correctly, and I updated to 6.06 or the newest version. as for the random restarts, It was being caused by my computer overheating (it's like 120 degrees in my room at the moment). thank you very much again for all the help, it's very much appreciated and I am very happy with ubuntu.

---

### Post by arnieboy on 2006-07-26
> **SeanHodges said:**
> Number 2... If I were you, I'd remove the repository you have saying "deb http://download.gna.org..." whatever - automatix probably added that, look in /etc/apt/sources.list and add a "#" at the beginning of the line to comment it out. Then download and use this:

[http://easyubuntu.freecontrib.org/]("http://easyubuntu.freecontrib.org/")
no. automatix did not add that repository.
folks should find less lame ways to promote their favorite s/w.

---

### Post by SeanHodges on 2006-07-27
> **arnieboy said:**
> no. automatix did not add that repository.
folks should find less lame ways to promote their favorite s/w.
__________________
[B]Automatix: Just works!
Automatix home: [www.getautomatix.com](www.getautomatix.com)[/B] 

The fact remains that EasyUbuntu worked for this scenario. Sorry I don't know anything about Automatix, I'm sure it's great and everything. Personally I dont use either, I've just seen EasyUbuntu do what it promises.

Glad you've got everything sorted sleepjump, good luck!

Cheers,

Sean

---

