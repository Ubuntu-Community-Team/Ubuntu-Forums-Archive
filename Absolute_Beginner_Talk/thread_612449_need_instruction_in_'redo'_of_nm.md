---
title: "need instruction in 'redo' of nm"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by nraney on 2007-11-13
My problems are:
1. network manager connects and works for a few minutes, then stops working even though the nm tells me it is still connected.

2. When i try to connect to a new wireless network with the nm-applet; nm-network manager fails and nm-applet disappers from gui

3. the IT people tell me the authentication is working (restricted.utexas.edu), but for some reason my computer is re-authenticating about every five minutes.  the connection fails each time this happens.  the re-authenticating is probably me trying to reconnect, **it works for five minutes, then dies.**

I think when i was setting it up i screwed something up.  I followed instructions from [https://management.pna.utexas.edu/static/faqs/dot1x/dot1x-linux.html](https://management.pna.utexas.edu/static/faqs/dot1x/dot1x-linux.html) before i realized i should just install the wpa in synaptic.  oops. im new.

I would like to start over with the network manager, but i am too inexperienced in ubuntu to accomplish this.  

on a side note my computer:
cannot hibernate - hal issue... any links for this?

when running update-manager from command prompt responds, "cannot initiate dbus" what does this mean?

thanks for anything,
nraney

---

### Post by nraney on 2007-11-14
This is my only source for help... are people not answering because I'm asking something too simple or because they don't know?

am I missing some walkthrough or something? can a moderator fill me in please?

---

### Post by p_quarles on 2007-11-14
The link you posted isn't working, so I have no idea what you did that messed things up. If you could provide some more details someone here might be able to give a better answer.

In any case, you can reinstall network manager by typing this:
```
sudo dpkg-reconfigure network-manager
```
That won't revert all settings, though, which is why I asked what you changed. Give that a try, though.

---

### Post by nraney on 2007-11-14
[https://management.pna.utexas.edu/static/faqs/dot1x/dot1x-linux.html](https://management.pna.utexas.edu/static/faqs/dot1x/dot1x-linux.html)

is the correct link.. my bad.

i did that stuff first..

it wasn't working, so i figured out i could just install wpa with apt-get or whatever.  so i did, it connects but then has the problems i described before.

the problem is I dont know what information to offer, because I dont know what the problem could be or where to look for these settings.  I think Im using ndiswrapper, but im not sure.

I have  a Compaq HP V3000 laptop. v3019us to be specific.  
compaq doesnt list what type of wireless card i have in their product specifications.  

i seem to be using a windows wireless driver. bcmwl5, however, network manager is using the driver ndiswrapper.. i dont know what that means.

ill do my best to give any information required to fix.

---

### Post by nraney on 2007-11-15
seriously guys.. anything, no matter how trivial you think it is.. even a basic description of how the windows wireless drivers works with ndiswrapper (which im assuming).. 

is my system configured well enough, i just need to wait for updates?

---

### Post by nraney on 2007-11-20
my buddy says I should go back to the old gnome-network-manager.  how do I do that?

---

