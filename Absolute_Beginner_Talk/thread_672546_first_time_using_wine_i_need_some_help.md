---
title: "first time using wine i need some help"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by 900donuts on 2008-01-19
i'm trying to install battlefield 1942 on my computer using wine this is my first time using wine for anything also space on my computer is cramped so i need to make sure it installs on my second  harddrive which has more free space 

i already installed the recent version wine of wine what do i do next?

thanks in advance:)

---

### Post by jleaker01z on 2008-01-19
According to the wine appdb the newest version of wine wont work with bf1942.  So you will probably have to uninstall it and install the next older version.  To install a game under wine, click places and find your cd rom.  Then right click setup.exe and choose open with other application (unless the Open with wine option is available).  Under the other application menu, click to open with a custom command, and in the field that pops up just type 'wine'.  Setup should commence then.

---

### Post by 900donuts on 2008-01-19
how do i install an older version? (that test was on 7.04)

and how do i set it to install on the second harddrive?

---

### Post by jleaker01z on 2008-01-19
Sourceforge is always a good place to look for multiple version of anything.  Its also a good source for anything Linux.

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803)

Linux uses what is called the Logical Volume Manager.  Unless you told it not to, the LVM takes control of all your hard drives and combines them to make them look like one big one.

---

### Post by 900donuts on 2008-01-19
the old version is not on source forge i'll just take my chances with 0.9.53 i tried runing setup.exe and this is what the terminal said

commander@droid1138-desktop:~$ cd /media/DISC_1_BF1942_1
commander@droid1138-desktop:/media/DISC_1_BF1942_1$ wine setup.exe
wine: Unhandled page fault on read access to 0x99c00000 at address 0x7bc46450 (thread 0009), starting debugger...
First chance exception: page fault on read access to 0x99c00000 in 32-bit code (0x7bc46450).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc46450 ESP:0034fd90 EBP:0034feb8 EFLAGS:00010286(   - 00      -RISP1)
 EAX:00000000 EBX:7bc85434 ECX:ffffffff EDX:00400000
 ESI:004096cc EDI:99c00000
Stack dump:
0x0034fd90:  00110000 00000002 00000020 0034fe28
0x0034fda0:  00000000 00000000 00000000 00000000
0x0034fdb0:  004096cc 7bc7cb90 7bc8d630 7bc7cb90
0x0034fdc0:  0034fe14 0034fe18 00000000 00000000
0x0034fdd0:  00000000 00000000 00000000 99c00000
0x0034fde0:  00000000 18000004 7bc602ba 7bc85434
Backtrace:
=>1 0x7bc46450 in ntdll (+0x36450) (0x0034feb8)
  2 0x7bc47e1b LdrInitializeThunk+0xf6() in ntdll (0x0034ff08)
  3 0x7b86eb0a in kernel32 (+0x4eb0a) (0x0034ffe8)
  4 0xb7e7a1cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc46450: repne scasb %es:(%edi)
Modules:
Module  Address                 Debug info      Name (16 modules)
PE        400000-  42c000       Deferred        setup
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Export          ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ef91000-7ef9c000       Deferred        libnss_files.so.2
ELF     7ef9c000-7efa6000       Deferred        libnss_nis.so.2
ELF     7efa6000-7efbe000       Deferred        libnsl.so.1
ELF     7efbe000-7efc7000       Deferred        libnss_compat.so.2
ELF     7efc7000-7efec000       Deferred        libm.so.6
ELF     b7cf9000-b7cfd000       Deferred        libdl.so.2
ELF     b7cfd000-b7e47000       Deferred        libc.so.6
ELF     b7e47000-b7e5f000       Deferred        libpthread.so.0
ELF     b7e73000-b7f87000       Export          libwine.so.1
ELF     b7f89000-b7fa5000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
0000000a 
        0000000b    0
00000008 (D) D:\setup.exe
        00000009    0 <==
Backtrace:
=>1 0x7bc46450 in ntdll (+0x36450) (0x0034feb8)
  2 0x7bc47e1b LdrInitializeThunk+0xf6() in ntdll (0x0034ff08)
  3 0x7b86eb0a in kernel32 (+0x4eb0a) (0x0034ffe8)
  4 0xb7e7a1cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

---

### Post by jleaker01z on 2008-01-19
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7591](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7591)

According to the Wine appdb it wont install with 0.9.53...The previous link I gave you should take you straight to the older versions of Wine for Ubuntu on Sourceforge.

They also have 0.9.52, but it is only available as source code:

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)

To install from source, uninstall 0.9.53 via Add/Remove under applications.  Download the .tar.bz2 file from Sourceforge.  Use the archive manager to extract it.  Open a terminal, cd to the directory you extracted it to, then type in the following commands:

sudo ./configure
sudo make
sudo make install

---

### Post by kostkon on 2008-01-19
Assuming that you have installed it from the *Wine repository*, then you can downgrade to the previous version by doing
```
sudo apt-get install wine=0.9.52~winehq0~ubuntu~7.10-1
```

In case the above will not work or if you have installed your Wine from a *.deb* package file, then simply visit the [*WineHQ .deb packages archive*]("http://wine.budgetdedicated.com/archive/index.html") and download the package file of the previous version (0.9.52, or any older version you like).

I hope I helped you somehow.

---

### Post by 900donuts on 2008-01-19
i downgraded to 0.9.52 heres the terminal output

```
wine: Unhandled page fault on read access to 0x99c00000 at address 0x7bc46428 (thread 0009), starting debugger...
First chance exception: page fault on read access to 0x99c00000 in 32-bit code (0x7bc46428).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc46428 ESP:0034fd90 EBP:0034feb8 EFLAGS:00010286(   - 00      -RISP1)
 EAX:00000000 EBX:7bc858d4 ECX:ffffffff EDX:00400000
 ESI:004096cc EDI:99c00000
Stack dump:
0x0034fd90:  00110000 00000002 00000020 0034fe28
0x0034fda0:  00000000 00000000 00000000 00000000
0x0034fdb0:  004096cc 7bc7c510 7bc8da90 7bc7c510
0x0034fdc0:  0034fe14 0034fe18 00000000 00000000
0x0034fdd0:  00000000 00000000 00000000 99c00000
0x0034fde0:  00000000 18000004 7bc60206 7bc858d4
Backtrace:
=>1 0x7bc46428 in ntdll (+0x36428) (0x0034feb8)
  2 0x7bc47df3 LdrInitializeThunk+0xf6() in ntdll (0x0034ff08)
  3 0x7b86eafa in kernel32 (+0x4eafa) (0x0034ffe8)
  4 0xb7e361cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc46428: repne scasb %es:(%edi)
Modules:
Module  Address                 Debug info      Name (16 modules)
PE        400000-  42c000       Deferred        setup
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Export          ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7efa4000-7efaf000       Deferred        libnss_files.so.2
ELF     7efaf000-7efc7000       Deferred        libnsl.so.1
ELF     7efc7000-7efec000       Deferred        libm.so.6
ELF     7efed000-7eff7000       Deferred        libnss_nis.so.2
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7cb5000-b7cb9000       Deferred        libdl.so.2
ELF     b7cb9000-b7e03000       Deferred        libc.so.6
ELF     b7e03000-b7e1b000       Deferred        libpthread.so.0
ELF     b7e2f000-b7f43000       Export          libwine.so.1
ELF     b7f45000-b7f61000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\setup.exe
        00000009    0 <==
Backtrace:
=>1 0x7bc46428 in ntdll (+0x36428) (0x0034feb8)
  2 0x7bc47df3 LdrInitializeThunk+0xf6() in ntdll (0x0034ff08)
  3 0x7b86eafa in kernel32 (+0x4eafa) (0x0034ffe8)
  4 0xb7e361cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
```

---

### Post by kostkon on 2008-01-19
> **900donuts said:**
> i downgraded to 0.9.52 heres the terminal output

```
wine: Unhandled page fault on read access to 0x99c00000 at address 0x7bc46428 (thread 0009), starting debugger...
First chance exception: page fault on read access to 0x99c00000 in 32-bit code (0x7bc46428).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc46428 ESP:0034fd90 EBP:0034feb8 EFLAGS:00010286(   - 00      -RISP1)
 EAX:00000000 EBX:7bc858d4 ECX:ffffffff EDX:00400000
 ESI:004096cc EDI:99c00000
Stack dump:
0x0034fd90:  00110000 00000002 00000020 0034fe28
0x0034fda0:  00000000 00000000 00000000 00000000
0x0034fdb0:  004096cc 7bc7c510 7bc8da90 7bc7c510
0x0034fdc0:  0034fe14 0034fe18 00000000 00000000
0x0034fdd0:  00000000 00000000 00000000 99c00000
0x0034fde0:  00000000 18000004 7bc60206 7bc858d4
Backtrace:
=>1 0x7bc46428 in ntdll (+0x36428) (0x0034feb8)
  2 0x7bc47df3 LdrInitializeThunk+0xf6() in ntdll (0x0034ff08)
  3 0x7b86eafa in kernel32 (+0x4eafa) (0x0034ffe8)
  4 0xb7e361cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc46428: repne scasb %es:(%edi)
Modules:
Module  Address                 Debug info      Name (16 modules)
PE        400000-  42c000       Deferred        setup
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Export          ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7efa4000-7efaf000       Deferred        libnss_files.so.2
ELF     7efaf000-7efc7000       Deferred        libnsl.so.1
ELF     7efc7000-7efec000       Deferred        libm.so.6
ELF     7efed000-7eff7000       Deferred        libnss_nis.so.2
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7cb5000-b7cb9000       Deferred        libdl.so.2
ELF     b7cb9000-b7e03000       Deferred        libc.so.6
ELF     b7e03000-b7e1b000       Deferred        libpthread.so.0
ELF     b7e2f000-b7f43000       Export          libwine.so.1
ELF     b7f45000-b7f61000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\setup.exe
        00000009    0 <==
Backtrace:
=>1 0x7bc46428 in ntdll (+0x36428) (0x0034feb8)
  2 0x7bc47df3 LdrInitializeThunk+0xf6() in ntdll (0x0034ff08)
  3 0x7b86eafa in kernel32 (+0x4eafa) (0x0034ffe8)
  4 0xb7e361cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
```


OK. According to the [*Wine Application DB* page for the game]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1370"), it is supposed to work with Wine versions from 0.5.0 to 0.5.2, but not 0.5.3.

Checking the comments on the page, and since your installation is the thing that fails, I saw that some people had installed it by copying all the discs of the game to the hard disk, and then running the setup.

The other way is to install it directly from the discs but you need to make sure that you have your CD/DVD drive mounted in the wine configuration. To do this, or to check that you are OK, then open a terminal and do
```
winecfg
```
Select the *Drives* tab, and check if your CD/DVD drive is there. If not, add it yourself.

---

