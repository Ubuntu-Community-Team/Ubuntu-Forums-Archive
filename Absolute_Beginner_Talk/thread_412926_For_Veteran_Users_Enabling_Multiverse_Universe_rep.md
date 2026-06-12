---
title: "For Veteran Users: Enabling Multiverse Universe repositories once?"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-04-18
Hello, again.
Some applications need the Universe and Multiverse repos enabled,and I remember doing them through Synaptic properly. Now my question is, do I have to enable the Uni/Multi repo. each time I need to download a specific app.? 
Or is enabling them the first time good enough?
And what is the best way to enable the Uni/Multi repos? Some tell me I have to enter a bunch of command scripts and such in the Terminal, others say I can do it through Synaptic Package Manager, which is the best way?

Ps. I've got another 2 Question, if you guys have the time: 
1. I've always read the words "Frontend" in many Ubuntu Tutorials not knowing what it means, what is it?

2. GUI, If I am correct, is software (like KDE, and GNOME) that allows user to connect with the computer through cool graphics, right? How would you know what GUI you have?

Thanks Ubuntu Community for always answering :]

---

### Post by BarfBag on 2007-04-18
No, you do not have to re-enable them each time you install a package.  That would be a total PITA.  :)

It really doesn't matter how you enable/disable them.  It does the exact same thing either way.  I'm a terminal person myself, so I prefer to do it this way.

> sudo gedit /etc/apt/sources.list

Uncomment (remove #) the repositories you want to enable or comment (add # to beginning of line) the repos. you want to disable.  Save and close.

> sudo apt-get update

That rebuilds your package database.

But like I said, it really doesn't matter.

A frontend is a graphical interface for a terminal-based program.  For example, Synaptic is a frontend for apt-get.  Apt-get is a terminal based package manager.

You are correct.  GUI stands for graphical user interface.  It's basically a giant frontend for the system.  Ubuntu comes with Gnome by default.  However, you can easily change to KDE or a light-weight window manager.

If you have any more questions, don't hesitate to ask.

---

### Post by Parasitesss on 2007-04-18
Thanks man, helped alot
1. more question though, How would you go about Downloading an application's latest download, let's say Beagle for example,  using the Terminal as opposed to the site itself?

and if I did wanted to use Synaptic instead of the site or the Terminal would synaptic automatically give me the Latest download for any app/software?

---

### Post by BarfBag on 2007-04-18
Let me make sure I'm understanding your question correctly.  Are you asking how to update your packages through the terminal as apposed to Software Update or Synaptic?  Also, if you were to try out working the terminal, they would continue to do their jobs if you switched back?

If you want to update your packages through the terminal, all you do is type the command below.

> sudo apt-get update && sudo apt-get upgrade

This will not interfere with Software Update or Synaptic.  You can switch back at any time.

---

### Post by Parasitesss on 2007-04-18
Umm, sorry, I was unclear, lettme redo this:

1. Okay, I want to download beagle's latest version knowing that this is my first time dowloading of ever having Beagle, but for some reason I couldn't access my internet browser so I decide to use Terminal. Would installing it through Terminal give me the Latest version of Beagle?

2. But Let's say that My Terminal and My Internet browser won't work, and I decide to go to SPM to download Beagle, would SPM give me the Latest download of Beagle?

---

### Post by BarfBag on 2007-04-18
Yes and yes.  Both do the same thing and use the same repositories.

---

### Post by Parasitesss on 2007-04-18
This is my repository list, where are my enabled Multi/Uni repo?
btw repositories are basically links, right?

> 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by BarfBag on 2007-04-18
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

Yes.  Repositories are just links to servers.

---

### Post by Parasitesss on 2007-04-18
Let me just say, thank you soo much for you volunteered help, appreciated!

---

### Post by BarfBag on 2007-04-18
No problem!  I enjoy it.  Welcome to the world of free software.  :)

---

