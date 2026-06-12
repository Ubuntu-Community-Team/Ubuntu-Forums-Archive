---
title: "AT&amp;T 4410  terminal Emulator not supported"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by mastromitsos on 2007-06-07
Hello all , i have installed Ubuntu , installed plugins , softmodem drivers etc. and now i enjoy  fast and stable performance that i never had experienced before on a laptop .

What i try to do is find a terminal emulator to support terminal AT&T 4410 , that i use to connectd to PBX's via modem for administration .

I tried minicom but it doesn't  support the terminal i need .

Should i try WINE and run the windows application ?
I tried once but it is very difficult to set up .

Any suggestions ?

Thanks in Advance 

Mastromitsos

---

### Post by Alterax on 2007-06-07
I don't know much about the AT&T 4410 TE, but in my office we use an  iSeries AS-400 for much of our paperwork.  After fighting with their custom installers, I finally gave up, then found out I could do it just fine with Telnet.  May not work in your case, but it may just be worth a shot.

--Alterax

---

### Post by mastromitsos on 2007-06-07
Thank you for your reply , no , it's a serial connection via modem , telnet can't help ...

---

### Post by steve.horsley on 2007-06-07
I think running the windows emulator under Wine should work. I surprised myself a while ago by succesfully upgrading the software in my DVR over the serial port by running a windows prog in wine, so I know that it can be done. No special setup needed - just right-click the .EXE and open with wine.

---

