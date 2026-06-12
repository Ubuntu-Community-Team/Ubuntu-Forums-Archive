---
title: "Using a Canon PIXMA MX850 scanner with 32bit Ubuntu-14.o4?"
date: 2015-02-06
forum: Apple Hardware Users
---

### Post by hrandiac on 2015-02-06
I am attempting to set-up a Canon PIXMA MX850 printer/scanner for use on 32bit Ubuntu-14.04. The OS is running in a vertual environment 
under VMware Fusion-6.0.5. The Canon network printer is recognized by Trusty, but not the scanner. I am a newby to Linux. Any help would be appreciated. Thank you, Ivan Craig

---

### Post by pdc on 2015-02-06
so the open-source programme sane that supports scanning in linux, says your device is completely supported [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) 

____________

this may have something to do with the virtual environment 

another possibility is to install the latest version of sane from here [https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git) ...........by necessity as not an official package, it is thereby labelled untrusted but in the world of scanner support, Rolf is very much relied on.

---

### Post by StephenG on 2015-05-20
Is there any reason this scanner/printer must be connected to the computer physically, rather than wirelessly, for the scan function to work?  Neither Xsane nor Simple Scan can find the device.  I've got a Pixma mx922

---

