---
title: "frustrated"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by ddollas on 2007-02-15
Ok I never managed to get my computer to boot again so I just reinstalled my Ubuntu, however while attemting to get IE for linux to work so I can use a certain webpage I have to use for work, I have managed to A: mess up my sources.list page so I can download anything anymore from terminal, so is there like a page that has what should be in there by default?  (also I have no idea what uncomment) means when they tell me to do that to a line.  and B: when I try to install IE for linux i get told there is a error in cabextract and for the life of me I can't figure out how to get it off and install it again to make it work, normally I'd just follow the steps provided by the wiki and it worked fine, this time, nothing.  I'm so frusterated now, I just don't know what to do with this thing.  

Advice again please? :(

---

### Post by sardion on 2007-02-15
sources.list should look like this:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

(replace feisty with edgy if that's what you run ... feisty is unstable so unless you know what you are doing, stick with edgy (or dapper)).

as to IE ... try removing your ~/.wine folder and starting over.  sometimes wine just goes nuts, remove ~/.wine and maybe even do a 

sudo apt-get --purge remove wine
sudo aptitude install wine

in the terminal to be sure it is a fresh start.  also, make sure you go for IE6 ... i don't think IE7 works too well on linux (but I may be wrong on that).

---

### Post by kittyhawk63 on 2007-02-15
I'm new to Linux. But having been on this forum for the past five days, I can tell you that I would only use Ubuntu. It seems to be first choice for an OS that is stable. Stick with the group and someone will be able to help you. I see you have Ubuntu. That's a good start.

---

### Post by ddollas on 2007-02-15
I'm still getting the following error when I attempt to install them

"An error occured when trying to cabextract some files."

I purged Wine and reinstalled, does cabextract go with it?  or does that need to be purged on it's own?

---

### Post by sardion on 2007-02-15
Oh definitely.  Ubuntu is the best choice.

My sources.list just has the word "feisty" where you want "edgy" because I am using the (highly unfinished and buggy) next version of ubuntu that will be released in april (once we get it working right).  That's what I meant by unstable.

---

### Post by Spike-X on 2007-02-15
> **ddollas said:**
> (also I have no idea what uncomment) means when they tell me to do that to a line.  

It means to remove the "#" or "##" from the beginning of a line.

---

