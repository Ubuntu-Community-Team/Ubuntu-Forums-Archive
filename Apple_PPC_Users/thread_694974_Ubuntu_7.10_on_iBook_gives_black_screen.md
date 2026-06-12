---
title: "Ubuntu 7.10 on iBook gives black screen"
date: 2008-02-12
forum: Apple PPC Users
---

### Post by octopuls on 2008-02-12
Dear Ubuntu comrades,

I have a hard time installing Ubuntu 7.10 on an Apple iBook 800 MHZ 664 MB Ram. I only get a complet black screen as a final result. When I use the downloaded and burned ISO image as a Live-CD I get this:

1) First message : "First stage Ubuntu bootstrap"
2) Second messsage : "Welcome to Yaboot 1.3.13"
3) The kernel is loading
4) The screen is recognized : "Done - Found display"
5) Some extra messages : "PCI: cannot allocate resource region of device 00001:30.19.0" and "Loading please wait..." and then ...
6) COMPLETE BLACK SCREEN (no prompt, no hard drive activity) :-(

Finally I managed to get the Live-CD working using a manual boot and selecting "no-splash" but once I installed Ubuntu 7.1 on my harddrive I was confronted with just the same problem (the black screen) when trying to boot from the harddrive. And I don't know of any workaround here. 

I also tried Kubuntu 7.10 and Xubuntu 7.10 but always have the exact same problem. I also tried it on another iBook ( a 1,2 GHz G4 iBook with 784 MB RAM) but still the same problem ( a problem that doesn't occur when I use an old Ubuntu 5.04 Live CD and under MacOS X everything works fine too).

Does anybody knows a solution to this problem? Thanks.

Hendrik, Brussels, Belgium.

---

### Post by stream303 on 2008-02-12
Ah, have you tried these at the boot: prompt  (you only have a few seconds here, so many just hit TAB to stop the countdown and see what options are provided)

live-nosplash-powerpc
or
live-nosplash-powerpc video=ofonly
or
live-nosplash-powerpc video=ofonly break=top

Here's a link to some known issues with Gutsy that goes into further detail:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Once we find a combo that gets you booted nicely, we can then make the changes permanent.

Another quick fix would be to try the Feisty 7.04 release using the "alternate" install image.

Let us know how it goes!

---

### Post by thierryg on 2008-02-13
[QUOTE=octopuls;4318678]Dear Ubuntu comrades,

Hi,

As far as I know on my iBook this problem is linked to the splash screen display no working (giving you the black screen). So, after installing gutsy (and before restarting the ibook), I have to change the yaboot options:

Mount your install volume (with Nautilus, for example)... so that you can access your /media/disk/etc/yaboot.conf.

edit /media/disk/etc/yaboot.conf

```
sudo vi /media/disk/etc/yaboot.conf
```

Remove splash from all append = lines.

```
append = "quiet"
```

Personally I also remove quiet... To let Ubuntu tell me lots of things on startup.

Then run ybin to update yaboot on your new file

```
sudo ybin -C /media/disk/etc/yaboot.conf
```

It should be Ok then to restart.

This is something you can do without reinstalling. Start with the live CD as usual, do the above and restart.

Thierry

---

### Post by octopuls on 2008-02-13
> **stream303 said:**
> Ah, have you tried these at the boot: prompt  (you only have a few seconds here, so many just hit TAB to stop the countdown and see what options are provided)

live-nosplash-powerpc
or
live-nosplash-powerpc video=ofonly
or
live-nosplash-powerpc video=ofonly break=top

Here's a link to some known issues with Gutsy that goes into further detail:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Once we find a combo that gets you booted nicely, we can then make the changes permanent.

Another quick fix would be to try the Feisty 7.04 release using the "alternate" install image.

Let us know how it goes!


Thanks for your feedback. To make the Live-CD work the "no-splash"  option definitely works (as mentionned in my previous post). So that's a workaround which makes it possible  once booted in to try Ubuntu live and to choose the install option . But then when everything is installed nicely on your harddrive you're faced with the same problem again and then the workaround which worked for the LIVE-CD is not an option anymore. Finaly I found a working solution on this forum ( see [http://ubuntuforums.org/showthread.php?t=669514](http://ubuntuforums.org/showthread.php?t=669514) ) . It takes a bit more time but it is damn easy (no fussing around in terminalcode or things like that) : I first installed Ubuntu 7.04 on my iBook (which works fine as a Live-CD or as an install on the harddrive) and then upgraded from within 7.04 to 7.10. Bingo! :-)  The only strange thing is that the fan is working a lot and making a lot of noise and my internetconnection via ethernet is not working anymore (problems that occured only after upgrading from 7.04 to 7.10). Any idea what can be the cause? Otherwise I'll have to downgrade to 7.04.

Thanks everybody for the feedback and have a nice day,

Hendrik
Apple iBook G4 800 MhZ | Ubuntu 7.10

---

### Post by stream303 on 2008-02-13
Wow!  Glad that worked out.  This just might be the ticket for eMac owners as well.

I'll bet that Network Manager is sucking up all the resources.  I had to disable it (NOT uninstall it) to get my iBook running cool again:

Top or my fav, htop, will show you.

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

Once it is disabled, you may have to back into network and re-enable your connections.

Note: only my iBook had this problem with network manage sucking up all the resources.  On other machines, it was ok.


BTW, do you have virtual terminals, ie CTRL-ALT-F1, or does the screen just stay blank?

---

### Post by linuxopjemac on 2008-02-13
you might wanna reconfigure your Xorg.conf settings by going into another terminal CTR-ALT-F1 for example, login and run:

sudo dpkg-reconfigure xserver-xorg

then do a CTRL-ALT-Backspace to restart Gnome...everything should work then

---

### Post by kavanayy on 2008-03-03
same problem occurs to me, black screen shows and I tried live-nosplash-powerpc, this can let me finish the installation, but can not boot the system, black screen again......

---

### Post by octopuls on 2008-03-04
If you have the same problem use the same solution. ;-)
Explanation : Do not install 7.10 directly on your computer but Install Ubuntu 7.04 instead and once 7.04 is installed upgrade from within 7.04 to 7.10.

Good luck.

---

