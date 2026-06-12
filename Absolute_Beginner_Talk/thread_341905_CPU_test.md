---
title: "CPU test"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by addisor on 2007-01-19
Found this script on [http://www-128.ibm.com/developerworks/library/l-hw1/](http://www-128.ibm.com/developerworks/library/l-hw1/) 

The cpubuild script
#!/bin/bash
make dep
while [ "foo" = "foo" ]
do
	make clean
	make -j2 bzImage
	if [ $? -ne 0 ]
	then
		echo OUCH OUCH OUCH OUCH
		exit 1
	fi
done

It's suppose to be for testing CPU because i cant get CPUburn-in to work at all. How would i go about running it? any good?

---

### Post by jd65pl on 2007-01-19
Here is a document I wrote on bash scripts earlier today for someone else, I have attached the link below. I think it should help you in understanding how to get the script to work.
[http://jamie.dumbill.googlepages.com/revdoc6.pdf](http://jamie.dumbill.googlepages.com/revdoc6.pdf)

Edit:
The document is not complete but what is there should help you!!! I will be finishing it on Monday.

---

### Post by Nik_Doof on 2007-01-19
You'll need the kernel source installed for that one, essentially it compiles the kernel constantly until it breaks :)

Its actually a good idea, even minor hardware issues could cause a heavy compile job to fail. I had a dodgy stick of ram that would cause all sorts of weird and wonderful errors with GCC :).

---

### Post by addisor on 2007-01-19
what does 'your need the kernal source for that one' mean?

---

### Post by mcduck on 2007-01-19
it means that you need to install the source code for linux kernel.

Anyway, there's also program called SuperPi that's commonly used by overclockers to test their CPU's. You only need to extract it somewhere and run. It's guaranteed to fail it there's anything wrong with your CPU ;)

[http://www.ocforums.com/showthread.php?t=405925]("http://www.ocforums.com/showthread.php?t=405925")

edit: there's also a thread about it in Cafe: [http://www.ubuntuforums.org/showthread.php?t=60264]("http://www.ubuntuforums.org/showthread.php?t=60264")

---

### Post by addisor on 2007-01-19
I like the look of that super PI test. seems simple to me. cheers

---

### Post by addisor on 2007-01-20
Got this

Parameter(%i) to super_pi is missing. Parameter value ? 20
 Start of PI calculation up to 1048576 decimal digits
 End of initialization. Time=       0.960 Sec.
 I= 1 L=       0        Time=       1.912 Sec.
 I= 2 L=       0        Time=       1.652 Sec.
 I= 3 L=       1        Time=       1.660 Sec.
 I= 4 L=       2        Time=       1.652 Sec.
 I= 5 L=       5        Time=       1.656 Sec.
 I= 6 L=      10        Time=       1.652 Sec.
 I= 7 L=      21        Time=       1.652 Sec.
 I= 8 L=      43        Time=       1.652 Sec.
 I= 9 L=      87        Time=       1.660 Sec.
 I=10 L=     174        Time=       1.656 Sec.
 I=11 L=     349        Time=       1.652 Sec.
 I=12 L=     698        Time=       1.656 Sec.
 I=13 L=    1396        Time=       1.660 Sec.
 I=14 L=    2794        Time=       1.656 Sec.
 I=15 L=    5588        Time=       1.664 Sec.
 I=16 L=   11176        Time=       1.636 Sec.
 I=17 L=   22353        Time=       1.648 Sec.
 I=18 L=   44707        Time=       1.588 Sec.
 I=19 L=   89415        Time=       1.468 Sec.
 End of main loop
 End of calculation.    Time=      33.706 Sec.
 End of data output.    Time=       0.172 Sec.
 Total calculation(I/O) time=      33.878(       0.804) Sec.
 ------ Ended super_pi run : Sat Jan 20 16:08:41 GMT 2007
What does this mean?

---

