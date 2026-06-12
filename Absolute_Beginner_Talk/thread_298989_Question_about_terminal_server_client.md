---
title: "Question about terminal server client"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by sindrum_murdnis on 2006-11-13
Im currently setting up a ubuntu box for my grandmother and was wondering if terminal server client(TSC) could be used to give her remote help when she needs it. The way i understand how TSC works is that its for setting up a server. I dont need that just looking for an easier way to help her when she needs it.:-k Can someone help me understand how this app works?

---

### Post by Chayak on 2006-11-13
Ok, first off forget terminal server as it's a big security issue.  OpenSSH is what you really need to use for remote assistance text wise. VNC over SSH is also a nice thing to have so you can see screens.

I would provide a bit more guidence but I don't have access to my linux box atm.

---

### Post by pnael on 2006-11-13
No the terminal server client can only be used to connect to a MSFT
server. For your usage, you have 2 options :
- via ssh (for command line and X server)
- via vnc 

Cheers
Philippe

---

### Post by sindrum_murdnis on 2006-11-13
Yeah ok... thats what i thought. i didnt know about ssh, i have used ssh for mud games thats it. i think ill try that out see how that works.  thanks:)

---

