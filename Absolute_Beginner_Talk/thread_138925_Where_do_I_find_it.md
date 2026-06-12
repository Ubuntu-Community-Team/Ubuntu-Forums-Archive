---
title: "Where do I find it???"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by rustyfx on 2006-03-02
Hello,

I'm writing code that uses a USB to serial adapter.  I'm able to transmit data just fine (I have a microcontroller that confirms receipt of the serial data).  However, when I send data back, it doesn't make it to my C code running on the linux box.  I suspect that data is getting hung up in a buffer somewhere.

Now, I know that there is source code somewhere - and I think I could figure this out if I find that source code.  I've been looking for a while, and I haven't been able to find it.

So - the question is - where can I locate the source code for USB drivers that are built into the kernel??

Thanks
Robert

---

### Post by moberry on 2006-03-02
It's gonna be under .../drivers/usb

good luck with that. Your braver than I am :-)

-jordan

---

