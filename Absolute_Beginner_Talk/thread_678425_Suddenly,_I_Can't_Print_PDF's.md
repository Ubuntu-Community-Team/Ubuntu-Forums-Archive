---
title: "Suddenly, I Can't Print PDF's"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by E.T.Smith on 2008-01-25
I am running 7.1 Gutsy Gibbon, and lately have become completely unable to print PDF's. I use the Evince viewer, and also installed XPDF in hopes that would work around the problem, but to no effect.

The print job does appear in the Document Print Satus box, but immediately becomes "stopped". The only option given is to cancel the job, but that creates the following error window: "CUPS server error - There was an error during the CUPS operation: 'client-error-not-possible'".

Other programs, such as OpenOffice, Abiword and the Text Editor continue to print without difficulty. I have tried deleting and reinstalling the printer through System>Administration>Printing, but the problem remains. My printer is a HP 5510 all-in-one, if that matters.

---

### Post by cmnorton on 2008-01-26
It sounds like a missing piece that's built into the applications that can print PDFs. Evince should not balk at printing pdf files. Check your logs, /var/log/messages and /var/log/syslogd.

---

### Post by E.T.Smith on 2008-01-26
How do I do that, what do I look for, and what do I change when I find it?

Please note, I was able to print PDF's until recently, and I have made no significant system changes (at least that I know of) that might be linked to the stoppage.

---

### Post by cmnorton on 2008-01-27
sudo tail /var/log/cups/error_log

for starters. I'd also print out the last (tail) of the other logs in /var/log/cups.

---

### Post by E.T.Smith on 2008-01-27
I've entered it, but its not doing anything on the command line, just leading to another prompt.

---

### Post by junglist313 on 2008-02-12
Apparently it is a conflict with Foomatic.(?) I am having the same problem w/ a HP PSC1501 printer. Log below. Ubuntu 7.10 64 bit vanilla setup here. Anyone have a workaround?  

E [12/Feb/2008:22:05:25 +0000] PID 14314 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [12/Feb/2008:22:05:33 +0000] [Job 112] Job stopped due to filter errors.

---

### Post by johantc on 2008-02-14
I've had the same problem. I normally use a work around for this problem.
pdf2ps <your document>. You might want to specify an output destination. My default is /home

Then open the .ps file and print
__________________

---

