---
title: "Shared Folders On Wireless Network"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-28
I am on a wireless network at home. My dad's PC is on the same network (he runs windows) and he has shared folders on his pc that i'd like to view from my computer.. Is it possible to view these on my pc from his?

---

### Post by jhnthn on 2007-12-29
In Nautilus go to Go > Network > Windows Network.

---

### Post by jordank on 2007-12-29
How do i get to nautilus and what does it do?

---

### Post by reverseninja on 2007-12-29
First, lets confirm which version of ubuntu your using.  Then I think I can explain the solution to you well enough.

---

### Post by chewearn on 2007-12-29
> **jordank said:**
> How do i get to nautilus and what does it do?

In your desktop (I assumed its gnome desktop), click on:
Top panel menu "Places" > Network

A window will appear, where you should be able to navigate around to find your dad's PC.

---

### Post by jordank on 2007-12-29
gutsy

---

### Post by reverseninja on 2007-12-29
Okay!  I would follow the advice in the post just above your last.  Also, make sure the folders on the windows machine are shared and ready to go and they should show up no problem.  Alternatively, you could go to system > administration > shared folders to add them there.

---

### Post by thamood on 2007-12-29
> **jordank said:**
> I am on a wireless network at home. My dad's PC is on the same network (he runs windows) and he has shared folders on his pc that i'd like to view from my computer.. Is it possible to view these on my pc from his?

[SIZE="5"][1] you have to install samba first
you can do this through synapatic package manager. look for samba.
after that you should be able to open shared folders in windows pc's and you can share some folders with them too....good luck[/SIZE]

---

