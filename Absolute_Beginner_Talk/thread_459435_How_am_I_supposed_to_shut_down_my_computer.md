---
title: "How am I supposed to shut down my computer?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-05-30
I have no option to shut down or restar my computer on my Ubuntu 6.06 partition. 

I click the red button on the top right, and the window comes up, but "shut down" and "restart" are completely gone, and there's just a long "hibernate" button along the bottom.

A confused person is me.

I don't know if this is a bug, or just something I'm doing wrong, but it's happened before and I restarted (from the button) and it went away, but now it appears to be here for good.

so...what could I possibly do about this odd little pickle I'm in?

---

### Post by Hobo Joe on 2007-05-30
Did you log on to the Xserver from recovery mode?

---

### Post by aeiah on 2007-05-30
a quick fix for a proper shutdown is to type 'shutdown' in the terminal, followed by the number of minutes you'd like before the pc shuts down. or 'shutdown now' for an instant shut down. the 'reboot' command follows the same principles.


as for an actual fix for your problem, i have no idea. its very strange. have you searched the forum?

---

### Post by Neon_Knight on 2007-05-30
I did log onto the X server from recovery mode, but that was several restarts ago (I could only turn it off manually from the button) and it's still there...

I've not searched the forum as of yet, I will proceed to do that now.

---

### Post by Ek0nomik on 2007-05-30
Are you using Beryl?

---

### Post by Hobo Joe on 2007-05-30
> **Neon_Knight said:**
> I did log onto the X server from recovery mode, but that was several restarts ago (I could only turn it off manually from the button) and it's still there...

I've not searched the forum as of yet, I will proceed to do that now.

Well, that could be the problem,  although, since you did restart since then I wouldn't think that would happen. Try:
```

sudo shutdown -r now

```

---

### Post by Ek0nomik on 2007-05-30
> **Hobo Joe said:**
> Well, that could be the problem,  although, since you did restart since then I wouldn't think that would happen. Try:
```

sudo shutdown -r now

```

That command will definitely work.  He wants his icons to show up though, that's the problem.

---

### Post by Neon_Knight on 2007-05-30
Yeah, I want the icons. D:

Okay, I did a search, and I think I know what the problem is. I recently changed to KDE, and back to gnome again, but it's still set to KDM as default, as opposed to GDM. (I think?)Which is why I still get the Kubuntu login screen.

Does anybody know how I can change the default back to GDM?

---

### Post by Hobo Joe on 2007-05-30
Who knows, considering he didn't do a proper shutdown before, this MAY fix it, but no promises.

---

### Post by Hobo Joe on 2007-05-30
> **Neon_Knight said:**
> Yeah, I want the icons. D:

Okay, I did a search, and I think I know what the problem is. I recently changed to KDE, and back to gnome again, but it's still set to KDM as default, as opposed to GDM. (I think?)Which is why I still get the Kubuntu login screen.

Does anybody know how I can change the default back to GDM?

OH,  you should have said that before.

I'm not sure all the packages, but check in synaptic for anything that has KDE or Kubuntu in it.

---

### Post by Neon_Knight on 2007-05-30
Okay, I'm looking in synaptic...

Would uninstalling KDM be wise?

---

### Post by Hobo Joe on 2007-05-30
Well, maybe, check and see if GDM is installed.

---

### Post by Neon_Knight on 2007-05-30
GDM is installed. I'll go ahead with it.

---

### Post by Hobo Joe on 2007-05-30
Cross your fingers and get ready to do some crazy crap! Becuase this might not work, just to warn you. I hope it does though.

---

### Post by ryanVickers on 2007-05-30
right now I'm having some problems that can be found [here]("http://ubuntuforums.org/showthread.php?t=457493"), but to shutdown, I do a logoff and then "sudo halt".
As for getting the buttons, I've noticed they tend to come and go as they please o_0 but like people have said, it's likily that it's something to do with the logon managers.  I would make sure you are using GDM - this might help.  Also, if you've started X in some odd way, they will not show up because you don't have "privilages" to shut down (using that screen at least).

---

### Post by Neon_Knight on 2007-05-30
> **Hobo Joe said:**
> Cross your fingers and get ready to do some crazy crap! Becuase this might not work, just to warn you. I hope it does though.

It didn't.

---

### Post by Neon_Knight on 2007-05-30
> **ryanVickers said:**
>   I would make sure you are using GDM 

Umm, I uninstalled KDM, does that mean  I'm automatically using GDM?

Edit:

Okay, it appears that gnome isn't installed...

O.o

installing now.

I was under the impression that I was USING gnome...O.o

Argh, this is why I am in the "Absolute Beginner's Forum". I have no idea what I am doing.

---

### Post by Ek0nomik on 2007-05-30
Are you using Beryl?

---

### Post by _simon_ on 2007-05-30
Can't see any mention that you've checked this so...

System -> Administration -> Login Window -> Local

Make sure that "Show Actions menu" is selected.

---

### Post by Neon_Knight on 2007-05-30
> **Ek0nomik said:**
> Are you using Beryl?

no...I don't think so...not that I know of...

---

### Post by Neon_Knight on 2007-05-30
> **_simon_ said:**
> Can't see any mention that you've checked this so...

System -> Administration -> Login Window -> Local

Make sure that "Show Actions menu" is selected.

It won't open.

I noticed that option in the menu before, but I click on it, it asks for my password, and then it has "starting administrator thing" at the bottom, but then it goes away and nothing happens.

---

### Post by _simon_ on 2007-05-30
> **Neon_Knight said:**
> It won't open.

I noticed that option in the menu before, but I click on it, it asks for my password, and then it has "starting administrator thing" at the bottom, but then it goes away and nothing happens.

Can you try it from terminal?

```

gksu /usr/sbin/gdmsetup

```

---

### Post by Neon_Knight on 2007-05-30
```

david@david-desktop:~$ gksu /usr/sbin/gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.

```

hmmmmmmmmmmm

---

### Post by _simon_ on 2007-05-30
Can't find a fix for that!

---

### Post by Neon_Knight on 2007-05-30
Oh dear...

Does anybody have a suggestion as to what I should be doing?

---

### Post by Ek0nomik on 2007-05-30
To get rid of that error, I think

```
sudo dpkg-reconfigure xserver-xorg
```

will do the trick.

However, any settings you have done to your xorg file will probably be lost.  Just a heads up.

---

### Post by daimaru on 2007-05-30
omg bad bad bad i installed kde-desktop on ubuntu once and it srewed everything up. had to reinstall ubuntu from sratch to get a working system again ... 
dont recommed installing kde from gnome  just stick with the original

---

### Post by Neon_Knight on 2007-05-30
> **Ek0nomik said:**
> To get rid of that error, I think

```
sudo dpkg-reconfigure xserver-xorg
```

will do the trick.

However, any settings you have done to your xorg file will probably be lost.  Just a heads up.

Oh god...

here we go reinstalling the ATI drivers.

Although, I have backup xorg files. Surely I could just reset one of those?

---

### Post by Ocxic on 2007-05-30
try just pushin you power button, most, if not all newer computers (including mine) will recognize the push of said button, and shutdown normally. give that a shot.

---

### Post by Neon_Knight on 2007-05-30
> **Ocxic said:**
> try just pushin you power button, most, if not all newer computers (including mine) will recognize the push of said button, and shutdown normally. give that a shot.

The problem isn't turning the computer off, the problem is that my icons are gone and I want them back,

I don't care if I can do it in command line mode or whatever, it's nicer and more pleasant to have a fully operational Ubuntu partition.

---

### Post by Neon_Knight on 2007-05-30
> **Ek0nomik said:**
> To get rid of that error, I think

```
sudo dpkg-reconfigure xserver-xorg
```

will do the trick.

However, any settings you have done to your xorg file will probably be lost.  Just a heads up.

Done that, but the error is still there.

Is there a specific repository that I need to remove/install to get the gnome login window and splash screen instead of the kubuntu ones? Because I think that's what's causing the problem,

---

### Post by ncappel1 on 2007-05-30
Try to see in synaptic if you have any broken packages related to the desktop. Did anything go wrong during installation?

---

### Post by Ek0nomik on 2007-05-30
> **Neon_Knight said:**
> Done that, but the error is still there.

Is there a specific repository that I need to remove/install to get the gnome login window and splash screen instead of the kubuntu ones? Because I think that's what's causing the problem,

If you want to remove KDE (I installed KDE on my desktop once.  I was running Gnome and wanted to try it out, but decided to get rid of it as well) open a terminal and type:

```
sudo aptitude remove kubuntu-desktop
```

---

### Post by _simon_ on 2007-05-31
Probably not what you want to hear but it may save you a lot of head scratching if you did a clean install, when I first started out I often chose the easy option of reinstalling because i knew it would save a lot of time!

Just a though!

---

### Post by mkjarema on 2007-06-06
> **_simon_ said:**
> Can't see any mention that you've checked this so...

System -> Administration -> Login Window -> Local

Make sure that "Show Actions menu" is selected.

This fixed it for me, THANKS!
Good Luck

---

