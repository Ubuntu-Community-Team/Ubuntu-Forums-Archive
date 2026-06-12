---
title: "hibernate computer from shell?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-11-28
ive recently been listening to radio/music before going to bed, and issuing the 'shutdown -h 20' command to switch off the pc automaticly after 20 mins.. but id prefer the system to hibernate

unfortunately i can't seem to find the hibernate option in shutdown, anyone know what I have to run? and even better if they know of a way to make it run after x minutes?

---

### Post by cet' on 2007-11-28
install hibernate
sudo apt-get install hibernate

then use
sudo hibernate

as for waking up after x amount of time hmmmm interesting...
check this out [http://winhlp.com/node/57](http://winhlp.com/node/57) 
might give you some ideas

---

### Post by nick_h on 2007-11-28
The hibernate script is /etc/acpi/hibernate.sh - you could run it with the *at* command.

See:
```
man at
```
for details.

---

### Post by PetePete on 2007-11-28
thanks nick, completly forgot about the 'at' command.

:)

---

