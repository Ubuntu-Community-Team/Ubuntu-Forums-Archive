---
title: "[SOLVED] No Internet - Vista in a VM"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-08-10
Ok, I had Vista installed in VMware server before, but now I'm using VirtualBox. I used the Bridged Networking option in VMWS. But I have no idea how to do it in Virtual Box. How do I do bridged networking in Vbox?

---

### Post by felicity on 2007-08-11
This is from the VirtualBox website FAQ's:
Windows Vista guests
* There is no networking in Windows Vista guests initially because, unfortunately, with Vista, Microsoft dropped driver support for the virtual AMD PCnet card that we are providing. See "Troubleshooting" -> "Windows guests" in the [User Manual]("http://www.virtualbox.org/wiki/Downloads") for a solution. The VirtualBox Guest Additions of version 1.4.0 contain the AMD PCnet driver.

---

### Post by Nekiruhs on 2007-08-11
> **felicity said:**
> This is from the VirtualBox website FAQ's:
Windows Vista guests
* There is no networking in Windows Vista guests initially because, unfortunately, with Vista, Microsoft dropped driver support for the virtual AMD PCnet card that we are providing. See "Troubleshooting" -> "Windows guests" in the [User Manual]("http://www.virtualbox.org/wiki/Downloads") for a solution. The VirtualBox Guest Additions of version 1.4.0 contain the AMD PCnet driver.
Thank you. That fixed it nicely!

---

