---
title: "No Internet connection when I use wired connection"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-08
I'm getting no connection when i'm connecting a wired internet connection to my computer, what can I do about this ?

---

### Post by czepluch on 2007-07-08
bump

---

### Post by oilchangeguy on 2007-07-08
> **czepluch said:**
> I'm getting no connection when i'm connecting a wired internet connection to my computer, what can I do about this ?

how 'bout some more details. are you using a cable or dsl modem? are you using a router? don't post a question with little or no details and expect an answer.

---

### Post by czepluch on 2007-07-08
> **oilchangeguy said:**
> how 'bout some more details. are you using a cable or dsl modem? are you using a router? don't post a question with little or no details and expect an answer.

I'm using a router and i dont know if there is anymore useable details?

---

### Post by oilchangeguy on 2007-07-08
> **czepluch said:**
> I'm using a router and i dont know if there is anymore useable details?

ok, you've got 83 beans. so you're not a newbie. what have you done recently to make any changes, that have stoped you from being able to get on the internet. how are you on the internet now?

---

### Post by czepluch on 2007-07-08
> **oilchangeguy said:**
> ok, you've got 83 beans. so you're not a newbie. what have you done recently to make any changes, that have stoped you from being able to get on the internet. how are you on the internet now?

I'm not at home. I'm visiting a friend and here i can use the cables from the router for my laptop. I'm using his PC right now and his works fine with the internet from the cable from the router. That is why i simply dont understand why i cant get a connection?

---

### Post by oilchangeguy on 2007-07-08
the router should generate it's own ip address. but it may not. so try resetting it (kill the power). and see what happens.

---

### Post by czepluch on 2007-07-08
> **oilchangeguy said:**
> the router should generate it's own ip address. but it may not. so try resetting it (kill the power). and see what happens.

Are you sure it will not mess up anything after the reset for the other computers on the network?

---

### Post by oilchangeguy on 2007-07-08
don't see why it would. what happens if a storm kills the power? also try connecting directly to the modem, you will have to perform a reset for this to work.

---

### Post by czepluch on 2007-07-08
> **oilchangeguy said:**
> don't see why it would. what happens if a storm kills the power? also try connecting directly to the modem, you will have to perform a reset for this to work.

Tried but still doesn't work

---

### Post by oilchangeguy on 2007-07-08
> **czepluch said:**
> Tried but still doesn't work

open the network manager and make sure it's set to eth0, and not something else.

---

### Post by Old Pink on 2007-07-08
Run **gksudo network-admin** and make sure Wired Connection is ticked (active) and set to auto configure, or use the correct information from your ISP. :)

---

### Post by czepluch on 2007-07-08
> **oilchangeguy said:**
> open the network manager and make sure it's set to eth0, and not something else.

What driver is reqruired?

---

### Post by oilchangeguy on 2007-07-08
> **czepluch said:**
> What driver is reqruired?

driver for what? is there not a two screened icon somewhere to the left of the clock?

---

### Post by czepluch on 2007-07-08
> **Old Pink said:**
> Run **gksudo network-admin** and make sure Wired Connection is ticked (active) and set to auto configure, or use the correct information from your ISP. :)

Still doesn't work

---

### Post by czepluch on 2007-07-08
When my friend opens the network-manager it says taht his driver is tg3, but mine says: 8139too, does that make a difference?

---

