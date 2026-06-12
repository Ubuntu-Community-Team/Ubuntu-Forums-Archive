---
title: "Dolphin questions"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2007-04-28
I am switching from Gnome to KDE.... Maybe? I have 2 questions.

1) How can I make Dolphin the default file manager?

2) How can I make Dolphin use a "double click" instead of a "single click" to open a folder?

---

### Post by octoberdan on 2007-04-28
> **DSn0wMan said:**
> I am switching from Gnome to KDE.... Maybe? I have 2 questions.

1) How can I make Dolphin the default file manager?

To get it as my default, I simply removed konqueror and then installed dolphin.

```

apt-get remove konqueror
apt-get install dolphin

```

You may be able to just install dolphin without removing konqueror, not sure.

---

### Post by DSn0wMan on 2007-04-28
I don't think I want to remove konqueror, as it is a dependancy for lots of other packages including kubuntu-desktop. 

There must be some setting/settings somewhere that will make Dolphin the default file manager.

---

### Post by octoberdan on 2007-04-29
Have you tried just installing dolphin to see if it became the default?

---

### Post by octoberdan on 2007-04-29
Alright, I asked in an irc channel for you

[20:58] <wolsni> you need to set the default application for viewing directories
[20:58] <wolsni> in the kde file associations
[20:59] <octoberdan> wolsni: How would I go about that?
[20:59] <Jucato> octoberdan: Konqueror -> Settings -> Configure Konqueror -> File Associations -> inode -> directory

Good luck!

---

### Post by DSn0wMan on 2007-04-30
Thanks for the help octoberdan! That worked perfectly.

---

### Post by brennydoogles on 2007-04-30
> **octoberdan said:**
> Alright, I asked in an irc channel for you

[20:58] <wolsni> you need to set the default application for viewing directories
[20:58] <wolsni> in the kde file associations
[20:59] <octoberdan> wolsni: How would I go about that?
[20:59] <Jucato> octoberdan: Konqueror -> Settings -> Configure Konqueror -> File Associations -> inode -> directory

Good luck!

::::OFF TOPIC NOOB QUESTION::::

How would I go about Joining an IRC Channel?? I have never used it, and it seems very foreign.

---

### Post by octoberdan on 2007-05-02
> **brennydoogles said:**
> ::::OFF TOPIC NOOB QUESTION::::

How would I go about Joining an IRC Channel?? I have never used it, and it seems very foreign.

Read [http://www.irchelp.org/irchelp/irctutorial.html](http://www.irchelp.org/irchelp/irctutorial.html) [https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat) and [http://amarok.kde.org/blog/archives/43-The-Rules-of-IRC-Support.html](http://amarok.kde.org/blog/archives/43-The-Rules-of-IRC-Support.html)

---

