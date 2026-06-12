---
title: "partioning"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by poysama on 2007-07-04
i made three partitions

1..ext3 - / 2.5gb
2..ext3 -  /home 15gb
3..swap -1.5gb

which should i set to logical? primary? 

btw, i will increase the / (root) size to 5gb

can i use live cd to repartition?

---

### Post by smoker on 2007-07-04
you can have up to four primary partitions, so i would set all three to be primary, you can use the partitioner (gparted, i think), on the live cd to do the partitions.

---

### Post by poysama on 2007-07-04
soo..being logical or primary doesnt matter at all?

---

### Post by dptxp on 2007-07-04
Do not make the 4th one Primary unless you do not want more.
You need 4 GB for /. You shall be adding more programs. Where will they go ?

---

