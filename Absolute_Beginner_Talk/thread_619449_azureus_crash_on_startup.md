---
title: "azureus crash on startup"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Pevichaey5 on 2007-11-21
hi

a slight problem i'm having with azureus which is really annoying me now :(


azureus 2.5 even tried 3.0 but still fails, i have install sun java from their website and also using the other one java6 in synaptic manger but still fails


toby@ubuntu-154:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b7021e3ee11, pid=8858, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/toby/.azureus/hs_err_pid8858.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

so i checked the log but still can't seem to find out what the problem is

any help will be apprechiated

cheers

sorry log file too big to attach to this post :(

---

### Post by MegaJim on 2007-11-21
is that a custom JRE? You might have more luck with an official build

---

### Post by gezzabob on 2007-11-21
Yes I have problems with Azureus chrashing at start up as well.

I recently downloaded and installed Deluge Bittorrent from the add and remove what does anybody else think of Deluge?

---

### Post by hilfer on 2007-11-21
> **gezzabob said:**
> Yes I have problems with Azureus chrashing at start up as well.

I recently downloaded and installed Deluge Bittorrent from the add and remove what does anybody else think of Deluge?


Deluge is the best.

Azureus takes too much ram.

hilfer

---

### Post by AndyCooll on 2007-11-21
I followed these intructions (can't remember where I got them from):

Azureus version in the repositories is old and broken, but you can manually 'update' it to the latest and working version without having to manually create the shortcuts, configuring FireFox to work with it etc.

Here's how it can be done:

1) Install Azureus (and Java) through Add/Remove Applications or through apt-get:

sudo apt-get install azureus sun-java6-bin

2) Download the latest Azureus 3.0.3.0 from the Azureus website. (You can download the 2.5.0.4 version but it will force you to update to 3.0 anyway.)

3) Extract it to your home folder.

4) Open the terminal and type:

sudo cp /home/yourname/azureus/Azureus2.jar /usr/share/java/

This will overwrite the existing Azureus file with a new one.

5) The SWT library provided with the libswt3.2-gtk-java package is outdated which will prevent Azureus from updating itself so you will have to manually update SWT.

sudo cp ~/azureus/swt.jar /usr/lib/eclipse/plugins/org.eclipse.swt.gtk.linux *

6) Now try launching Azureus. If you get any errors while updating azureus, then launch Azureus using this command:

sudo azureus

After Azureus has updated, you may launch it normally.

7) If everything works all right, you may delete the azureus folder in your home folder. Have fun!

:cool:

---

### Post by dormant on 2007-11-21
Worked for me. 

Many thanks.

I plan to switch to deluge soon, but I just upgraded to Gutsy and had some torrents to finish.

---

### Post by gezzabob on 2007-11-27
> **AndyCooll said:**
> I followed these intructions (can't remember where I got them from):

Azureus version in the repositories is old and broken, but you can manually 'update' it to the latest and working version without having to manually create the shortcuts, configuring FireFox to work with it etc.

Here's how it can be done:

1) Install Azureus (and Java) through Add/Remove Applications or through apt-get:

sudo apt-get install azureus sun-java6-bin

2) Download the latest Azureus 3.0.3.0 from the Azureus website. (You can download the 2.5.0.4 version but it will force you to update to 3.0 anyway.)

3) Extract it to your home folder.

4) Open the terminal and type:

sudo cp /home/yourname/azureus/Azureus2.jar /usr/share/java/

This will overwrite the existing Azureus file with a new one.

5) The SWT library provided with the libswt3.2-gtk-java package is outdated which will prevent Azureus from updating itself so you will have to manually update SWT.

sudo cp ~/azureus/swt.jar /usr/lib/eclipse/plugins/org.eclipse.swt.gtk.linux *

6) Now try launching Azureus. If you get any errors while updating azureus, then launch Azureus using this command:

sudo azureus

After Azureus has updated, you may launch it normally.

7) If everything works all right, you may delete the azureus folder in your home folder. Have fun!

:cool:

Thanks for that AndyCooll, I will try that in a bit and let you know if it worked or not :) ...

---

### Post by mahiyar on 2007-11-27
Whenever I face such problem in Azureus (and it was previously working) I just delete the .azureus directory from my home and restart.

---

### Post by pommattski on 2007-11-30
> **mahiyar said:**
> Whenever I face such problem in Azureus (and it was previously working) I just delete the .azureus directory from my home and restart.
Thanks mahiyar.
I second that.

---

