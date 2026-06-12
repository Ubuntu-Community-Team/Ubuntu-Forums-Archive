---
title: "[SOLVED] Building amarok, got KDE stuff by accident"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by dmub82 on 2008-04-19
On Gutsy, GNOME. Was trying to compile amaroK 1.4.9.1. It worked but somewhere along the way, getting the build-dependencies I guess, I wound up accidentally installing a ton of KDE apps I don't want. I understand amaroK requires some KDE libs, but I'd successfully compiled amaroK before without getting all the extra stuff (I was redoing it this time because I accidentally downgraded). Only thing that changed is I think backports was enabled in my repositories this time when it wasn't before. When I ran ```
sudo apt-get build-dep amarok
``` it installed what seemed like a lot more things than I remembered from before, the download on build-dep was about 55Mb but I let it go because I wasn't sure if anything was wrong.

Now my Applications menus are filled with a bunch of unnecessary things -- Accessories now includes KJobViewer; Internet inclues Konquerer; Sound & Video has Krec, Kmid, KsCD; System has Konsole and KSysGuard. The Other menu is the worst, it's completely stuffed with a couple dozen things I know weren't there before but I couldn't necessarily pick out all the new ones to list here. Most of the KDE apps listed in Other have the generic icon but they do run, if that means anything.

I can't remove any of these through Add/Remove..., it says other things depend on them. How can I get rid of all this stuff and make sure it's all gone? I'd prefer not to have to try to figure out the package to remove for each individual app. ```
sudo apt-get autoremove
``` didn't catch anything. And once I fix this, anyone know where I went wrong in compiling amaroK so I can try again without getting all the unnecessary stuff?

---

### Post by forrestcupp on 2008-04-19
Maybe check Synaptic and see if you accidentally installed kubuntu-desktop

---

### Post by dmub82 on 2008-04-19
Thanks for the quick reply.

Nope, kubuntu-desktop is not installed, nothing else listed under kubuntu as well. Also searched for anything listed under "kde", I do have "kdesktop", could that be the errant package? Browsing the list I see some of these listed individually like konqueror and konsole, but I'd like to get them all in one fell swoop so I can be sure they're gone and I didn't leave anything that might cause a problem behind the scenes. What's the best course of action from here?

eta: Also noticed I have kdebase-bin, kdebase-data, kdebase-kio-plugins and kdebase-dev installed but not kdebase itself.

---

### Post by dmub82 on 2008-04-19
OK, I basically went through in Synaptic and purged most anything that appeared to be a KDE package that I didn't need for anything else and I think that got rid of everything without screwing me up further. Thanks, and if anyone has an idea what I did wrong in the first place, still curious.

---

