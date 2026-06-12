---
title: "Evolution newline in text"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Julian Lewis on 2008-03-11
When I compose new mail, evolution puts in newline characters in my text.
I do not want this, it destroys the readability of the text I am sending.
When I enter this text ...

Mod[1] Int[0x004 2] Time[Tue-11/Mar/2008 12:00:14] Cntr2 Hptdc: 0x00000000
Mod[1] Int[0x004 2] Time[Tue-11/Mar/2008 12:00:14.0156250000] Cntr2 Hptdc: 0x02625A00
Mod[1] Int[0x004 2] Time[Tue-11/Mar/2008 12:00:14.0312500000] Cntr2 Hptdc: 0x04C4B400

It dose this to it rendering it unreadable ...

Mod[1] Int[0x004 2] Time[Tue-11/Mar/2008 12:00:14] Cntr2 Hptdc:
0x00000000
Mod[1] Int[0x004 2] Time[Tue-11/Mar/2008 12:00:14.0156250000] Cntr2
Hptdc: 0x02625A00
Mod[1] Int[0x004 2] Time[Tue-11/Mar/2008 12:00:14.0312500000] Cntr2
Hptdc: 0x04C4B400

How can I switch this behavior off and get evolution to send exactly what I type.

---

### Post by neurostu on 2008-03-11
I think email by default inserts \n chars into the text, otherwise really long emails would be interpretted as a really long single line.

Try messing around with the message formating/encoding and see what happens.

---

