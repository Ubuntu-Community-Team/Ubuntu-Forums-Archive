---
title: "firefox goes grey and freezes"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Fanin on 2007-12-16
i am having a problem with Firefox.. it sometimes goes gray and freezes and i have to force quit FF.. this is the first time i have ever been mad at Ubuntu (unlike an other OS i know :)) and i would very much like this to be fixed.. please help :confused:
by the way, it always happens when I'm watching something on youtube

---

### Post by Gambini on 2007-12-16
You're probably running low on RAM. It happens to me all the time when I use Gnome. So if you want, you can try Fluxbox or Xfce which are a little bit lighter desktop managers/window managers. They load up less stuff at start up (fluxbox loads in literally less than a second) which allows you to have more RAM for FF to eat up.

---

### Post by Fanin on 2007-12-16
> **Gambini said:**
> You're probably running low on RAM. It happens to me all the time when I use Gnome. So if you want, you can try Fluxbox or Xfce which are a little bit lighter desktop managers/window managers. They load up less stuff at start up (fluxbox loads in literally less than a second) which allows you to have more RAM for FF to eat up.

I have 2GB of RAM so I'm guessing that this is not the problem :confused:
FF only uses about 70MB

---

### Post by dondad on 2007-12-16
> **Fanin said:**
> I have 2GB of RAM so I'm guessing that this is not the problem :confused:
FF only uses about 70MB
I have the same problem. Haven't been able to figure out what is causing it. I tried running FF from the terminal, but it doesn't show any errors when it dies. I find that it seems to happen most often when I try to stop the video and then do something else. If I either let it finish, or close the tab with it still running, it doesn't seem to happen as often.

BTW, I am running with 2 gig of ram also, and it is not using too much of it.

---

### Post by rickycodie on 2007-12-16
me too, maybe there's a bug on it?

---

### Post by timzak on 2007-12-16
I usually only notice this happen when I visit the Ubuntu Forums...when I first load the forum index.  I don't know why it only happens at this site for me, but almost never do I notice it happen anywhere else.

---

### Post by benny bronx on 2007-12-16
It may be a bug with the flash plugin.  I was having a problem with opera and flash so I uninstalled flash from synaptic and reinstalled from here.

[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb]("http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb")

 Based on the thread here:

[http://ubuntuforums.org/showthread.php?t=635241&highlight=opera+flash]("http://ubuntuforums.org/showthread.php?t=635241&highlight=opera+flash")      See post#4

It also has seemed to fix the FF crash I was experiencing when on youtube.  It has only been a few days, so take this with a grain of salt.

---

### Post by Fanin on 2007-12-17
> **benny bronx said:**
> It may be a bug with the flash plugin.  I was having a problem with opera and flash so I uninstalled flash from synaptic and reinstalled from here.

[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb]("http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb")

 Based on the thread here:

[http://ubuntuforums.org/showthread.php?t=635241&highlight=opera+flash]("http://ubuntuforums.org/showthread.php?t=635241&highlight=opera+flash")      See post#4

It also has seemed to fix the FF crash I was experiencing when on youtube.  It has only been a few days, so take this with a grain of salt.

i tried reinstalling the package but it made no difference :(

---

### Post by Kingsley on 2007-12-17
Do you have Compiz turned on? That might be an underlying cause.

---

### Post by Caffeine_Junky on 2007-12-17
This can be caused by a **compiz** "ping_delay" setting..

See Here:
[http://ubuntuforums.org/showpost.php?p=3880353&postcount=170](http://ubuntuforums.org/showpost.php?p=3880353&postcount=170)


I had the same problem with FF greying-out whilst using **you tube**, and adjusting the "ping_delay" did the trick.

---

### Post by jan quark on 2007-12-19
have the same symptoms no compiz, flash is working fine, but sporadic freezes, any ideas?

---

### Post by Fanin on 2008-01-07
> **Caffeine_Junky said:**
> This can be caused by a **compiz** "ping_delay" setting..

See Here:
[http://ubuntuforums.org/showpost.php?p=3880353&postcount=170](http://ubuntuforums.org/showpost.php?p=3880353&postcount=170)


I had the same problem with FF greying-out whilst using **you tube**, and adjusting the "ping_delay" did the trick.

i tried changing it to 6000, and i haven't had any problems so far.. thanks :)

---

### Post by Fanin on 2008-01-23
[**http://ubuntuforums.org/showpost.php?p=3880353&postcount=170**]("http://ubuntuforums.org/showpost.php?p=3880353&postcount=170")
after changing the ping delay to 6000 i had no problem for a couple of days (maybe just luck) then it started to go gray again, so i changed it to 8000 and it made no difference at all.
any other suggestions?
:confused::confused::confused:

---

### Post by ctswhole on 2008-01-23
I get these issues as well, at first I thought it was just a buggy flash/64-bit thing, but even running 32 bit apps I get the "grey" issues as well.  This includes using the search function in Synaptic as well.  Don't think it's a memory issue, as I have 2 Gigs of it.  Eventually I solved the problem of my laptop locking up by adding the "noirqpoll" option to my grub parameters.
 I don't remember having these issues in Feisty, just in Gutsy.

---

### Post by JohnnyC44 on 2008-01-23
I have it, too.  It's a bug in FF and has been reported -
[https://bugs.launchpad.net/bugs/172419]("https://bugs.launchpad.net/bugs/172419")

---

