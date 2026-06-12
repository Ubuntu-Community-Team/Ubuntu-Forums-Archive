---
title: "Managing external modem in GNOME?"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by bro.bill on 2007-02-18
Hi all,

I can do the pppconfig thing at the command line but when I go to the GUI in GNOME the hardware list neither sees my external modem nor does the little modem monitor no it is even there.  The activate command is grayed out.  It there a way to manage the modem connection dialing, monitoring and hanging up in the GUI without resorting to the command line?

thanks,
bill.

---

### Post by tagginannie on 2007-02-18
> **bro.bill said:**
> Hi all,

I can do the pppconfig thing at the command line but when I go to the GUI in GNOME the hardware list neither sees my external modem nor does the little modem monitor no it is even there.  The activate command is grayed out.  It there a way to manage the modem connection dialing, monitoring and hanging up in the GUI without resorting to the command line?

thanks,
bill.

Go to your home folder and right click and select "create new ->text file. It has to blank. and name it "resolv.conf"  Now open the terminal and type "sudo cp resolv.conf /etc/resolv.conf" with out the quotes. Now go in to the "PPP" folder in the etc directory and right click on options actions-> edit as root enter your password  and look for "auth" and put a '"#" before it

Suzy:KS

---

