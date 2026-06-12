---
title: "logging into another account graphically with sudo"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Andrew Golightly on 2007-12-31
Hi there.

So the other day after reading some posts, I decided to switch to Epiphany for a whole bunch of reasons. Part of that switch included setting this up for my mum on her account. This included changing a few icons on her desktop, changing the default home for her web browser, setting up some bookmarks, and enabling the adblocker.

Now this is trivially easy if I login into her account graphically as she would. I do know how to login into her account via a terminal, but what I would need to do behind the scenes to make these type of changes is currently beyond me without a fair bit of digging around.

So is there a way to login to another's account graphically if I have administrative privileges?

---

### Post by spiderbatdad on 2007-12-31
looks like there is a tool for this in add/remove called Disk Management.

---

### Post by exile on 2007-12-31
Can you use the "Switch User" feature? That will give you complete GUI access to the other account while not affecting your session?

[http://www.ubuntu.com/getubuntu/releasenotes/710tour#head-0aa6ad76d31d444b76441290615de6ed85feb866]("http://www.ubuntu.com/getubuntu/releasenotes/710tour#head-0aa6ad76d31d444b76441290615de6ed85feb866")

---

### Post by Andrew Golightly on 2007-12-31
> looks like there is a tool for this in add/remove called Disk Management.

I found the tool under add/remove. However it only seems to have the functionality for a few administrative type tools (namely userinfo, usermount and userpasswd). BTW, when looking at programs under add/remove, how can I find out what packages it actually uses? For example, [when searching for it online]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=disk+management&searchon=all&subword=1&version=gutsy&release=all"), I got an error.

> Can you use the "Switch User" feature? That will give you complete GUI access to the other account while not affecting your session?

That sounds like a great idea. I have no way of testing whether it would work though, as I am using Xubuntu and that option doesn't appear to be available. Understandably I suppose, since it would require a fair bit of memory I'm assuming.

---

### Post by spiderbatdad on 2007-12-31
Usermode, as referenced in that package is in synaptic. Unfortunately the packagers do not always include contact or website information. Another thing to consider, when looking into applications, is are they officially supported, with the Ubuntu symbol? More and more I'm wary of third party software.  Google "usermode linux"

---

