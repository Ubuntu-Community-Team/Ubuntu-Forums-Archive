---
title: "Macs can't use Ubuntu CUPS server"
date: 2011-12-19
forum: Apple Hardware Users
---

### Post by John Chambers on 2011-12-19
Is this an appropriate forum for this question?

I have an Ubuntu system with two printers attached, and CUPS running.  We have several Macs in our house, including this Macbook Pro.  They can all "see" the two printers, and believe that they can sent print jobs.  However, when they do, nothing prints.

There seem to be two failure modes.  The most common has a long pause with the little printer-status window showing the message:
   Opening printer connection
After 30 or 40 seconds, this disappears, and I get:
   Attempting to connect to host 192.168.1.42 for printer
      Network host '192.168.1.42' is busy; will retry in 30 seconds...
Actually, it starts with lower numbers of seconds, and slowly increases the number.  This state lasts forever, or until I tell it to delete the print job.

The other failure mode has the printer window claiming that the printer is paused.  Pressing the Resume button gets a message saying that I'm not authorized to do that.  If I check with the Ubuntu server, it says the printer is up and "accepting requests".

In both of these failures, the server's /var/log/cups/access_log and error-log files show no activity.  It's as if the server doesn't even see the connections.  But note that the address given is the IP address of the server, and "netstat -an" shows that someone (presumably CUPS) is listening on port 631.

I've dug around looking for ways to diagnose these problems.  Google finds lots of questions about both of them, but they are either unanswered, or their answers don't seem to work here.  The answers seem to usually be about total failures to see the printers, but our Macs see the printers just fine, give correct descriptions (and pictures), and think that they can send jobs to the printers.  So some sort of communication is happening; it's just that printing doesn't happen.

Is there a CUPS troubleshooting guide somewhere that works for Mac-Ubunto links?  I haven't found one.  I've found a few that deal with MS Windows as the server or client, but the stuff there doesn't seem to apply to Macs (or Ubuntu).

(And is this the right forum for such questions?  If not, is there one here that would be better?)

---

