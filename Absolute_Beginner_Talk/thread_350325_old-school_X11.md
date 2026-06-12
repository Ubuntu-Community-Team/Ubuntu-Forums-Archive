---
title: "old-school X11?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by yakshavers on 2007-01-31
I'm new to ubuntu (just installed 6.10) but I've been using Unix     
for close to 20 years.  And while the desktop ubunto logs me into
by default is nicely understated as such things go, I'd really
prefer to use plain vanilla X and my old-school window manager
(ctwm).  Is there a way for me to do this without getting elbows-
deep in ubuntu's guts?  (In the best of all possible worlds,
someone would reply saying all I need to do is run apt-get install
{foo, bar, baz}, copy my dotfiles from an old X head, reboot, and  
I'm all set.  I don't generally find this to be the best of all
possible worlds, but I'd appreciate knowning how far I am from 
it.)

Thanks in advance,
---Alex

---

### Post by Brunellus on 2007-01-31
> **yakshavers said:**
> I'm new to ubuntu (just installed 6.10) but I've been using Unix     
for close to 20 years.  And while the desktop ubunto logs me into
by default is nicely understated as such things go, I'd really
prefer to use plain vanilla X and my old-school window manager
(ctwm).  Is there a way for me to do this without getting elbows-
deep in ubuntu's guts?  (In the best of all possible worlds,
someone would reply saying all I need to do is run apt-get install
{foo, bar, baz}, copy my dotfiles from an old X head, reboot, and  
I'm all set.  I don't generally find this to be the best of all
possible worlds, but I'd appreciate knowning how far I am from 
it.)

Thanks in advance,
---Alex
download the alternate CD, choose a minimal or server install, and add the packages you need.

in your case, it'd be xorg and foowm.

---

### Post by IYY on 2007-01-31
> In the best of all possible worlds,
someone would reply saying all I need to do is run apt-get install
{foo, bar, baz}, copy my dotfiles from an old X head, reboot, and
I'm all set.

```
sudo apt-get install ctwm 
```

should do it, I think. But of course, then you will still have Gnome installed and GDM will be used as the login manager, you can just choose to log into CTWM instead of Gnome. The other option, as the poster above said, is to install from the server CD and add only the components you want via apt-get.

---

### Post by tcrroadie on 2007-01-31
> **yakshavers said:**
> I'm new to ubuntu (just installed 6.10) but I've been using Unix     
for close to 20 years.  And while the desktop ubunto logs me into
by default is nicely understated as such things go, I'd really
prefer to use plain vanilla X and my old-school window manager
(ctwm).  Is there a way for me to do this without getting elbows-
deep in ubuntu's guts?  (In the best of all possible worlds,
someone would reply saying all I need to do is run apt-get install
{foo, bar, baz}, copy my dotfiles from an old X head, reboot, and  
I'm all set.  I don't generally find this to be the best of all
possible worlds, but I'd appreciate knowning how far I am from 
it.)

Thanks in advance,
---Alex

If you really want the old school feeling with the ease of apt-get it is very easy.  Here are the steps.  Modify to your taste.

Use Alternate Install CD.

1.  At boot options, choose "Install command line system"

2.  After you have installed the base system install the X server (xorg).

```
sudo apt-get install x-window-system-core
```

3.  Install your prefered window manager, in your case ctwm.  

```
sudo apt-get install ctwm
```

4.  Now just install any applications that you prefer.  For example. 

```
sudo apt-get install gnome-terminal firefox thunar xmms gtk-theme-switch gnome-themes gnome-themes-extras
```

5.  Now you need to create a xinitrc file so you can start ctwm with startx.

In your home directory create a file called .xinitrc

```
nano .xinitrc
```

Place this in your new .xinitrc file. 

```

#! /bin/sh
    exec /usr/bin/ctwm
```

The executable for ctwm may be in a different location, but you get my point. 

6.  Now make .xinitrc executable.

```
chmod +x .xinitrc

```

Now to launch ctwm you just need to log-in and type **startx**.

Hope this helps. :D

---

