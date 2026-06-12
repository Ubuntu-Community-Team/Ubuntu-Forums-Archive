---
title: "[SOLVED] xorg.conf question"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by gshockxc on 2007-12-12
When I edit the xorg.conf file, it doesn't update the settings.  I'm trying to change the display resolution to 1024x768.  I made a back up of the xorg.conf file based on some suggestions I saw here.  Then I restarted X and it's still the same.  If I go to Applications --> Settings --> Display Settings, I only have one "Default" display.  It doesn't give any resolution.  Please help.  I'm going cross-eyed looking at a 4x6 display on my computer!  :(

---

### Post by sowelie on 2007-12-12
What video card do you have?  Have you installed the latest drivers?  Post the display portion of your xorg.conf and I'll see if I can help.

---

### Post by oeolycus on 2007-12-12
I lifted the following instructions from another [post]("http://ubuntuforums.org/showthread.php?t=83973"). Did you use dpkg-reconfigure xserver-xorg yet from a command line?

> How to reconfigure Xorg
Notice that auto detection of devices works best if Xorg is not running. Therefore it's recommended to stop X before reconfiguring this will put you to text only mode / command line:
```
sudo /etc/init.d/gdm stop (or kdm for KDE)
```
You can do the whole X configuration process by entering:
```
sudo dpkg-reconfigure xserver-xorg
```
To start Gnome/KDE again:
```
sudo /etc/init.d/gdm start (or kdm for KDE)
```

How to test configuration without restarting X?
See this excellent tip from [henriquemaia ]("http://ubuntuforums.org/showpost.php?p=679706&postcount=23")(Thanks!) 

You may have already tried this but it's a worth a shot before we start doing anything too complex.

---

### Post by gshockxc on 2007-12-12
> **sowelie said:**
> What video card do you have?  Have you installed the latest drivers?  Post the display portion of your xorg.conf and I'll see if I can help.

Chips and Technologies F65555.  Not sure if I have the latest drivers or not.  It might be a moot point though.  I was following a link that had some suggestions for tuning the display using vidtune.  Nothing happened until I restarted X, and then it hosed the whole display.  So I'm going to reinstall Xubuntu 7.10.  We'll see what happens.

---

### Post by gshockxc on 2007-12-12
> **oeolycus said:**
> I lifted the following instructions from another [post]("http://ubuntuforums.org/showthread.php?t=83973"). Did you use dpkg-reconfigure xserver-xorg yet from a command line?

 

You may have already tried this but it's a worth a shot before we start doing anything too complex.

I think I did do a reconfigure.  It brought me to a configuration screen much like what I saw on the install. I selected a bunch of display settings that I thought might work.  When I was finished, I lost the 800x600 resolution.  When I went back to tinker with vidtune, all I could find was 640x480.  I was modifying the screen size - or so I thought, but it didn't have any effect when I clicked "show."  

So I quit and went back to xorg.conf to tinker some more.  I did something with "Modeline" in xorg.conf. and nothing changed.  So I restarted X, and that killed the whole thing.  Whatever I did, I hosed the display.  So I'm going to reinstall X and see what happens.

---

