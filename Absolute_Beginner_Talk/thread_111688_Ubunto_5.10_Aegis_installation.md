---
title: "Ubunto 5.10 Aegis installation"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by Browser_ice on 2006-01-02
I have installed the Aegis package. It says successful but I cannto find any trace of it in any menus.

Is it normal ?

It is supposed to be that hard to find once a package like that is installed ?

Will I be able to simply right click on a folder/file to access Aegis ?

I want to have right click access (like above) and to put it on the desktop menu bar.

How does it compare to the rest of the Anti-virus software ?
Is it reliable/safe ?

---

### Post by bluefrog on 2006-01-03
use applications > system tools > applications menu editor  to add a menu wherever you want.

for the menu  use the following command line   gksudo aegis-virus-scanner

if you want to open the scanner from a terminal use
sudo aegis-virus-scanner

if you don't sudo or gksudo you won't be able to update file::scan but it will work nevertheless...

james

PS if you have only linux in your network or if you don't use it as a mail server/file server for your network you don't really need a virus scanner. if you have an email/file server for your network with windows pcs in it you should consider clam anti virus. if only have file server i guess aegis will be enough.

---

### Post by bluefrog on 2006-01-03
after having tested aegis on a virus I have (somefool.dat) I would not recommend you to use this scanner. the virus was not found. (while it is found by clamav)

james

---

