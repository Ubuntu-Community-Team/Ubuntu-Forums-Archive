---
title: "Did you get wpa_supplicant with madwifi drives to work on a macbook [Ubuntu 7.04]?"
date: 2007-09-14
forum: Apple Intel Users
---

### Post by mr.gizm0 on 2007-09-14
Maybe this topic will help a few users, if someone can answer my questions. What I wanted to know was, if you managed to get wpa_supplicant to work with your macbook, what procedure did you take, I haven't been able to find a definitive guide anywhere and people seem to be suggesting different methods, but the ones I have tried haven't worked.

1)what version of the madwifi driver and where did you download it from (a link would greatly appreciated).

2)what version of wpa_supplicant did you use and did you make any modifications to it?

3) what did your .config for wpa_supplicant look like?


This is what I did and it on my system and I had no luck.

```

1) downloaded the latest madwifi drivers from and compiled it: http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz (which appeared to work), this was version: "madwifi-ng-r2706-20070911"
2) executed apt-get remove on "wpasupplicant" and "networkmanager"
3) downloaded wpasupplicant from http://hostap.epitest.fi/releases/wpa_supplicant-0.5.8.tar.gz, compiled it (which failed)
4) apt-get install networkmanager again (anyway, even though the previous step failed). 

```

Wpasupplicant fails to install:
```

make: [tls_openssl.o] Error 1

```
This is version 0.5.8, I have absolutely no idea how to fix this. I thought maybe I'd have to configure where the sources for openssl are installed, but theyre not on the system, only the binary, so should I recompile openssl myself aswell?

After removing networkmanager and installing it again, it does not start up, not even to display my ethernet connection. 


thanks for reading my thread and I appreciate your suggestions.

regards.
mr.gizm0

edit: sorry for the typeo in the topic.

---

### Post by cyberdork33 on 2007-09-14
Why does everyone keeps messing with wpa_supplicant? Network-Manager in the repos works... there is nothing wrong with it, and I wouldn't suggest compiling either network-manager or wpa_supplicant from scratch. Doing that removes the ability of apt to manage those applications and upgrade them when needed.

I am going to go out on a limb here and suggest that there have been some recent changes in madwifi that is screwing up everything for Mac users. I am saying this because all the sudden there are several posts about madwifi not working. On the other hand, several people state that build 2695 DOES work... I would suggest getting rid of the other versions and stick with that until some better code is released.

[http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2695-20070829.tar.gz](http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2695-20070829.tar.gz)

Also, the madwifi developers are not going to know about these issues unless you report them: [http://madwifi.org/wiki/TicketSubmissionGuidelines#a...submitabugreport](http://madwifi.org/wiki/TicketSubmissionGuidelines#a...submitabugreport)

---

### Post by mr.gizm0 on 2007-09-14
Sorry cyberdork, thanks again for your reply, I'll download and try out that version instead then. I've attempted to report the bug, but the page just seems to refresh and remove my input without any kind of notification that it's been submitted, so I'm not sure if it did or not. I'll do some more research into it.

thanks again
mr.gizm0

---

