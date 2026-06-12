---
title: "USB Printer not working"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by trueboy on 2006-01-01
I have selecteted the Lexmark 1100 printer as the local printer E.G.

On local printer port I selected :-
USB Printer #1 (Lexmark X 1100 series)

However when printing, the error in syslog, from the printer the local printer port goes to :-
hp no_device_found  port

In other words the printer configuration appears to not be saving correctly for
the selected USB connected printer.

Can anyone please explain how to overcome this situation ?

---

### Post by poofyhairguy on 2006-01-01
Did you install it?

System-Preferences- Printing

?

---

### Post by trueboy on 2006-01-01
Yes I used the System/Administration/Printing to set the printer up.

It "Found" the lexmark printer and appeared to install correctly, it even recommended a reasonable sounding print driver.

It just does not print.

I have since looked at the printer under the CUPS print admin and the priter URI
looks like "usb://Lexmark/X1100%20Series" which seems odd as when I set up a second USB printer (no hardware attached) the URI is "usb:/dev/usb/lp1" which is more like I would have expected.

I have even "hacked" the printers file under CUPS and made the URI  "usb:/dev/usb/lp0" but that does not work either!!!

---

### Post by poofyhairguy on 2006-01-02
[QUOTE=trueboy]Yes I used the System/Administration/Printing to set the printer up.

It "Found" the lexmark printer and appeared to install correctly, it even recommended a reasonable sounding print driver.

It just does not print.
[/QUOTE]

Darn. I thought it was supported. Was in Hoary....

Have you done anything to your install that might have broken this support?

---

### Post by trueboy on 2006-01-02
I have been looking through the various logs.

here is the output from  tail -n 100 -f /var/log/cups/error_log

I [02/Jan/2006:20:10:45 +1100] Adding start banner page "none" to job 95.
I [02/Jan/2006:20:10:45 +1100] Adding end banner page "none" to job 95.
I [02/Jan/2006:20:10:45 +1100] Job 95 queued on 'X125' by 'edwin'.
I [02/Jan/2006:20:10:45 +1100] Started filter /usr/lib/cups/filter/pstops (PID 9191) for job 95.
I [02/Jan/2006:20:10:45 +1100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 9192) for job 95.
I [02/Jan/2006:20:10:45 +1100] Started backend /usr/lib/cups/backend/usb (PID 9193) for job 95.
E [02/Jan/2006:20:10:46 +1100] PID 9192 stopped with status 1!
I [02/Jan/2006:20:10:46 +1100] Hint: Try setting the LogLevel to "debug" to find out more.

The only question is.... What is foomatic-rip and why is it stopping with status 1????

---

### Post by poofyhairguy on 2006-01-02
[QUOTE=trueboy]I have been looking through the various logs.

here is the output from  tail -n 100 -f /var/log/cups/error_log

I [02/Jan/2006:20:10:45 +1100] Adding start banner page "none" to job 95.
I [02/Jan/2006:20:10:45 +1100] Adding end banner page "none" to job 95.
I [02/Jan/2006:20:10:45 +1100] Job 95 queued on 'X125' by 'edwin'.
I [02/Jan/2006:20:10:45 +1100] Started filter /usr/lib/cups/filter/pstops (PID 9191) for job 95.
I [02/Jan/2006:20:10:45 +1100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 9192) for job 95.
I [02/Jan/2006:20:10:45 +1100] Started backend /usr/lib/cups/backend/usb (PID 9193) for job 95.
E [02/Jan/2006:20:10:46 +1100] PID 9192 stopped with status 1!
I [02/Jan/2006:20:10:46 +1100] Hint: Try setting the LogLevel to "debug" to find out more.

The only question is.... What is foomatic-rip and why is it stopping with status 1????[/QUOTE]

Here is what it is:

[http://www.math.ucla.edu/computing/docindex/foomatic-filters-man-2.html](http://www.math.ucla.edu/computing/docindex/foomatic-filters-man-2.html)

I hope this is not one of the many things that worked in Hoary but is broken in Breezy. Maybe install Hoary than upgrade it?

---

### Post by trueboy on 2006-01-05
:KS   Solution found. :KS 

The LexMark X1100 series printers appears to be compatable with the Z600 printer driver.

I am greatly indebted to jmurray who provided 99% of the solution through this site:
[http://www.jmurray.id.au/lex.html](http://www.jmurray.id.au/lex.html)

The only difference from the instructions given were:
1. I had to use alien to convert the printer driver files from RPM to DEB
2. I had to install the DEB files with "sudo dpkg -i *.db" 
3. I had to reboot the computer to "find" the added lexmark printer.

Once these three steps were done I was able to install the priner using the SYSTEM / ADMINISTARTION /PRINTING menu.

The printer is automatically detected and lists two appropriate printer drivers (the second is correct).

It was actually fairly easy in the end :p

---

### Post by noob_Lance on 2006-01-05
i still cant get mine to work... it installed.. btu whats really messed is one time.. a few days after i tied to print and canceled... my xserver crashed and then it started to print the picutres.... wtf.. anyone help me :(

---

