---
title: "Help: Gnome Network Manager Under KDE"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by bubbalouie on 2007-10-28
I have started using the Gnome network manager applet under KDE as it provides some WPA enterprise features I need. However, it does not remember any of the keys I give it. As a result every time I join a network I have to re-enter all of the details. 

How can I make it remember all of my details, which gnome components does it depend upon for this functionality. Any help would really be appreciated.

Cheers :)

---

### Post by bubbalouie on 2007-10-28
Anyone?

---

### Post by testube_babies on 2007-10-29
Is there some reason you can't use knetworkmanager?  It's the same program but integrated into KDE so that, for instance, it will remember your network details.

For gnome-network-manager to remember all of this stuff, you will need to load some gnome daemons (which may entail installing large portions of the gnome desktop as well).  The most important of these would probably be gnome-keyring-daemon, although you might need more.

---

### Post by bubbalouie on 2007-10-29
Thanks, I will try wby startng with the keyring daemon.

Under WPA2 enterprise there are some settings such as the key type that I need, knetworkmanager does not include these options, with that exception I find knetwork manager to be MUCH nicer, but at the end of the day, it is a tool, and whilst the gnome tool is uglier, it does some things I can't otherwise do.

Thanks,  will be sure to post results.

Ryan

*Results: No cigar, I have installed all of the gnome packages with the word keyring in them (mallet aproach) and no luck, for now I will just need to hope the next version addresses this deficiency, frankly given the nature of OS I'd be surprised if it wasn't fixed....

Thanks for the help, it's a pitty KDE is missing such a small feature

---

