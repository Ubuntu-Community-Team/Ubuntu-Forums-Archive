---
title: "Run xkbset at login"
date: 2014-06-29
forum: Assistive Technology &amp; Accessibility
---

### Post by spacebar2020 on 2014-06-29
I use mouse keys but as its settings are too slow I have to run

xkbset ma 30 10 10 5 2 

in order to use it. 

In Ubuntu 14.04 how can I run that command at login?

I tried adding it to /etc/init.d/rc.local but it does not run the command as noted elsewhere (there is no "exit 0" in that file as referred to in some threads).

Then I created it as a bash script with .bash extension and added it as startup application. That did not work. Gedit is default app to open bash scripts. Should I specify some other command than   xkbset ma 30 10 10 5 2 in the start up dialogue to actually run that script?

Thanks

---

### Post by DaniPhii on 2014-06-29
Have you tried putting that command in Startup Applications? I mean, not making a .bash script, just putting that command in a new entry.

---

### Post by ajgreeny on 2014-06-29
Your script must be made executable before you can get it to work as a startup application. So if your script is called xkbset.sh and is in your home run command **chmod +x xkbset** to make it executable, then point to it with the full pathway in the startup list, ie **/home/spacebar2020/xkbset.sh**, assuming your username is spacebar2020.

---

### Post by spacebar2020 on 2014-07-02
> **ajgreeny said:**
> Your script must be made executable before you can get it to work as a startup application. So if your script is called xkbset.sh and is in your home run command **chmod +x xkbset** to make it executable, then point to it with the full pathway in the startup list, ie **/home/spacebar2020/xkbset.sh**, assuming your username is spacebar2020.
Thanks, making the script executable was what I was missing.

---

