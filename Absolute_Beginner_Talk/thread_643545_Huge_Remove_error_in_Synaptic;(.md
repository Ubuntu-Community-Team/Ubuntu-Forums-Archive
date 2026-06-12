---
title: "Huge Remove error in Synaptic;("
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by RustyWyatt on 2007-12-17
Hi Folks,

Well I have just made a major newbee error!  Until today, I have been a VERY happy 7.10 user on my T60 laptop. So, today I spent all day trying to play a movie DVD on the T60...

Finally, I decided that a day of following lots of command line instructions that I did not understand may have lead to a completely confused system. And, I still could not play a movie DVD.

So, I  used Synaptic to remove all of what I thought were the multi-media files and start over from scratch...

I have now discovered that I have removed everything from Open Office to VirtualBox to "Add/Remove" from my menu to who knows what else.

I am afraid to reboot because I may have really killed my system;(

Is there anyway I can restore my system?

All comments GREATLY appreciated!!

Tom

---

### Post by nitro_n2o on 2007-12-17
You can just reinstall the stuff you removed using Synaptic and everything will be fine again. To know exactly what did you remove you should look in the Synaptic log. It must have a log somewhere, but sorry i don't know where exactly, but you can check their website. 

if you really don't know what did you remove and you have no idea on how to bring it back... then reinstall ubuntu again. This would be the safest option.. 

And don't reboot, it is not a good idea now 

Good luck :)

---

### Post by santaslittlehelper on 2007-12-17
In synaptic go to "File > History" to view the log.

Also -
```
sudo cat /var/log/apt/term.log > logfile
```
- Should place a text file in you're home folder with the apt log, might make things easier.

The last suggestion I got I am not to sure about so wait until someone says you could give it a go.
But you can try to run it with the "-s" switch (--simulate) and see what it suggests. 

```
sudo aptitude -s reinstall --purge ubuntu-desktop
```

---

### Post by sports fan Matt on 2007-12-17
When ive carelessly uninstallled things in the past and realized it, sometimes (unless im wrong) culdnt u use under "synmaptic* the reduial config area ( left bottom, if it displays and it would be able to be marked for reinstallation?

---

