---
title: "Updates in update manager but not apt-get?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by bigjuan on 2007-02-10
I ssh into my box from work while I'm bored (and so I can then telnet out to my favorite mud o:-) ), and while I'm there it's pretty regular that I'll sudo apt-get and find no updates available...yet when I get home, there's a whole fist-full of updates through the update manager to install.

I've even gone so far as to ssh into the box from my XP laptop sitting 3 feet away and doing an apt-get with no updates available, yet I can then turn my chair back to this keyboard and see there's updates in the update manager...all of which download and install without issue.

So, my question is...doesn't the update manager use apt-get to update the system?  Being a Windows geek who's slowly making the change to Linux, I understood apt-get to be THE update program.  Is this not the case?  Or am I missing some switch when I run apt-get update from the console which, in turn, isn't showing me all the available updates?

---

### Post by mozkaynak on 2007-02-10
do you use edgy or dappler drake?
I think the graphical package manager is more comprehensive than apt-get update command.

I would be happy to see more clear answer to this thread because I have the similar issue.

---

### Post by dkartik on 2007-02-10
I'm using Edgy, and I was just checking through the forums to see if there was an answer for this as well.  Starting up the update manager takes a long time, it would be nice if there was a way to do this from the shell.

---

### Post by bigjuan on 2007-02-10
I'm using Edgy as well.  Sorry, shoulda mentioned that.  More of my Windows nerdness peeking out, I guess :p

---

### Post by dkartik on 2007-02-10
I figured it out. Typing:

```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

Should do the trick.

---

