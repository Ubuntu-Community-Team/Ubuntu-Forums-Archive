---
title: "Printer sharing"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by csaunier on 2008-04-09
Hi
I'm missing something here.  I dual boot Ubuntu 6.06 with win xp.  The windows was my origional computer so my printer is connected to  it. The problem is that in windows, the printer works for all computers on the network, just as it should (a mix of win xp, win 98 and Suse linux).  When I boot into Ubuntu, however, I can print from Ubuntu, but not from any other computer.  Samba is installed and files can be shared.  What am I missing?
 When I get this sorted out I will gladly use Ubuntu more than windows.

---

### Post by alexforcefive on 2008-04-09
have you tried System > Administration > Printing > Policies and ticking the "shared" checkbox?

---

### Post by csaunier on 2008-04-09
No I haven't done that, but I will as soon as I get back to that computer.
Thanks. I knew there was something simple I was missing.

---

### Post by csaunier on 2008-04-10
It's not there.  I've got system>administration>printers but no policy.  I looked in properties, but there was no place to check sharing.

---

### Post by alexforcefive on 2008-04-10
Well that's strange. Just so we're clear, I've uploaded a screenshot of the window. You have to select a printer to see its properties, but for me the default printer is selected anyway

---

### Post by csaunier on 2008-04-10
Hmmm, that doesn't look like mine.  Perhaps it's the difference between your version 7.10 and my older version 6.06. I've attached a screenshot of what I've got.

---

### Post by alexforcefive on 2008-04-10
Ah, ok, I missed that bit :) You should just need to change the part where it says "printer type" from  local to network. Are you in the right workgroup?

---

