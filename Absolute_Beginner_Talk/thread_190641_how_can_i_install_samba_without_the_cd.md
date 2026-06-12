---
title: "how can i install samba without the cd?"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by 00zero on 2006-06-06
how can i install samba with out the cd? i had to take appart a rack of servers to install from the cd and i dont want to do it again just to install samba.

thanks
Jonathan

---

### Post by someusernoob on 2006-06-06
sudo apt-get install samba

---

### Post by steve.horsley on 2006-06-06
Lol! Can't handle a screwdriver eh?

(Joking)

Open synaptic, choose Settings->Repositories, and un-check the CD in that list.

At least, that's what I did in Breezy. Just chacking in dapper, and no CD source is listed, so maybe they've changed it, or maybe somehow my Dapper won't ever ask for the CD.

---

### Post by 00zero on 2006-06-06
i was able to change the repository file and comment out the cd entry and then apt-get worked and dl the files it needed

---

