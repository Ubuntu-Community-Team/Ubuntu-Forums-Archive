---
title: "What happens when you add CDROM to repository?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-10-25
Doing this command will add the cdrom to the repository /etc/apt/sources.lst.
```
apt-cdrom add
```

But since the cdrom isn't included in Feisty repository list by default I must assume that it have been like this 20 years back also.  Which makes me wonder what happens when you add this line to the repository?

I used it on a non Internet connected PC to be able to install some common programs in order to get the wireless working.  But once I'm connected to the Internet should I disable that line in my repository list?

Why isn't CDROM included in the repository by default?  Is it an optimization issue?

---

### Post by mikewhatever on 2007-10-25
That is a strange question. Why is it included or not is like asking why is the default desktop brown. You can enable or disable the CD repository with a few clicks, so what's the deal.
When the CD is added to the list, you are able to install stuff from there, otherwise you aren't, no matter if there is internet connection.

---

### Post by mikeyphi on 2007-10-25
I believe the CDROM option (for installing software) is in Gutsy by default.

A worthwhile option now that aptoncd is available.

---

### Post by jingo811 on 2007-10-25
> **mikewhatever said:**
> That is a strange question. Why is it included or not is like asking why is the default desktop brown. You can enable or disable the CD repository with a few clicks, so what's the deal.
When the CD is added to the list, you are able to install stuff from there, otherwise you aren't, no matter if there is internet connection.

Well for a Linux veteran like yourself to have or not to have cdrom in repository list is off minor importance.  But I'm thinking from the Absolute Beginner perspective.  They don't know what repository is and even dare to edit its file called /etc/apt /sources.lst without destroying their OS.

So for a total newbie say from the 3rd world with no Internet connection that you and me take for granted.  They then get a wireless USB  by donation or something.  They run a Linux distro which isn't Gutsy.  They don't even know the meaning why there's Gutsy, Feisty, Edgy, etc. etc. along with all the other 100 Linux distros out there.

So they try and get their unsupported wireless USB connect to the Internet.  But it requires them to install some kernel headers, iwconfig for example that might not have been included with the installation.
They don't know how to install the extra programs and dependencies from the CDROM.

That's why I ask because it seems like Linux as a whole have been doing everything they can to trip beginners and keep ppl using Windows because of something minor such as this.  And that makes me wonder why wasn't it included in repository by default in ages past.
Something minor like this not being default is stupid unless it's motivated with some optimization issues involved.  That's basically my question :)

---

### Post by mikewhatever on 2007-10-26
Well, people are able to learn. The person you described, from the 'third world' (really don't like the expression) will go and ask around what to do with unsupported hardware. If you think that packages like iwconfig (does not exist, by the way) can solve the lack of a driver, it is very naive. Even more so, if you think that adding the cd-rom to the repositories will get linux more market share.

---

### Post by jingo811 on 2007-10-26
I'm just saying with Windows there's zero headaches to get your wireless operational with Linux as a whole not including Gutsy distro you'll have to go through hell unless they are you.

> **mikewhatever said:**
> Well, people are able to learn. The person you described, from the 'third world' (really don't like the expression) will go and ask around what to do with unsupported hardware. If you think that packages like iwconfig (does not exist, by the way) can solve the lack of a driver, it is very naive. Even more so, if you think that adding the cd-rom to the repositories will get linux more market share.

Well if you're poor your're poor if you're rich you're rich why cloud things up and beat around the bush about it.  If some place is labeled poor you just concentrate all economic and intellectual recources into that area.  If you say a contry is not so poor even if they're then you get status quo.

---

### Post by mikewhatever on 2007-10-26
Wireless operability depends on hardware support. If it is a broadcom you may need to figure things out. It is essential to do some research in advance and pick what works. This approach will strongly encourage vendors to provide linux support. Lastly, it does not matter who you are, and I am no linux veteran of any kind.

Some countries are reacher then others, and the same applies to people. There are reach people in poor countries and vise versa, there are also those in the middle, but I do not think it really matters in linux world.

---

