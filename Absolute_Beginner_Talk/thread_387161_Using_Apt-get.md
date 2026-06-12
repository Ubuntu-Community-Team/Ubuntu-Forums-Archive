---
title: "Using Apt-get"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by islander_810 on 2007-03-18
I want to install applications using apt-get. Now how do i know what to type? K, that's pretty vague, lemme give an eg.

Browsing through Synaptic Package Manager let's say, i come across this interesting thingy which i want to install. It's called vim-full. Now how do i know what to type to install it using apt-get?

---

### Post by h0ax on 2007-03-18
sudo apt-get install vim-full

---

### Post by johnc4510 on 2007-03-18
sudo apt-get install vim-full

---

### Post by dreadlord_chris on 2007-03-18
> **islander_810 said:**
> I want to install applications using apt-get. Now how do i know what to type? K, that's pretty vague, lemme give an eg.

Browsing through Synaptic Package Manager let's say, i come across this interesting thingy which i want to install. It's called vim-full. Now how do i know what to type to install it using apt-get?

You realize you'll have to shut Synaptic down before you enter the apt-get command, don't you?

Also, since you're browsing packages already with Synaptic - why not just install with it as well?

---

### Post by passonno on 2007-03-18
A bit of helpful advice is in order.

The previous poster is correct, in that while Synaptic is open,  you cannot install apps or libraries using apt-get. Essentially, you can only use one package managment app at a time, though you can use either one as you see fit.

A good hint when using apt-get is the simplest, yet most effective use of the Linux command line.

Let's say I am attempting to install a plugin for xmms, called xmms-alarm.

So long as xmms-alarm is in the repositories (in your /etc/apt/sources.list file) all I have to do is issue the following command, using the tab key to complete the command, listing the file if it is in the repository:

sudo apt-get install xmms-alarm 

or

to install two different packages simultaneouly:

sudo apt-get install xmms xmms-alarm (thus installing both the xmms app and the alarm plugin)

I hope this helps.

Please feel free to either pm me or reply to this post if you need any further help.

---

### Post by islander_810 on 2007-03-18
Ppl, when i said vim-full i just quoted it as an eg. It might be any other application as well. And i'm aware that i've to close synaptic to run apt-get

But thx for the auto-complete feature. Never thought i could use it that way. That helps. That'll come in handy...

---

