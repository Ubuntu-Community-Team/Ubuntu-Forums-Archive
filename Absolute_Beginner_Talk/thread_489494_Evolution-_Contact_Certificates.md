---
title: "Evolution- Contact Certificates"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by rabideau on 2007-07-01
I have been trying to IMPORT a *Contact Certificate* in evolution and nothing happens.  No errors, no addition... nothing.  I have looked high and low to see if anyone else may have had this problem.  I can find none... 

I have one *.asc certificate that I am trying to import.  I am also unable to add my own certificate .  I am guessing that I am having a stupid user problem.  Any ideas???

Thanks!

---

### Post by cleverselfreferentialname on 2007-07-05
I am not sure, but I have a hunch that the solution might involve installing an evolution extension/plugin/whatevertheycall'em pertaining to PGP/GPG. Who and what generated these certificates? Are they PGP then, or X.509?

---

### Post by matiasv on 2008-06-18
I have the same issue, but in my case the certificate are working but not displayed. I can encrypt messages and check signatures even without seeing the certificate.

See bug: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/233620](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/233620)

---

### Post by SeanCondon on 2008-07-17
I doesn't look like this has been fixed in 2.22.3.1 which has been released today. 

BTW does anyone know what extension Evolution is looking for in Contact Certificates? When I browse for Contact Certificates, through Import the filter is set to "All email Certificate Files", but the .p7c and .pem files in the folder cannot be seen in the view, until I select the filter "All files"

Sean

---

