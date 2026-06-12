---
title: "solving modem problems thrpugh kde's gui"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by jamil_1 on 2007-03-03
i have problem with my modem. i m just a newbie, i have win lucent modem. all the solution available on the net to solve the driver problem of modem require me to  compile the code and then configure the modem using the terminal or shell. i have moved from windows to linux .i m used to mouse and gui not dos or terminal so plz tell me the way i can compile and install the driver  for modem through kde's gui .


P.S: i have already posted two threads two days ago but got no response.  this is my last attempt before becoming desparate and returning to windows

---

### Post by ingo on 2007-03-04
Right, let's see whether we can get this baby onto the internet :) There is a GUI which does exactly what you ask. To install do > sudo apt-get install kinstallerAfter the successful install you will find it under "Utilities". Start it up and tell it the location of your tar.gz file and off you go...

Having said all that, the steps ./configure, make and sudo make install aren't all that hard, are they? Whatever you do, make sure to read the README file beforehand, 'cos sometimes there is actually important stuff in there  :)

Best of luck

Ingo

---

