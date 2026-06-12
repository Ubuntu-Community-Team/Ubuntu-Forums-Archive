---
title: "what to remove?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by drtvasudevan on 2006-06-12
my partition with dapper ubuntu plus kubuntu desktop is now over flowing.
i use this to try out fixes /updates /experiments before executing them on my main installation.
what can i safely remove to have some space?
hopefully not the kde

tv

---

### Post by ProjectGod on 2006-06-12
have you recently downloaded alot of packages? if so try

**df -h**

note the amount of storage you have used...

the try...

**sudo apt-get clean**

then check the storage usage with 

**df -h**

you should notice increased free space...

---

### Post by frodon on 2006-06-12
You can remove old kernel installations which you don't use now.

You should read this guied too : [http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

---

### Post by drtvasudevan on 2006-06-12
thanks.
but i dont think i can remove much that way
installation is fairly new.
i have updated just once.
installed not many prgrams extra.

tv

---

