---
title: "KDE Install"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by flaak_monkey on 2006-05-16
Since nobody saw my post in one similar to this. I will make a topic, cause i need answers. :confused: 

Anyways, total n00b question, how do you install programs on Kbuntu?

---

### Post by dmizer on 2006-05-16
[QUOTE=flaak_monkey]Since nobody saw my post in one similar to this.[/QUOTE]
i saw it ... but it's better that you started your own thread.

edit ... whoops

what programs specifically are you trying to install?  it's easier with an example.

---

### Post by Sutekh on 2006-05-16
You can use Synaptic, just like in GNOME, or Adept, which is a similar package manager

---

### Post by flaak_monkey on 2006-05-16
where are they located though?

---

### Post by aysiu on 2006-05-16
Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

For graphical installation, you can use Adept, but Adept is a crippled package manager. It's much better to use Synaptic.

---

### Post by flaak_monkey on 2006-05-16
ok, so what is a terminal? is it the "RUN Command"?

---

### Post by aysiu on 2006-05-16
[QUOTE=flaak_monkey]ok, so what is a terminal? is it the "RUN Command"?[/QUOTE] Well, my signature tells you where the terminal is, but the *run* dialogue box is also a terminal of sorts. The only limitation being that the *run* dialogue can run only one command. In the terminal you can type a whole sequence and see the output of those commands.

---

### Post by flaak_monkey on 2006-05-16
oh, ok. thx. :P

---

### Post by flaak_monkey on 2006-05-16
So one more thing. I just downloaded limewire. how would i execute that to install?

---

### Post by aysiu on 2006-05-16
[QUOTE=flaak_monkey]So one more thing. I just downloaded limewire. how would i execute that to install?[/QUOTE] Maybe this will help?
[http://doc.gwos.org/index.php/Special:Search?search=limewire&go=Go](http://doc.gwos.org/index.php/Special:Search?search=limewire&go=Go)

---

### Post by flaak_monkey on 2006-05-17
OK, but that is about the same as the thread i saw on Aoutmatix. Which told me absolutely nothing on how to run/install it. (because the link that it does give, is non-existent)

---

### Post by aysiu on 2006-05-17
Sorry. I don't really use Limewire or any of those P2P programs. Someone else will probably know about it, though.

---

### Post by Perfect Storm on 2006-05-17
Limewire:

Download the Linux .rpm version - [http://www.limewire.com/english/content/downloadfree2.shtml](http://www.limewire.com/english/content/downloadfree2.shtml)
and save it to Desktop.
Also make sure you have Sun Java version 1.5 installed.

```
cd Desktop
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install alien
sudo alien -i XXXXXXXXX.rpm

```
*[size=1]XXXXX =name of the package*[/size]

---

