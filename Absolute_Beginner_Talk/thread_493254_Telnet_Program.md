---
title: "Telnet Program?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by sarsippius on 2007-07-05
I am trying to show that Ubuntu is a viable option at work to Windows.  Does anyone know of a good Open Source program out there that I can use to connect to an IBM 3151 server?

I've heard of x3270, but does it work?

Any help would be greatly appreciated!

---

### Post by Malibu Illusion on 2007-07-05
...you still use telnet?

What's wrong with ssh?

---

### Post by Raineer on 2007-07-05
Would [Tn3270]("http://linux.maruhn.com/sec/tn3270.html") work for you?

---

### Post by sarsippius on 2007-07-05
I don't think TN3270 will work for what I need.  I need it to connect to be able to connect to an IBM 3151.  I will give it a try, but x3270 did not work for me.

As for SSH, would it work in this instance very well?

---

### Post by steve.horsley on 2007-07-05
A quick google tells me that a 3151 is an ASCII terminal, not a server. I couldn't find a document to be sure, but I think they're probably RS323 serial connected. So a normal telnet program might do, or you might need a special application that emulates the 3151 command sequences. 

I couldn't find an open source 3151 emulator with Google. Commercial ones exist.

---

### Post by sarsippius on 2007-07-05
Thanks for the info!

---

