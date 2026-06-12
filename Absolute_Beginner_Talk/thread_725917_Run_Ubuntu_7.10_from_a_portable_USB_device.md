---
title: "Run Ubuntu 7.10 from a portable USB device"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by bapaknyaAnak2 on 2008-03-16
Hello all,

I am totally new in Linux. I found this site during my adventure:guitar:.  [http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/](http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/) . Does it mean we don't have to make dual booting ? Any one had tried it before ? have you found any weakneas by doing that ? can you share things need to be considered by doing this ?

look forward to hearing from you.

---

### Post by rudihawk on 2008-03-16
I ran DSL from a flashdisk at one stage. It worked allright but was far from ideal, a tad slow as well (Due to it running through the whole USB thing)

---

### Post by bapaknyaAnak2 on 2008-03-28
I did this  [http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/](http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/) . When I pressed QPU 710.bat file, it asked me to install kqemu, then I installed it to the same directory as QPU710 that I have created in my usb stick. At the boot menu I pressed F6, typed persistent, then it went to all the processes till I got below error message;

An error occured while loading or saving configuration for gome-setting-daemon. Some of your configuration settings may not work properly. 

Then: 

GConf error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBIT, or you have stale NFS locks due to a sistem crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 1: IOR file '/tmp/gconfd-ubuntu/lock/ior' not opened successfully, no gconfd located: Not a directory 2: IOR file '/tmp/gconfd-ubuntu/lock/ior' not opened successfully, no gconfd located: Not a directory. All further errors shown only on terminal.

Any one knows what is going on ???

---

### Post by dcstar on 2008-03-28
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

