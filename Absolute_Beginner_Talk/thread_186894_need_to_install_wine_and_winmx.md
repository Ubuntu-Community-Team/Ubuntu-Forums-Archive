---
title: "need to install wine and winmx"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by cabbie 69 on 2006-06-02
[SIZE="4"][/SIZE]
i need to install wine so i can run winmx

---

### Post by sir_cheats_a_lot on 2006-06-03
Why not FrostWire? you won't need to bother with wine if you choose FrostWire.
[http://www.frostwire.com/](http://www.frostwire.com/)

If you are set on using WinMX check out this link:
[http://www.slyck.com/forums/viewtopic.php?t=6255&sid=6af7601875811e3c9727e7a9029e9d6c](http://www.slyck.com/forums/viewtopic.php?t=6255&sid=6af7601875811e3c9727e7a9029e9d6c)

hope this helps.

---

### Post by ngch on 2006-06-03
I don't know if winmx can work with wine, but in case u want to try, there are two ways to install wine.

**The easier-to-understand way**
[LIST=1]
[*]Start Synaptic Package Manager in System>Administration
[*]Go to Settings>Repositories and check the universe repositories under Ubuntu
[*]Under sections, choose Cross Platform (universe)
[*]Scroll down the long list of packages till you find the [COLOR="Red"]wine[/COLOR] package
[*]Mark the package for installation and click apply
[*]Click apply again, and synaptic will download and install wine for you
[/LIST]

**The faster way**
[LIST=1]
[*]Open the terminal in Applications>Acessories
[*]Type ```
sudo apt-get install wine
```
[*]Enter "y" and watch it download and install wine, quicker!
[/LIST]

After you have installed wine, you can then try running exe programs using wine. I don't know whether it can run winmx though, since I've never tried it and it may require files from Windows that are not installed with wine. It's worth a try though. ;)

If it doesn't work... then you'e probably better off trying out the alternative programs given in the last post.

To uninstall programs installed under wine, enter this command in the terminal

```
wine uninstall
```

Then, select the program to uninstall and click uninstall

---

### Post by sir_cheats_a_lot on 2006-06-03
Oh and after searching the forum; WinMX has been shut down for about the last year.  but someone found a work around, so it is possable to access the network, but i'm not sure if you can in Linux...i don't care for the program myself but for some reason other people do, so i wasn't exactly sad to hear of it's official closing...ok, found the "fix" here it is;
[http://www.winmxworld.com/tutorials/winmx_fix.html](http://www.winmxworld.com/tutorials/winmx_fix.html)

 good luck getting it to work on wine (hopefully something on the second link will help)

---

### Post by Sitix on 2006-06-03
@sir cheats a lot: Well, actually Frostwire or Limewire is a waste of CPU and RAM... It runs on Java, is slow, takes up loads of memory: and that while there are more than enough alternatives.

Actually I suggest to use a P2P client like Apollon. Or else use torrents... it's like nonsense to emulate a program just for file sharing... next to that, Apollon can connect to several networks at a time (I don't know if that's the case in WinMX.)

---

### Post by sir_cheats_a_lot on 2006-06-03
[QUOTE=Sitix]@sir cheats a lot: Well, actually Frostwire or Limewire is a waste of CPU and RAM... It runs on Java, is slow, takes up loads of memory: and that while there are more than enough alternatives.

Actually I suggest to use a P2P client like Apollon. Or else use torrents... it's like nonsense to emulate a program just for file sharing... next to that, Apollon can connect to several networks at a time (I don't know if that's the case in WinMX.)[/QUOTE]
i had never heard of Apollon, so naturally i suggested what i knew of...i would have suggested KLR(Kazaa Lite Ressurection) but i haven't been able to get it to work on wine...to be honest i have never gotten limewire working on linux at all.  Yes; java is a little slow on a dialup connection, but then again i imagine wine is too :p .   in the mean time i'll look into apollon.

---

### Post by roderikk on 2006-06-05
Hm, Apollo however requires the KDE libraries to be intalled. Can't be bothered with that.
You suggest a bittorrent client, however, I haven't been able to find any good bittorrent client. Azureus is unmanagable with all its freezes and other stuff just don't give you any options.
I tried using utorrent ([www.utorrent.com](www.utorrent.com)) in wine, but I couldn't get it to connect to the network. I know it is a bit of a work around to run a filesharing program in Wine but as long as I don't know any other good alternative, I will try to get this to work.

---

### Post by localzuk on 2006-06-05
According to appdb, winmx does work with wine ([http://appdb.winehq.org/appview.php?appId=288)](http://appdb.winehq.org/appview.php?appId=288)).

Details for installing wine are here: [https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine)

---

