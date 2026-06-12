---
title: "Synaptic requiring CD?"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by tiuk on 2006-04-25
When I try to install things via Synaptic (or just apt-get) I keep getting prompted to insert the CD (I'm running Dapper Flight 6 if it matters).

I know there should be a way to set it to download packages from the net instead of from the CD, I just can't figure out how. Any help would be greatly appreciated.

---

### Post by oldmanstan on 2006-04-25
settings >> repositories >> "add"

make sure "officially supported" is checked and that the drop down menu reads something like "ubuntu 6.06" and the hit "ok" and "ok" again

that should work, i am running breezy but i don't think they changed synaptic too much in dapper

the reason it does that is that it is not looking on the net, it is only using the CD, you have to add sources for it to look in

---

### Post by aysiu on 2006-04-25
Go to Settings > Repositories and uncheck the first check box (the one that's for the CD-ROM. Then click the Reload button.

---

### Post by tiuk on 2006-04-26
Thanks guys, worked perfectly.

---

