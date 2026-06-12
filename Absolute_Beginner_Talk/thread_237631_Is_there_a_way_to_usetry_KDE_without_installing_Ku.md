---
title: "Is there a way to use/try KDE without installing Kubuntu?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-08-16
I'm running regular ol' Ubuntu right now, but I'd like to try KDE since a lot of people are telling me that they prefer it to Gnome.

---

### Post by benuski on 2006-08-16
Sure.  If you go to Synaptic, you can search for and download KDE.  Then, you need to log out, and then when its time to log back in, click on the options   button in the lower left corner, then on sessions(I believe), and then just click on KDE.  When you log in, it will ask you if you want to make KDE your default or use it for just that session.

---

### Post by GuitarHero on 2006-08-16
You can do sudo aptitude install kde I think.  Then just do sudo aptitude remove kde to get rid of it.

Oh and you could also just try the kubuntu live cd.

---

### Post by Amablue on 2006-08-16
> **benuski said:**
> Sure.  If you go to Synaptic, you can search for and download KDE.  Then, you need to log out, and then when its time to log back in, click on the options   button in the lower left corner, then on sessions(I believe), and then just click on KDE.  When you log in, it will ask you if you want to make KDE your default or use it for just that session.

I did a quick search a minute ago for KDE and there were a ton of packages. Which one(s) would be the one(s) I need?

---

### Post by xpod on 2006-08-16
Ive seen a few people complaining about problems with the two of them...... kde/gnome together.
The only thing ive noticed that seems to be different is that i can change all the 4 default workspaces to different backgrounds in Kubunto where as i can only have the same one through all workspaces in Ubunto.Obviously theres many more but overall it`s the same thing aint it?

Ive got them on both on separate pc`s though as i would`nt risk them messing eachother up on the same one

---

### Post by Amablue on 2006-08-16
I just want to experiment around with stuff. I can always uninstall it if it gives me problems. 

I found the package I need in the wiki, but now I have another question. There's three to choose from, Kubuntu-desktop, kde and kde-core. Kubuntu desktop looks like it comes with openoffice stuff. Are those KDE versions of the program or are they the same thing? Should I go with the kde package or the Kubuntu package?

---

### Post by aysiu on 2006-08-16
If you install it following these instructions, it can be easily removed with one command: [http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)
To remove it, you'd do ```
sudo aptitude remove kubuntu-desktop
```

If you want just the basic KDE without all the Kubuntu frills, do ```
sudo aptitude update
sudo aptitude install kde-core
``` To remove it, you'd do ```
sudo aptitude remove kde-core
```

If you want to try it without installing it, get the **Desktop CD** of Kubuntu--it's a live CD that won't affect your installation.

---

### Post by benuski on 2006-08-16
The most basic package that will give you everything to run KDE is called "kdebase" in the repos.  Its a metapackage that will download everything that you need.

---

### Post by aysiu on 2006-08-16
> **Amablue said:**
> I just want to experiment around with stuff. I can always uninstall it if it gives me problems. 

I found the package I need in the wiki, but now I have another question. There's three to choose from, Kubuntu-desktop, kde and kde-core. Kubuntu desktop looks like it comes with openoffice stuff. Are those KDE versions of the program or are they the same thing? Should I go with the kde package or the Kubuntu package?
**kdebase** - the absolute minimal to get a working KDE desktop environment... emphasis on the word *minimal*!

**kde-core** - the basic but more functional KDE desktop environment.

**kubuntu-desktop** - Kubuntu's default KDE packages.

**kde** - all of the KDE bells and whistles (installs more stuff than Kubuntu).

---

### Post by jelly on 2006-08-17
Hi, I've just installed KDE and XFCE on my Ubuntu Dapper install.  But, sadly, I installed it through Synaptic.  So, I've realised that I don't really like KDE at all and would like to remove it.  Any ideas on how I would go about that?  I read somewhere here about the orphan program, which I have installed, but I'm not sure what to remove with that?  Should I just select kubuntu-desktop?  There seems to be a lot of things in the orphans list that I actually want.

So, in conclusion.. use the aptitude install / remove method - do NOT use Synaptic / apt get.  If anyone has any advice on what I need to do to completely remove KDE I'd be much appreciated.

You live and learn!  :)

Thanks,

- Jelly.

---

### Post by aysiu on 2006-08-17
Try this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Be forewarned: if you have server stuff running (like Apache and MySQL), those may get removed too!

---

### Post by Amablue on 2006-08-18
After playing around with it I decided I'm happy with Gnome. I went to uninstall it and it came up with a prompt saying there was something running that needed to be stopped and I could either kill it and let it continue of just have it clear it out next time I restarted (at least, I think that's what happened.). I chose to end the process, which caused it to restart for some reason. Kubuntu still seems to be there (however, the login screen changed, and when I tried to start up Kubuntu out of curiosity, it had me go through some new setup wizard I hadn't seen before). I tried to start the process over and it game me this error

```
sudo aptitude remove kubuntu-desktop
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```


And so I tried what it suggested ang got this:

```
dpkg --configure -a
dpkg: requested operation requires superuser privilege
```

---

### Post by aysiu on 2006-08-18
Have you tried this? ```
sudo dpkg --configure -a
```

---

### Post by Amablue on 2006-08-18
I can't beleive I didn't realize that. ](*,) 

Anyway, everything seems to be good now except one thing. The boot up screen is still a Kubuntu screen. A minor detail, I know, but I'd like to have it back to normal.

---

### Post by darkenedday on 2006-08-18
sudo apt-get install kubuntu-desktop then simply log out, change your session to KDE and log back in

---

