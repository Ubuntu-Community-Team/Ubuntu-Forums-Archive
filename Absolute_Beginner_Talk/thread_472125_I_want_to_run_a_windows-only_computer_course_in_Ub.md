---
title: "I want to run a windows-only computer course in Ubuntu!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by purplearcanist on 2007-06-12
I am going to take a computer course very soon on C programmng.  It has software that requires Windows, and it requires the Microsoft Visual C++ .net.  Is there any way to run this course on ubuntu?

The course website is:
[http://epgy.stanford.edu/courses/cs/C11A]("http://epgy.stanford.edu/courses/cs/C11A")

---

### Post by kilroy423 on 2007-06-12
I have used wine to run several applications in Ubuntu that use windows one being counter strike source..so it is possible..also if that won't work for you try using VirtualBox which is availble through the repositories, it is a Virtual machine which works great where wine is lacking


dan

---

### Post by Inxsible on 2007-06-12
Most common Windows applications do work via WINE VmWare etc. Some, not so common ones work too. But not all. You might have to try it out to actually see if it works flawlessly.

You surely dont want to have it *seemingly* work and then find out during your mid-terms that the results you are getting are all incorrect. Try it out thru WINE or VmWare. Check it out thoroughly, before you commit to using it on a Linux platform.

Always err on the side of caution, when it comes to your studies :)

---

### Post by zekopeko on 2007-06-12
i suggest installing virtualbox or vmware and setting a virtual WinXP machine. 
if you have a second hard drive put the image there because it will work far better (reading and writing files of 2 OS can be a little overwhelming for a single hardrive).

also you might check this for a really nice setup: 
[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by purplearcanist on 2007-06-16
Thanks for your information.  :)

---

### Post by phr0ze on 2007-06-16
If you have a newer machine (Core2) try XEN or KVM. They are very fast virtual machines.

---

### Post by Atomic Dog on 2007-06-16
I ran a coreduo laptop and used a windows VM to code MS visual c#, and later grade a similar class.  Performance was more than acceptable.  That will allow you to use linux, and still use the required MS application.

---

