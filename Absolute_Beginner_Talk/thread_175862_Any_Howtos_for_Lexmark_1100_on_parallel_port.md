---
title: "Any Howtos for Lexmark 1100 on parallel port"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by Blur-king on 2006-05-13
Found a good Howto for lexmark printers. Got through with all steps until checking the backends. Then realised its for USB port. So back to square one. Any pointer to the right direction is appreciated. Thanks. Need to get this going soon before, its back to windows.....:(

---

### Post by richbarna on 2006-05-14
Hi Blur-king.
This might help :-
[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-1100]("http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-1100")

---

### Post by skippy81 on 2006-05-14
I got my HP printer working by changing "ECP" to "Normal" for the parallel port settings in my Bios.

---

### Post by Pitxyoki on 2006-11-19
I am having this problem.
When I try to print anything, nothing comes out.
The printer status says "Ready: /usr/lib/cups/filter/foomatic-rip failed"
This is a local printer connected by the LPT1 port to my computer.
I have already tried to change the "ECP" setting on the BIOS to "Normal" but nothing changed.

On the link that richbarna recommended, there is an indication to users with gcc greater than some versions.. Which happens to be my case. I'm on Ubuntu Dapper 6.06, I'm using *gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)*.
> Important: If you use gcc 3.1 or later for compiling this driver you should apply a little correction by running the command

perl -p -i -e 's/friend Lexmark/friend class Lexmark/' *.h

in the source directory of the driver before you compile the driver with the "make" command.

To use gcc 3.4 or later, you need to apply [this patch](http://www.linuxprinting.org/download/printing/lm1100/lm1100.1.0.2a-fix-compile-gcc-3.4.patch.gz).

For gcc 4.1 or later, you need to run the command

perl -p -i -e 's/\b[^\s:]+:://' *.h

in the source directory of the driver before compiling. This removes the now deprecated extra qualifications "<class>::<member>" on class members.

...but I don't how to "apply that patch" they say there.
Any help would be appreciated.
Thanks.

---

### Post by Pitxyoki on 2008-01-12
I did some progress today... But the best I got when trying to print a file was to make the printer choke, print a blue, senseless line at the top of the page and then it started bogging up and nothing else could be done.

I guess we'll have to keep waiting until a generous developer picks this driver again and updates it or simply give up on this printer. :-?

---

