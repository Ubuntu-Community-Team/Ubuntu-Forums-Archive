---
title: "Intel 980 X - ASUS P6X58D Prem One Cores missing"
date: 2011-10-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by riderepe on 2011-10-30
I recently updated to UBUNTU Studio 11.10 and did a check of /proc/cpuinfo the results are as follows:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 44
model name	: Intel(R) Core(TM) i7 CPU       X 980  @ 3.33GHz
stepping	: 2
cpu MHz		: 3340.722
cache size	: 12288 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes[U]
fpu_exception	: yes[/U]
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc up arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat epb dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6681.44
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

 Note CPU Core is incorrect it should be 6 and siblings should be 6 as well. 
  I then did a "sudo dmidecode" with the results as follows (only mother board and CPU info provided due to size):

# dmidecode 2.9
SMBIOS 2.5 present.
79 structures occupying 3002 bytes.
Table at 0x000F0700.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 1201   
	Release Date: 11/01/2010
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 2048 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 8.15
...
Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer INC.
	Product Name: P6X58D PREMIUM
	Version: Rev 1.xx
	Serial Number: 105244630001571
	Asset Tag: To Be Filled By O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To Be Filled By O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0
....
Handle 0x0004, DMI type 4, 40 bytes
Processor Information
	Socket Designation: LGA1366
	Type: Central Processor
	Family: <OUT OF SPEC>
	Manufacturer: Intel            
	ID: C2 06 02 00 FF FB EB BF
	Version: Intel(R) Core(TM) i7 CPU X 980 @ 3.33GHz            
	Voltage: 1.2 V
	External Clock: 133 MHz
	Max Speed: 3333 MHz
	Current Speed: 3333 MHz
	Status: Populated, Enabled
	Upgrade: Other
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: 0x0007
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.
	Core Count: 6
	Core Enabled: 6
	Thread Count: 12
	Characteristics:
		64-bit capable

   Note the number of cores (6) and number of threads (12) is correctly reported. 
  Even the System Monitor reports only 1 CPU where before the upgrade it reported 6. I also booted from the install disk and cpuinfo reported the incorrect value of 1 core and 1 sibling. 
   At the moment I am downloading the latest Debian iso to boot from the install disk to compare. 
   I may have missed something in the doc that explains this but I have yet to find it. I shall continue to debug on my side but if anyone has any ideas, I would appreciate the help.
 Thanks and be well

---

### Post by riderepe on 2011-10-31
I tried Debian and the same issue. Next check was hardware. I have a 500 gb hard drive in port 1 of the Marvel Storage controller. I had problems with Linux  when my SSD Drives were connected to the Marvell. On a whim I disconnected the drive from the the controller and disconnected the power to the drive (drive unused) and the 12 CPUs now appear in System Monitor and CPUINFO is correct.
   I figure it is either the MARVELL Controller or the power supply; i.e. at the upper limit of my 850 watt supply.
   Regardless, the problem has gone away. If anyone can shed more light on this I would appreciate it.
Be Well

---

