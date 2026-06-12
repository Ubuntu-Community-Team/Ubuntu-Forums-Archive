---
title: "Understanding Top and CPU use...."
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by esaym on 2007-03-15
Can someone explain to me what all the info means when you type top into the console?

More specifically what the cpu line means:

Cpu(s):  0.7% us,  0.0% sy,  0.0% ni,  0.0% id, 98.7% wa,  0.0% hi,  0.7% si

:confused:

---

### Post by John.Michael.Kane on 2007-03-15
Have a look. It should help with explaining.

[top description]("http://linux.about.com/od/commands/l/blcmdl1_top.htm")

[top infomation]("http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=t/top")

---

### Post by weresheep on 2007-03-15
Hello,

I am not an expert but here is what I know (or at least what I think I know :)).

us - % time the CPU spent executing "user space" code.

sy - % time the CPU spent executing "system" or "kernel" code.

ni - not sure about this one, possibly % time the CPU spent executing a nice'd process.

id - % time the CPU was idle.

wa - don't know this one.

hi - % time the CPU spent dealing with hardware interrupts

si - % time the CPU spent dealing with software interrupts


-weresheep

---

### Post by esaym on 2007-03-16
> **weresheep said:**
> Hello,

I am not an expert but here is what I know (or at least what I think I know :)).

us - % time the CPU spent executing "user space" code.

sy - % time the CPU spent executing "system" or "kernel" code.

ni - not sure about this one, possibly % time the CPU spent executing a nice'd process.

id - % time the CPU was idle.

wa - don't know this one.

hi - % time the CPU spent dealing with hardware interrupts

si - % time the CPU spent dealing with software interrupts


-weresheep

Thats pretty good.  I would still like to know what the heck wa is.  It only goes up when accessing the hard drive or usb.

---

### Post by John.Michael.Kane on 2007-03-16
w=Cycle backward through all four windows.

a Cycle forward through all four windows.

The links posted give the info..

---

