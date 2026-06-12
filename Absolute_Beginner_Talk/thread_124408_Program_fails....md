---
title: "Program fails..."
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by sudirt on 2006-02-01
I am trying to run Seatools Enterprise on UBUNTU. But I keep getting the same error. Below is the error and if you notice in the first few lines it will say something about a directory, /home/test/.Seatools/app.properties...
But I haven't seen nor can find the ".Seatools" folder. Does the "." denote a temporary folder? or perhaps something on the root?

I am completely lost...any and all help is greatly appreciated. Just fyi I have followed to a "T" the directions and troubleshooting for Seatools, UBUNTU, all of em...I need the super ubuntu experts advice. I figured I would atleast post and see if any of you can help.

Thanks
Sudirt

Error loading properties JSTError: /home/test/.Seatools/app.properties (No such file or directory)
exit form : /home/test/.Seatools/app.properties (No such file or directory)
exit form : /home/test/.Seatools/app.properties (No such file or directory)
java.lang.UnsatisfiedLinkError: /usr/local/Seatools/lib/libPTISTJ.so.5.2.23: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
/usr/lib/j2re1.5-sun/lib/i386/client:/usr/lib/j2re1.5-sun/lib/i386:/usr/lib/j2re1.5-sun/../lib/i386:/usr/local/Seatools/lib:.
java.lang.UnsatisfiedLinkError: /usr/local/Seatools/lib/libPTISTJ.so.5.2.23: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
at java.lang.ClassLoader$NativeLibrary.load(Native Method)
at java.lang.ClassLoader.loadLibrary0(Unknown Source)
at java.lang.ClassLoader.loadLibrary(Unknown Source)
at java.lang.Runtime.loadLibrary0(Unknown Source)
at java.lang.System.loadLibrary(Unknown Source)
at Devices.CSCSIDriver.<clinit>(CSCSIDriver.java:40)
at Devices.JComputerSystem.ScanSystem(JComputerSystem.java:115)
at jtabpnlSelectDevs.<init>(jtabpnlSelectDevs.java:42)
at Seatools.jbtnSelectDevsActionPerformed(Seatools.java:635)
at Seatools.main(Seatools.java:1674)
JSTError: java.lang.UnsatisfiedLinkError: /usr/local/Seatools/lib/libPTISTJ.so.5.2.23: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory Please contact PTI

---

### Post by sudirt on 2006-02-02
Bump...maybe last try...

sudirt

---

