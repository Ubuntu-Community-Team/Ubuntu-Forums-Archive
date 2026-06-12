---
title: "Palm Problems with Gnome-pilot etc"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by dykesy61 on 2007-10-02
OK - running Ubuntu 7.04 but using KDE desktop.  Have been trying to get my Palm m500 to sync with various bits of software, including evolution jpilot, kontact, using gnome-pilot, kpilot etc.

after trying many options and program combinations I ended up finding that Kpilot and Kontact worked the best for what I wanted.  The problem is I then shut down and started up, and when I now try and sync the system runs gnome-pilot instead, and says its user id doesn't match - it doesn't get near Kpilot, which just freezes.  so I can no longer sync at all!

I deleted the gnome-pilot directory in Home, and then the user file for the Palm, but I can't sort it out.

How do I get rid of gnome-pilot so that kpilot can run properly?  I think gnome-pilot is stopping kpilot from working now, though how and why and I don't know.  help, please?

---

### Post by dykesy61 on 2007-10-02
right - moved on from there - now can get Kpilot and Lontact working after a fashion.

the problem I now have is that whatever I set the conduit settings to, I can't get the handheld transferred to the PC.  if I delete stuff on the handheld, the PC overwrites it, whatever setting the Hotsync is set to.  Is this a bug in Jpilot or Kontact or is it my problem?

Help anyone?

---

### Post by nowshining on 2007-10-02
with jpilot u'll have to start up the program - press the hotsync icon on the program insert ur palm handheld and then press the hotsync button.

---

### Post by nowshining on 2007-10-02
n/m

---

### Post by dykesy61 on 2007-10-02
thanks for replying...

I can get it to sync, in that it does go through the motions, but it won't take notice of what is on the handheld, and just overwrites from the PC.  could it be that the hotsync file (is there one?) is corrupted?

---

### Post by nowshining on 2007-10-02
I myself use a palm IIIxe and use the jpilot program myself. I use gnome - and it uses diff. library files than kde even tho I have some myself to run KDE apps in gnome.

---

### Post by nowshining on 2007-10-02
hmmm odd tho after re-reading u say gnome pilot which should of catched my eye earlier.

open up a terminal and paste the outcome of 

```

sudo apt-get install -f

```

enter ur password when asked to - and please note that while typing out the password it will not show and this normal - type it out as u normally do and hit enter - don't do nothing yet after u posted the outcome until further instructions.

---

### Post by dykesy61 on 2007-10-02
sorry...I started with a gnome-pilot problem which has now become a Kpilot one.
I sync using kpilot to kontact, but it doesn't seem to matter what I set the settings to, it does not recongnise changes on the handheld.

thanks for the instruction - I discovered I had libgnome-pilot2 when I didn't need it, so have now removed it.

---

### Post by nowshining on 2007-10-02
oh that's right kpilot i was thinking of jpilot but instead of a j with a k :P

after u tried again after removing the lib file - I myself issued it and it said pidgin was no longer needed - removed - saw no pidgin IM client and i also purged the files - reinstalled and reissued the command to see what it would say - didn't mention pidgin for an uninstall..

Well anyway ur problem is beyond me, maybe u can go here

[http://www.launchpad.net](http://www.launchpad.net)

find the kpilot project and report a bug there or wait for some else with a kde desktop to come around.. At least all this bumped up ur thread up incase they do come.

---

