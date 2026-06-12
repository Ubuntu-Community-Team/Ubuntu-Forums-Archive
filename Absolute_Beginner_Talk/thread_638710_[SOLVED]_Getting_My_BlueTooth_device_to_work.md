---
title: "[SOLVED] Getting My BlueTooth device to work"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-12-12
Hi...... I have a Kensington BlueTooth Dongle (Model: 33085)
and a Plantronics Voyager 510 Headset that I am trying to
pair up and get to work on Ubuntu 7.10

I have open the BlueTooth Analyzer from the Accessories Menu
and choose Browse Device. I put my Voyager in " Find Me Mode "
and the Kensington finds the Voyager headset.  Well when I choose
the connect button, I get this message.

"obex://[00:03:89:5a:16:58]" is not a valid location.

Anyone know how to fix this?

---

### Post by linuxwizard on 2007-12-12
Look at the bottom of this page for Troubleshooting

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by pete on 2007-12-12
I've had good luck getting the same Bluetooth dongle to connect to a set of Motorola headphones (HT820) using hcitool in Terminal:

1. Put headphones in pairing mode
2. "hcitool scan" (this should return the hardware address of your headphones)
3. "sudo hcitool cc [hardware address]"

Headphones should then show up as connected in the Bluetooth Manager.

---

### Post by Orbital75 on 2007-12-12
Thanks....... I'll give that a try.
I'm not to good with the command line though is there
a gui that would be better suited for someone like me.

---

### Post by linuxwizard on 2007-12-12
Open a terminal > copy this line > sudo apt-get install gnome-vfs-obexftp > (same line from link) > paste into terminal > press enter > will ask for password > enter password > press enter > than just follow along what it is doing in the terminal > make sure no error messages should not be any

---

### Post by Orbital75 on 2007-12-12
Thank you, I'll give it a try.....
Just to know what to expect, will this install a Gui program
or is this just the command line thing you were talking about.

---

### Post by A$h X on 2007-12-12
Try this thread, it contains all the instructions to get you up and running.

[http://ubuntuforums.org/showthread.php?t=531753](http://ubuntuforums.org/showthread.php?t=531753)

---

### Post by linuxwizard on 2007-12-12
Orbital75
You are making this harder than it is. Open Synaptic search for:: >gnome-vfs-obexftp   >install it

---

### Post by Orbital75 on 2007-12-13
Thank you the ( gnome-vfs-obexftp ) did the trick.
Haven't tried it with my phone yet but it enabled my
Plantronics Bluetooth headset and my Ubuntu to pair.
I'm sure that it will work with the Phone as well.  :KS

You guys are great.

---

### Post by linuxwizard on 2007-12-13
You're Welcome. Glad to hear you got it installed and it worked for you. Please mark thread solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

