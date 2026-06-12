---
title: "not a problem. a question."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-28
what is the difference (if any) between

apt-get
and
aptitude

is it true aptitude installs recccomended packages aswell as crucial ones?

---

### Post by overdrank on 2007-06-28
> **skymera said:**
> what is the difference (if any) between

apt-get
and
aptitude

is it true aptitude installs recccomended packages aswell as crucial ones?

HI, my understanding is that it does search and install all dependences it is just the preference of the user to you apt-get or aptitude. I use apt-get. :D

---

### Post by xelnaga666 on 2007-06-28
For me, one is easier to search through, apt. Aptitude to me seems bloated and difficult.

I personally prefer "apt"

The ability to "apt-cache search X" makes life easier. For example, I might be looking for a podcatcher, and I would type "sudo apt-cache search podcatcher". Very handy!!

---

### Post by mcduck on 2007-06-28
Aptitude has ncurses-based interface, so if you want something between CLI and a GUI try that.

And yes, it's true that aptitude by default installs recommended packages.

Many people recommend aptitude because it can automatically remove packages installed as dependencies, but lately apt-get got that feature too so there's no difference.

I only use apt-get myself. I used aptitude for a while and sometimes it tried to do really stupid things like removing half my system. Apt-get has always worked perfectly so I rather use it..

---

### Post by nick_h on 2007-06-28
Is there any problem using both?  I have been using aptitude.  Would I encounter any problems if I went back to apt-get?

---

### Post by Sweet Mercury on 2007-06-28
> **nick_h said:**
> Is there any problem using both?  I have been using aptitude.  Would I encounter any problems if I went back to apt-get?

[http://ubuntuforums.org/showthread.php?t=485050](http://ubuntuforums.org/showthread.php?t=485050) Here's a thread that has a bit of into on the subject as well.

Also, I think that you might not want to use apt and aptitude interchangeably on the same packages, but I could be mistaken on that.

I don't like aptitude for the same reason another poster mentioned: it's unnecessarily bloated.

---

### Post by nick_h on 2007-06-29
Thanks, that was a useful link.  I have been using synaptic as well as aptitude from the command line so it looks like I have been mixing both already.  I may have to be a little careful when using the autoremove option.

---

### Post by Nythain on 2007-06-29
sweet i had no clue aptitude had an interactive ncurses mode... not that ill ever use it but it still cool

---

