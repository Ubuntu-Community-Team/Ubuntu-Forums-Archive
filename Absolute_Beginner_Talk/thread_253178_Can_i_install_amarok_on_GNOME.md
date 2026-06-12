---
title: "Can i install amarok on GNOME"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by manojvekaria on 2006-09-07
When i search the packages.ubuntu.com

i only get the option of installing amarok on kde. Will this work well in ubuntu GNOME too??

What other things do i have to download with it too work well?. It gives a huge list.

---

### Post by orb9220 on 2006-09-07
Yes open a term and enter each of these commands.

echo "deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main" >> /etc/apt/sources.list

apt-get update

apt-get install amarok amarok-engines

---

### Post by aysiu on 2006-09-07
You can install AmaroK in Gnome. You'll just end up installing a lot of KDE libraries as well (but not the complete KDE desktop environment): ```
sudo aptitude update
sudo aptitude install amarok
```

---

### Post by dwasifar on 2006-09-08
> **manojvekaria said:**
> When i search the packages.ubuntu.com

i only get the option of installing amarok on kde. Will this work well in ubuntu GNOME too??

What other things do i have to download with it too work well?. It gives a huge list.

I installed it in Gnome just by using Synaptic.  It did bring some dependencies with it.  But it's a great player, well worth installing, and works just fine in Gnome.

---

### Post by Dinerty on 2006-09-08
Installed fine here mate and I'm using gnome, like previously mentioned you can install any (Quote me if I'm wrong) kde application in gnome.

---

