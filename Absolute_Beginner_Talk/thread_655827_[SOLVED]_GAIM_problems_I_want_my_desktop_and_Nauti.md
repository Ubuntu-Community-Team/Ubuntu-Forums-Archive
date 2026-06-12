---
title: "[SOLVED] GAIM problems: I want my desktop and Nautilus!"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Knoll318 on 2008-01-01
I saw that GAIM was no support for Gchat and Pidgin does, so I wanted to install it.  I went to Package manager and it said I need to remove the Ubuntu Desktop and Nautilus!  Can anyone help me, because I really use Gchat a lot.  Also, the less I have to be in Terminal, the better.  I'll go into it, but if you can find a way with less Terminal, that would be great.  Also, if I have to do anything with source code, I am as lost as a man with a woodcutting axe in the ocean.:confused:

---

### Post by shad0w_walker on 2008-01-01
What are you trying to install from the package manager? Because there shouldn't be any packages that want to remove ubuntu-desktop to be installed. Are  you sure you didn't try uninstalling it?

---

### Post by SOULRiDER on 2008-01-01
Paste the putput of this command
```
sudo aptitude install pidgin
```

What version of Ubuntu are you running?

---

### Post by kevdog on 2008-01-01
I see that you are using Feisty as your Ubuntu version based on your id up in the corner.  GAIM was fully supported in Feisty and pre-releases.  You could install pidgin, however you either needed a precompiled binary from a third part repository or you needed to manually install the dependencies and compile pidgin from source.  Beginning with gutsy and its repositories, you could install pidgin.   Im not sure what you want to do.  

Upgrade to gutsy.
Third party repository
Compile from source code

---

### Post by nitro_n2o on 2008-01-01
kevdog gave u a lot of possibilities.. i vote for compile from source, it is fun :)

---

### Post by kevdog on 2008-01-01
Compiling from source is definitely the best, b/c in addition you can compile and install the purple-plugin-pack (over 50 additional pidgin plugins -- very cool) and otr (off the record) plugin that allows for encrypted IM (similar to gpg for email).  All very cool.  Will need the talkfilter packages also if you want the purple-plugin talkfilter plugin (which is really fun to play with).

---

### Post by SOULRiDER on 2008-01-01
Theres a cool howto on the howto section that talks about how to compile Pidgin from source. You should check it out.

---

### Post by kevdog on 2008-01-01
Or I can help you compile it -- its a little tricky with feisty because the feisty repository doesnt provide the pidgin dependency package.

---

### Post by Knoll318 on 2008-01-02
Kevdog, if you can help me compile from source, whatever that means, that would be great.  Let me put this down into simple terms for anyone who wants to understand my situation:

Anytime I upgrade to Gutys I Kernel Panic, so that's out
I want Pidgin so I can Gchat, but the package says that GAIM needs to be removed
I go to Synaptics Package Manager but it says to remove GAIM I need to remove Nautilus and Ubuntu Desktop
I'm lost now

PS: What does it mean to compile from source code?

---

### Post by llamakc on 2008-01-02
This helps explain it:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

After you compile Pidgin from source (on Feisty) you'll still have GAIM installed at /usr/bin and you'll end up with Pidgin installed at /usr/local/bin. They will coexist just fine. EDIT: The howto at [https://help.ubuntu.com/community/Pidgin?action=show&redirect=InstallPidgin2.0](https://help.ubuntu.com/community/Pidgin?action=show&redirect=InstallPidgin2.0) mentions removing GAIM. 

Perhaps somebody here will come by and clarify.

FORGET ALL THAT ABOVE: HERE: [http://www.debuntu.org/pidgin-2.0.0-deb-ubuntu-feisty-fawn](http://www.debuntu.org/pidgin-2.0.0-deb-ubuntu-feisty-fawn)

---

### Post by kevdog on 2008-01-02
Ok -- no problem

This might take a few rumblings and grumblings b/c I cant remember exactly all the needed dependencies,   this will be the most difficult part about the compilation.

Lets install the basics
sudo aptitude install build-essential linux-headers-`uname -r` 
(Notice these are backticks and not single quotes)

Dependency section (expect this to grow as we figure them out)
sudo aptitude install libtool libnss-dev libgpg-error-dev libgcrypt11-dev libnspr-dev gettext libxml2-dev libgtk2.0-dev
sudo aptitude install libtasn1-3-dev libgnutls13-dev libgtkspell-dev

I will post more dependencies later as we figure them out.  (You can see its a lot)

Go to the pidgin website and download the tar.gz file (source code)
or do the following

cd ~
mkdir devel
cd devel
mkdir pidgin
cd pidgin
wget [http://downloads.sourceforge.net/pidgin/pidgin-2.3.1.tar.bz2](http://downloads.sourceforge.net/pidgin/pidgin-2.3.1.tar.bz2)

Unpack the archive
tar -jxvf pidgin-2.3.1.tar.bz2

Initially lets just run a
./configure

This is going to give you some errors (because I know some dependencies will not be satisfied).  Can you post back where this process quits.  I somehow the configure process makes it all the way through with a miracle, can you cut and post and post the summary (this will be obvious to you)!

---

### Post by Knoll318 on 2008-01-02
Thanks for trying, but Update Manager just popped up with Pidgin, so thanks, but somehow, I already have Pidgin.  I just added some repositories, and Update manager came up.

---

