---
title: "Window-switching in GNOME"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by infidel on 2006-11-13
Hello, all. I've decided to give GNOME an extended tryout. having had my fill of KDE's sluggishness (which boggles my mind, by the way, given my RAM, graphics, and processor). In GNOME, however, I've noticed that the only way I appear to be able to switch among windows with mouseclicks is by clicking on the window's titlebar; clicking on any other visible part of the window fails to bring it into focus.

As I tend to have many windows open at a time, the titlebars aren't always immediately accessible. Rather than having to keep things neatly cascaded, or to hunt through the taskbar for what I want, I'd like to raise a given window by clicking on any visible part of it (as has been the norm in every other DE I've ever used). I haven't been able to find a setting in GNOME along these lines. Am I missing something?

[By the way, "Select windows when the mouse moves over them" isn't an attractive option.]

Any guidance would be greatly appreciated. Many thanks in advance.

---

### Post by IYY on 2006-11-13
> **infidel said:**
> Hello, all. I've decided to give GNOME an extended tryout. having had my fill of KDE's sluggishness (which boggles my mind, by the way, given my RAM, graphics, and processor). In GNOME, however, I've noticed that the only way I appear to be able to switch among windows with mouseclicks is by clicking on the window's titlebar; clicking on any other visible part of the window fails to bring it into focus.

As I tend to have many windows open at a time, the titlebars aren't always immediately accessible. Rather than having to keep things neatly cascaded, or to hunt through the taskbar for what I want, I'd like to raise a given window by clicking on any visible part of it (as has been the norm in every other DE I've ever used). I haven't been able to find a setting in GNOME along these lines. Am I missing something?

[By the way, "Select windows when the mouse moves over them" isn't an attractive option.]

Any guidance would be greatly appreciated. Many thanks in advance.

This is not the default behaviour of Gnome, at least not on any of my machines. It works exactly as you describe. However, if the default has been somehow changed on your machine, go to A**pplications > System tools > Configuration editor** (you may have to add it in the menu editor if it's hidden) and edit **applications > metacity > general > raise_on_click** to be on.

---

### Post by akniss on 2006-11-13
Or let go of the mouse and   ALT + TAB

---

### Post by infidel on 2006-11-13
> **akniss said:**
> Or let go of the mouse and   ALT + TAB

Thanks, akniss, but that doesn't work for me, either. That is, it *doesn't work*, period. Nothing happens on ALT+TAB.

> **IYY said:**
> This is not the default behaviour of Gnome, at least not on any of my machines. It works exactly as you describe. However, if the default has been somehow changed on your machine, go to A**pplications > System tools > Configuration editor** (you may have to add it in the menu editor if it's hidden) and edit **applications > metacity > general > raise_on_click** to be on.

Believe it or not, IYY, but raise_on_click *is* checked. Nevertheless, I'm not getting the desired behavior. Some windows gain focus (ie, the titlebars switch to the 'active' color) but don't raise; most windows do absolutely nothing.

I don't see anything else in the gconftool that I would think might conflict with raise_on_click. There are other enabled items that aren't working, either, such as the run dialog on ALT+F2 (btw, nothing else should be trapping that shortcut). I'm stumped.

---

### Post by IYY on 2006-11-13
Is there anything unusual about your setup? Have you installed Beryl, Xgl, or switched the window manager to something other than Metacity?

---

### Post by localuser on 2006-11-13
> **infidel said:**
> I don't see anything else in the gconftool that I would think might conflict with raise_on_click.

Have you tried 

System | Preferences | Windows | Select Windows when the mouse moves over them

---

### Post by infidel on 2006-11-13
> **IYY said:**
> Is there anything unusual about your setup? Have you installed Beryl, Xgl, or switched the window manager to something other than Metacity?

As a matter of fact, I've spent the last couple of days working through the recent crop of Xgl/Beryl HOWTOs for Edgy without success (despite having been able to use Xgl/Compiz on Dapper; this *before* I learned how to enable hardware acceleration...). The thing is, I was fairly certain that I had removed all traces of Beryl, including configs. I'm back to plain old X.org as shipped with Edgy, and running GNOME with Metacity. Nothing Beryl-related in my startup programs, and relevant config files either deleted, or restored from pre-experimentation backups.

The only "unusual" thing about my setup is that it's a sort of K/X/Ubuntu hybrid, though any given DE (KDE, GNOME, XFce) runs as packaged with its respective default window manager. My upgrade from Dapper was also clumsy but generally successful (I think).

> **localuser said:**
> Have you tried 

System | Preferences | Windows | Select Windows when the mouse moves over them

Thanks, localuser, but that's not the effect I'm looking for. Raise-on-mouseover is a sure way to drive myself bughouse.

---

### Post by IYY on 2006-11-14
Just to make sure you're running good old Metacity,  

```
ps aux | grep metacity
```

and

```
cat /usr/share/gnome/default.wm
```

---

### Post by infidel on 2006-11-14
> **IYY said:**
> Just to make sure you're running good old Metacity,  

```
ps aux | grep metacity
```

and

```
cat /usr/share/gnome/default.wm
```

```
marv@kane:~$ ps aux | grep metacity
marv     17935  1.0  3.3  24740 12440 ?        Ss   00:20   0:00 /usr/bin/metacity --sm-client-id=default0
marv     18182  0.0  0.2   2800   752 pts/0    R+   00:20   0:00 grep metacity
marv@kane:~$ cat /usr/share/gnome/default.wm
[Default]
WM=metacity
marv@kane:~$ 

```

---

### Post by akniss on 2006-11-14
What happens if you hit ALT + ESC ?

---

### Post by jhaitas on 2006-11-17
i am experiencing the exact same thing... is there a way to fix it?
```
jhaitas@curious-george:~$ ps aux | grep metacity
jhaitas  14549  0.1  0.2  14572  8588 ?        S    15:43   0:05 metacity --replace
jhaitas  12952  0.0  0.0   2856   748 pts/5    R+   16:34   0:00 grep metacity
jhaitas@curious-george:~$ cat /usr/share/gnome/default.wm
[Default]
WM=metacity
jhaitas@curious-george:~$ 

```

also "Select windows when the mouse moves over them" is a load of **** - who wants that

---

### Post by infidel on 2006-11-23
> **akniss said:**
> What happens if you hit ALT + ESC ?

Absolutely nothing that I can discern.

(By the way, my apologies to everyone who has participated in the thread -- I've been away from home [and thus the machine in question] for several days.)

---

### Post by infidel on 2006-12-28
> **akniss said:**
> What happens if you hit ALT + ESC ?

Not a blessed thing.

(BTW, sorry for the long delay in responsing...)

Another thing I've noticed since my last post on the subject: This may or may not have anything to do with anything, but I've found that when GNOME is running in an Xnest, clicking on any part of a window raises it (which is my target behavior here). Running on its own, GNOME steadfastly refuses to pull window focus unless the titlebar is clicked, regardless of what the configuration says should happen.

Am I right in I'm guessing that the "host" window manager's default behavior is being passed through the Xnest? (I obviously don't know much about window management, let alone Xnest). If so, I'd love to know how it does it. _I_ can't seem to get the behavior I want out of GNOME, but it appears as though different desktop environments can. :???: 

Thanks.

---

### Post by Jussi01 on 2006-12-28
Out of curiosity, have you tried reinstalling the gnome DE? I had a problem and did this and it fixed everything.

---

### Post by infidel on 2006-12-29
> **Jussi01 said:**
> ...have you tried reinstalling the gnome DE? I had a problem and did this and it fixed everything.

I considered it, but I'm not sure where to begin -- there's *so much* GNOME-related stuff on here. Might I also run the risk of having to reinstall everything depending on GNOME?

---

### Post by Jussi01 on 2006-12-30
I dont think this will delete all your prgrams, just reinstall the de... hmmm well you could try:

```
sudo apt-get install gnome --reinstall
```

BUT - Im not sure about the programs... Perhaps someone with a little more experience can help...

---

### Post by infidel on 2007-01-07
Well, I actually just went ahead and replaced Metacity outright, with XFwm4 (XFce's window manager). It's much more responsive than Metacity ever was, even when it behaved as advertised.

Thanks for your help, everyone.

---

