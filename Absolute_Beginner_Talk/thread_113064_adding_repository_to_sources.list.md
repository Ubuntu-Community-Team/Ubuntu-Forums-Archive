---
title: "adding repository to sources.list"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by NiTsi on 2006-01-05
can someone help and tell me how can i add repository : packages.ubuntu.com/hoary-backports   to my sources.list?    :confused:

---

### Post by byen on 2006-01-05
the command you want to type in the terminal would be 
sudo gedit /etc/apt/sources.list

---

### Post by kingsidy on 2006-01-05
or in synaptic, click on the repositories menu and click on add repository. then paste the address you want to add and click on OK. then reload and you're good to go.

---

### Post by NiTsi on 2006-01-05
i know that i must go to/etc/apt/sources.list and i know that i must write the address but when i write : deb http//packages.ubuntu.com/hoary-backports i get a message 

Failed to fetch [http://packages.ubuntu.com/hoary-backports/dists/main/uinerse/binary-i386/Packages.gz](http://packages.ubuntu.com/hoary-backports/dists/main/uinerse/binary-i386/Packages.gz)  404 Not Found
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by NiTsi on 2006-01-05
[QUOTE=byen]the command you want to type in the terminal would be 
sudo gedit /etc/apt/sources.list[/QUOTE]


know that i must go to/etc/apt/sources.list and i know that i must write the address but when i write : deb http//packages.ubuntu.com/hoary-backports i get a message

Failed to fetch [http://packages.ubuntu.com/hoary-bac...86/Packages.gz](http://packages.ubuntu.com/hoary-bac...86/Packages.gz) 404 Not Found
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by bored2k on 2006-01-05
[QUOTE=NiTsi]know that i must go to/etc/apt/sources.list and i know that i must write the address but when i write : deb http//packages.ubuntu.com/hoary-backports i get a message

Failed to fetch [http://packages.ubuntu.com/hoary-bac...86/Packages.gz](http://packages.ubuntu.com/hoary-bac...86/Packages.gz) 404 Not Found
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/QUOTE]
You need to **manually** right click on the link and select COPY. Notice how that link you posted has "..." in it. That shouldnt happen. Apparently you just highlighted and copied that from somewhere here. Here, grab mine: [http://www.rafb.net/paste/results/IunYSC25.html](http://www.rafb.net/paste/results/IunYSC25.html)

```
sudo apt-get update
```

---

### Post by NiTsi on 2006-01-05
[QUOTE=bored2k]You need to **manually** right click on the link and select COPY. Notice how that link you posted has "..." in it. That shouldnt happen. Apparently you just highlighted and copied that from somewhere here. Here, grab mine: [http://www.rafb.net/paste/results/IunYSC25.html](http://www.rafb.net/paste/results/IunYSC25.html)

```
sudo apt-get update
```[/QUOTE]




thanks i'll try it bored2k, i hope i manage it

---

### Post by aysiu on 2006-01-05
You could see the first link of my sig for detailed instructions.

---

### Post by patrick295767 on 2006-01-06
[QUOTE=NiTsi]know that i must go to/etc/apt/sources.list and i know that i must write the address but when i write : deb http//packages.ubuntu.com/hoary-backports i get a message

Failed to fetch [http://packages.ubuntu.com/hoary-bac...86/Packages.gz](http://packages.ubuntu.com/hoary-bac...86/Packages.gz) 404 Not Found
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/QUOTE]
  
this lock is of course there cos of this :
synaptic is already running ... 
  
Or in an xterm you are having a apt-get already running (process)
  
Do :
```
ps -A
```
  
And ```
kill -9 process_number
```
to all processes synaptic & apt-get
 
then:
```
[CODE]xterm
apt-get -f install program
```[/CODE]

---

