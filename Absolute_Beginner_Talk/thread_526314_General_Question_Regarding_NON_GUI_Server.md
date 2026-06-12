---
title: "General Question Regarding NON GUI Server"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by guilly on 2007-08-15
When i connect to my server i usually use VNC wrapped with SSH for security or just plain old SSH now my question is, i plan on completly removing GNOME from my server when i'm completly finished setting it up, is there a way some how to connect remotely with SSH and then running a command lets say sudo firestarter and then firestarter would come up in a GUI view ?

am I making myself clear? i hope so...

thanks!!!

---

### Post by bodhi.zazen on 2007-08-15
ssh -X <server>

That will forward x applications to the client.

---

### Post by Hospadar on 2007-08-15
> 
ssh -X <server>
 
That will forward x applications to the client.
yep, just make sure you have the apps installed on the server.
Oh: and it's not like you'll have a virtual desktop, you'll just get the window as if you opened it from a command line on your machine.

---

### Post by guilly on 2007-08-15
ok great...

that's exactly what i was looking for.

---

