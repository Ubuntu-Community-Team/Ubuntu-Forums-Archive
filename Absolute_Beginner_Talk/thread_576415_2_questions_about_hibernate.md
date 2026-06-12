---
title: "2 questions about hibernate"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Martje_001 on 2007-10-15
Hi,
I've got 2 questions:

1. If I hibernate and I turn it back on, there's no network connection. If I reconnect however, there is.. How do I automatically reconnect after hibernate?

2. Can I remove the password being asked after a hibernate?

---

### Post by haldean on 2007-10-15
Hi!

1: I don't have that problem when I hibernate... do you use wireless or a wired connection?

2: Not that I know of :(

---

### Post by LowSky on 2007-10-15
> **Martje_001 said:**
> Hi,
I've got 2 questions:

1. If I hibernate and I turn it back on, there's no network connection. If I reconnect however, there is.. How do I automatically reconnect after hibernate?
reconnect or restart? I'm confused? Is it wireless?

2. Can I remove the password being asked after a hibernate?[/QUOTE]

Do you have automatic login enabled?

Try that

---

### Post by Martje_001 on 2007-10-15
1. I'm using a wired connection. When I deactivate and activate the network via the network-applet it works.

2. :(

---

### Post by haldean on 2007-10-16
@LowSky: I don't think that autologin makes a difference. I have autologin on mine and I still have to put in my password when I un-hibernate or un-suspend :(

and @Martje: What version of Ubuntu are you using / what kernel?

---

### Post by az on 2007-10-16
Your networking problems are a bug.

You can set the lock setting using gconf-editor.

Run gconf-editor from the terminal and select 

apps/gnome-power-manager 

and you should find the lock on hibernate key.

---

### Post by Martje_001 on 2007-10-16
Ubuntu 7.10. Don't know which kernel :oops:

---

