---
title: "did I run a malicious command?"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by aBitLater on 2008-02-14
hi,

First, let me say plainly that I will show the command I used in a code box here and you should **NOT** execute it.  

For syncing with multisynch, I was trying to find which device my Sony Ericsson phone was on, and I had no clue how to go about this.  Being a noob, I typed this into a root terminal command line:

**(please do not run this - I have no idea of the consequences, and that is why I am posting it here)**
```

dmesg | grep -i tty*

```

I was looking for something that might tell me what happened when I connected the phone via usb.

but what I got was a a filled up terminal (with blanks) and I couldn't CTRL-C out or CTRL-Z or any other combo I tried.  I finally clicked the X to close the console.

After I did that, one of my desktop notes (Sticky Notes 2.20.0) started growing in size very rapidly.

I clicked the logoff/shutdown icon and the logoff window kept blinking, so I couldn't use it.  Finally, I did CTRL-ALT-BACKSPACE, came to a new login window, and shut down from there.

My questions are:
1. What happened?
2. Are there any consequences after the reboot?

Thanks for help, and again I want to make this disclaimer:
[B]
This post is not intended to solicit others to run a malicious command.
[/B]

---

### Post by emarkd on 2008-02-14
That isn't a malicious command.  It searches through a type of system log for mention of 'tty' and prints the results.  Nothing malicious there.  Your problem is unrelated.

---

### Post by wieman01 on 2008-02-14
'dmesg' only lists system messages. It reads stuff from system log files, so you are safe. Don't worry. :-)

_**EDIT:**_
A friendly advice if you don't mind... Ask first next time you run a command that you don't know. :-)

---

### Post by aBitLater on 2008-02-14
thanks for the input.

So anyone know how to find which serial port my Sony Ericsson phone is on? USB connected, not bluetooth

lsusb
```

Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0fce:d089 Sony Ericsson Mobile Communications AB 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:00f9 Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

```

---

### Post by aBitLater on 2008-02-14
> **wieman01 said:**
> 'dmesg' only lists system messages. It reads stuff from system log files, so you are safe. Don't worry. :-)


why did it interfere with my notes and other part of my system?  After X'g out of the terminal, it was if the output from the command still want to "go" somewhere - my sticky note was growing in the same way that the console was scrolling before I x'd out of it.

---

### Post by wieman01 on 2008-02-15
> **aBitLater said:**
> why did it interfere with my notes and other part of my system?  After X'g out of the terminal, it was if the output from the command still want to "go" somewhere - my sticky note was growing in the same way that the console was scrolling before I x'd out of it.
This is very strange, I cannot help you there unless I try it myself. I might do that tonight and get back you. Odd, very odd.

---

