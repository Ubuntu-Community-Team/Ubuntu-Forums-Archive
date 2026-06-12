---
title: "MacBook Compiz not working - won't install from Terminal or Package Manager"
date: 2007-11-11
forum: Apple Intel Users
---

### Post by ginistheman on 2007-11-11
[EDIT] Solved thread title problem, but have a new one! [EDIT]

Hi everyone I'm having a tough time trying to get Compiz Fusion running on my C2D MacBook.

Originally when I installed Ubuntu, I went into the preferences menu and then to appearance to turn on the Extra Visual Effects. Done, wobbly windows, nice icons etc.

Then I tried to install the Compiz Config settings manager using

> sudo aptitude install compizconfig-settings-manager

This returns;

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched
"compizconfig-settings-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done

I thought that this all looked normal, but when I go to my preferences menu it still has not added the CCSM option. 

I read somewhere this could be a plugin issue and to uninstall compiz from the synaptic package manager which I did. This caused my titlebars to disappear (so I have switched to Normal from pref>appearance>visual effects). 

Really stuck from here! Can anybody help me to get compiz back and then to install the settings manager?

---

### Post by ronocdh on 2007-11-11
Have you tried searching in Synaptic for "compiz" or perhaps "compiz manager"? Even "compiz settings" should turn up hits. Try installing (maybe after completely removing everything) from there, and perhaps that'll put you in good order.

Man, I hate those disappearing titlebars! :mad:

---

### Post by ginistheman on 2007-11-11
> **ronocdh said:**
> Have you tried searching in Synaptic for "compiz" or perhaps "compiz manager"? Even "compiz settings" should turn up hits. Try installing (maybe after completely removing everything) from there, and perhaps that'll put you in good order.

Man, I hate those disappearing titlebars! :mad:

Thanks for replying ronocdh.

I've tried searching for "compiz" in Synaptic an it doesn't return anything. 

I think I've messed up when I tried to uninstall it. I went into Synaptic and typed in "compiz" and then "mark for uninstallation" to remove compiz so I could reinstall it but it' not even appearing now!

If i go into the terminal and type;

> compiz

it returns this;

> The program "compiz" is not currently installed. You can install  it by typing:
sudo apt-get install compiz-core
bash: compiz: command not found

Where does this leave me? I take it I successfully uninstalled it, but how do I reinstall it now?

---

### Post by ginistheman on 2007-11-11
Okay good news is that I got CCSM working. 

Bad news is that some of the plugins like Water Effects don't work. Aren't these supposed to function properly on a MacBook?

---

### Post by ginistheman on 2007-11-13
Hi everyone, I'm just bumping this as I'm in desperate need of help.

I've installed Ubuntu on my sisters old Dell Laptop (256MB RAM, Celeron) which is basically totally inferior to my MacBook. 

The odd thing is that it runs Ubuntu better than my MacBook can. The trackpad on it responds really well to Ubuntu unlike the problems I had with the trackpad on my MacBook when I installed Ubuntu on it.

Also, I could not get all of the brilliant Compiz effects to work on my MacBook whereas they run fine on the crappy old Dell (Water Effects is a good example, runs really well on the Dell but not on my MacBook).

How is this possible? I read this article  ([http://ubuntu-tutorials.com/2007/10/04/compiz-fusion-on-ubuntu-710-gutsy-gibbin/](http://ubuntu-tutorials.com/2007/10/04/compiz-fusion-on-ubuntu-710-gutsy-gibbin/) ) and it says that Compiz requires "zero config" although I'm really struggling to get all of the features working.

---

### Post by cleentrax on 2007-11-13
A couple of thoughts. First, do you have a brand new MacBook with the X3100 video? The X3100 is blacklisted for Compiz.

Second, have you tried the obvious:

```
sudo apt-get install compiz
```

I don't see that mentioned above.

---

### Post by cyberdork33 on 2007-11-13
> **cleentrax said:**
> A couple of thoughts. First, do you have a brand new MacBook with the X3100 video? The X3100 is blacklisted for Compiz.

Second, have you tried the obvious:

```
sudo apt-get install compiz
```I don't see that mentioned above.

Compiz is installed by default in Gutsy.

Did you enable the extra software sources?

---

### Post by cleentrax on 2007-11-13
> **cyberdork33 said:**
> Compiz is installed by default in Gutsy.

Did you enable the extra software sources?


Yes, but apparently he tried to uninstall Compiz. Perhaps he succeeded.

---

### Post by ginistheman on 2007-11-14
Sorry for the late response, time zone differences.

I do have Compiz running (I reinstalled Ubuntu, as I had some partition issues), so I can get the 3D cube, Expo etc - the thing that confused me was how poorly it ran (actually did not run at all) effects like Water and Blur in comparison to my sisters old Dell Laptop which is arachaic compared to my MacBook.

I have a GMA950 MacBook and not the new one. 

Excuse the ignorance, but what does "enabling the extra software sources" involve? 

Can the MacBook actually run Compiz in all it's glory or is it not possible?

---

### Post by cyberdork33 on 2007-11-14
> **cleentrax said:**
> Yes, but apparently he tried to uninstall Compiz. Perhaps he succeeded.

I missed that post apparently, sorry. I thought he was just trying to mess with compiz-config, not the entirety of compiz.

>  		Sorry for the late response, time zone differences.

I do have Compiz running (I reinstalled Ubuntu, as I had some partition issues), so I can get the 3D cube, Expo etc - the thing that confused me was how poorly it ran (actually did not run at all) effects like Water and Blur in comparison to my sisters old Dell Laptop which is arachaic compared to my MacBook.

I have a GMA950 MacBook and not the new one. 

Excuse the ignorance, but what does "enabling the extra software sources" involve? 

Can the MacBook actually run Compiz in all it's glory or is it not possible?

Compiz should work fairly well on your macbook. Make sure that you are using the 'Intel' driver for your video card in the /etc/X11/xorg.conf file.

You are, however, limited by video RAM, so if you are trying to drive a particularly large screen resolution, you will have slower effects.

---

### Post by ginistheman on 2007-11-14
> Compiz should work fairly well on your macbook. Make sure that you are using the 'Intel' driver for your video card in the /etc/X11/xorg.conf file.

You are, however, limited by video RAM, so if you are trying to drive a particularly large screen resolution, you will have slower effects.

How would I check that I am using the 'Intel' driver? Sorry, I'm a newb! I would assume I am, if it's letting me do some of the effects and not others. 

If I'm not, how can I make sure I am?

Another thing I'm trying to get to the bottom of is how my sisters old Dell laptop can run Compiz better than my MacBook? They both have the same graphics (Intel GMA950) and the MB has a better processor and more RAM! Surely it should be able to handle Water/Fire/Snow etc.?

---

### Post by cyberdork33 on 2007-11-14
> **ginistheman said:**
> How would I check that I am using the 'Intel' driver?

open said config file and look.

---

### Post by ginistheman on 2007-11-14
> **cyberdork33 said:**
> open said config file and look.

Thanks for the help, I'm at work currently but will check when I get home.

Also, the other thing you mentioned about "enabling extra software resources", I'll try that as it could be the issue. 

Will report back, as hopefully this info is of use to other people in the same boat as me.

---

### Post by cyberdork33 on 2007-11-14
> **ginistheman said:**
> Also, the other thing you mentioned about "enabling extra software resources", I'll try that as it could be the issue.

Oh yea, never gave direction on that. It is in the System menu under Administration.

---

