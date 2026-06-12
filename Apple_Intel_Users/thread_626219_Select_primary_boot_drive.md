---
title: "Select primary boot drive"
date: 2007-11-28
forum: Apple Intel Users
---

### Post by DPic on 2007-11-28
Is there a way to change the default partition that an iMac boots to in a dual-boot instead of having to hold down the option key every time the computer starts? 

Also, why does is my Ubuntu drive titled "Windows"?

---

### Post by cyberdork33 on 2007-11-28
> **DPic said:**
> Is there a way to change the default partition that an iMac boots to in a dual-boot instead of having to hold down the option key every time the computer starts? 

Also, why does is my Ubuntu drive titled "Windows"?
[rEFIt]("http://refit.sourceforge.net/")

---

### Post by volanin on 2007-11-28
> Also, why does is my Ubuntu drive titled "Windows"?

The [GPT GUID]("http://en.wikipedia.org/wiki/GUID_Partition_Table") of Linux and Windows partitions is the same.
Apple firmware chooses to print Windows.
:)

---

### Post by DPic on 2007-11-29
> **cyberdork33 said:**
> [rEFIt]("http://refit.sourceforge.net/")


Thanks, not how do i set it to make Ubuntu to boot by default when starting up the computer?

---

### Post by volanin on 2007-11-29
> **DPic said:**
> Thanks, not how do i set it to make Ubuntu to boot by default when starting up the computer?

Uncomment **legacyfirst** in **refit.conf**
:)

---

### Post by DPic on 2007-12-10
> **volanin said:**
> Uncomment **legacyfirst** in **refit.conf**
:)

Okay well that starts up rEFFit but now i need to get Ubuntu to start up by itself.

---

### Post by cyberdork33 on 2007-12-10
> **DPic said:**
> Okay well that starts up rEFFit but now i need to get Ubuntu to start up by itself.

That does cause Ubuntu to boot first... I do not understand what else you want to do. There is a delay... there is an option in the refit.conf to adjust that as well.

---

