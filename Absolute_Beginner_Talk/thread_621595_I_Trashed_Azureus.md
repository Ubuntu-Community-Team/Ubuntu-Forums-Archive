---
title: "I Trashed Azureus"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by ah pook on 2007-11-23
tried to upgrade, and nothing worked. now Nothing runs, I've got torrents 98% done, and nothing runs. anyone have any ideas? I uninstalled and re-installed azureus, but nothing works....HELP!

---

### Post by PmDematagoda on 2007-11-23
If you tried to upgrade the OS, could you tell us exactly what went wrong? And did you try another torrent client such as Deluge or Ktorrent?

---

### Post by ah pook on 2007-11-23
no, no. i kept getting an upgrade script window from azureus, it said either upgrade a file in \opt\azureus\something or to upgrade to Vuze entirely. I tried that, and now nothing works. I can't even get Deluge working....grrrr.

---

### Post by Sarteck on 2007-11-23
If you re-install azureus after completely removing it, maybe that will work for you?  Your torrents will still be at 98% after they are checked by azureus when you restart it.

---

### Post by ah pook on 2007-11-23
ok,l let me try that.. thanks so much......

---

### Post by Sarteck on 2007-11-23
No problem.  Remember to save your torrents, if you can't remember where you downloaded them from, so that you can re-start them.

---

### Post by ah pook on 2007-11-23
Weird. Azureus still shows up in App>Internet>azureus, plus i deleted the directory, and if I re install it there's nothing there.. hmmm.and Add/Remove programs shows it's still there. i'm very confused..

---

### Post by Sarteck on 2007-11-23
Try to ```
sudo apt-get remove --purge azureus
``` in order to remove it.

To install, follow this thread for guidance: [http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)

EDIT: Note that you might have to change the following line: **sudo tar jxvf Azureus_3_0_linux.tar.bz2 -C /opt/** to whatever filename it is that you download.

---

### Post by jpkotta on 2007-11-24
I just installed an update of azureus from gutsy-updates.  I had previously installed whatever azureus comes with gutsy and copied the Azureus2.jar from the latest tarball.  The problem was that even though I had set sun-java-6 as my JRE, it was using icedtea-java-7.  If I explictly set the AZUREUS_JAVA environment variable to Sun Java 6, it worked again.  I don't know what Icedtea Java is or why I have it, so I removed it and nothing else has broken so far (but Azureus is the only thing that uses 64-bt java on my machine).

Simple workaround:
```
AZUREUS_JAVA=/usr/lib/jvm/java-6-sun/jre/bin/java azureus
```

---

### Post by jpkotta on 2007-11-24
OK, I see why it was not using my java alternative.  The wrapper script explicitly prefers java-7-icedtea, even though it doesn't work.  WTF.  You could just edit /usr/bin/azureus instead of setting an environment variable.

```
#!/bin/sh
if [ x$AZUREUS_JAVA = x ]; then
   echo "Looking for and picking a preferred Java runtime"
   echo "Use environment AZUREUS_JAVA to override"
#   if [ -f /usr/lib/jvm/java-7-icedtea/jre/bin/java ]; then
#      JAVA='/usr/lib/jvm/java-7-icedtea/jre/bin/java'
#   elif [ -f /usr/lib/jvm/java-6-sun/jre/bin/java ]; then
#      JAVA='/usr/lib/jvm/java-6-sun/jre/bin/java'
#   elif [ -f /usr/lib/jvm/java-1.5.0-sun/jre/bin/java ]; then
#      JAVA='/usr/lib/jvm/java-1.5.0-sun/jre/bin/java'
#   else
      echo '******** WARNING **********'
      echo 'Unable to find a supported Java runtime'
      echo 'Going to assume java is in your PATH'
      echo '****************************'
      JAVA='java'
#   fi
else
   # User explicitly set an AZUREUS_JAVA; let's use it!
   echo "Java Runtime specified using AZUREUS_JAVA environment"
   JAVA=$AZUREUS_JAVA
fi
echo "Using Java: $JAVA"
SWT=/usr/lib/java/swt.jar
```

---

### Post by jpkotta on 2007-11-24
This is a known bug: [https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/157162](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/157162)

---

