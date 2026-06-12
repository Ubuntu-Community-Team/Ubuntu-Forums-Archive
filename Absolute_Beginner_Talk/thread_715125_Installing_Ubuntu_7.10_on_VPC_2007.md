---
title: "Installing Ubuntu 7.10 on VPC 2007"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by sbussy89 on 2008-03-04
I am trying to install Ubuntu on VPC 2007 following the guide shown here: [http://codespin.blogspot.com/2008/01...microsoft.html](http://codespin.blogspot.com/2008/01...microsoft.html)

I add the line "i0842.noloop" as instructed, but when I hit enter to boot I get the following:
[ 2385.402932] isapnp: checksum for device 1 is not valid (0x89)

What do I do?

---

### Post by sbussy89 on 2008-03-04
OK now I have a new problem... When I booted for the first time after the install I got the error message again, so I just turned of the virtual machine and tried it again, but now it just sits at a blank screen that says "Starting up..."    Any ideas on how to fix this???

---

### Post by sbussy89 on 2008-03-04
I have an HP, so I had to add "noapic irqpoll noirqdebug" to the boot sequence... now it works sometimes but still not most of the time.  Sometimes it just sits at the "starting up..." screen, other times it get passed the starting up to give me this error: "[ 7469.377741] isapnp: checksum for device 1 is not valid (0x89)"  Any idea what this could be?

---

