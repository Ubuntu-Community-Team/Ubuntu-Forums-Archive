---
title: "azureus won't start"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by kaston on 2008-01-19
hi, i tried running azureus today from the terminal and got the following error message:

Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-6-sun/jre/bin/java
The program 'SWT' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 343 error_code 11 request_code 148 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

i'm pretty much a noob and don't really know what to do with the fix suggested by the message.  can anyone help me out?  thanks a lot in advance!

---

### Post by Kingsley on 2008-01-19
It might be a problem with xorg-core. Open up Synaptic, do an upgrade, and then restart your computer.

---

### Post by kaston on 2008-01-19
that did the trick!  thanks!  could you please give me some insight as to how you knew that might be the problem?

---

### Post by ajgreeny on 2008-01-19
The upgrade of xserver-xorg-core two days ago made java have big problems and several programs including azureus, vlc and others were unusable.  Two quick further upgrades put things right.

---

### Post by acridfusion on 2008-01-19
so thats why i got the forbidden 443, they had to fix it, cool, this is so much better than being left in the dark w/ winblows!

---

