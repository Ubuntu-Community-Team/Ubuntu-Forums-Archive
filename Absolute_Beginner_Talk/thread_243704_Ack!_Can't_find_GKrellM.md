---
title: "Ack! Can't find GKrellM"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by xlobsterx on 2006-08-25
I've been trying to install gkrellm, but have been unsuccessful thus far.
I've tried:

apt-get update
apt-get install gkrellm

(said it couldnt find the package)

I've searched through the synaptic package manager thing and found nothing, and I've also tried installing it from source but that keeps poppin up errors when I try the make command.

Now from what I read I should be able to find it in synaptic, right? Does anyone have any ideas?

Thanks much in advance.

---

### Post by Crosbie on 2006-08-25
It's in there for me.  You may need to enable new repositories - Universe, I think.  Try a quick forum search for help on this. :)

In Synaptic, Settings > Repositories will tell you what repositories you're using.

---

### Post by Jerome36 on 2006-08-25
Perhaps it's not showing up because you don't have the right repository, which has gkrellm, enabled.

---

### Post by Woei on 2006-08-25
GKrellm is available in a prepackaged form Ubuntu, but not in any of the repositories enabled by default on a standard install. It's also quite normal you're not able to compile the package from source, as you're probably missing compilers and development libraries that are necessary to build, but not run, GKrellm.

To install GKrellm through Synaptic, you'll have to enable the "Universe" repository, run apt-get update, and then apt-get install gkrellm. There are various ways to enable the 'Universe' repository, but probably the easiest way is opening up a console, typing 'sudo gedit /etc/apt/sources.list' and adding a line like 'deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper universe multiverse' at the bottom of that file.

---

### Post by bulldog on 2006-08-25
I think it has something to do with your repositories.
You have to enable the multiverse and universe repositories in your synaptic.

Then you do 

sudo aptitude update
sudo aptitude install gkrellm

This should do the trick I guess.

---

### Post by Jerome36 on 2006-08-25
There should also be an option in synaptic package manager, to add a new repository.  I'm not on my Linux Machine at the moment, to give specific instructions, but I think there's an option to do so.

---

### Post by xlobsterx on 2006-08-25
Awesome. Here I've been banging my head against a wall for an hour and all I needed to do was ask for a lil help. Thanks much, works like a charm. ^_^

edit: 
Forgot to mention what the problem turned out to be; I did indeed need to enable some things in /etc/apt/sources.list

---

