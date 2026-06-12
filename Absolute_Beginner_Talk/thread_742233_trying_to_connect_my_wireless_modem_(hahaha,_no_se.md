---
title: "trying to connect my wireless modem (hahaha, no seriously...)"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by h-town on 2008-04-01
So I'm trying it from another angle this time. Mainly through the ndiswrapper installation tool. 

So I've downloaded my wireless driver:

[http://support.gateway.com/support/drivers/getFile.asp?id=20449&dscr=Gateway%20Intel%20Wireless%20Network%20Card%20DriverRevision:%2010.1.0.13&uid=156075824](http://support.gateway.com/support/drivers/getFile.asp?id=20449&dscr=Gateway%20Intel%20Wireless%20Network%20Card%20DriverRevision:%2010.1.0.13&uid=156075824)

and I've started ndiswrapper, but when I click on add driver it says to select the inf file which somewhat perplexes me since the driver is a .exe that I downloaded from gateway

what can I do?

---

### Post by wolfen69 on 2008-04-01
did you check restricted drivers manager to see if it is in there?

---

### Post by ugm6hr on 2008-04-01
Start from the beginning.  Otherwise we may end up leading you down the garden path.

Which version of Ubuntu are you using?

Post the output from:
```
lshw -C network
iwlist scan
```

And let us know what other angles you have tried.

---

### Post by wolfen69 on 2008-04-01
also, do in terminal:
```
lspci
```
after you find out what intel wireless card it is, go here [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&DwnldId=13000&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&DwnldId=13000&lang=eng)   to download the driver. having an .exe will not help you.

---

### Post by prshah on 2008-04-01
> **h-town said:**
> somewhat perplexes me since the driver is a .exe that I downloaded from gateway
what can I do?

The exe file MAY be a self-extractor. You can run it in Wine or (easier) just rename it to a .zip and then you can use archive manager to open it and extract the files.

Eg
```
cp D00508-001-001.exe D00508-001-001.exe.zip
```

Then right-click the .zip file and "Open with Archive Manager"

(Tried to download it to check, but the 79Mb tag defeated me).

---

