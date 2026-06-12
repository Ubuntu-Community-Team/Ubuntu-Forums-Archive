---
title: "Loss of wireless after running Beryl?"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by the7yearplan on 2007-02-09
Just switched over to Ubuntu and love it.  I have a brand new Dell Latitude D620 with a broadcom 1390 wlan card inside.  Got my wireless card to work via ndiswrapper and Beryl installed and running but they don't seem to want to work at the same time.  I can connect to my wireless network and the internet but as soon as I start beryl-manager poof no connection and I can't reconnect.  I'm brand new to Linux but not to computers in generals so let me know what I can to provide more information to help diagnose this problem.

---

### Post by jd65pl on 2007-02-09
Beryl isn't really a topic for absolute beginners, your problem with beryl seems quite bizarre I would try to look on the [beryl forums]("http://forum.beryl-project.org/") or post a question there.

---

### Post by steveneddy on 2007-02-09
> **jd65pl said:**
> Beryl isn't really a topic for absolute beginners, your problem with beryl seems quite bizarre I would try to look on the [beryl forums]("http://forum.beryl-project.org/") or post a question there.

Or even trying:

[Beryl Project]("http://www.beryl-project.org/index.php") website. All things Bery;, all the time.

FYI - on my Edgy laptop from System76 (Serval Performance) if Beryl is in the start up of sessions, my wireless goes away also. If I start Beryl manually after a regular startup, everything is A-OK.

-SE

---

### Post by the7yearplan on 2007-02-09
Ok so I don't think it's just Beryl that's killing my wireless.  It has happened without it running, Beryl is just a sure fire way to trigger the problem which seems to be an irq issue of some sort.  Here is the output from dmesg once I lose internet connectivity:

```
[17179826.664000] irq 7: nobody cared (try booting with the "irqpoll" option)
[17179826.664000]  <c01499a4> __report_bad_irq+0x24/0x80  <c0149a9d> note_interrupt+0x9d/0x270
[17179826.664000]  <f8e60102> ndis_isr+0x52/0xc0 [ndiswrapper]  <c0149448> __do_IRQ+0xf8/0x110
[17179826.664000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179826.664000]  <c0149307> handle_IRQ_event+0x17/0x60  <c01493ed> __do_IRQ+0x9d/0x110
[17179826.664000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179826.664000]  <c0149307> handle_IRQ_event+0x17/0x60  <c01493ed> __do_IRQ+0x9d/0x110
[17179826.664000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179826.664000]  <c012782f> __do_softirq+0x5f/0xe0  <c01278e5> do_softirq+0x35/0x40
[17179826.664000]  <c010413c> apic_timer_interrupt+0x1c/0x30  <f88596dd> acpi_processor_idle+0x220/0x3af [processor]
[17179826.664000]  <c0102122> cpu_idle+0x42/0xb0  <c03f27a1> start_kernel+0x321/0x3a0
[17179826.664000]  <c03f2210> unknown_bootoption+0x0/0x270 
[17179826.664000] handlers:
[17179826.664000] [<f8e600b0>] (ndis_isr+0x0/0xc0 [ndiswrapper])
[17179826.664000] Disabling IRQ #7

```

I have tried to boot with the noapictimer irqpoll option and the problem still occurs both with Beryl and without.

---

