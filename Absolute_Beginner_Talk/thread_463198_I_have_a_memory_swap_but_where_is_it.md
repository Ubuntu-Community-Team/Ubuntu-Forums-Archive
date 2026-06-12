---
title: "I have a memory swap but where is it"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-06-03
I have a memory swap and when I go to the system monitor it does not show up at all.

---

### Post by taurus on 2007-06-03
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
free
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Inxsible on 2007-06-03
The swap is never mounted. so it wont show up in the File Systems tab in the System Monitor.

If you click on the Resources tab, you will see the memory usage and the swap usage graphs

---

### Post by jonward0690 on 2007-06-03
Ok here is the what I get.  

jon@jon-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       2066288     459616    1606672          0      11636     247636
-/+ buffers/cache:     200344    1865944
Swap:            0          0          0
jon@jon-desktop:~$ sudo fdisk -l
Password:

---

### Post by jonward0690 on 2007-06-03
> **Inxsible said:**
> The swap is never mounted. so it wont show up in the File Systems tab in the System Monitor.

If you click on the Resources tab, you will see the memory usage and the swap usage graphs

Well why has it always showed up till today when I was resizing resisizing my partitons

---

### Post by Inxsible on 2007-06-03
> **jonward0690 said:**
> Well why has it always showed up till today when I was resizing resisizing my partitons

Under the File Systems tab in the System Monitor

---

### Post by jonward0690 on 2007-06-03
Yea but now I can't suspend my computer eather cause you need the swap to do that

---

### Post by bashologist on 2007-06-03
I don't know if this'll help, but you can find your mounted swap partition like this:
```
swapon -s
```

---

### Post by jonward0690 on 2007-06-03
> **bashologist said:**
> I don't know if this'll help, but you can find your mounted swap partition like this:
```
swapon -s
```

It doe'nt show up

---

### Post by ageilers on 2007-06-03
Looks like you hosed your swap partition. you need to open a partition editor to see if you even have a swap partition anymore. Maybe while resizing it you removed it. It would have been unpartitioned space ~512-1024MB.

---

