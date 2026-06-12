---
title: "downgrade from 8.04 to 7.10"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Dbugger on 2008-04-04
8.04 BETA has turned my system upside down. How do I downgrade?

Thank you.

---

### Post by misfitpierce on 2008-04-04
I do not believe you can downgrade an OS. This is why it is advised to backup all your materials before going to 8.04 BETA or ALPHA tests as it may have problems and require you to reformat the drive. :(

---

### Post by schiznik on 2008-04-04
You CAN downgrade debian based systems (I have a box that has run stable, then unstable then testing)

You will need to change /etc/apt/sources.list to point at the old repo's then dist-upgrade. It could get a little hairy with alot of important packages needing to be removed (with the box above, at one point during the downgrade I needed to remove X, bash and a while lot more). You'll probably want to make note of whats removed so you can reinstall it before you reboot.

Unless you know what you are doing (and the above doesnt sound scary), I'd recommend backing up your /home folder and reinstalling.

Edit.. I updated my laptop to hardy the other day and its been a bit crashy ever since. I might give the downgrade a go ;-)

---

### Post by fela on 2008-04-04
reinstall imo

---

### Post by hyper_ch on 2008-04-04
reinstall the system...

---

