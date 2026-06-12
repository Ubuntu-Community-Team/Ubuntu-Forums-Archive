---
title: "So I decided to compile a custom kernel, still showing 386 why?"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by comfortablynumb on 2006-09-07
Well I decided to compile a custom kernal today, I followed [Dapper Compilation Guide]("http://doc.gwos.org/index.php/Kernel_Compilation_Dapper") I selected K7 from the Processor Family, (I have an AMD Duron) as the guide instructs, and I followed the guide to a tee. When I reboot and do uname -r it shows 2.6.15-26-386 shouldn't it show K7? What could I have possibly done wrong?

---

### Post by Metacarpal on 2006-09-07
I don't think it's anything you've done wrong.  I compiled a custom kernel for a -686 processor and it showed -386 in the file name for the compiled kernel.  It's basically just part of the naming convention the kernel source uses.

There's a step in the process where you can tell it to use a revision number of your choosing - in your case, for example, you could call it K7 - but it really doesn't make a difference.  It's just a file name.

---

### Post by comfortablynumb on 2006-09-07
Ok cool :) I just wanted to make sure I didn't screw up lol

---

### Post by nero2150 on 2006-09-07
I think when u boot up you can choose the right kernel
ie K7 or 386
once in xwindow you can check the version

---

