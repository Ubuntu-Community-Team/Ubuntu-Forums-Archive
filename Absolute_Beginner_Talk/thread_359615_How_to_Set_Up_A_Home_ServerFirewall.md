---
title: "How to Set Up A Home Server/Firewall"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by blake1 on 2007-02-12
How can I set a home file server and firewall for use in a mostly windows network with ubuntu? (I already have a windows network, do I need Samba or something?)

---

### Post by shoaibi on 2007-02-12
yes for file server you do need Samba to share your files on network, and for firewall have you tried installing FireStarter?

---

### Post by blake1 on 2007-02-12
Can you use firestarter and samba from the terminal, cos I was hoping to be GUI-free?

---

### Post by apollo13 on 2007-02-12
No, there is no way running without gui, cause Firestarter is just a gui for iptables...

---

### Post by shoaibi on 2007-02-12
Nope, i would agree with apollo13.
If you want a CLI based Firewall, i would have to excuse...

---

### Post by apollo13 on 2007-02-12
I ran aptitude search firewall and ferm came up. Haven't tested it yet, but it could suit your needs: [http://ferm.foo-projects.org/](http://ferm.foo-projects.org/)

---

