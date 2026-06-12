---
title: "Simple system monitoring needed"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Dencorub on 2007-03-24
Hi All,

I'm after an easy-to-setup system monitoring package that keeps stats etc. for an Ubuntu 6.10 installation.

I've been fiddling with munin, but just have no luck getting it going.

The machine is a standalone, not a server.

I need to be able to look back over system performance, preferably in an easy-to-read format such as a graph.

I need to monitor such things as CPU usage, bandwidth used, etc.

Any ideas?

A bit of background on this PC:

It's a business PC serving as a customer access point to the company website. Customers can select products from the company website, then print out the brochure for that product.

It's also used for the manager to do e-mail, and write reports etc.

Not sure why they want this monitoring, but they do.

I think mainly they want to be able to look over the logs and see what times of the day certain system resources get used most.

For most of the time, the only thing running will be firefox.

---

### Post by AndyCooll on 2007-03-24
And are System Log and System Monitor (System > Administration > System Log/Monitor) not enough?

:cool:

---

### Post by Dencorub on 2007-03-24
System monitor looks to have the monitoring I need, but it doesn't appear to have logging.

What I need is the ability to log the values in System monitor, and then produce graphs etc.

---

### Post by Marsolin on 2007-03-24
You could try [Nagios]("http://linuxappfinder.com/package/nagios2").

---

