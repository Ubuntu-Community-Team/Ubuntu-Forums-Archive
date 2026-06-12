---
title: "VMWare, XP and Ubuntu"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2007-02-28
I would like to run Ubuntu in a virtual machine on my Win2K (work machine) laptop. I went to the VMWare.com website and found the free VMPlayer, but the description leads me to believe I need a product other than the free download so I can do what I need: 

[INDENT]*"VMware Inc makes VMware Player available free of charge to run guest virtual machines produced by other VMware products: it cannot itself create new virtual machines."*[/INDENT]

I this all I need to run Ubuntu in a virtual machine on the Win2K platform?

---

### Post by arochester on 2007-02-28
You need a VMPlayer and a Virtual Appliance. Go here: [http://www.vmware.com/vmtn/appliances/directory/693](http://www.vmware.com/vmtn/appliances/directory/693)

---

### Post by rjfioravanti on 2007-02-28
You need VMWare Server to make new machines, you dont need VMWare player at all

[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

---

### Post by Sleestack on 2007-02-28
Thank you. I'm still a little confused, though. Once I install the VMPlayer, is the appliance simply an ISO used to install Edgy Eft?

---

### Post by rjfioravanti on 2007-02-28
Install VMWare Server

Then make sure you have a windows application that you can mount ISO files on to emulate CD Drives, I use Daemon Tools

Then you can mount the ubuntu OS image on your Daemon tools or whatever you are using

Open VMWare server
- choose local host
- click File -> New -> Virtual Machine
- click Next
- click typical
- select Linux radio button
- choose Ubuntu from the drop down list
- pick a name and location
- use bridged networking

etc

Then when you load the machine, your ubuntu image will act like a live cd, because it is mounted and vmware will treat it like your CD Drive (you may have to tell it to)

---

### Post by Sleestack on 2007-02-28
Excellent. Thanks for your help.

---

