---
title: "Installing Ubuntu errors"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Darklin99 on 2007-03-06
Hi guys,

Im a new to Ubuntu and Linux in general. I downloaded the 6.10 live CD and tried to install/get it to start on my desktop. the problem i am having is that it will boot to the options menu but when i select start/install Ubuntu it won't load.  it displays a error line about hda not ready. what can this mean? the only hdd in the sys is a SATA drive. can some one offer some insight on this problem? 

thanks,

Darklin

---

### Post by Kateikyoushi on 2007-03-06
What is your motherboard ? Might be a promise sata controller issue.

---

### Post by Darklin99 on 2007-03-06
it is a MSI VIA K8M Neo-V

---

### Post by Kateikyoushi on 2007-03-06
Try to boot with this option.

At boot press F6 then add pci=nomsi to the end.

---

### Post by Darklin99 on 2007-03-06
Thanks that did the trick 
=D

---

