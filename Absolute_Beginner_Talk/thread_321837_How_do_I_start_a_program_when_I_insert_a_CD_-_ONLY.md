---
title: "How do I start a program when I insert a CD - ONLY when it's not open?"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by jsully1 on 2006-12-19
Tiny gripe alert!

When I insert a CD I have Ubuntu launch Grip, however it continues to spawn new instances instead of seeing if one is already open - so if I eject a CD and insert a new one I now have two instances open.  Is there a way I can have it launch Grip only if Grip isn't open already?  I'm cool with writing a little script I guess to check and see if grip is in the list of running processes, then spawn it if it's not.

Any help on a built in way to accomplish this or a way to do it with a script would be very helpful!

---

### Post by BarfBag on 2006-12-19
Can't help you with the script, unfortunately.

Have you looked in System > Preferences > Removable Drives and Media?

---

### Post by 23meg on 2006-12-19
This should do:```
#!/bin/sh
ps -e | grep grip
x=$?;
if [ $x -eq 1 ]; then
#do nothing
else
        killall -9 grip
        grip
fi
```I haven't tested it though.

---

### Post by jsully1 on 2006-12-19
After research and bit of help I did:

pid=$(ps -C grip -o pid=)
if [[ -z ${pid} ]]; then
	grip
fi

Then had gnome call that script in System > Preferences > Removable Drives and Media.

It doesn't actually launch it though :(

If I call the script directly it works properly - any ideas?

---

### Post by jsully1 on 2006-12-21
If I launch the script from a terminal it works.  If I launch it from Nautilus or have Gnome try to call it with the Removable Drives and Media setting it doesn't work.  I have two versions, one owned by root, and one owned by me, and both chmodded to 777 - any ideas?

---

