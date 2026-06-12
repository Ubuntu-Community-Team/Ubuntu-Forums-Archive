---
title: "Wine install error msg, and unable to start game."
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by Unfadable on 2005-11-12
Hello guys,
I just recently switched to Ubuntu from windows98. There is a guy that I play a lot and I'm trying to get it installed to run in Ubuntu.

The 1st time I installed Wine it went ok, and I even installed Colonization and ran it fine. I attempted to run install.exe for Anarchy Online large client download from its website, and it ran setup. However once running the App, it kept on asking for this one missing file.

I deleted Anarchy Online's folder, and attempted to reinstall with wine. At this point it will simply not even run install.exe

I removed Wine using synaptic, and I followed installation process with wine again. It seemed to have installed correctly, but when I attempt to run Wine +*.exe it gives me this error: 

faldana@c-67-167-12-00:~/Desktop/MyDocuments/AOInstall$ wine Setup.exe
wine client error:37: version mismatch 194/197.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

Is there something I can do to fix this and be able to install Anarchy Online?

Thanks in advance.

---

### Post by etc on 2005-11-12
First off
wine --version
then a
killall -9 wineserver

Try again, post results

---

### Post by thedevilsjester on 2005-11-12
I dont think plain wine supports Anarchy Online yet, I dont even think Cedega does (I could be wrong though)

A good thing to remember when migrating to linux and attempting to use Wine to run games and software is that wine is a beta product and is not even close to being compatible with most games.  It will run a large portion of software pretty good, but modern game support in wine is still a fairly new thing.  Its getting there though, but dont expect miricles at this stage in the game.

I think Wine has a 'big exe' flag when trying to run/install games that have a fairly large exe, I know that Cedega has this flag, you might attempt it with that if you dont have luck with wine.

---

### Post by Unfadable on 2005-11-12
Hi
Thanks for the help. Here are the results:

faldana@c-67-167-12-00:~$ wine --version
wine: creating configuration directory '/home/faldana/.wine'...
wine: '/home/faldana/.wine' created successfully.
Wine 0.9.1
faldana@c-67-167-12-00:~$ killall -9 wineserver
wineserver: no process killed

---

