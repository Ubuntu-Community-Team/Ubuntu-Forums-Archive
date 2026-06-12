---
title: "Problem with installing"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by lucid on 2005-08-29
This is a bit embarassing, having an issue with simply being able to install a piece of software, but there it is and there you have it. I'm a complete Linux newbie. 

I'm trying to install Tinyfugue. I think I have to type these commands:
: ./configure [options]
: make install

On the first I got:
loading cache ./config.cache
Configuring TinyFugue version 5.0 beta 7

Core dumps disabled.
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH

Any suggestions as to where I'm going wrong? 

Cheers.

---

### Post by essexman on 2005-08-29
[QUOTE=lucid]This is a bit embarassing, having an issue with simply being able to install a piece of software, but there it is and there you have it. I'm a complete Linux newbie. 

I'm trying to install Tinyfugue. I think I have to type these commands:
: ./configure [options]
: make install

On the first I got:
loading cache ./config.cache
Configuring TinyFugue version 5.0 beta 7

Core dumps disabled.
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH

Any suggestions as to where I'm going wrong? 

Cheers.[/QUOTE]

This software doesn't appear to be supported within Ubuntu or Debian, though if your lucky someone might disagree and port it on a repository.

I suggest mailing to [EMAIL=hawkeye@tcp.com]Ken Keys[/EMAIL]  or posting a copy of the readme install instructions to see if someone can figure it out.  At first galnce it looks like a dependancy problem which might be fixed by installing every item in the list of "checking for item .. no".  This can be done by ```
sudo apt-get install item
```

This can also be done via synaptic > System>>Administration>>Synaptic Package Manager  Check the [Ubuntu Guide](http://www.ubuntuguide.org/) to find out about adding repositories and general install instructions  With synaptic you can search and tick all the missing spftware and intsall in one go, but you must do the set-up stuff in the ubuntu guide first.

There is the posibility that there is a Debian package available, but this risks messing up your Ubuntu system if you make a mistake.

Best of luck

---

### Post by KingBahamut on 2005-08-29
Looks like youll need build essential if your going to compile from source. 

try 

sudo apt-get install build-essential 

and then re attempt your source compile.

---

