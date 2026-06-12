---
title: "KVM on iMac Core Duo 20&quot;"
date: 2007-04-21
forum: Apple Intel Users
---

### Post by niklas-komani on 2007-04-21
Hell Community,
first I want to thank you for this great Distribution I am now able to run on 2 out of my 3 Computers (One Windows System for my Mum remains) Feisty is great, well done.
So now what's my problem:
1. KVM doesn't work
Here is what I did:
after apt-get install kvm qemu kvm-source kvm-utils
and I have added mysqlf to the kvm group.
```

niklas@niklas-iMac:~$ sudo modprobe kvm-intel
Password:
niklas@niklas-iMac:~$ kvm -no-acpi -boot d -cdrom ubuntu-7.04-desktop-i386.iso 
exception 12 (0)
rax 0000000000000238 rbx 0000000000040080 rcx 0000000000002000 rdx 0000000000016600
rsi 00000000ffff0800 rdi 0000000000040000 rsp 0000000000087bdc rbp 0000000000000000
r8  0000000000000000 r9  0000000000000000 r10 0000000000000000 r11 0000000000000000
r12 0000000000000000 r13 0000000000000000 r14 0000000000000000 r15 0000000000000000
rip 000000000000a4bc rflags 00033206
cs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ds 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
es 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ss 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
fs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
gs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
tr 0000 (08850000/00002088 p 1 dpl 0 db 0 s 0 type b l 0 g 0 avl 0)
ldt 0000 (00000000/0000ffff p 1 dpl 0 db 0 s 0 type 2 l 0 g 0 avl 0)
gdt fa4d1/37
idt 0/3ff
cr0 60000010 cr2 0 cr3 0 cr4 0 cr8 0 efer 0
Aborted (core dumped)


```

here is my dmesg output after this:
```

[  749.348000] kvm: msrs: 1

```

Don't know how to get it working properly, since it is a Mac I can't use BIOS settings, vt seems to be enabled though since parallels on OS X could use it.

Another question I have is wether one can get the Radeon X1400 in my 20" iMac to work with  the open radeon driver, fglrx works but it doesn't suport aiglx.

EDIR: i just noticed a problem also described in another Thread here where it happens on a MacBook pro, when I hold a key pressed (for example arrow up or some letter) and then try to move the mouse, it just stands still on the screen, this also is the case for Nexuiz where I can walk and look around at the same time

---

### Post by niklas-komani on 2007-04-26
I hate to bump but this is imho a very important feature especially on a Mac where one can't run every Windows version or other OS on the rela Hardware.
Maybe this topic should be moved to a more general place if noboy here has tried kvm yet.

---

### Post by sklarsky on 2007-04-26
to answer the second question- no - but you can get XGL to work with the fglrx driver and use beryl 0.2.0 from [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) but NOT the ones from the ubuntu universal repository

btw - are you sure thats not an x1600?

-j

---

### Post by bluetoad on 2007-04-26
I'm getting the same sort of thing on an Intel GC11010N motherboard.  This is a Core Duo board.

I found that it is a well-know problem and haven't worked around it yet.

[http://kvm.qumranet.com/kvmwiki/FAQ#head-34a6ebff198dc73f61f9c0fb269cfb8b70e97018](http://kvm.qumranet.com/kvmwiki/FAQ#head-34a6ebff198dc73f61f9c0fb269cfb8b70e97018)
which leads you to
[http://kvm.qumranet.com/kvmwiki/Intel_Real_Mode_Emulation_Problems](http://kvm.qumranet.com/kvmwiki/Intel_Real_Mode_Emulation_Problems)

---

