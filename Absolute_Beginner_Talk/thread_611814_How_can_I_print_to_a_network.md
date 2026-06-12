---
title: "How can I print to a network?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Alpha_Omega on 2007-11-13
I'm trying to use ubuntu to print things with a network printer. My computer teacher told me to use CUPS or something. Is there a guide to printing to a network?

---

### Post by taurus on 2007-11-13
Does the printer have it own IP or does it connect to a server?

---

### Post by ofh on 2007-11-13
Hello
I am in the same situation.
I have a HP 4250n on a network (Not connected to a server).
I am using 7.10.
How do I connect to that printer using only the IP address on the printer.

BR
OFH
Denmark

---

### Post by taurus on 2007-11-13
> **ofh said:**
> Hello
I am in the same situation.
I have a HP 4250n on a network (Not connected to a server).
I am using 7.10.
How do I connect to that printer using only the IP address on the printer.

BR
OFH
Denmark

We have HP LaserJet 4200 with a static IP and it works great with Gutsy.

Here is how.

System -> Administration -> Printing -> New Printer and wait for the Searching to finish.  If your printer is not on the list of Devices, then scroll down the the end and pick LPD/LPR Host or Printer.  And on the right side, enter the IP address of your printer in Hostname and just enter HP for the Printername and click Forward.

Now, pick HP in the Makes and click Forward.  Pick LaserJet 4250 on the list of Models and use the recommended driver in the Drivers window and click Forward.

I would leave the Install Option window unchanged unless you have a reason to change those fields.  You can still do that later once you have set up your printer.  Click Forward.

Give the Printer Name (again, I use HP), Description, and Location and click Apply.

That should do it.

---

### Post by ofh on 2007-11-15
Hi taurus
Thanks for reply
I think it's the solution I was looking for.
I will try that tomorrow,
:)

---

