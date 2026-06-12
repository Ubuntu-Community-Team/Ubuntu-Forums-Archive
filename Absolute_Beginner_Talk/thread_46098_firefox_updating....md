---
title: "firefox updating..."
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-07-03
When I go to synaptic it shows that I have the latest version of firefox. However, I want to add some extensions to the browser (dev toolbar etc). When I go to firefox extensions page though it says I need to upgrade firefox. I have downloaded the installer package but it looks to be the same version as reported in synaptic...what is going on?

---

### Post by Kvark on 2005-07-03
First double check that you have the latest version of firefox from apt-get/synaptic.

Then type about:config in the address field in firefox, and change the value of "general.useragent.vendorSub" to "1.0.4".

Ubuntu forgot to update that version number when adding the security updates.



As the firefox extension site says:
> 
[SIZE=4]Firefox on Ubuntu[/SIZE]

You appear to be using the Firefox package provided by Ubuntu Linux. Ubuntu distributed a new version of Firefox which contains the security fixes from Firefox 1.0.4, however, they did not update the version number, so we have no way to tell whether your copy of Firefox contains the security fixes or not. A request to Ubuntu to update the version number has been filed at [Ubuntu Bug 10681](https://bugzilla.ubuntu.com/show_bug.cgi?id=10681). A workaround you can use to get access to addons.mozilla.org is given in comment 3 on that bug. Please ensure you have updated to the latest Firefox package using apt-get, Synaptic, or the Ubuntu Update Manager before trying the workaround.

---

### Post by mike1138 on 2005-07-06
Might this have caused a problem with Evolution? I have Evolution set to display all messages as text only, and before I "updated" Firefox, when I got e-mail with html, it would prompt me to open the message in Firefox.

This no longer happens. Now I have to save the .html file and drag it to Firefox. Double clicking won't even work.

Any help?

 ](*,)

---

