---
title: "kernels and  symbol resolution  ?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by tom_adams on 2007-01-02
I don't understand something basic about  kernels and modules. 

I installed open-scsi-2.0.730.   The iscsid daemon service and the iscsiadm tools work a little bit (they are discovering shared storage on a rlinux/openfiler appliance).  

The "make install" process for open-scsi replaced  the isci_tcp.ko and scsi_transport_iscsi.ko   located at /lib/modules/2.6.17-10-generic/kernel/drivers/scsi. It also created a file called libiscsi.ko.

**Question**: These .ko files are modules that make up the running kernel?

When I start the open-scsi iscsid daemon process ... I find  77 messages in dmesg that complain about "Unknown symbol" ... they look like this "**iscsi_tcp: Unknown symbol iscsi_conn_start**".

**Question**: Does this mean that the iscsid code is looking for the symbols in the kernel and they are not there?    So the make install process for open-iscsi  did not alter/addto the kernel?  Maybe the symbols are defined in the .ko modules referenced above but the resolution process is not looking there?

**Question**: If the open-isci code expects these symbols in the kernel and they are not there, then I will be forced to build a new kernel?   Will it be difficult for me to build a new kernel?

Thanks for taking the time to read this and respond?

---

