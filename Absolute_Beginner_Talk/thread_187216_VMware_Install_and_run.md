---
title: "VMware Install and run"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by KaMZaTa on 2006-06-02
I downloaded VMware Player from official website and I converted the .rpm file to .deb. After this I try to run vmware by consolle typing wmplayer but I recived follow error:

> 
root@notebook:/home/kamzata/Desktop# vmplayer
/usr/bin/vmplayer: line 85: /etc/vmware/locations: Nessun file o directory
/usr/bin/vmplayer: line 177: /lib/wrapper-gtk24.sh: Nessun file o directory
/usr/bin/vmplayer: line 177: exec: /lib/wrapper-gtk24.sh: impossibile eseguire: Nessun file o directory
root@notebook:/home/kamzata/Desktop#


---

### Post by KaMZaTa on 2006-06-02
does anybody can help me?

---

### Post by KaMZaTa on 2006-06-03
up

---

### Post by jon_gunnar on 2006-06-03
[QUOTE=KaMZaTa]I downloaded VMware Player from official website and I converted the .rpm file to .deb. After this I try to run vmware by consolle typing wmplayer but I recived follow error:[/QUOTE]

Dont understand the language,may be that some files is missing?
Why dont use the tar download instead of converting with alien,and why run it as root?

---

### Post by imagine on 2006-06-03
Why don't you just install VMware-Player from the repositories?
```
sudo apt-get install vmware-player
```

---

### Post by KaMZaTa on 2006-06-03
What's the exactly procedure to run Windows Xp with VMware on Linux? How can install VMware? Tnks

---

### Post by KaMZaTa on 2006-06-03
[QUOTE=imagine]Why don't you just install VMware-Player from the repositories?
```
sudo apt-get install vmware-player
```[/QUOTE]

Because I don't know the repository where I can find VMware. I've already try to search it with Synaptic but nothing to do.

---

### Post by KaMZaTa on 2006-06-03
Ok now I've installed VMware Workstation by repository and I've create a Virtual Machine "Windows Xp" but when I try to start the virtual machine I recive this errors:

[IMG]http://img145.imageshack.us/img145/9559/schermataerror3dj.png[/IMG]

[IMG]http://img145.imageshack.us/img145/4377/schermataerror15wh.png[/IMG]

How can I do? Tnks for support :o

---

### Post by mrtisoy on 2006-06-04
Did you install Workstation or Player?

What repository did you use?

Have you run the vmware config script yet?

---

