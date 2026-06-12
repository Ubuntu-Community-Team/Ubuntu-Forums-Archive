---
title: "Trouble with firefox"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Hickler on 2007-07-06
A similar problem has already been posted but it was a tad confusing and I was hoping everything would be more clear. Also, I am using he Wubi version of Ubuntu so I don't know if that makes a difference. Anyways, After all the initial system upgrades, I tried opening firefox, and nothing. Then I saw in the top right corner I had to reboot, so, thinking this would solve my problem, I did. But firefox still doesn't work, It just shows the "starting firefox browser" or something like that at the bottom of the screen. Please help.

---

### Post by felicity on 2007-07-06
Did you try opening firefox from the command line? It may display some error messages that would help.

---

### Post by starcraft.man on 2007-07-06
> **felicity said:**
> Did you try opening firefox from the command line? It may display some error messages that would help.

Yup, thats a good idea. Just open any terminal and type "firefox" to open it. If it says something post it here. In the off chance somethings gone wrong with firefox (somehow you corrupted the install or something), you can just reinstall it to get it working again.

```
sudo aptitude reinstall firefox
```

Oh and no, to my knowledge Wubi doesn't make a difference for firefox.

---

### Post by sra136 on 2007-07-07
I have the same problem.  It was working perfectly until I removed some package cleaning.  However, when I type firefox from terminal, I get this:

/opt/firefox/firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

Any suggestions.

---

### Post by eternalsword on 2007-07-07
sra136, looks like you've installed the mozilla version of firefox as opposed to the ubuntu version of firefox.  Try this, alt+f2 and enter in ```
gksu gedit /usr/bin/firefox2
```

in gedit, paste in
```

#!/bin/sh

export MOZILLA_FIVE_HOME="/opt/firefox/"

url="$1"
if [ "x$url" = "x" ]; then
  url="about:blank"
fi

if $MOZILLA_FIVE_HOME/mozilla-xremote-client openURL\("$url"\); then
  exit 0
fi
exec $MOZILLA_FIVE_HOME/firefox "$url"

```
save and close it, then alt+f2 and the command ```
gksu chmod +x /usr/bin/firefox2
```

now instead of running /opt/firefox/firefox, run firefox2

---

