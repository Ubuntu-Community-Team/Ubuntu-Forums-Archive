---
title: "how make executable &quot;shortcut&quot; on Desktop -- age 70 Dad needs easy"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2007-09-01
Hello !!

I have managed to install the game Freeciv on my Dad's Ubuntu.

It is properly installed in /usr/bin .  Actually, the executable script is in /usr/bin/freeciv-2.0.9

Question:  Right now, to start the game, he would have to hit
   ALT + F2 , then type "civ" (without quotes)
   in the GUI dialogue which appears, and then hit the GUI "Run" button.

And even after that, he is presented with four choices and another button click:
   Run in Command Line,  Display, Run etc.

I have included the script below for the "civ" executable.  

How can I alter the script, and/or just make a desktop icon for him so that when he doubleclicks on that icon, wham, the game starts right up?

Regarding the script below:  **Since my desire is to execute from a shortcut on the desktop, it's my understanding that the PATH variable below may need to be altered, but I don't know enough about how to do it correctly.**

THANKS a lot for any help!


-----

[PHP]
```


#!/bin/sh


BUILDDIR=`dirname $0`

# Use cd + pwd instead of manual concatentation in case of absolute paths
BUILDDATA=$(cd $BUILDDIR/data ; pwd)
SRCDATA=$(cd $BUILDDIR ; cd ./data ; pwd)

if [ "x$FREECIV_PATH" = "x" ] ; then
  FREECIV_PATH=".:data:~/.freeciv"
fi
export FREECIV_PATH="$FREECIV_PATH:$BUILDDATA:$SRCDATA"

[ -x $BUILDDIR/client/civclient ] && EXE=$BUILDDIR/client/civclient
[ -x $BUILDDIR/civclient ] && EXE=$BUILDDIR/civclient

if [ "$EXE" = "" ]; then
  echo $0: Unable to find civclient.
  exit 1
fi

exec $EXE ${1+"$@"}



```
[/PHP]

---

### Post by wormser on 2007-09-01
Right click on the desktop and Create Launcher.  You might need to use the full path.

---

### Post by Average_Joe on 2007-09-01
> **wormser said:**
> wormser wrote:

Right click on the desktop and Create Launcher.  You might need to use the full path.




Yes!  That worked nicely.  Thanks **_very much_** for your help! :guitar:

---

