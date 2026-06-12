---
title: "[SOLVED] how do I install pidgin without messing up?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-07-22
I've been a windows user for many years and I've only just switched to ubuntu feisty. There are a lot of things I can't figure out, and here's one:
Gaim is already installed, but I can't get it to connect to my gtalk account. How do I install pidgin? (I've read several ways to do this in different places, but I'm looking for the simplest. I'm not so comfortable with the command-line, and I don't want to mess up stuff - many places say that something breaks if you uninstall gaim.)
Please help.
Thanks.

---

### Post by tomcheng76 on 2007-07-22
[http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.0.2/pidgin_2.0.2-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.0.2/pidgin_2.0.2-1_i386.deb)
download to your desktop, then properly with a double click...

if it doesnt work, just a simple command to install it

sudo dpkg -i ~/Desktop/pidgin_2.0.2-1_i386.deb

---

### Post by kleo skywalker on 2007-07-22
> **tomcheng76 said:**
> [http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.0.2/pidgin_2.0.2-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.0.2/pidgin_2.0.2-1_i386.deb)
download to your desktop, then properly with a double click...

if it doesnt work, just a simple command to install it

sudo dpkg -i ~/Desktop/pidgin_2.0.2-1_i386.deb

Can't install. Get the following error msg:
**Error: Conflicts with the installed package "gaim" Conflicts with the installed package "gaim-data"**
What do I do?
Thanks

---

### Post by Jonq on 2007-07-22
uninstall gaim by typing code below into terminal
```
sudo apt-get remove gaim
```

and try again

---

### Post by kleo skywalker on 2007-07-22
> **Jonq said:**
> uninstall gaim by typing code below into terminal
```
sudo apt-get remove gaim
```

and try again

as I said earlier, I read in several places (such as [this)]("http://ubuntuforums.org/showthread.php?t=490191&highlight=pidgin") that removing gaim uninstalls the ubuntu-desktop metapackage.
I don't want to break anything, mainly because I'm not sure I can fix it later.
So what do I do?

---

### Post by nitro_n2o on 2007-07-22
yeah.. true it happened to me i removed everything from the system while playing with Gaim... 
to install pidgin you need some libraries so: 
```
sudo apt-get install libssl-dev libnspr4-dev 
sudo dpkg -i Desktop/pidign.... 

```
I didn't have the conflicting thingy.. 
you can also remove Gaim from synaptic it will prompt you if you are sure and it'll tell you all the things it'll will remove.. so if it's removing so many things dont do it

---

### Post by M!K3_$ on 2007-07-22
here is the tutorial i used
workd great

[http://ubuntuforums.org/showthread.php?t=474071&highlight=pidgin+how+to](http://ubuntuforums.org/showthread.php?t=474071&highlight=pidgin+how+to)

---

### Post by Jamesbowden on 2007-07-22
> **kleo skywalker said:**
> as I said earlier, I read in several places (such as [this)]("http://ubuntuforums.org/showthread.php?t=490191&highlight=pidgin") that removing gaim uninstalls the ubuntu-desktop metapackage.
I don't want to break anything, mainly because I'm not sure I can fix it later.
So what do I do?

this won't break anything, ubuntu-desktop package doesn't actually do anything, its only there to keep track of things (and annoy people like you and me) the only thing this will do that is slightly annoying is remove the nautilus-sendto package (which you mostly likely don't use and will never use)

so just

```
sudo apt-get remove gaim
```

and then install the package that was linked to before

---

### Post by Kimm on 2007-07-22
If you don't want to mess with unstandard packages you can try another Jabber (GTalk) client.

Gajim is realy good, its in the repositories. Psi is also nice, but it is Qt (so it might not blend in well if your using Gnome)

If you deside to go with Pidgin anyway, I recommend these packages :) [http://www.getdeb.net/release.php?id=1045](http://www.getdeb.net/release.php?id=1045)

PS.
You can try uninstalling gaim and gaim-data with aptitude (instead of apt-get), in general it is a bit "smarter". I cant say whether or not it will work though.

sudo aptitude remove gaim gaim-data

---

### Post by Kimm on 2007-07-22
> **Jamesbowden said:**
> this won't break anything, ubuntu-desktop package doesn't actually do anything, its only there to keep track of things (and annoy people like you and me) the only thing this will do that is slightly annoying is remove the nautilus-sendto package (which you mostly likely don't use and will never use)

Actually, removing ubuntu-desktop can mess up dist-upgrades

---

### Post by Jamesbowden on 2007-07-22
> **Kimm said:**
> Actually, removing ubuntu-desktop can mess up dist-upgrades

hasn't been a problem for me at all.

how so? what problems can it cause?

---

### Post by happy-and-lost on 2007-07-22
You can compile it from source. It works fine this way, it just will not be managed by APT, and will not show up in Synaptic. It's easy too...

First
```
sudo apt-get install build-essential gettext libglib2.0-dev libgtk2.0-dev libxml2-dev libssl-dev
```

Then grab the source code from [pidgin.im]("http://pidgin.im/pidgin/download/source/"). Download it to the desktop.

Untar that .tar.gz, open up a terminal and type:

```
cd ~/Desktop/pidgin-2.0.2
./configure
make
sudo make install
```

And there you have it. It'll take a while to compile, but once it's done, it should have created all the menu entries and stuff you want.

But in all honesty, you'd be better off waiting until Gutsy (Or if you fancy a challenge, Alpha testing it now ;)) for a supported package.

(Those dev libs can be safely removed after install if you're running a system tight on space)

[COLOR="Red"]Edit: Does anyone know how to compile in SSL support using this method? MSN will NOT work without it.[/COLOR]

---

### Post by Jamesbowden on 2007-07-22
> **M!K3_$ said:**
> here is the tutorial i used
workd great

[http://ubuntuforums.org/showthread.php?t=474071&highlight=pidgin+how+to](http://ubuntuforums.org/showthread.php?t=474071&highlight=pidgin+how+to)

This guide seems best actually, do this, its idiot proof.

---

### Post by kleo skywalker on 2007-07-22
I tried the idiot proof thing but get the following error message:
[COLOR="Red"]Error: Dependency is not satisfiable: pidgin[/COLOR]
And the compiling from source business is wayyy too complicated for me - I'm  a newbie, remember?
What do I do now?
P.S. - When removing gaim, the package that gets removed and causes trouble - ubuntu-desktop - anyway to fix that after installing pidgin?

---

### Post by pyros on 2007-07-22
> **kleo skywalker said:**
> I tried the idiot proof thing but get the following error message:
[COLOR="Red"]Error: Dependency is not satisfiable: pidgin[/COLOR]
And the compiling from source business is wayyy too complicated for me - I'm  a newbie, remember?
What do I do now?
P.S. - When removing gaim, the package that gets removed and causes trouble - ubuntu-desktop - anyway to fix that after installing pidgin?

You can force ubuntu-desktop to reinstall after you install pidgin.

---

### Post by kleo skywalker on 2007-07-22
Ok I know everyone's trying to help, but the options here are either not working or too complicated.
Can anyone please give me a simple, non-destructive way of installing pidgin? Or do I have to wait for gutsy?
Thanks.

---

### Post by pyros on 2007-07-22
> **kleo skywalker said:**
> Ok I know everyone's trying to help, but the options here are either not working or too complicated.
Can anyone please give me a simple, non-destructive way of installing pidgin? Or do I have to wait for gutsy?
Thanks.

Here's what you do, install pidgin. Let it uninstall ubuntu-desktop. *When* Gutsy Gibbon is released, assuming that you want to upgrade to it, reinstall ubuntu-desktop. Let it uninstall pidgin. Then you can do a dist-upgrade. By that time the pidgin package will have replaced gaim anyway.

---

### Post by kleo skywalker on 2007-07-22
> **pyros said:**
> You can force ubuntu-desktop to reinstall after you install pidgin.

How? And will everything be ok if and after I do this? Plus, what about the dependency error I got earlier?

---

### Post by kleo skywalker on 2007-07-22
I figured out what was missing, and did the idiot proof thing for the latest version of pidgin. Everything worked, now Gaim's gone and pidgin's here, so thanks.
Except - it looks exactly like gaim! And I have a bit of trouble figuring out 2 things:
How do I change the font and font-size of my IMs?
How do I get those little pop-up alerts when people on my buddy list sign in?

---

### Post by kleo skywalker on 2007-07-22
Oh and one more thing:
I followed the steps here but still can't connect to my gtalk account - "read error". What to do?

---

### Post by kleo skywalker on 2007-07-24
Thanks for the advice everyone, I'm putting it together for the next newbie who's just installed Feisty and wants Pidgin.
This is very simple and it worked.
1) Go to **System**-->**Administration**-->**Synaptic Package Manager**. Search for **tcl8.4** and **tk8.4** and install them.
2) The latest version of Pidgin is split in 2 packages. Click [here]("http://www.getdeb.net/download.php?release=1045&fpos=1") for the first one. (I opted to **Open with  GDebi Package Installer**, but I guess you can save to disk and install from there as well.)
3) Click [here]("http://www.getdeb.net/download.php?release=1045&fpos=0") for the second part of the package.
4) To access, **Applications**-->**Internet**-->**Pidgin**.
5) If you want to remove Gaim, click [here]("http://www.mbhoy.com/wp-content/uploads/mfimg/gaim_2.0.1-1%7Efeisty0.1_all.deb").

P.S.: Can't get gtalk to work, but with the gtalk gadget and the option to chat from inside gmail, I suppose that's not a big problem.

---

