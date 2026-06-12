---
title: "Printer sharing"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Rhaddad on 2007-04-28
Hello, My printer sharing used to work with edgy. All of a sudden it doesn't work with fiesty?. Is there anyway I can fix this?

---

### Post by Najand on 2007-04-28
System -> Administration -> Printing
Select Global Setting and then Select Share Printers.

---

### Post by Rhaddad on 2007-04-29
yea i did that, still doesen't work. I mean i can acess my shared folders from other computer's just not the printers. Its really wierd

---

### Post by fable on 2007-04-30
I have the same problem.  My HP LaserJet printer is locally connected to my Ubunutu computer.  My Ubuntu computer used to run Dapper, i.e. 6.06.  This week I upgarded to 7.04.  Everything works fine except printer sharing.  I did to to Global Settings and Share Printer.  Unfortunately my XP machines on the same router still cannot see the HP printer.  

I have Samba set up on my Ubuntu machine.  All my XP machines can share folders with the Ubuntu machine.  So I know network is set up correctly.

Any advice will be much appreciated.

---

### Post by fable on 2007-04-30
I found the smb.conf file in /etc/samba.
I uncommented the two lines:
  printing = cups 
  printcap name = cups
Now my XP machines can see the HP printer on the Ubuntu machine.

:)

---

