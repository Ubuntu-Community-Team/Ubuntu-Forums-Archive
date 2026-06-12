---
title: "1 update available"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Tiller on 2007-04-22
Hi, I'm getting the icon telling me i have an upgrade,cool, i go to install it and i get this.E: /var/cache/apt/archives/hotkey-setup_0.1-17ubuntu9_i386.deb: subprocess new pre-removal script returned error exit status 1...i dont have a laptop i jus wanna get rid of this. Any suggestions,thanks.

---

### Post by heimo on 2007-04-22
I'd try:
```
sudo mv /var/lib/dpkg/info/hotkey-setup* /tmp/
sudo aptitude --purge remove hotkey-setup
sudo aptitude update

```

EDIT: Added the 3rd line. Shouldn't give any errors.

---

### Post by bubz_the_troll on 2007-04-22
Could you post more details?  Such as the version of Ubuntu you are using.

---

### Post by Tiller on 2007-04-22
yes,sorry, i just did the upgrade to Fiesty Fawn. took all nite but i did it.lol.I dont have a lap top so i jus wanna get rid of the update,thanks.

ok,it worked Heimo Thanks..one quick note,it told me as a fix,removeing the desktop would do it , i guessed NO as an answer and it provided other alturnatives, i'm think the no was a good guess huh?  lol,thanks again.

---

### Post by heimo on 2007-04-22
> **Tiller said:**
> ok,it worked Heimo Thanks..one quick note,it told me as a fix,removeing the desktop would do it , i guessed NO as an answer and it provided other alturnatives, i'm think the no was a good guess huh?  lol,thanks again.

Definitely! With aptitude it could have done bad things (removed a lot of stuff probably), with apt-get it wouldn't be a problem as removing just ubuntu-desktop (but not its dependencies) is not catastrophic. I tested the commands I gave and didn't see this, but then, I probably don't have ubuntu-desktop package installed. No was a good choice. :)

---

### Post by turbotom on 2007-04-24
I have the same problem and when I try to remove it with aptitude or apt-get it wants to remove ubuntu-desktop. No other solutions are available except for the upgrade that fails.

---

### Post by heimo on 2007-04-24
> **turbotom said:**
> I have the same problem and when I try to remove it with aptitude or apt-get it wants to remove ubuntu-desktop. No other solutions are available except for the upgrade that fails.

Use apt-get and let it remove ubuntu-desktop, if you have to remove some package that is required by ubuntu-desktop. Ubuntu-desktop is a meta package and can be safely removed as long as you don't remove all of its dependencies.

---

### Post by lkz on 2007-04-25
The problem is in the file /etc/init.d/hotkey-setup, you can easily fix this by opening the file

```
sudo gedit /etc/init.d/hotkey-setup
```

Find the following lines

```

	if [ -f $SAVED_STATE ]; then
		setkeycodes $(cat $SAVED_STATE)
	fi

```

and change to

```

	if [ -f $SAVED_STATE ]; then
		setkeycodes $(cat $SAVED_STATE) || true
	fi

```

When you try to upgrade now, you will get the following

```

Configuration file `/etc/init.d/hotkey-setup'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** hotkey-setup (Y/I/N/O/D/Z) [default=N] ?

```

Type 'Y' and then enter.

---

