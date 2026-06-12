---
title: "What's the default password for root?"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by nguyenvanthoai on 2006-03-02
I've installed Ubuntu, I didn't set a password for root. I need root permission, what's the default one. I tried the blank password, but that's not it :D

---

### Post by ygarl on 2006-03-02
[QUOTE=nguyenvanthoai]I've installed Ubuntu, I didn't set a password for root. I need root permission, what's the default one. I tried the blank password, but that's not it :D[/QUOTE]

Hello!

It's not often I get to help someone here...

The ROOT password is YOUR password you used for your main login...
You can add other users but they won't get ROOT access unless you set them up that way. 

I haven't bothered on mine, and just use the main one.

Thanks

---

### Post by kaamos on 2006-03-02
Root has some randomly generated password, but the account is disabled. Use sudo instead and enter your user password when prompted. For example instead of
```
$ su
# nano /etc/X11/xorg.conf
```
use
```
$ sudo nano /etc/X11/xorg.conf
```

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by AtinLango on 2006-03-02
[QUOTE=nguyenvanthoai]I've installed Ubuntu, I didn't set a password for root. I need root permission, what's the default one. I tried the blank password, but that's not it :D[/QUOTE]

If you need root permission at command line, precede your command with **sudo** e.g. **sudo mkdir dir1**. After pressing enter, you will be prompted for your password. This way, you will have executed commands with root privileges.

---

### Post by cotcot on 2006-03-02
Ubuntu by default does not install a root login with password. By the installation you create your account with password. This gives you the possibility to use "sudo" for administrator tasks. This is done to reduce the risk for messing up your installation by error. 
If you want you can make a root login and password (see : [http://makuchaku.info/amnesty/#setchangeenablerootpassword](http://makuchaku.info/amnesty/#setchangeenablerootpassword) ), however it is not advised.

---

### Post by jamyskis on 2006-03-02
There's absolutely no reason to create a root login and password. If you need root access to do loads of stuff from the command line and can't be bothered to type sudo everytime, just type "sudo bash" in a console. Just remember to close the terminal when you're finished, as you shouldn't use root more than necessary.

---

### Post by qwazert on 2006-03-02
It has happened to me more than once before, where the Foomatic GUI (to setup printers) asks for ROOT password. When I enter my password, it tells me that it is wrong and terminates the process.

---

### Post by jamyskis on 2006-03-02
[QUOTE=qwazert]It has happened to me more than once before, where the Foomatic GUI (to setup printers) asks for ROOT password. When I enter my password, it tells me that it is wrong and terminates the process.[/QUOTE]

Have you tried running it using sudo?

---

### Post by qwazert on 2006-03-02
When I run it as SUDO, it works. But when I launch it from the menu as a regular user, that is what would happen.
In fact, there's a couple of apps that do the same thing.

---

### Post by jamyskis on 2006-03-02
That's perfectly normal. Foomatic (among others) was written with distros in mind that provide a root account which the user could log into and perform admin duties (i.e. at least 95% of all distros). Basically all the program does is check if you have root access, and if you don't, will ask you for the root password and attempt to log in on your behalf, not knowing that you don't have root access.

---

### Post by Jucato on 2006-03-02
[QUOTE=qwazert]When I run it as SUDO, it works. But when I launch it from the menu as a regular user, that is what would happen.
In fact, there's a couple of apps that do the same thing.[/QUOTE]

You could try editing the menu entry for that app and add gksudo (or kdesu if you're in KDE).

---

### Post by nguyenvanthoai on 2006-03-02
I've solved all problem with my software installation. Thank you all guys.

---

### Post by stanz on 2006-03-03
Hi All...
I'm not grasping this well... 
With upgrades- & Automatix, I'm greeted with this new request- that my passwords ain't working. This is a home pc, & i've been doing ok, changing permissions-at will, but- don't know enough to work thru this.
> **qwazert=**When I run it as SUDO, it works. But when I launch it from the menu as a regular user, that is what would happen.
In fact, there's a couple of apps that do the same thing.
I'm still mainly a 'clicker', not knowing `bout running apps from terminal{commands learnt-are few & slow coming}.
-----------
> **Fenyx**=You could try editing the menu entry for that app and add gksudo (or kdesu if you're in KDE). I'm gnome~ and still wondering what/how, to work this? 
"gksudo" ?~ as in: " :~$ gksuso "  and ...thats it? 
*My pw/Root pw..added after?*
Where to edit menu entry?
I Will read /Rootsudo page...but, as hard as i try- i'm a slow learner.
Thanks!

---

### Post by aysiu on 2006-03-03
[QUOTE=stanz]
 I'm gnome~ and still wondering what/how, to work this? 
"gksudo" ?~ as in: " :~$ gksuso "  and ...thats it? [/quote] No, it goes in front of the regular command. For example, to launch Synaptic Package Manager, you need root privileges, so the command would be ```
gksudo synaptic
``` instead of just ```
synaptic
```

> 
*My pw/Root pw..added after?* You'll be prompted for your password in a little pop-up dialogue box.

> 
Where to edit menu entry? Go to Applications > System Tools > Applications Menu Editor

---

### Post by stanz on 2006-03-05
Hi aysiu... Thanks for your response. 
I've done ok with terminal sudo, it is additional programs that are requesting a root pw, and replying my imput is wrong.
It's a " Debian App Manager" i believe. It's placed itself in the 'Applications' menu, and i've noticed a 'doubling' of file icons also.
With this, i'm wondering if i truly want/need it.
I've not used the terminal to run the Synaptic Package Manager, as the panal menu does well.
Since you passed that info- and i want/need to learn more- i used it now. My terminal response is:
[I]:~$ gksudo synaptic
(synaptic:9365): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
(synaptic:9365): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed[/I]
I entered the command- only once.
At the same time, the - Syn Pac Man, loaded up. I didn't run anything- it looked like it usually does...So i closed it out, and the terminal gave the ready [I]' :~$ '.
[/I]Now, i'm more clueless.
I then followed info, to the menu editor.
*Go to Applications > System Tools > Applications Menu Editor*
Only on my second try, did my hd give a hint- it was trying to load something- but, nothing came up, to my desktop.
I'll try to attach png's of those error messeges, and pw requests- maybe they'll help make my many words clearier!

---

### Post by aysiu on 2006-03-06
When you launch graphical applications from the terminal, you sometimes get things that *look* like errors, but it's fine.

I don't know what's going on with those graphical error message pop-ups, though--I've never seen them before.

---

### Post by stanz on 2006-03-07
Well aysiu... some other things are 'happening', and i'm at the point
of reinstalling as the fix.
I'm too new to linux to figure out what i'm screwing up.
Thanks again- for your help...
C`ya later.....

---

### Post by aysiu on 2006-03-07
[QUOTE=stanz]i'm at the point
of reinstalling as the fix.
I'm too new to linux to figure out what i'm screwing up.[/QUOTE] Lord knows I've done that many a time before, especially in the first two months. A separate /home partition comes in handy--that way you can reinstall as many times as you want and keep your files and settings.

---

### Post by stanz on 2006-03-13
Separate...as in- like, another mount point or in filesystem?
I don't really keep important stuff on my pc- music mostly.. so its just
a time thing, about reinstalling...till i learn to fix~ what i brake  ;)
I found out, the double icon stuff- is debian's menu...no big thing there.
I've got by the password error/not working thing, by going in by:
"newly found out, howto add... Root Terminal".
Other things...well, it's a work in progress!!
Thanks for being here & being a help!!
Catch ya later ;)

---

### Post by aysiu on 2006-03-13
Yes, a separate /home partition is a separate partition that's mounted at /home

So when Ubuntu goes looking for the /home "folder," it really sees that separate partition.

It doesn't matter if you keep important files. Having a separate /home partition saves you the trouble of redoing all your settings and preferences for every single program once you reinstall.

Now, I happen to love redoing settings on a clean install (I'm sick that way), but most people don't, so I recommend a separate /home partition.

---

### Post by stanz on 2006-04-07
Hi All....
Just in from another 'Fresh Install'!!!!!
..and getting better at it & with gparted. 
I will think about the seperate, /home - partition...but-
jus' that~ that'll include me messing up permissions & stuff... which i kinda jus' did.   ](*,) 
Mumm- might not work for me...
And no more Debian menu, thingy...'doubling menu entries & password prompts from hell. 
I need to get back to redoing all settings...again~  :???:
[quote=aysiu]Now, I happen to love redoing settings on a clean install (I'm sick that way), but most people don't, so I recommend a separate /home partition.[/quote]

---

