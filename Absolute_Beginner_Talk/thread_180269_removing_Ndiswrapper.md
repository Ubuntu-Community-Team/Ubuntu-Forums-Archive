---
title: "removing Ndiswrapper"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by rubrboots on 2006-05-21
Hello I had previously installed Ndiswrapper via synaptic. Now that I have a different wifi card working I removed Ndiswrapper again using synaptic. But when I reboot ndiswrapper continues to load and show up when I lsmod. Why is it still loading when I have removed it? How can I completely remove ndiswrapper?
Thanx

---

### Post by popkid on 2006-05-26
You can blacklist ndiswrapper module so it doesn't load by doing the following

echo blacklist ndiswrapper | sudo tee -a /etc/modprobe.d/blacklist

pK

---

