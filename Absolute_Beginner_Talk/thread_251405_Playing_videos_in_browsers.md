---
title: "Playing videos in browsers"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by pkc2 on 2006-09-05
Hi, Can someone please point me in the direction of how to get FF or Opera to play videos? I'm specifically trying to play news videos on bbc.co.uk. The browser takes me to a page and offers Windows media or RealPlayer, none of which work. Where do I get a player please? (looked in add/remove programs but didn't find anything)
Thanks
Peter

---

### Post by Skogix on 2006-09-05
```
sudo aptitude install mozilla-mplayer
```
```
sudo aptitude install kaffeine-mozilla
```
Try and check which you prefer. I'm using mplayer :).

---

### Post by ajgreeny on 2006-09-05
I would suggest you use mozilla-mplayer which plays videos in the browser.  Kaffeine-mozilla just launches kaffeine as a separate window, which I find less useful.  Try both, however; you may well prefer kaffeine running in a separate window.

---

### Post by pkc2 on 2006-09-05
Hi, thanks for the quick responses. I'm struggling with both the above commands. Tried them both and for both I get that the package has not been found and therefore won't be installed. I do already have a package called Kaffeine in my Applications > Sound and Vision but I don't know how to get it to load when I want to wwatch a video in a browser. 
I have also downloaded a file RealPlayer10GOLD.bin to my bin directory (following instructions I found on the BBC web site) but I am unable to run it. I have used 
"sudo ./RealPlayer10GOLD.bin" but it doesn't work and I can't run the file in Nautilus cos it's owned by root.
I'm a bit stuck. I thought this one was going to be easy to solve:-(
any advice please?
Thanks, Peter

---

### Post by Shay Stephens on 2006-09-05
This is how I got mine working:

add the 'universe' and 'multiverse' repositories in synaptic

```
sudo apt-get -y install mplayer
sudo apt-get -y install mozilla-mplayer
sudo apt-get -y install flashplugin-nonfree
```

---

### Post by gkiller on 2006-09-05
Did you add the universe and multiverse repositories?

See here for info on how to do that:
[http://easylinux.info/wiki/Ubuntu_dapper#Repositories](http://easylinux.info/wiki/Ubuntu_dapper#Repositories)

After that, just run
```
apt-get update
```
and then the other "apt-get install" commands.

---

### Post by PPAAUULL on 2006-09-05
Just use Automatix. It is so much easier to get it all done at once!!!!! K.I.S.S (Keep It Simple Stupid) Lol

---

