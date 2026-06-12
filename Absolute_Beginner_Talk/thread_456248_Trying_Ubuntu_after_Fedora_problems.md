---
title: "Trying Ubuntu after Fedora problems"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by 2WhEElTeRRoRisT on 2007-05-27
I had decided to try putting linux on my laptop so i used a copy of FC5, but was having major issues with wireless.  They directed me to try Ubuntu.  I actually have a wireless internet now, so that is sweet.  i am having to issues though.  one is that my samba only lets me connect to the windows network when i have the wired connection.  i did go through the original install with it connected that way so i think that is probably the issue.  is there a way to reinstall samba with my wireless connection or is there a setting i need to change?

The other issue is that i can not change my resolution from 800x600, well besides 600x480.  i got xorg-edit program which says my resolution is 1024x800.  it is certainly not that though.  in the settings, pref, change screen resolution it lists it as 800.  i have seen a lot of articles about how to change it with gedit, but it just doesnt seem to change anything.  in fedora i just had to change the monitor settings from generic to laptop lcd 1024 and then it was fine.  is there a way to do that in ubuntu?  i think it is the screen resolution that is giving me all the problems with my dvd playback.  it also give me a lot of artifacts any time a window is open.

besides those two issues i have been very happy with ubuntu.  any help to get these fixed would be greatly appreciated.

---

### Post by Happy_Man on 2007-05-27
If you have a Nvidia card, install nvidia-glx and then run nvidia-settings:
```
sudo apt-get install nvidia-glx
sudo nvidia-settings
```

If you don't......
```
sudo dpkg-reconfigure xserver-xorg
```

---

