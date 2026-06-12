---
title: "Multiple Window Managers simultaneously?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Iesos on 2006-07-10
Hi, is there a way to to have several windowmanagers (WM) running at the same time? This is the reason to my question:
I never restart my computer (uptime > 40 days), I don't even restart my WM. I I would like to continue having my WM running, BUT! But I would realy like to test new WM's while I have some grafical applications running in my first WM. I'm sort of looking for something that crates a new tty, so I get like tty1-5 text and tty6-7 grafics (or something like that). 
I there any possibility to do this?

---

### Post by christhemonkey on 2006-07-10
I think it is probably do-able.
After installing your new window manager, then:
```
startx :1 
```

Then type:
```
windowmanager --replace 
```
Obviously replacing windowmanager with the new window manager name.

---

### Post by Iesos on 2006-07-10
Okey, the 
$ startx :1
kind of worked. It started up a tty7 and moved tty7 (where I got my original desktop) to tty8. And tty7 is just a blackscreen with a marker (and you can type text there). But when I ran the command I'v got the following error

```
Fatal server error:
Server already active for display 0.
    If the server is no longer running, remove /tmp/.X0-lock
    and start again
```

which is the same error I get when I try to start the new WM with:
$ startxfce4 --replace
with a slight difference startx :1 also says

```
xauth: creating new autority file /home/johan/serverauth.31145
```

and startxfce4 says

```
/usr/bin/sratxfce4: Srating X server
```

which are messages that comes before the error above. And xfce4 doesn't seem to have started anywhere.

---

### Post by christhemonkey on 2006-07-10
Try something like that.
Cant seem to find the syntax for startxfce4, so might need to be invoked with a :1 option as well.

```
startx -- :1 && killall metacity && sleep 5s && startxfce4 & 
```
or
```
startx -- :1 && killall metacity && sleep 5s && startxfce4 :1 & 
```

---

### Post by Iesos on 2006-07-10
Won't 
killall metacity 
like kill the WM thats allready running? I would appriciate if you could tell when any command would kill the currently running GUI-applications. Right now I have some importat stuff running so I can't test right now. I'll do it soon.
Thanks for the help this far!

---

### Post by christhemonkey on 2006-07-10
You only want to kill the WM on the second Xwindow session.
Not quite sure how you would go about that though!

Im sure someone else has actually managed this before; it isnt really that difficult!

---

### Post by Iesos on 2006-07-10
Okey, I have sort of made progress myself with the help of

[http://gentoo-wiki.com/HOWTO_get_2_users_on_1_pc](http://gentoo-wiki.com/HOWTO_get_2_users_on_1_pc)

There they say one can start a new display with

```
startx -display :1 -- :1 vt7
```

since the display I've allready got is :0 and is located at tty8, then this new one will be named :1 and located at tty7. (See instructions at the page above)
When I run this, X starts at tty7, but only with a grey background and one terminal (wherever that came from) the terminal says:

```
Warning: locale not supported by C library, locale unchanged
```

And after saying that like 20 times it craches with the following outprint

```
xauth:  creating new authority file /home/johan/.serverauth.803

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15-ubuntu1 x86_64
Current Operating System: Linux totoro 2.6.15-25-amd64-k8 #1 SMP PREEMPT Wed Jun 14 11:39:18 UTC 2006 x86_64
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Tue Jul 11 02:13:03 2006
(==) Using config file: "/home/johan/xorg.conf"

The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Could not init font path element unix/:7100, removing from list!
Warning: locale not supported by C library, locale unchanged

waiting for X server to shut down FreeFontPath: FPE "/usr/lib/X11/fonts/misc" refcount is 2, should be 1; fixing.
```

And I don't have a single clue what that means.
Will continue to work on it, If anyone knows, please...

Thanks.

---

### Post by Iesos on 2006-07-10
I ran
```
xinit -display :1 -- :1 vt7
```
instead and ran the wanted WindowManager in the terminal that was created at display :1. 
It's working.

---

### Post by Iesos on 2006-07-10
Well... I have to correct myself again, it doesn't work... as I want it to.
I can no longer start applications on my :0 display. When I try to, it only says

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
```

That comes if I use the "-display :0" flag or not.
If anyone knows, please...

---

### Post by Iesos on 2006-07-11
I've got it. Running
$ sudo xhost +
solves it.

---

### Post by Iesos on 2006-07-12
For people that are interested in a more sumrized version of this thread, I have crated a HowTo: [http://www.ubuntuforums.org/showthread.php?t=213756](http://www.ubuntuforums.org/showthread.php?t=213756)
Please ask there if you got any questions.

---

