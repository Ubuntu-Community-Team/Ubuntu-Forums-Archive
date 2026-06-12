---
title: "Trouble importing photos"
date: 2007-02-24
forum: Art &amp; Design
---

### Post by eamonn on 2007-02-24
Hi,

Hi,

I just bought a Kodak Z710 digital camera at Best Buy. It takes lovely photographs but whenever I plut the USB board into my laptop, after being notified by Ubuntu that a digital camera has been detected, I get the following message: 

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

I was thinking that I may need to login as the root user (because it mentioned that I only have "read/write" access) but I'm not sure. I have no idea what "sdc2xx, stv680, or spca50x are. Does anyone know how to remedy this problem?
-Eamonn

---

### Post by compwiz18 on 2007-02-24
My first idea would be the same as yours: try logging in as root somehow (not sure how you would go about doing this - maybe gksudo something ??

---

### Post by ankara on 2007-02-26
> **compwiz18 said:**
> My first idea would be the same as yours: try logging in as root somehow (not sure how you would go about doing this - maybe gksudo something ??

this solution worked for me. 

(for the noobs :) )
got to ubuntu menu, System > preferences > Removable Drives and Media > Cameras'
and then simply put gksu (with a space afterwards) in front of whatever text is there already for the option to import pictures whenever camera is connected. 
HTH

---

