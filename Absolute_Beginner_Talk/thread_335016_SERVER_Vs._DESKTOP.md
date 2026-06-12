---
title: "SERVER Vs. DESKTOP??????"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Hamm on 2007-01-09
I know this has been asked before, but it is my turn to ask. I have 2 desktops running now (for my school aged sons) and I would like to do a file server. I also would like to do other things too. The with no GUI scares me on the sever.... can I live in two worlds?... 

On the machine that I have for the server, has 2 80g HD, P4 2.53mhz, with 1g RAM. I should do well with it, but I only want to set it up once. Any suggestion? :-k  (I ask knowing that I will get a few)

Hamm

---

### Post by mcduck on 2007-01-09
There's no reason why you couldn't have desktop on your server. And if you want to avoid command line as much as possible, do a desktop install first and the just install the server packages you want.

---

### Post by jvc26 on 2007-01-09
You can always install a desktop environment -
```

sudo apt-get install xubuntu-desktop

```
If I remember rightly would enable you to have a GUI to use, and that would take out some of the daunting prospect of a terminal only setup
Il

---

### Post by bodhi.zazen on 2007-01-09
Her is a nice link on file sharing (NFS)

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by Modernity on 2007-01-09
> **mcduck said:**
> There's no reason why you couldn't have desktop on your server. And if you want to avoid command line as much as possible, do a desktop install first and the just install the server packages you want.

For new users of Linux, I think the majority of us will tell you to install the Desktop version and then install what you need. If you haven't already downloaded a version yet, stick with the 6.06 version (Dapper Drake). Download the ISO and install. Since you are a newcomer to Linux, it will be easier for you to use a GUI (so you can visualy see what you are doing), stick with the desktop version and not the server edition. After install you will be able to add the packages you want to run your server, without feeling lost in a text prompt.

---

### Post by Hamm on 2007-01-09
The two desktops I have running are on 6.10 a Christian Edition. The CE had a great web filters i.e. "Net Nanny" type, right out of the box. 5th and 6th grade boys I need that kind of piece of mind. Now, on the third machine do I install 6.06 desktop then L.A.M.P. from the 6.06 server iso? 

-=Hamm=-

---

### Post by Modernity on 2007-01-09
> **Hamm said:**
> The two desktops I have running are on 6.10 a Christian Edition. The CE had a great web filters i.e. "Net Nanny" type, right out of the box. 5th and 6th grade boys I need that kind of piece of mind. Now, on the third machine do I install 6.06 desktop then L.A.M.P. from the 6.06 server iso? 

-=Hamm=-

Just my opinion, I would install 6.06, get it up and running and then use the Synaptic (ADD/REMOVE) to do it for you.

---

### Post by Hamm on 2007-01-09
> **Modernity said:**
> Just my opinion, I would install 6.06, get it up and running and then use the Synaptic (ADD/REMOVE) to do it for you.


Desktop or the server?????

---

### Post by jeffathehutt on 2007-01-09
I think the easiest route is to install the desktop edition, then manually add the server software you need from synaptic.  That way you get a GUI and can still install the servers that you require.

---

### Post by lukemack on 2007-01-14
Is there a way of adding a GUI to the server install?

---

### Post by mcduck on 2007-01-14
> **lukemack said:**
> Is there a way of adding a GUI to the server install?

'sudo apt-get install ubuntu-desktop' (or kubuntu-desktop or xubuntu-desktop). Or then you can just install packages you want yourself. All ubuntu variants use same repositories, so there's no difference in programs you can install.

---

### Post by lukemack on 2007-01-14
thanks - i've done this. its now downloading and installing everything. presumably i can remove packages that I don't need afterwards?

---

### Post by bodhi.zazen on 2007-01-14
Yep ....

---

### Post by lukemack on 2007-01-14
ok - i have installed and rebooted. no gui is loaded and neither startx or sudo /etc/init.d/gdm start works.

am i missing something?

---

### Post by lukemack on 2007-01-15
i ran the apt-get install command again and this worked. it seems the packages were downloaded but not installed the first time around.

---

### Post by riven0 on 2007-01-15
What I recommend is to first get a little familiar with the terminal - check out some good sites like linuxcommand.org - then get rid of the GUI. You'll find the terminal is surprising easy to learn, and after a month or two, you'll find you won't even need it anymore. 

Take it from me, the ultimate Linux newb! :mrgreen:

---

