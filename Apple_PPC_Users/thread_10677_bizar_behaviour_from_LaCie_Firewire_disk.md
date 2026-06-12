---
title: "bizar behaviour from LaCie Firewire disk"
date: 2005-01-10
forum: Apple PPC Users
---

### Post by mistic on 2005-01-10
I've got this 250Gb fire-wire disk from LaCie for mac and it works really well under mac osx

the thing is it sometimes doesn't work under ubuntu. 

Sometimes, when I put it in, it immediately detects it and mounts it in the /media-dir , but other times it just notices its there and that's all, ubuntu doesn't even make a special device in /dev (normally the disk goes under /dev/sda ) 

when I check my kernel / system-messages it just says 'hey something happend on your firewire port' (cant give you the specific notification because i am atm in the next 'area' )and that's all

other times it doesn't even notice what's going on in the firewire-area, allthough i clearly hear it (iBook) reacting to the connecting of the disk

it really sucks major ass because i need the disk a lot and now i simply can't rely on it :s

anybody know how i can 'command' my ubuntu into scanning for it on my firewire and then how i can force it to make the /dev/sda ?

grtz
mistic

---

### Post by diabolo on 2005-01-10
My Lacie FireWire drive rarely auto-mounts, but I've never had it fail to show up in /dev. All I can think of is check to see you've got the necessary modules loaded, do **lsmod** in the terminal and see if ieee1394 and ohci1394 are in the list. Hopefully someone who knows more about this stuff will post something more helpful than this. 8-[

---

