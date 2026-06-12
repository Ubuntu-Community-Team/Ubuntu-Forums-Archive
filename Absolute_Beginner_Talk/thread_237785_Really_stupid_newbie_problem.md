---
title: "Really stupid newbie problem"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by druvoid on 2006-08-16
I have recently gone back to Breezy because Dapper was not playing nicely on my computer.  Now then...I have a Home directory where everything is stored.  Under /Home/File System is /home/myusername.  I need to cd to Home to wprk with some tar balls that I downloaded, but for some reason I am not allowed to:

myusername@MyMachine:/$ cd Home
bash: cd: Home: No such file or directory

I have tried every variant of cd (cd .., cd /Home, etc) that I can think of.  I'm sure there is something stupidly obvious that I'm missing here, but I can't figure out what it is.

---

### Post by ComplexNumber on 2006-08-16
isn't it /home (ie with a small 'h')? bear in mind that its case sensitive.

i get the impression there is something is being missed out. for example, is this "Home" directory one that you've manually created in addition to your /home directory?

---

### Post by arkham on 2006-08-16
There are many ways to get to your home directory:

cd
cd ~
cd /home/username
cd $HOME

The first one, i.e. the cd command with no arguments at all, will bring you to your default home directory.  To determine which directory you are in at any time, use this command:

pwd

I'm trying to figure out what other kind of problems you might be having, you didn't change you username between installs did you?

Other common gotchas on this are that Firefox will save files to the Desktop forlder, not your home folder by default (i.e. /home/username/Desktop)

Finally, be wary of case in Linux, unlike windows, it matters - /Home is not the same as /home

Hope it helps,

Adam

---

### Post by druvoid on 2006-08-16
There are both Home and home.  In the directory tree, Home is way above home.

---

### Post by kepos on 2006-08-16
if you mean /home than after you open terminal yust type
[INDENT]cd ..[/INDENT]
if theat 'home' is directory created by you, lokk for small and capital leters. terminal is case-sensitive.

---

### Post by IYY on 2006-08-16
I'm not sure I understand... Have you created a directory /Home yourself? The directory /home is there by default. If it says that you can't CD to that directory, means it doesn't exist.

---

### Post by druvoid on 2006-08-16
I just answered my own question.  Never mind.  As I thought, it was something stupidly obvious.

---

### Post by ComplexNumber on 2006-08-16
> **druvoid said:**
> There are both Home and home.  In the directory tree, Home is way above home.
whats the FULL path of the "Home" directory. for example, it may be /home/<your-username>/Home. have you tried typing in the full path to get to it (typing it EXACTLY as it is)?

EDIT: this post is now irrelevant because its been solved.

---

