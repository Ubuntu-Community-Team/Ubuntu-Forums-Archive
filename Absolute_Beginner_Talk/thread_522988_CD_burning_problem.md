---
title: "CD burning problem"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Boris-- on 2007-08-11
Everything works normally, but some cds stop burning in the middle of the progress and I can throw them away. I've tried like 3-4 programs and it's the same everywhere so I don't think it's a software problem. Error reports return something like DMA is disabled and I have to enable it. How to do that? 

Thanks in advance!

---

### Post by ddrichardson on 2007-08-11
```
sudo hdparm -d1 /dev/hdc
```

Where /dev/hdc is the drive to enable dma on

---

