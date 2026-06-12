---
title: "Clarification on Virtualization"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-06-05
Cheers,

I noticed that one of the local groups Im affiliated with are having a seminar on OpenVZ.
So I was intrigue to know what OpenVZ is, so I googled it and foudn this [http://openvz.org/](http://openvz.org/).

From what I read, the way I understand it is that it operates like VMWare or VirtualBox.
Am I correct to assume that it is?

What is the difference between OpenVZ and VMWare? Advantages/disadvantages?

Thanks.

---

### Post by Daishiman on 2007-06-05
No. VMWare emulates an entire machine including its hardware. Xen is a paravirtualization solution which allows all virtual machines access to the same hardware and Xen administers that. OpenVZ created virtual environments within linux, that is, all the processes of each environment are isolated, but they are all run by the same Linux kernel.

---

