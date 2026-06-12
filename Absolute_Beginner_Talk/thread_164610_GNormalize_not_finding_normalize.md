---
title: "GNormalize not finding normalize"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by jethro10 on 2006-04-23
Hi,
I've managed to install gnormalize and a pre-requisite is the command line normalize it seems.

Now Gnormalize tells me it cant find it which is correct.
The gnormalize web site points to normalize site but this has an apt-get of normalize-audio. Changed it's name it seems. The ubuntu package manager also calls it normalize-audio.

Can anyone help ?
is this one of these symbolic link thingies I need pointing normalize-->normalize-audio ? if so How?

Jeff

---

### Post by jethro10 on 2006-04-23
Well, I sorta solved it myself, if infact it was the right thing to do in the first place!

Ran package manager and found normalize-audio, looked up its properties to find the path to it /usr/bin this seemed to be protected from a normal user so :-
I run nautilus from a command line with sudo nautilus.

I could then create a link by right clicking the file, then renamed the link to nomalize and then gnormalize did not give "...not found...." error.

Wow.
Not sure its the right thing to do but I got closer.

Jeff

---

### Post by jobezone on 2006-04-23
Yep, that's the way to do it!
You could also have done it in the command line, using the "ln" program, like this:

sudo ln -s <original_file> <symbolic link>

If you feel like it, you could report this as a bug to the normalize-audio package in ubuntu at [https://launchpad.net/distros/ubuntu/+source/normalize-audio/+bugs](https://launchpad.net/distros/ubuntu/+source/normalize-audio/+bugs)
You'll have to register with launchpad (you can do it from this link).If you don't feel like doing it, or it's too troublesome, say it, and I can submit it myself.

---

