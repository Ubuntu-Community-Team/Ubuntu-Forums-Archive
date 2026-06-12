---
title: "Gnome2 takes longer and longer to login - slow loading DURING login"
date: 2011-07-22
forum: Any Other OS
---

### Post by Redsandro on 2011-07-22
[SIZE="1"]**[update]**[/SIZE]
*Artificial Intelligence* added the Mint prefix. But like I stated in this post: The exact same happens in Ubuntu 10.04 LTS. So **it has nothing to do with Mint**.
[SIZE="1"]**[/update]**[/SIZE]

Running Ubuntu 11.04 with Gnome classic. I discovered logging in takes longer and longer, like 30+ seconds. And I mean the time it takes until I get a desktop and panels, not hard drive activity after that like discussed in _[this topic]("http://ubuntuforums.org/showthread.php?t=1660918")_.

Login with a brand new user takes about 2 seconds. So I figured it must be some configuration loading.

I removed every .hidden folder from home, and the reboot was fast again. Then I slowly put stuff back one by one, leaving out stuff I didn't care about, and it kept being fast. This process took a long time.

Now I know it is impossible but I swear it's like this: Next day, it was slow again! Not as slow as before, now it's like 15 seconds, but it's supposed to be faster than that, come on 2011!

I tried one by one moving .config, .cache, .gconf2 away and back but I cannot get it to login near-instant again like with a new user.

I tried removing all my autostart apps but of no avail.

Are there any known retarded configuration folders that are known to be snailish slow? 
What is this dconf daemon something about converting gconf? 
Is there an alternative to bootchart that logs the login sequence and isn't impossible to read for non-rocket-scientists?

[SIZE="1"]Had the exact same problem on Ubuntu 10.04. This was one of the reasons I moved to 11.04. Okay you got me, I am using Mint 11 instead of Ubuntu 11.04 because I don't like the retarded unity interface, but it's essentially the same. Even uname sais Ubuntu.[/SIZE]

---

### Post by Perfect Storm on 2011-07-22
Moved to Other OS/Distro Talk.

---

### Post by Redsandro on 2011-07-24
No clues on this? Anyone?

I think it's rather important to figure out what program configuration(s) is causing the account session start to lag like this. Because once your account starts to take more than a few seconds to login, you're not part of the future anymore.

:-({|= [img]http://tweakers.net/ext/f/M82BwAhU0QYKtKxzManwFCFR/full.gif[/img]

---

### Post by 23dornot23d on 2011-07-24
Do you use ubuntuone .....

as when I removed the packages for it with Synaptic things improved quite a lot ..... just a thought ...

It may be something else .... but this did cause me some problems a long time ago .....

---

### Post by BrokenKingpin on 2011-07-27
I have the same problem on Mint 11 where it takes a while for the panels to load after login. When I first loaded it everything seemed pretty snappy after login, but as time goes on it seems to get longer and longer.

I have switched to Xubuntu on all my other machines and I do not have this issue. So I will be replacing the Mint 11 with that when I get a chance (or maybe I will wait for Xubuntu 11.10).

---

