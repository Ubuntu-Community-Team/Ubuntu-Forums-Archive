---
title: "Installing Programs"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by allroz on 2005-08-16
Obviously, im new to this completely. Im sorry if this has been answered, but i've been looking for a couple days now. I just can't find it. I've searched on here and read through the sites but i just don't understand how i install files onto here. Can someone help me out? Im trying to install limewire but i just don't understand how the hell i do it, as well as the java plug in. Could someone please help me out? I have aim if you could help me on that. Its NSaticity . Thanks.

---

### Post by Strangerdave on 2005-08-16
Sure thing friend, just check out [this](http://ubuntuguide.org/#jre) and [http://ubuntuguide.org/#limewire]this[/URL].  The rest of the guide is quite handy too :) 

So what you want to do is to Click Applications -> System Tools -> the Terminal and sopy and paste the text.  You could also use Synaptic manager.

That is click System -> Administration -> Synaptic Package Manager and do a search for the program you want, but I don't think that Limewire is there.

Before doing any of this though, I would add the repositories to your list, by clicking [here](http://ubuntuguide.org/#extrarepositories) and reading through it all.

That should get you going, any more questions make sure you search first, because most likely the question has been asked and answered.
 
-SD-

---

### Post by wellery on 2005-08-16
The ubuntu guide will help you install things. This is how you install limewire:

[http://www.ubuntuguide.org/#limewire](http://www.ubuntuguide.org/#limewire)

Generally apt-get is used to install software which is stored in a software repository stored on the internet. to install a program from the repository just type 

apt-get install <program>  on the console or you can use Synaptic which is a graphic  tool for apt-get.

The standard repository doesn't have have a lot of software but most of it will be available if you add the universe repository and others by doing this:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by aysiu on 2005-08-16
If you want to know how to install programs in general, take a look at this:

[http://www.psychocats.net/essays/winuxinstall.php](http://www.psychocats.net/essays/winuxinstall.php)

Same method can be used for Limewire--you just need to enable extra repositories first (see responses above).

---

### Post by allroz on 2005-08-16
Thanks for the help guys. Im going to take a look at that stuff right now.

---

### Post by allroz on 2005-08-16
I keep seeing the word repositories, what exactly does that mean? What is the advantage?

---

### Post by aysiu on 2005-08-16
[QUOTE=allroz]I keep seeing the word repositories, what exactly does that mean? What is the advantage?[/QUOTE] It means you don't have to go searching around the internet for stuff to download and figure out how to install. Synaptic has a few sources (repositories) of stored software that it draws from. You pick what you want to install, and Synaptic will pull that program from the repositories and install it (and all its dependencies).

So, when we say "enable extra repositories," we're really saying "add more places where software is stored."

---

### Post by allroz on 2005-08-16
I really appreciate the help.

---

