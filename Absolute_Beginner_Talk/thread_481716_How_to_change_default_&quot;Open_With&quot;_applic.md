---
title: "How to change default &quot;Open With&quot; application in nautils for remote files?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by magnav0x on 2007-06-22
Ok, well I initially installed Screem and it was set as my default PHP editor in Nautils.  I uninstalled Screem and installed gPHPEdit and successfully changed Nautils to open PHP files with gPHPEdit on my local files.

Here is where the trouble is.  When I connect via SSH in nautils (sftp) and I open PHP files, Nautils opens them with gEdit.  I've tryed going to "Open With" and chose Custom command and specified 'gphpedit'.  It opens fine, but I have to do it every time for remote files or else it opens with gEdit.  

How can I change this?  Why is it not using the same default applications as local PHP files?

Thanks in advance!

---

### Post by Inxsible on 2007-06-23
Right click a php file (probably a remote one ??), then go to the Properties. Go to the Open With tab and select the radio button beside gphpedit. If gphpedit is not in the list you can add it by clicking the Add button below. 


Hope that helps !

---

### Post by NaSiO6 on 2007-09-22
hi!
its pretty silly of me to ask.. but how do you 'add' applications if they are not in the applications list.
i can see a 'custom command line', does it have to do soemthing with that?

Thanks

---

