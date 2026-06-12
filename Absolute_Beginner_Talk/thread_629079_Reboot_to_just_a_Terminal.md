---
title: "Reboot to just a Terminal"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Fred_E _krugar on 2007-12-01
I just want to be able to boot and use just the terminal. No Xserver running.

 How would I go about doing that??

---

### Post by Kingsley on 2007-12-02
Remove GDM.
```
sudo update-rc.d -f gdm remove
```

Bring back GDM.
```
sudo update-rc.d gdm defaults
```

---

### Post by Fred_E _krugar on 2007-12-02
That didnt do what I wanted it to do. I am trying to install the Nvidia drivers manually because I am trying to get my SLI working.
 
But every time I try it it tells me I have X running. hmmm

---

### Post by Partyboi2 on 2007-12-02
you could try going to a terminal and typing:
```
sudo killall Xorg
```

---

### Post by PmDematagoda on 2007-12-02
Do:-

```
sudo /etc/init.d/gdm stop
```

After you install the driver do:-

```
sudo /etc/init.d/gdm start
```

---

### Post by Fred_E _krugar on 2007-12-02
Thanks Guys PM yours worked but after all that the problem persists with my SLI problem.

---

