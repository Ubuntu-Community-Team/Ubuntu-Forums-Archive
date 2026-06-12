---
title: "Black screen problem"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by LouisChappell on 2008-01-06
Hi, I was fiddling around with the colours for the task panel thing, tried to change one, typed in killall gone-panel to refresh it all and now when I log on I just get a black screen, it plays the log on music but just gives me a black screen. Any help would be appreciated as I've had to revert to xp for the time being  :(

---

### Post by stump138 on 2008-01-06
You can try a failsafe session by clicking the options button on the login screen and see if you can undo whatever changes caused the problem in the first place, else,

if you can get a terminal (type ctrl+alt+f1) when the screen goes black, then try this:

```
sudo aptitude reinstall ubuntu-desktop
```

That is the fix I've seen most others offer in the situation you are having.

---

### Post by daimaru on 2008-01-06
check if nautilus is running
heres my output.
```
ps aux |grep nautilus
    6513  0.1  1.2 115996 24980 ?        S    15:16   0:07 nautilus --no-default-window --sm-client-id default2
    6671  0.0  0.0   2664   900 ?        S    15:17   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
    7852  0.0  0.0   2980   772 pts/0    S+   16:58   0:00 grep nautilus

```if its not running start it manually 
```
nautilus
```

---

### Post by LouisChappell on 2008-01-06
Thanks thats a command I should probably remember, due to my 'curiosity killed the cat'-esque nature.

---

### Post by LouisChappell on 2008-01-06
Round two of a problem much the same, I tried to install kiba dock, adn everything froze, I attempted to log out and it gave me a black screen with the small loading icon in it, which it does for an indefinate time. I can get back to terminal but the; sudo aptitude reinstall ubuntu-desktop won't do anything and returns me to the prompt after login. 
Any takers on another balls up?

Tried uninstalling kiba dock with no success.

EDIT may not have been clear enough. I can log out but not back in. I can get to a text terminal but can't get onto the nautilus GUI. The loading is the mouse icon if any of that helps.

---

### Post by LouisChappell on 2008-01-06
after reading and more researching i pulled this command up;
sudo dpkg-reconfigure xserver-xorg, i think this has made the situation worse. I'm desperate for help if anyone knows what to do?

---

