---
title: "GUI log in problems"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by zuperxtreme on 2007-08-01
I've searched for a while and I couldn't really find any solutions...

So, here it goes:

Yesterday I decided to try a new desktop environment because KDE is a bit slow for my taste(on my machine, of course), so I decided to go for IceWM. I searched for it with apt-get and I started to do the installation along with some kubuntu upgrades. My machine sometimes tends to turn off and this was one of those times.

I started it back up and everthing seemed fine(it auto logs in), I downloaded and installed IceWM and I pressed CTRL+ALT+Backspace to kill X. I know, I should have just logged out but I didnt...

This time instead of giving me the regular pretty GUI Login screen, it sent me straight to the command line (blah@blah:), I started X back up with 'sudo startx', but now in my logout screen it only showed log out. No shutdown, no restart,hybernate or suspend. Just log out. I tried loggin out and it took me back to the command line. I restarted 'sudo shutdown -r now' and I booted into recovery mode.

It took me to command again(but I think thats what its meant to do) and I started up X, KDE booted up, I checked out the log out screen and it only showed log off again. I started reading up a bit and tried to reconfigure Xserver. 'dpkg-reconfigure xserver-xorg', I configured it by defaults like my original install, restarted kdm '/etc/init.d/kdm restart' and KDE loaded again. This time it did have restart,shutdown, log off, etc in the log out box. So I restarted.

I started Kubuntu regularly, no recovery and in auto logged me in. I checked the log out again and everthing was there. I logged off and the GUI came up, I thought everything was fine so I decided to go ahead and change sessions(to E17, if it matters) used it for a while and decided to go back t KDE because it was getting late so I could leave it for the rest of the family members. But to my surprise, it took me back to the command line again.

So, my question is: What the hell?! What did I break? :/

Oh, I also went back to the original xserver config file(I forgot the command) just in case, but to no avail.

Im running Kubuntu 5.04 upgraded to the latest, if that helps any.

ANY help appreciated, while the problem isn't crippling, it sure is annoying...

Thanks!

---

### Post by wolfen69 on 2007-08-01
are you sure you're running 5.04? if you are, i don't believe it is supported anymore. this might be a good time to upgrade and do a fresh install.

---

### Post by zuperxtreme on 2007-08-01
I was thinking the same thing. It might just be easier to download a new Install CD and just start fresh.

Since we're on topic. I partitioned my harddrive and made the 2nd, larger partition mount to /home. When I reinstall ubuntu, I should still have all my stuff, right? (given that I dont reformat /home, duh :P )

---

