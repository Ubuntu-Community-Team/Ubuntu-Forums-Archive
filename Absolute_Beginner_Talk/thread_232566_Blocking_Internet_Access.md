---
title: "Blocking Internet Access"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by flycast on 2006-08-08
I am experimenting with a PC box as a backup/apache/mysql/file server. We use internet filters to prevent certain trash from reaching our and our childrens eyes. The filter is a XP filter installed on each XP machine.

Is there a way that I can securly block the Ubuntu box form accessing http to the internet but still allow network communications between it and the other PC;'s and Mac on my network?

I have already checked and found that my gateway does not support this kind of block.

---

### Post by jms1989 on 2006-08-08
Try "Firestarter" it's a firewall that can block incoming and probaly outgoing connections.

```
sudo apt-get install firestarter
```

You can also use Synaptic Package Manager and search for "firestarter".

---

### Post by robins_web on 2006-08-09
Firestarter is installed as part of Ubuntu/Kubuntu, and runs automagically when you boot. The Firestarter you can get via synaptic or adept is actually the GUI program you can use to *configure* the firewall, which for a lot of folks--myself included--is a lot easier and safer than manually editing the firewall ip config tables.

---

### Post by davebgimp on 2006-08-09
> **robins_web said:**
> Firestarter is installed as part of Ubuntu/Kubuntu, and runs automagically when you boot. The Firestarter you can get via synaptic or adept is actually the GUI program you can use to *configure* the firewall, which for a lot of folks--myself included--is a lot easier and safer than manually editing the firewall ip config tables.

Ubuntu as I understand does not by default come with Firestarter. Firestarter is a GUI that lets you manipulate iptables, which is default. You can use firestater, install it from synaptic...sure. Guarddog is another one in the repos that has a lot of preset one-click settings where you can easily turn off http and https protocols as well as others if you need.

---

### Post by flycast on 2006-08-09
> Guarddog is another one in the reposWhat is a repos?

---

### Post by skymt on 2006-08-09
> **flycast said:**
> What is a repos?

Ubuntu geek-speek for repositories. Those are the sites that Ubuntu knows how to automatically download software from. To get (for example) guarddog, open System > Administration > Synaptic Package Manager. Search for it, check the box next to it, and click Apply.

---

### Post by flycast on 2006-08-09
Firestarter and guarddog do not show up in the Synaptic package manager. When I tried apt-get neither package showed up either.

I do have shorewall available and iptables is already installed.

---

### Post by Linux4HumanBeings on 2006-08-10
Thanks Firestarter Worked for Me

---

