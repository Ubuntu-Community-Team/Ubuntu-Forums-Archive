---
title: "sd card reader not recognised, not seen."
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by stoer on 2006-10-02
[COLOR="Red"][SIZE="5"]Thread closed - waiting for EDGY.[/SIZE][/COLOR]

hi all,
Just a quick question.
I've tried the forums, i see stuff such as "updating the kernel", to "mounting issues".
just wondering if anyone has some "easy and straightforward advice for a novice"?
I'm using Ubuntu, Gnome on my laptop.
Built in sd (multi card) card reader.

dmesg | tail gives the following

```
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xf6c9b650 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf6c9b640 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xf6c9b650 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf6c9b640 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xdfb91b50 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfb91b40 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xdfb91b50 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfb91b40 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xf6c9b650 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf6c9b640 still mapped
steve@laptop:~$ dmesg | tail
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xf6c9b650 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf6c9b640 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xf6c9b650 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf6c9b640 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xdfb91b50 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfb91b40 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xdfb91b50 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfb91b40 still mapped
[17182442.856000] [fglrx:firegl_rmmap] *ERROR* map 0xf6c9b650 still in use (map_count=1)
[17182442.856000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf6c9b640 still mapped
```

And lspci the following

```
0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4

```

dmesg | tail seems to freak out and i'm sorry i've no idea what the output here implies.  Apart from the card reader everything else appears to be working like a train.

---

### Post by amo-ej1 on 2006-10-02
the dmesg | tail output is related to something wrong with the drivers of your ati graphics card. And not related to your card reader issue.

---

### Post by stoer on 2006-10-02
> **amo-ej1 said:**
> the dmesg | tail output is related to something wrong with the drivers of your ati graphics card. And not related to your card reader issue.

Oh...
Everything seems to be ok with the graphics, 

 fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5946 (8.27.10)

Games work etc, 3d renedering etc.

I'll leave that for now... unless it's causing a problem further or you know what the problem/cure is.?
Thanks for replying though

---

### Post by Sef on 2006-10-02
I know the current kernel in Dapper can't read sd cards.  That will come with the new kernel in Edgy.

---

### Post by stoer on 2006-10-02
> **Sef said:**
> I know the current kernel in Dapper can't read sd cards.  That will come with the new kernel in Edgy.

Ok, thanks for the clear answer.
Then i shan't beat myself up trying to reslove this.
Cheers.

---

