---
title: "Runlevel 3"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by tygr88 on 2007-10-07
i want to install an Nvidia driver but need runlevel 3....... but as soon as i type telinit 3 in recovery mode the gui starts which i do not want......i have tried /etc/init.d/gdm stop but that has not helped.

---

### Post by bodhi.zazen on 2007-10-07
Yea, in Ubuntu the run levels are all the same and they all have X ...

At any rate, you can do this from a regular boot.

Hit Ctrl-Alt-F1 or Ctrl-Alt-F2, log in ...

Then run :```
sudo /etc/init.d/gdm stop
```

Install the nvidia driver

Re-start X (GDM) with

```
sudo /etc/init.d/gdm start
```

Post if you have further questions.

---

### Post by Cannaregio on 2007-10-07
> **tygr88 said:**
> i want to install an Nvidia driver but need runlevel 3....... but as soon as i type telinit 3 in recovery mode the gui starts which i do not want......i have tried /etc/init.d/gdm stop but that has not helped.

If the previous suggestion by bodhi.zazen does not work (it happens that, because of a [old bug]("https://launchpad.net/ubuntu/+source/gdm/+bug/47320") you often cannot stop and start gdm effectively, and the nvidia driver still wont start), you can try a dirty and effective method: rename gdm!

```
sudo mv /etc/init.d/gdm /etc/init.d/gdmnope
```

then restart, install your driver, restart again, rename back [COLOR="Blue"]gdmnope[/COLOR] to [COLOR="#0000ff"]gdm[/COLOR] and you'r done
not elegant, but cuts the mustard :-)

---

