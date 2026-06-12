---
title: "~/bin magically added to PATH"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by oniichan on 2008-02-21
Unlike everyone else, I can't get rid of ~bin in my PATH=/home/jim/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games.
I know it's not a problem but it's driving me crazy becuase I can't find where it is coming from?!
It's not in /etc/environment, /etc/profile, /etc/bash.bashrc, ~/profile, or ~/.bashrc. Does anyone know where it is being added so I can get some sleep?
Thanks.

---

### Post by amingv on 2008-02-21
It's not "magic" it works like that. Look for these lines at the bottom of ~/.bashrc:

```
if [ -d ~/bin ] ; then
PATH=~/bin:"${PATH}"
fi

```
In plain english it means "If the directory ~/bin exists, then PATH equals itself plus ~/bin".

If you don't want/need it, just comment those three lines.

Sleep well ^_^.

---

### Post by Tharmas on 2008-03-13
> **amingv said:**
> It's not "magic" it works like that. Look for these lines at the bottom of ~/.bashrc:

Are you sure they are there?
In my (Ubumtu Gutsy) system these line are in ~/.profile

---

### Post by rgeddes on 2008-03-13
I have the following in  ~/.bash_profile

```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

and ~/bin is not added to PATH

```
$0> echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
```

```
test -d ~/bin
$0>
```
returns success

I **would** like to get ~/bin into PATH... any ideas?

Richard

---

### Post by taurus on 2008-03-13
> **rgeddes said:**
> I have the following in  ~/.bash_profile

```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

and ~/bin is not added to PATH

```
$0> echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
```

```
test -d ~/bin
$0>
```
returns success

I **would** like to get ~/bin into PATH... any ideas?

Richard

Just add these two lines to ~/.bashrc.

```
PATH=$PATH:~/bin
export PATH
```
Save it.  Then, either log out and back in or rehash it.

```
source ~/.bashrc
```

---

### Post by rgeddes on 2008-03-13
Before I start rearranging my login startup files, I noticed that when I login to a terminal... not a gnome terminal... ie Alt-F1, and login... I **do** get ~/bin in PATH.  So the PATH info at login is not being passed to the GNOME terminal.

How can I get that login PATH info into the GNOME terminal PATH.

Thanks
R

---

