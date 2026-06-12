---
title: "getting updates offline"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Learn!ng on 2007-08-20
hello can i get updates in iso format for a pc with no inet?

---

### Post by Learn!ng on 2007-08-20
is it not possible?

---

### Post by davidsrsb on 2007-08-20
If you can find anothe Ubuntu machine that is on the Internet, the easiest way is to copy the .deb files in /var/cache/apt/archive onto a usb memory stick

---

### Post by plucky on 2007-08-20
APTonCD will create an ISO file and burn a CD of all updates on an UBUNTU system that is online.
The CD can then be transferred to the offline system and under the SYNAPTIC package manager you can add the CD as a repo. Update Manager will then update your system.

APTon CD is in the repos under Synaptic. Also checkout 
                                                    
[HTML]http://aptoncd.sourceforge.net/index.html[/HTML]

Hope this helps...

---

### Post by Learn!ng on 2007-08-20
> **davidsrsb said:**
> If you can find anothe Ubuntu machine that is on the Internet, the easiest way is to copy the .deb files in /var/cache/apt/archive onto a usb memory stick

so what you mean is that when an ubuntu machine downloads the updates they are stored in that directory as deb files and i can copy them to a cd/external hdd and transfer them to the offline machine?

then do i need to run an application to make sure the deb file runs?  do i have to make sure they are executed in order?

---

### Post by Learn!ng on 2007-08-20
> **plucky said:**
> APTonCD will create an ISO file and burn a CD of all updates on an UBUNTU system that is online.
The CD can then be transferred to the offline system and under the SYNAPTIC package manager you can add the CD as a repo. Update Manager will then update your system.

APTon CD is in the repos under Synaptic. Also checkout 
                                                    
[HTML]http://aptoncd.sourceforge.net/index.html[/HTML]

Hope this helps...

thk for the info... is that the same process of copying the deb files to cd as davidsrsb says but is automated by APTon?

---

### Post by Learn!ng on 2007-08-20
is there no standard iso containing updates that i can download from the net?

---

### Post by Learn!ng on 2007-08-21
at the moment i can't get access to another ubuntu machine ... are there any other alternatives?  download to a harddisk and burn then transfer to the machine?

---

