---
title: "After three months, ubuntu suddenly hanged"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by nandan on 2007-07-29
Hi
Am a Newbie and not very comfortable with CLI. Installed ubuntu on dual boot, with win xp. (ubuntu 7.04 Feisty) around 1.5 months back. It was working well till two days back, when I changed the login page (downloaded from art.gnome.org) When I restarted, it showed me the ubuntu startup screen (black background and orange ubuntu with progress bar), but then the screen went blank and I could only see the 'busy' mouse icon. 
I was able to start in recovery mode ( I could even login using some trial and error and some long forgotten DOS fundamentals), but I am confronted with a CLI and don't know what to do there. I looked through a few of the posts in this forum, but they did not help.

I am writing this in Win XP. Would really appreciate if somebody could diagnose this for me and get me back on ubuntu...Have been championing Ubuntu in my little circle of friends in Mumbai (India), so would be more comfortable if I know it works under most conditions...
Cheers

---

### Post by p_quarles on 2007-07-29
Perhaps you installed a bad startup screen. I've heard that Gnome can be kind of finicky about those things. Try setting up GRUB to boot without the splash screen, and see if that helps. This following post shows the changes that need to be made:
[http://ubuntuforums.org/showpost.php?p=3043507&postcount=3](http://ubuntuforums.org/showpost.php?p=3043507&postcount=3)

You can open the file for editing by typing:
```
sudo nano /boot/grub/menu.lst
```

---

### Post by kostkon on 2007-07-29
It happened to me in the past, with *Ubuntu Hoary 5.04*. I had downloaded a GDM theme from gnome-look but it did not work. Thus, here's what I did:

Go to recovery mode and open the file *gdm.conf* like this:

```
sudo nano /etc/gdm/gdm.conf-custom
```

If you go down down the file you will find some lines like this:
```
[greeter]
GraphicalTheme=Human
GraphicalThemes=happygnome/:circles
GraphicalThemedColor=#0583ff
```

At this line, instead of Human it will say the name of the theme you installed.

```
GraphicalTheme=*name of your theme*
```

Replace the name of your theme with *Human* as it is above, which is a theme that is preinstalled in Ubuntu and should work of course!

After that restart with:

```
sudo shutdown -r now
```

and hopefully after boot you will get the Human themed GDM greeter and everything will be OK.

I hope I helped you somehow!

---

### Post by nandan on 2007-07-30
Let me try this out, would know by tomorrow...thanks a lot for the response!

---

### Post by nandan on 2007-08-01
Hi
I tried what kostkon said. The file opens and shows me the menu, but it shows up as a blank file, i do not see the Graphical Theme = Human anywhere...
Did I miss some step? Thanks

---

### Post by kostkon on 2007-08-01
Which version of Ubuntu do you use? I assumed that you have 7.04. Anyway, the fact that you don't have a */etc/gdm/gdm.conf-custom* file means that your Ubuntu has and older version of *GDM* that does not use this file. Thus, try to do this
```
sudo nano /etc/gdm/gdm.conf
```
go down the file where you will find lines similar to these
```
# These two keys are for the themed greeter (gdmgreeter).  Circles is the
# standard shipped theme.  If you want GDM to select a random theme from a
# list then provide a list that is delimited by /: to the GraphicalThemes
# key and set GraphicalThemeRand to true.  Otherwise use GraphicalTheme
# and specify just one theme.
GraphicalTheme=Human
#GraphicalThemes=circles/:happygnome
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false
```

Again, instead of *Human* the following line will have the name of the theme you installed.
```
GraphicalTheme=name of your theme
```
Replace the name of your theme with *Human* as it is above, and then reboot.

---

### Post by nandan on 2007-08-01
hi
Somehow, I was still unable to see the contents of the file...but I looked at another thread and reinstalled gdm through the command line interface...and it worked!
Thanks a lot for all your help...

---

