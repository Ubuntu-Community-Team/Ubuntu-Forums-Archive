---
title: "XDCMP keymap"
date: 2008-02-05
forum: Apple Intel Users
---

### Post by sunstriker on 2008-02-05
Hi,
I'm trying to connect to my Ubuntu box via 'ssh -X -query <ip>', 'Xnest :1 -query localhost' (on the server) and XDMCP. It all works but I have one big problem: my keyboard layout gets messed up (numbers on letters, a comma on backspace, a 'b' on tab and so on) whenever I launch an X program or session. I looked everywhere for solution but nothing seems to work. I've tried making a new xmodmap on the server, on my mac and locally (in front of) the server and tried to use it. But the keys stay messed up. It looks that when I start a gnome program or when I try to log in with Xnest (running on the server) the keys get messed up.
Another question: I think that runing Xnest through a ssh session is the most secure way (compared to just use XDMCP). Am I right?

Thanks in advance!

---

### Post by sunstriker on 2008-02-09
Reinstalling Leopard solved the problem. I needed to reinstall anyway for various reasons

---

