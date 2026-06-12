---
title: "vmware trouble"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by baldr on 2006-07-14
i am quite new to ubuntu and linux.

I have been having trouble with VMware i keep getting the following error

"Unable to change virtual machine power state: The process exited with an error:
End of error message."

here is my vmware tmp file

```
Jul 14 21:28:16: vmui| Log for VMware Server pid=12206 version=1.0.0 build=build-27828 option=Release
Jul 14 21:28:17: vmui| Using log file /tmp/vmware-balder/ui-12206.log
Jul 14 21:28:17: vmui| HAL04LoadHALLibraries: Could not dlopen libhal.so.0.
Jul 14 21:28:17: vmui| HAL05LoadGlibLibrary: Could not dlopen libdbus-glib-1.so.1.
Jul 14 21:28:17: vmui| HAL05Init: HAL05 Initialized successfully.
Jul 14 21:28:17: vmui| SMBIOS: can't open /dev/mem
Jul 14 21:28:17: vmui| VmhsHostInfoPopulateSystem:  Could not get information from smbios to populate VMDB.
Jul 14 21:28:17: vmui| HOSTINFO: Seeing AMD CPU, numCoresPerCPU 1 numThreadsPerCore 1.
Jul 14 21:28:17: vmui| HOSTINFO: This machine has 1 physical CPUS, 1 total cores, and 1 logical CPUs.
Jul 14 21:28:18: vmui| System libcrypto.so.0.9.7 library is older than our library (90707F < 90709F)
Jul 14 21:28:19: vmui| Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: _Stop and _Stop
Jul 14 21:28:19: vmui| Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: _Forward and _Forward
Jul 14 21:28:19: vmui| Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: _Information and Information
Jul 14 21:28:29: vmui| VMUIGtkVmdb_LoadDevice: unhandled device class vcpu

```

here is my ls -lrta vm/win2k
```
-rw------- 1 balder balder 2147221504 2006-07-12 01:18 Windows 2000 Professional-f002.vmdk
-rw-r--r-- 1 [user of vm process] [group of vm process]    47215 2006-07-12 01:50 vmware-2.log
-rw-r--r-- 1 [user of vm process] [group of vm process]      42060 2006-07-12 20:04 vmware-1.log
-rw-r--r-- 1 [user of vm process] [group of vm process]      62930 2006-07-13 00:47 vmware-0.log
-rw------- 1 [user of vm process] [group of vm process]  860566016 2006-07-13 21:05 Windows 2000 Professional-f007.vmdk
-rw------- 1 [user of vm process] [group of vm process] 2147221504 2006-07-13 21:05 Windows 2000 Professional-f006.vmdk
-rw------- 1 [user of vm process] [group of vm process] 2147221504 2006-07-13 21:45 Windows 2000 Professional-f005.vmdk
-rw------- 1 [user of vm process] [group of vm process] 2147221504 2006-07-13 23:48 Windows 2000 Professional-f004.vmdk
-rw------- 1 [user of vm process] [group of vm process] 2147221504 2006-07-13 23:48 Windows 2000 Professional-f003.vmdk
-rw------- 1 [user of vm process] [group of vm process] 2147221504 2006-07-13 23:49 Windows 2000 Professional-f001.vmdk
-rw------- 1 [user of vm process] [group of vm process]       8664 2006-07-13 23:49 nvram
-rw-r--r-- 1 [user of vm process] [group of vm process]      41810 2006-07-13 23:49 vmware.log
-rwxr-xr-x 1 [user of vm process] [group of vm process]        298 2006-07-14 18:59 Windows 2000 Professional.vmx
drwxr-xr-x 2 [user of vm process] [group of vm process]       4096 2006-07-14 21:14 .
drwxrwxrwt 3 [user of vm process] [group of vm process]       4096 2006-07-14 21:14 ..

```

i have tried restrating vmware, doing an init 1; init 5, restarting the whole system moving all of the vmware files from one dir to another and i always get the same thing. 

one intresting thing that i noticed is that when i moved the files from on dir to another i gained 64.4mb of avalible memory on the partition with the vm machine.

before i moved the data i had the following on the vm partition

Total: 13.5Gb  free: 625.4mb  avalible: 0b

after i had 

Total: 13.5Gb  free: 625.4mb  avalible: 64.4mb

*this info was gathered using "system monitor" - devices

another question would be why dont i have 625.4 avalible i.e. why isn't all my free data avalible like the other partitions.  fuser /vm (the mount) produces no output


any help will be apricated, thanks

---

### Post by baldr on 2006-07-14
i forgot, her is the vmx file
```
 cat vm/win2k/Windows\ 2000\ Professional.vmx
virtualHW.version = "1"
memsize = "276"
floppy0.fileName = "/dev/fd0"
usb.present = "TRUE"
displayName = "/media/vm/windows2K/Windows 2000 Professional.vmx"
guestOS = "win2000pro"
priority.grabbed = "normal"
priority.ungrabbed = "normal"

floppy0.startConnected = "FALSE"
undopoint.action = "keep"

```

---

### Post by baldr on 2006-07-14
oh yer i also ran /usr/bin/vmware-config.pl, no diffrence

ill have to get a better memory so i only need to post once.  the really anyoing things is, i'll probly remember something else in 15 mins and have to post again

---

