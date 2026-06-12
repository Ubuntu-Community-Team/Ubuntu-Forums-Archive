---
title: "How to know what Grachic Card i'm using"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by kokas on 2006-06-01
Ok the subject says it all....it may seem ridiculous but I don't remember if it is ATI or Nvidia and I did look at the device manager but I couldn't find any info...

Any help ?

---

### Post by tonyr on 2006-06-01
In a terminal do
```

lspci | grep VGA

```

---

### Post by bluevoodoo1 on 2006-06-01
cat /etc/X11/xorg.conf


look for this section...
Section "Device"
	Identifier	"NVIDIA FX 5500"
	Driver		"nvidia"
	BusID		"PCI:2:9:0"

---

### Post by kokas on 2006-06-01
Problem solved...thank you guys...the people here are the best

VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] 

:)

---

