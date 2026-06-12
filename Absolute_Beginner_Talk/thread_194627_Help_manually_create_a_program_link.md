---
title: "Help manually create a program link"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by domino on 2006-06-11
I use Paralells and I need to manually create a link that as of now can only start in terminal. Can someone help me with creating a new link on the desktop or better yet in the Application menu under System Tools?

This is the command: XLIB_SKIP_ARGB_VISUALS=1 parallels

thank you

---

### Post by bruce89 on 2006-06-11
You just right click on the Applications menu, and select _E_dit Menus.

---

### Post by domino on 2006-06-11
Ya, I tried that already and with no luck. The original enrty was * /usr/bin/parallels* and I changed it to *XLIB_SKIP_ARGB_VISUALS=1 parallels* and *XLIB_SKIP_ARGB_VISUALS=1 /usr/bin/parallels*. Got this error:

> Could not launch menu item

Details: Failed to execute child process "XLIB_SKIP_ARGB_VISUALS=1" (No such file or directory)

---

### Post by dcstar on 2006-06-12
[QUOTE=domino]Ya, I tried that already and with no luck. The original enrty was * /usr/bin/parallels* and I changed it to *XLIB_SKIP_ARGB_VISUALS=1 parallels* and *XLIB_SKIP_ARGB_VISUALS=1 /usr/bin/parallels*. Got this error:[/QUOTE]
You probably need to create an **executable** file with the following:
```
#! /bin/sh

XLIB_SKIP_ARGB_VISUALS=1 /usr/bin/parallels
```
and then make the launcher use the filename of the above code.

---

### Post by domino on 2006-06-12
Thanks David. All I needed was a jumpstart to jar my brain a little. There was already a parallels executable in the /usr/bin dir and edited it by adding the *XLIB_SKIP_ARGB_VISUALS=1* in front of the *run= line*. For furure reference:

```
#!/bin/sh

run="XLIB_SKIP_ARGB_VISUALS=1 /usr/lib/parallels/parallels-linux $@"

if [ -e "/etc/linspire-version" ]; then
    aw=`which audiowrapper 2> /dev/null`
    if [ "$aw" -a -x "$aw" -a "`$aw 2> /dev/null | grep -c oss-native`" != 0 ]; then
        run="sh $aw --oss-native $run"
    fi
fi

eval $run
```

---

