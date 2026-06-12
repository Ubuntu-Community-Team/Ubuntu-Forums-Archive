---
title: "CDU-680/itfchg-source code"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Paul86fxr on 2008-01-30
After many hour of work,  I stiill have not found a reliable way to use my CDU-680 usb modem on 7.10. it works sometimes and for whatever reason, it stops.Franklin-wireless sent me the source code for the interface changer but i am not sure how to use it, I will post it below. My problem is getting the device to switch from USB MASS STORAGE to usb modem in a stable manor, here is what they sent. Maybe someone out there ha some ideas. Thanks:CDU-680 : source code for Linux

typedef struct scsi_ioctl_command {
           unsigned int inlen;
           unsigned int outlen;
           unsigned char data[10];
} Scsi_Ioctl_Command;
#define SCSI_IOCTL_SEND_COMMAND 1
       
Void Rdevchg1()
{
char devname[32];
int fd;
sprintf(devname,"/dev/sg1");  => //may be sg1, sg2, sg3 . when it is
 the
case of CD-ROM 
					=> //may be sda, sdb . when it is
the case of DISK 
fd = open(devname, O_RDWR);
if (fd > 0 ) 
 {
       sic.inlen = 9;
     sic.outlen = 0;
sic.data[0] = 0xFF;
     memcpy(sic.data + 1, "RDEVCHG1", 8);
     ioctl(fd, SCSI_IOCTL_SEND_COMMAND, &sic);
     close(fp);
}
}  

This guy spoke really poor english so he sent this

---

### Post by yellowbread on 2008-02-12
Man, how do you rate? I asked them for the same thing and they said it was "unavailable at this time". I had to figure it out on my own. I wrote my own version which finds the device /dev/sda, /dev/sdb or whatever, unmounts it if it is mounted, (although this part will have trouble if you unplug and plug in a lot of usb devices),  then changes the mode. I've been using it on Gutsy and Hardy ever since to change the mode whenever necessary.

What exactly do you want to do with this code? What do you mean by getting the device to switch in a stable manner?

---

### Post by Paul86fxr on 2008-02-12
I think the code he gave me was the 'itfchg' file, I have had to switch the device the same way you have been 'sudo ./itfchg /sdb/sdc' however, i use a powered hub for my modem and sometimes it hangs in 'mass storage or modem' mode, I got to the point that I would have to reinstall Gusty to get it to work, this was true even if the modem was powered down over night, it seems to alter wvdial settings in some way but the 'wvdial.conf' stays the same, I would be very interested in what code you have written if it has been working well for you. I have since reverted back to Fiesty until I can get some help with this, as far as the code he gave me? I have no idea, it looks like it could possibly be run in shell but I dont understand it. Any of your ideas will be welcomed.

Paul:confused:

---

### Post by spiderbatdad on 2008-02-12
This author, poorly translated, says he finally had to use kppp to run the dialer. [http://translate.google.com/translate?hl=en&sl=es&u=http://www.islascruz.org/html/index.php%3FBlog/SingleView/id/Franklin-CDU-680-en-Slackware-Linux&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3D%2B16d8:6803%26num%3D50%26hl%3Den%26safe%3Doff%26sa%3DG](http://translate.google.com/translate?hl=en&sl=es&u=http://www.islascruz.org/html/index.php%3FBlog/SingleView/id/Franklin-CDU-680-en-Slackware-Linux&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3D%2B16d8:6803%26num%3D50%26hl%3Den%26safe%3Doff%26sa%3DG)

---

### Post by yellowbread on 2008-02-13
Yes, that looks like code related to itfchg. Its c code, but as it stands it would not compile. The stuff I wrote does essentially the same thing. The only advantages my program has over itfchg are that you don't have to bother unmounting the device before changing the mode, you don't have to locate the device at /dev/sd?, the feedback is a little more accurate and informative, and you have the source code so you can change it however you like. I'm at work right now, but when I get home I'll post my code here.

---

### Post by Paul86fxr on 2008-02-13
Thanks Yellowbread, I look foward to it, I'm going to do a clean install of 7.10 in the mean time, I appreciate the info.:)

---

### Post by yellowbread on 2008-02-13
So here's the code.
```

#include <stdio.h>
#include <fcntl.h>
#include <sys/ioctl.h>
#include <linux/fs.h>
#include <strings.h>

/* Returns the line number and the line itself for the line in inputfile that begins with inputstring
   Returns 0 if there is no such line
   Returns -1 and prints an error message if the inputfile can't be opened*/
int find_line(char *inputfile, char *outputline, char *inputstring, int inputlength){
        FILE *fp;
	int linenumber = 0;

	if((fp = fopen(inputfile,"r"))==NULL){
		printf("Unable to open %s.\n", inputfile);
		return -1;
	}
	do{
		if(fgets(outputline, 128, fp)==NULL) return 0;
		linenumber++;
	} while(strncmp(outputline,inputstring,inputlength));
	fclose(fp);

	return linenumber;
}

int main(int argc) {
	char file[26];
	char string[20];
	char devicename[9];
	char line[128];
	int fd;
	struct {
		unsigned int inputlength;
		unsigned int outputlength;
		char data[10];
	} ifchg;

	sprintf(devicename,"/dev/sda");
	sprintf(string,"RDEVCHG1");
	ifchg.inputlength = 9;
	ifchg.outputlength = 0;
	ifchg.data[0] = 0xff;
	memcpy(ifchg.data + 1,string,strlen(string));

	//Check if the device is plugged in and recognized, if so, get the /dev/sd? value.
	sprintf(file,"/proc/scsi/sg/device_strs");
	sprintf(string,"CMOTECH");
	devicename[7] += find_line(file,line,string,strlen(string)) - 1;
	if(devicename[7] < 'a'){
		printf("Modem not found.\n");
		return 1;
	}

	//Check if the device is mounted, if so, unmount it.
	sprintf(file,"/etc/mtab");
	sprintf(string,"/media/CDU680_UMSD");
	if(find_line(file,line,devicename,strlen(devicename)) > 0) umount2(string ,1);

	//Change the mode.
	if((fd = open(devicename,O_RDWR)) <= 0) {
		printf("Unable to open modem.\n");
		return 2;
	}
	usleep(800);
	ioctl(fd,FIBMAP,&ifchg);
	close(fd);
	
	return 0;
}

```
Copy and paste this into a file, save it as anything.c the name doesn't matter, give it a .c extension. cd to wherever you saved the file and then compile with
```
gcc anything.c
```
You will need the package build-essential to do this. There will be a couple warnings that you can safely ignore when it compiles. The result is a file called a.out. You can rename a.out to anything you like, eg changemode with
```
mv a.out changemode
```
Then run
```
sudo ./changemode
```
to get the cdu680 into modem mode. The cdc_acm driver now claims the modem and assigns it to /dev/ttyACM0. You can run wvdialconf to confirm this. The rest is between you and your dialer.

---

### Post by Paul86fxr on 2008-02-14
Cant wait to try it, thank you.

Paul

---

### Post by Paul86fxr on 2008-02-15
I may have done something wrong, here is the output after trying to compile this:paul@Paul-Thinkpad:~/Desktop$ gcc anything2.c
anything2.c:1:19: error: stdio.h: No such file or directory
anything2.c:2:19: error: fcntl.h: No such file or directory
anything2.c:3:23: error: sys/ioctl.h: No such file or directory
anything2.c:4:22: error: linux/fs.h: No such file or directory
anything2.c:5:21: error: strings.h: No such file or directory
anything2.c: In function ‘find_line’:
anything2.c:11: error: ‘FILE’ undeclared (first use in this function)
anything2.c:11: error: (Each undeclared identifier is reported only once
anything2.c:11: error: for each function it appears in.)
anything2.c:11: error: ‘fp’ undeclared (first use in this function)
anything2.c:14: error: ‘NULL’ undeclared (first use in this function)
anything2.c:15: warning: incompatible implicit declaration of built-in function ‘printf’
anything2.c: In function ‘main’:
anything2.c:39: warning: incompatible implicit declaration of built-in function ‘sprintf’
anything2.c:44: warning: incompatible implicit declaration of built-in function ‘memcpy’
anything2.c:44: warning: incompatible implicit declaration of built-in function ‘strlen’
anything2.c:51: warning: incompatible implicit declaration of built-in function ‘printf’
anything2.c:61: error: ‘O_RDWR’ undeclared (first use in this function)
anything2.c:62: warning: incompatible implicit declaration of built-in function ‘printf’
anything2.c:66: error: ‘FIBMAP’ undeclared (first use in this function)
paul@Paul-Thinkpad:~/Desktop$ 




Any ideas on where I went wrong?  Thanks in advance

---

### Post by yellowbread on 2008-02-15
Do you have build-essential installed?

```
sudo apt-get install build-essential
```

---

### Post by Paul86fxr on 2008-02-15
I do now and I did get it to compile, now it says 'unable to open modem' very weird, any other thoughts will be appreciated.

Paul

---

### Post by Paul86fxr on 2008-02-15
also I ran 'dmesg' with these results:[    4.422662] NET: Registered protocol family 20
[    4.422765] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[    4.422802] pnp: 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    4.422839] pnp: 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    4.422877] pnp: 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    4.423761] Time: tsc clocksource has been installed.
[    4.453178] PCI: Bridge: 0000:00:01.0
[    4.453212]   IO window: 3000-3fff
[    4.453247]   MEM window: c0100000-c01fffff
[    4.453282]   PREFETCH window: e0000000-e7ffffff
[    4.453322] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[    4.453357]   IO window: 00004000-000040ff
[    4.453392]   IO window: 00004400-000044ff
[    4.453428]   PREFETCH window: e8000000-ebffffff
[    4.453465]   MEM window: c4000000-c7ffffff
[    4.453500] PCI: Bus 7, cardbus bridge: 0000:02:00.1
[    4.453535]   IO window: 00004800-000048ff
[    4.453570]   IO window: 00004c00-00004cff
[    4.453606]   PREFETCH window: ec000000-efffffff
[    4.453642]   MEM window: c8000000-cbffffff
[    4.453677] PCI: Bridge: 0000:00:1e.0
[    4.453711]   IO window: 4000-8fff
[    4.453748]   MEM window: c0200000-cfffffff
[    4.453783]   PREFETCH window: e8000000-efffffff
[    4.453830] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    4.454202] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    4.454238] PCI: setting IRQ 11 as level-triggered
[    4.454243] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.454677] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    4.454713] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    4.454815] NET: Registered protocol family 2
[    4.491750] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    4.491891] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    4.494064] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    4.495055] TCP: Hash tables configured (established 131072 bind 65536)
[    4.495095] TCP reno registered
[    4.503886] checking if image is initramfs... it is
[    4.955366] Switched to high resolution mode on CPU 0
[    5.234772] Freeing initrd memory: 7057k freed
[    5.234965] Simple Boot Flag at 0x35 set to 0x1
[    5.235249] audit: initializing netlink socket (disabled)
[    5.235298] audit(1203091105.032:1): initialized
[    5.235412] highmem bounce pool size: 64 pages
[    5.237665] VFS: Disk quotas dquot_6.5.1
[    5.237762] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    5.237914] io scheduler noop registered
[    5.237948] io scheduler anticipatory registered
[    5.237982] io scheduler deadline registered
[    5.238037] io scheduler cfq registered (default)
[    5.238144] Boot video device is 0000:01:00.0
[    5.238316] isapnp: Scanning for PnP cards...
[    5.591222] isapnp: No Plug & Play device found
[    5.624243] Real Time Clock Driver v1.12ac
[    5.624394] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    5.624662] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    5.625735] pnp: Device 00:0a activated.
[    5.625934] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    5.626221] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    5.626315] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    5.626948] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    5.627224] input: Macintosh mouse button emulation as /class/input/input0
[    5.627346] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    5.634983] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.635023] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.635228] mice: PS/2 mouse device common for all mice
[    5.635364] EISA: Probing bus 0 at eisa.0
[    5.635403] Cannot allocate resource for EISA slot 1
[    5.635438] Cannot allocate resource for EISA slot 2
[    5.635473] Cannot allocate resource for EISA slot 3
[    5.635508] Cannot allocate resource for EISA slot 4
[    5.636931] Cannot allocate resource for EISA slot 5
[    5.636966] Cannot allocate resource for EISA slot 6
[    5.637001] Cannot allocate resource for EISA slot 7
[    5.637035] Cannot allocate resource for EISA slot 8
[    5.637070] EISA: Detected 0 cards.
[    5.637220] TCP cubic registered
[    5.637272] NET: Registered protocol family 1
[    5.637336] Using IPI No-Shortcut mode
[    5.637557]   Magic number: 12:135:993
[    5.637599]   hash matches device ttyd6
[    5.638026] Freeing unused kernel memory: 364k freed
[    5.670743] input: AT Translated Set 2 keyboard as /class/input/input1
[    5.817499] AppArmor: AppArmor initialized<5>audit(1203091105.532:2):  type=1505 info="AppArmor initialized" pid=1171
[    5.827070] fuse init (API version 7.8)
[    5.833536] Failure registering capabilities with primary security module.
[    5.852810] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    5.852936] ACPI: Processor [CPU] (supports 8 throttling states)
[    5.855070] ACPI: Thermal Zone [THM0] (41 C)
[    6.290427] usbcore: registered new interface driver usbfs
[    6.290492] usbcore: registered new interface driver hub
[    6.290545] usbcore: registered new device driver usb
[    6.292005] USB Universal Host Controller Interface driver v3.0
[    6.292113] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    6.292211] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    6.292215] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    6.292422] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    6.292489] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    6.292661] usb usb1: configuration #1 chosen from 1 choice
[    6.292720] hub 1-0:1.0: USB hub found
[    6.292759] hub 1-0:1.0: 2 ports detected
[    6.382472] SCSI subsystem initialized
[    6.393442] libata version 2.21 loaded.
[    6.396235] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    6.396276] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    6.396373] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    6.396377] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    6.396438] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    6.396504] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    6.396655] usb usb2: configuration #1 chosen from 1 choice
[    6.396716] hub 2-0:1.0: USB hub found
[    6.396754] hub 2-0:1.0: 2 ports detected
[    6.448482] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[    6.448526] Copyright (c) 1999-2006 Intel Corporation.
[    6.498564] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    6.498607] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    6.498705] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    6.498709] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    6.498770] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    6.498837] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    6.498992] usb usb3: configuration #1 chosen from 1 choice
[    6.499055] hub 3-0:1.0: USB hub found
[    6.499094] hub 3-0:1.0: 2 ports detected
[    6.578007] Floppy drive(s): fd0 is 1.44M
[    6.603302] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    6.603346] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[    6.603446] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    6.603451] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    6.603521] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    6.603602] ehci_hcd 0000:00:1d.7: debug port 1
[    6.603640] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    6.603649] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    6.607568] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.607715] usb usb4: configuration #1 chosen from 1 choice
[    6.607783] hub 4-0:1.0: USB hub found
[    6.607823] hub 4-0:1.0: 6 ports detected
[    6.619145] FDC 0 is a National Semiconductor PC87306
[    2.796000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.800000] Time: acpi_pm clocksource has been installed.
[    2.824000] ata_piix 0000:00:1f.1: version 2.11
[    2.824000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    2.824000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.824000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    2.824000] scsi0 : ata_piix
[    2.824000] scsi1 : ata_piix
[    2.824000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
[    2.824000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
[    2.988000] ata1.00: ATA-6: TOSHIBA MK1234GAX, AC001A, max UDMA/100
[    2.988000] ata1.00: 234441648 sectors, multi 16: LBA48 
[    2.996000] ata1.00: configured for UDMA/100
[    3.104000] usb 4-3: new high speed USB device using ehci_hcd and address 2
[    3.236000] usb 4-3: configuration #1 chosen from 1 choice
[    3.236000] hub 4-3:1.0: USB hub found
[    3.236000] hub 4-3:1.0: 4 ports detected
[    3.316000] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4242N, 0201, max UDMA/33
[    3.488000] ata2.00: configured for UDMA/33
[    3.488000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1234GA AC00 PQ: 0 ANSI: 5
[    3.492000] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4242N 0201 PQ: 0 ANSI: 5
[    3.492000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.512000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    3.512000] sd 0:0:0:0: [sda] Write Protect is off
[    3.512000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.512000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.512000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    3.512000] sd 0:0:0:0: [sda] Write Protect is off
[    3.512000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.512000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.512000]  sda:<6>e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:0d:60:fd:82:fd
[    3.744000]  sda1 sda2 <<6>usb 4-3.4: new low speed USB device using ehci_hcd and address 3
[    3.768000]  sda5 >
[    3.768000] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.780000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.796000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.796000] Uniform CD-ROM driver Revision: 3.20
[    3.796000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.800000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.800000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.840000] usb 4-3.4: configuration #1 chosen from 1 choice
[    3.856000] usbcore: registered new interface driver hiddev
[    3.864000] input: HID 062a:0000 as /class/input/input2
[    3.864000] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.7-3.4
[    3.864000] usbcore: registered new interface driver usbhid
[    3.864000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    3.980000] Attempting manual resume
[    3.980000] swsusp: Resume From Partition 8:5
[    3.980000] PM: Checking swsusp image.
[    3.980000] PM: Resume from disk failed.
[    4.028000] kjournald starting.  Commit interval 5 seconds
[    4.028000] EXT3-fs: mounted filesystem with ordered data mode.
[   13.204000] Linux agpgart interface v0.102 (c) Dave Jones
[   13.212000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.220000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.560000] agpgart: Detected an Intel 855PM Chipset.
[   13.688000] agpgart: AGP aperture is 256M @ 0xd0000000
[   14.288000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
[   14.288000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   14.288000] Yenta: Routing CardBus interrupts to PCI
[   14.292000] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
[   14.324000] iTCO_vendor_support: vendor-support=0
[   14.328000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   14.524000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   14.524000] Socket status: 30000020
[   14.524000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   14.524000] cs: IO port probe 0x4000-0x8fff: clean.
[   14.524000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   14.524000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   14.524000] Yenta: CardBus bridge found at 0000:02:00.1 [1014:0552]
[   14.524000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   14.524000] Yenta: Routing CardBus interrupts to PCI
[   14.524000] Yenta TI: socket 0000:02:00.1, mfunc 0x01d21b22, devctl 0x64
[   14.712000] irda_init()
[   14.712000] NET: Registered protocol family 23
[   14.756000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   14.756000] Socket status: 30000086
[   14.756000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   14.756000] cs: IO port probe 0x4000-0x8fff: clean.
[   14.760000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   14.760000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   14.912000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[   14.912000] serio: Synaptics pass-through port at isa0060/serio1/input0
[   14.952000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   14.956000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   14.956000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.968000] input: PC Speaker as /class/input/input4
[   14.968000] parport_pc 00:0b: reported by Plug and Play ACPI
[   14.968000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   14.988000] intel_rng: FWH not detected
[   15.064000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   15.064000] nsc-ircc, chip->init
[   15.064000] nsc-ircc, Found chip at base=0x02e
[   15.064000] nsc-ircc, driver loaded (Dag Brattli)
[   15.064000] nsc_ircc_open(), can't get iobase of 0x2f8
[   15.064000] nsc-ircc, Found chip at base=0x02e
[   15.064000] nsc-ircc, driver loaded (Dag Brattli)
[   15.064000] nsc_ircc_open(), can't get iobase of 0x2f8
[   15.068000] pnp: Device 00:0c disabled.
[   15.160000] pccard: CardBus card inserted into slot 0
[   15.292000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   15.292000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   15.460000] cs: IO port probe 0x100-0x3af: clean.
[   15.460000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.460000] cs: IO port probe 0x820-0x8ff: clean.
[   15.460000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.460000] cs: IO port probe 0xa00-0xaff: clean.
[   15.460000] cs: IO port probe 0x100-0x3af: clean.
[   15.464000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.464000] cs: IO port probe 0x820-0x8ff: clean.
[   15.464000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.464000] cs: IO port probe 0xa00-0xaff: clean.
[   16.220000] intel8x0_measure_ac97_clock: measured 55466 usecs
[   16.220000] intel8x0: clocking to 48000
[   16.468000] lp0: using parport0 (interrupt-driven).
[   16.516000] Adding 3791300k swap on /dev/sda5.  Priority:-1 extents:1 across:3791300k
[   16.824000] EXT3 FS on sda1, internal journal
[   18.876000] ACPI: AC Adapter [AC] (on-line)
[   18.908000] ACPI: Battery Slot [BAT0] (battery present)
[   19.004000] input: Power Button (FF) as /class/input/input5
[   19.008000] ACPI: Power Button (FF) [PWRF]
[   19.056000] input: Lid Switch as /class/input/input6
[   19.060000] ACPI: Lid Switch [LID]
[   19.108000] input: Sleep Button (CM) as /class/input/input7
[   19.108000] ACPI: Sleep Button (CM) [SLPB]
[   19.216000] ACPI: ACPI Dock Station Driver 
[   19.220000] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: found ejectable bay
[   19.220000] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: Adding notify handler
[   19.220000] ACPI: Error installing bay notify handler
[   19.220000] ACPI: Bay [\_SB_.PCI0.IDE0.SCND.MSTR] Added
[   19.244000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   20.308000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   20.524000] input: TPPS/2 IBM TrackPoint as /class/input/input8
[   20.636000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   20.636000] PCI: Setting latency timer of device 0000:00:1f.6 to 64
[   20.804000] ttyS1: LSR safety check engaged!
[   21.184000] ppdev: user-space parallel port driver
[   21.504000] audit(1203091125.939:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5046 profile="/usr/sbin/cupsd"
[   21.616000] IBM machine detected. Enabling interrupts during APM calls.
[   21.616000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   21.616000] apm: overridden by ACPI.
[   21.820000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
[   21.820000] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   21.820000] thinkpad_acpi: ThinkPad EC firmware 1RHT71WW-3.04
[   21.824000] thinkpad_acpi: another device driver is already handling bay events
[   21.824000] thinkpad_acpi: disabling subdriver bay
[   22.204000] Failure registering capabilities with primary security module.
[   22.404000] Bluetooth: Core ver 2.11
[   22.404000] NET: Registered protocol family 31
[   22.404000] Bluetooth: HCI device and connection manager initialized
[   22.404000] Bluetooth: HCI socket layer initialized
[   22.424000] Bluetooth: L2CAP ver 2.8
[   22.424000] Bluetooth: L2CAP socket layer initialized
[   22.524000] Bluetooth: RFCOMM socket layer initialized
[   22.524000] Bluetooth: RFCOMM TTY layer initialized
[   22.524000] Bluetooth: RFCOMM ver 1.8
[   22.560000] Clocksource tsc unstable (delta = -149017146 ns)
[   23.932000] [drm] Initialized drm 1.1.0 20060810
[   23.948000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   23.952000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   26.312000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   26.312000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   26.312000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   27.620000] [drm] Setting GART location based on new memory map
[   27.620000] [drm] writeback test succeeded in 2 usecs
[   87.732000] usb 4-4: new high speed USB device using ehci_hcd and address 4
[   87.864000] usb 4-4: configuration #1 chosen from 1 choice
[   88.008000] usbcore: registered new interface driver libusual
[   88.076000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   88.076000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   88.084000] Initializing USB Mass Storage driver...
[   88.084000] scsi2 : SCSI emulation for USB Mass Storage devices
[   88.084000] usb-storage: device found at 4
[   88.084000] usb-storage: waiting for device to settle before scanning
[   88.084000] usbcore: registered new interface driver usb-storage
[   88.084000] USB Mass Storage support registered.
[   93.084000] usb-storage: device scan complete
[   93.084000] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  4.04 PQ: 0 ANSI: 2
[   93.084000] sd 2:0:0:0: [sdb] 1992337 512-byte hardware sectors (1020 MB)
[   93.088000] sd 2:0:0:0: [sdb] Write Protect is off
[   93.088000] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   93.088000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   93.088000] sd 2:0:0:0: [sdb] 1992337 512-byte hardware sectors (1020 MB)
[   93.088000] sd 2:0:0:0: [sdb] Write Protect is off
[   93.088000] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   93.092000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   93.092000]  sdb: sdb1
[   93.092000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   93.092000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  142.924000] ieee80211_crypt: registered algorithm 'NULL'
[  142.932000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  142.932000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  142.940000] bcm43xx driver
[  142.940000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[  142.940000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[  142.940000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  144.876000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  144.876000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  144.876000] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[  144.876000] cs: memory probe 0xe8000000-0xefffffff: excluding 0xe8000000-0xefffffff
[  144.876000] cs: memory probe 0xc0200000-0xcfffffff: excluding 0xc0200000-0xd01fffff
[  154.548000] NET: Registered protocol family 17
[  155.044000] SoftMAC: Open Authentication completed with 00:1c:f0:58:dd:83
[  159.728000] NET: Registered protocol family 10
[  159.728000] lo: Disabled Privacy Extensions
[  159.728000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  169.768000] eth1: no IPv6 routers present
[  696.304000] usb 4-4: USB disconnect, address 4
[ 3152.632000] usb 4-3.1: new full speed USB device using ehci_hcd and address 5
[ 3152.724000] usb 4-3.1: configuration #1 chosen from 1 choice
[ 3152.824000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3152.824000] usb-storage: device found at 5
[ 3152.824000] usb-storage: waiting for device to settle before scanning
[ 3157.824000] usb-storage: device scan complete
[ 3157.824000] scsi 3:0:0:0: Direct-Access     CMOTECH  Mass Storage     2.31 PQ: 0 ANSI: 6
[ 3157.832000] sd 3:0:0:0: [sdb] 135169 512-byte hardware sectors (69 MB)
[ 3157.832000] sd 3:0:0:0: [sdb] Write Protect is off
[ 3157.832000] sd 3:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 3157.832000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3157.836000] sd 3:0:0:0: [sdb] 135169 512-byte hardware sectors (69 MB)
[ 3157.840000] sd 3:0:0:0: [sdb] Write Protect is off
[ 3157.840000] sd 3:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 3157.840000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3157.840000]  sdb: sdb1
[ 3157.852000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 3157.852000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 3242.464000] program itfchg is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 3242.544000] usb 4-3.1: reset full speed USB device using ehci_hcd and address 5
[ 3243.032000] usb 4-3.1: USB disconnect, address 5
[ 3243.108000] scsi 3:0:0:0: rejecting I/O to dead device
[ 3244.288000] usb 4-3.1: new full speed USB device using ehci_hcd and address 6
[ 3244.380000] usb 4-3.1: configuration #1 chosen from 1 choice
[ 3244.384000] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3244.384000] usb-storage: device found at 6
[ 3244.384000] usb-storage: waiting for device to settle before scanning
[ 3244.468000] cdc_acm 4-3.1:1.0: ttyACM0: USB ACM device
[ 3244.752000] usbcore: registered new interface driver cdc_acm
[ 3244.752000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 3249.384000] usb-storage: device scan complete
[ 3249.384000] scsi 4:0:0:0: Direct-Access     CMOTECH  Mass Storage     2.31 PQ: 0 ANSI: 6
[ 3249.392000] sd 4:0:0:0: [sdb] 135169 512-byte hardware sectors (69 MB)
[ 3249.392000] sd 4:0:0:0: [sdb] Write Protect is off
[ 3249.392000] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 3249.392000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3249.396000] sd 4:0:0:0: [sdb] 135169 512-byte hardware sectors (69 MB)
[ 3249.400000] sd 4:0:0:0: [sdb] Write Protect is off
[ 3249.400000] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 3249.400000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3249.400000]  sdb: sdb1
[ 3249.408000] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 3249.408000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 3274.364000] ttyS1: LSR safety check engaged!
[ 3318.744000] program itfchg is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 3378.816000] usb 4-3.1: reset full speed USB device using ehci_hcd and address 6
[ 3393.888000] usb 4-3.1: device descriptor read/64, error -110
[ 3409.064000] usb 4-3.1: device descriptor read/64, error -110
[ 3409.240000] usb 4-3.1: reset full speed USB device using ehci_hcd and address 6
[ 3424.312000] usb 4-3.1: device descriptor read/64, error -110
[ 3439.488000] usb 4-3.1: device descriptor read/64, error -110
[ 3439.664000] usb 4-3.1: reset full speed USB device using ehci_hcd and address 6
[ 3450.072000] usb 4-3.1: device not accepting address 6, error -110
[ 3450.144000] usb 4-3.1: reset full speed USB device using ehci_hcd and address 6
[ 3460.556000] usb 4-3.1: device not accepting address 6, error -110
[ 3460.556000] sd 4:0:0:0: scsi: Device offlined - not ready after error recovery
[ 3460.556000] sd 4:0:0:0: rejecting I/O to offline device
[ 3460.556000] usb 4-3.1: USB disconnect, address 6
[ 3460.556000] scsi 4:0:0:0: rejecting I/O to dead device
[ 3460.556000] scsi 4:0:0:0: rejecting I/O to dead device
[ 3460.556000] scsi 4:0:0:0: rejecting I/O to dead device
[ 3460.556000] scsi 4:0:0:0: rejecting I/O to dead device
[ 3460.556000] scsi 4:0:0:0: [sdb] READ CAPACITY failed
[ 3460.556000] scsi 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3460.556000] scsi 4:0:0:0: [sdb] Sense not available.
[ 3460.556000] scsi 4:0:0:0: rejecting I/O to dead device
[ 3460.556000] scsi 4:0:0:0: [sdb] Write Protect is off
[ 3460.556000] scsi 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 3460.556000] scsi 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3460.628000] scsi 4:0:0:0: rejecting I/O to dead device
[ 3460.628000] usb 4-3.1: new full speed USB device using ehci_hcd and address 7
[ 3475.700000] usb 4-3.1: device descriptor read/64, error -110
[ 3490.876000] usb 4-3.1: device descriptor read/64, error -110
[ 3491.052000] usb 4-3.1: new full speed USB device using ehci_hcd and address 8
[ 3506.676000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[ 3506.840000] usb 2-2: configuration #1 chosen from 1 choice
[ 3506.844000] scsi5 : SCSI emulation for USB Mass Storage devices
[ 3506.844000] usb-storage: device found at 2
[ 3506.844000] usb-storage: waiting for device to settle before scanning
[ 3511.844000] usb-storage: device scan complete
[ 3511.848000] scsi 5:0:0:0: Direct-Access     CMOTECH  Mass Storage     2.31 PQ: 0 ANSI: 6
[ 3511.852000] sd 5:0:0:0: [sdb] 135169 512-byte hardware sectors (69 MB)
[ 3511.856000] sd 5:0:0:0: [sdb] Write Protect is off
[ 3511.856000] sd 5:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 3511.856000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3511.864000] sd 5:0:0:0: [sdb] 135169 512-byte hardware sectors (69 MB)
[ 3511.868000] sd 5:0:0:0: [sdb] Write Protect is off
[ 3511.868000] sd 5:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 3511.868000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3511.868000]  sdb: sdb1
[ 3511.876000] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 3511.876000] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 3528.104000] ttyS1: LSR safety check engaged!
paul@Paul-Thinkpad:~/Desktop$

---

### Post by spiderbatdad on 2008-02-15
Run lsusb without the CDU-680 inserted in the usb port
(make note of results)
Next run lsusb with the CDU-680 inserted in the usb port
lsusb gives the Vendor and Product IDs:
(compare results and see that a new device ID shows up)

Bus 001 Device 002: ID 16d8:6803

Use dmesg to see if the usbserial module is loaded:

dmesg | grep usbserial
(nothing shows up)

So load the usbserial module and IDs with modprobe:

modprobe usbserial vendor=0x16d8 product=0x6803

Use dmesg to make sure it worked:

dmesg | grep usbserial
usbcore: registered new interface driver usbserial
usbcore: registered new interface driver usbserial_generic

now run ./a.out  from Yellowbread's compiled script.

---

### Post by yellowbread on 2008-02-15
Just to verify: are you running "sudo ./changemode" instead of "./changemode"?
If it didn't need to unmount the device, that's the first place where the lack of sudo would cause a problem.

If that's not the problem, it might have to do with the powered usb hub you are using. If that's the problem, it looks like my program might not do you any good.

Other than that, debugging the program, suggesting lines of code you could insert into the source, compiling and then running it for me, telling me the results, I can't think of anything else. I'm willing to try this if you are.

---

### Post by yellowbread on 2008-02-15
After reading your last post, I have the question: was the device busy when you ran ./changemode?
./changemode will not be able to open the modem if it is already being used (in which case the modem is obviously already in modem mode.)

---

### Post by Paul86fxr on 2008-02-15
I followed the above posts and it still is unable to open modem, I tried the modem direct, not on the powered hub with the same result. How would I debug the program? maybe there is a conflict somewhere, its strange, I even re-downloaded a fresh copy of 7.10 from a different server and installed it. My modem is detected. the modem lights are strange though, I go from red to green, back to red and so on, no blue light at all. Its getting weirder all the time. I really do appreciate all the help and I will try anything, the worst that can happen is I re-install 7.40.

---

### Post by yellowbread on 2008-02-15
First I want to make sure the program is detecting the modem at the correct location. In the source file, there is a section commented at the beginning with

```
//Check if the device is mounted, if so, unmount it.
```

Could you insert the following line just before that comment, recompile, run the resulting a.out and tell me what it says?

```
else printf("Modem found at %s\n",devicename);
```

Also could you post the result of the command in the terminal?

```
mount
```
 
No hurry, I'm off to lift some weights, will be back in about an hour.

---

### Post by Paul86fxr on 2008-02-15
paul@paul-laptop:~$ cd Desktop
paul@paul-laptop:~/Desktop$ gcc anything.c
anything.c: In function ‘main’:
anything.c:44: warning: incompatible implicit declaration of built-in function ‘memcpy’
anything.c:44: warning: incompatible implicit declaration of built-in function ‘strlen’
paul@paul-laptop:~/Desktop$ mv a.out changemode
paul@paul-laptop:~/Desktop$ sudo ./changemode
Modem found at /dev/sdc
Unable to open modem.
paul@paul-laptop:~/Desktop$

---

### Post by Paul86fxr on 2008-02-15
paul@paul-laptop:~$ cd Desktop
paul@paul-laptop:~/Desktop$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
paul@paul-laptop:~/Desktop$ 


hope this is what you needed, thanks

---

### Post by yellowbread on 2008-02-15
Yes that's what I needed. It tells me that the device is being correctly detected at /dev/sdc, and that it is being unmounted sucessfully.
Next try this: towards the bottom there is a line

```
if((fd = open(devicename,O_RDWR)) <= 0) {
```

Change the <= to < so that it reads


```
if((fd = open(devicename,O_RDWR)) < 0) {
```

and try again.

---

### Post by Paul86fxr on 2008-02-15
Getting closer!!!



paul@paul-laptop:~$ cd Desktop
paul@paul-laptop:~/Desktop$ gcc anything.c
anything.c: In function ‘main’:
anything.c:44: warning: incompatible implicit declaration of built-in function ‘memcpy’
anything.c:44: warning: incompatible implicit declaration of built-in function ‘strlen’
paul@paul-laptop:~/Desktop$ mv a.out changemode
paul@paul-laptop:~/Desktop$ sudo ./changemode
[sudo] password for paul:
Modem found at /dev/sdc
Unable to open modem.
paul@paul-laptop:~/Desktop$ sudo ./changemode
Modem found at /dev/sdc
Unable to open modem.
paul@paul-laptop:~/Desktop$

---

### Post by Paul86fxr on 2008-02-15
this is the code as it reads so far:


#include <stdio.h>
#include <fcntl.h>
#include <sys/ioctl.h>
#include <linux/fs.h>
#include <strings.h>

/* Returns the line number and the line itself for the line in inputfile that begins with inputstring
   Returns 0 if there is no such line
   Returns -1 and prints an error message if the inputfile can't be opened*/
int find_line(char *inputfile, char *outputline, char *inputstring, int inputlength){
        FILE *fp;
	int linenumber = 0;

	if((fp = fopen(inputfile,"r"))==NULL){
		printf("Unable to open %s.\n", inputfile);
		return -1;
	}
	do{
		if(fgets(outputline, 128, fp)==NULL) return 0;
		linenumber++;
	} while(strncmp(outputline,inputstring,inputlength));
	fclose(fp);

	return linenumber;
}

int main(int argc) {
	char file[26];
	char string[20];
	char devicename[9];
	char line[128];
	int fd;
	struct {
		unsigned int inputlength;
		unsigned int outputlength;
		char data[10];
	} ifchg;

	sprintf(devicename,"/dev/sda");
	sprintf(string,"RDEVCHG1");
	ifchg.inputlength = 9;
	ifchg.outputlength = 0;
	ifchg.data[0] = 0xff;
	memcpy(ifchg.data + 1,string,strlen(string));

	//Check if the device is plugged in and recognized, if so, get the /dev/sd? value.
	sprintf(file,"/proc/scsi/sg/device_strs");
	sprintf(string,"CMOTECH");
	devicename[7] += find_line(file,line,string,strlen(string)) - 1;
	if(devicename[7] < 'a'){
		printf("Modem not found.\n");
		return 1;
	}
else printf("Modem found at %s\n",devicename);
	//Check if the device is mounted, if so, unmount it.
	sprintf(file,"/etc/mtab");
	sprintf(string,"/media/CDU680_UMSD");
	if(find_line(file,line,devicename,strlen(devicename)) > 0) umount2(string ,1);

	//Change the mode.
	if((fd = open(devicename,O_RDWR)) < 0) {
		printf("Unable to open modem.\n");
		return 2;
	}
	usleep(800);
	ioctl(fd,FIBMAP,&ifchg);
	close(fd);
	
	return 0;
}

---

### Post by spiderbatdad on 2008-02-15
just curious if you run ```
dmesg | usbserial
``` if it shows the modules loaded.

---

### Post by yellowbread on 2008-02-15
Ok. Try changing the third line of this part from this

```
//Change the mode.
if((fd = open(devicename,O_RDWR)) < 0) {
printf("Unable to open modem.\n");
return 2;
}
```

to this

```
//Change the mode.
if((fd = open(devicename,O_RDWR)) < 0) {
printf("Unable to open %s fd = %d\n",devicename,fd);
return 2;
}
```

---

### Post by Paul86fxr on 2008-02-15
paul@paul-laptop:~$ dmesg | usbserial
bash: usbserial: command not found
paul@paul-laptop:~$ cd Desktop
paul@paul-laptop:~/Desktop$ dmesg | usbserial
bash: usbserial: command not found
paul@paul-laptop:~/Desktop$

---

### Post by spiderbatdad on 2008-02-15
> **Paul86fxr said:**
> paul@paul-laptop:~$ dmesg | usbserial
bash: usbserial: command not found
paul@paul-laptop:~$ cd Desktop
paul@paul-laptop:~/Desktop$ dmesg | usbserial
bash: usbserial: command not found
paul@paul-laptop:~/Desktop$

 SORRY ```
dmesg | grep usbserial
```

See post 13 on setting usbserial module. Also that isn't a backslash it's a pipe.

---

### Post by Paul86fxr on 2008-02-15
paul@paul-laptop:~$ dmesg | usbserial
bash: usbserial: command not found
paul@paul-laptop:~$ cd Desktop
paul@paul-laptop:~/Desktop$ dmesg | grep usbserial
[ 6941.356000] usbcore: registered new interface driver usbserial
[ 6941.360000] usbcore: registered new interface driver usbserial_generic
paul@paul-laptop:~/Desktop$

---

### Post by Paul86fxr on 2008-02-15
[ 6941.356000] usbcore: registered new interface driver usbserial
[ 6941.360000] usbcore: registered new interface driver usbserial_generic
paul@paul-laptop:~/Desktop$ sudo ./changemode
Modem found at /dev/sdc
Unable to open modem.
paul@paul-laptop:~/Desktop$ 


after loading modprobe

---

### Post by Paul86fxr on 2008-02-15
paul@paul-laptop:~/Desktop$ gcc anything.c
anything.c: In function ‘main’:
anything.c:44: warning: incompatible implicit declaration of built-in function ‘memcpy’
anything.c:44: warning: incompatible implicit declaration of built-in function ‘strlen’
anything.c: At top level:
anything.c:62: error: expected identifier or ‘(’ before ‘if’
anything.c:66: error: expected declaration specifiers or ‘...’ before numeric constant
anything.c:66: warning: data definition has no type or storage class
anything.c:67: error: expected ‘)’ before ‘(’ token
anything.c:68: warning: data definition has no type or storage class
anything.c:68: warning: parameter names (without types) in function declaration
anything.c:70: error: expected identifier or ‘(’ before ‘return’
anything.c:71: error: expected identifier or ‘(’ before ‘}’ token
paul@paul-laptop:~/Desktop$ 



did I screw up?

---

### Post by Paul86fxr on 2008-02-15
I really appreciate all the help.

---

### Post by yellowbread on 2008-02-15
Maybe you screwed up, maybe I gave you some bad code. Lets start fresh with this. After saving this to a flie, go through the usual cycle of compile, run, post results. This time, try unplugging and reinserting the modem before running the program.

```

#include <stdio.h>
#include <fcntl.h>
#include <sys/ioctl.h>
#include <linux/fs.h>
#include <strings.h>

/* Returns the line number and the line itself for the line in inputfile that begins with inputstring
   Returns 0 if there is no such line
   Returns -1 and prints an error message if the inputfile can't be opened*/
int find_line(char *inputfile, char *outputline, char *inputstring, int inputlength){
        FILE *fp;
	int linenumber = 0;

	if((fp = fopen(inputfile,"r"))==NULL){
		printf("Unable to open %s.\n", inputfile);
		return -1;
	}
	do{
		if(fgets(outputline, 128, fp)==NULL) return 0;
		linenumber++;
	} while(strncmp(outputline,inputstring,inputlength));
	fclose(fp);

	return linenumber;
}

int main(int argc) {
	char file[26];
	char string[20];
	char devicename[9];
	char line[128];
	int fd;
	struct {
		unsigned int inputlength;
		unsigned int outputlength;
		char data[10];
	} ifchg;

	sprintf(devicename,"/dev/sda");
	sprintf(string,"RDEVCHG1");
	ifchg.inputlength = 9;
	ifchg.outputlength = 0;
	ifchg.data[0] = 0xff;
	memcpy(ifchg.data + 1,string,strlen(string));

	//Check if the device is plugged in and recognized, if so, get the /dev/sd? value.
	sprintf(file,"/proc/scsi/sg/device_strs");
	sprintf(string,"CMOTECH");
	devicename[7] += find_line(file,line,string,strlen(string)) - 1;
	if(devicename[7] < 'a'){
		printf("Modem not found.\n");
		return 1;
	}
	else printf("Modem found at %s\n", devicename);
	//Check if the device is mounted, if so, unmount it.
	sprintf(file,"/etc/mtab");
	sprintf(string,"/media/CDU680_UMSD");
	if(find_line(file,line,devicename,strlen(devicename)) > 0) umount2(string ,1);

	//Change the mode.
	if((fd = open(devicename,O_RDWR)) <= 0) {
		printf("Unable to open %s , fd = %d.\n", devicename, fd);
		return 2;
	}
	usleep(800);
	ioctl(fd,FIBMAP,&ifchg);
	close(fd);
	
	return 0;
}

```

---

### Post by spiderbatdad on 2008-02-15
Hopefully Yellowbread will be back to analyse the additional error messages...looks like it failed to compile with the changes. There is another post on this modem where he and I participated. The guy (jwill1515) did get his modem working with yellowbread's program (without altering it.) I assume Yellowbread is h. aving you make changes in order to diagnose possible problems. I'm sure you will get it working soon. I don't know why ./changemode is unable to open the modem. It worked for jwill1515, but we never saw that specific issue. I think there must be a permissions problem somewhere

---

### Post by yellowbread on 2008-02-15
That's pretty much the idea of what I'm trying to do. I' thinking right now that for some reason there is a lock on /dev/sdc from something done previously. If unplugging the device doesn't work, I'm going to actually have to go learn something about the error messages the open function gives.

---

### Post by Paul86fxr on 2008-02-16
Hey! You guys are great!! I dont get discouraged easily (my job is an daily exercise in frustration) and most important i'm learning. Thanks for giving your time for this, here are the results you asked for:



paul@paul-laptop:~$ cd Desktop
paul@paul-laptop:~/Desktop$ sudo ./changemode
[sudo] password for paul:
Modem found at /dev/sdc
Unable to open /dev/sdc , fd = -1.
paul@paul-laptop:~/Desktop$

---

### Post by yellowbread on 2008-02-16
Last bit of information I need before plunging in and figuring out the open function's error codes:

After running sudo ./changemode, what happens when you cd to itfchg's directory and run sudo ./itfchg /dev/sdc

---

### Post by Paul86fxr on 2008-02-16
With no modem plugged in:

paul@paul-laptop:~$ cd Desktop
paul@paul-laptop:~/Desktop$ sudo ./changemode
Modem not found.
paul@paul-laptop:~/Desktop$ 

with modem plugged in:


paul@paul-laptop:~$ cd Desktop
paul@paul-laptop:~/Desktop$ sudo ./changemode
Modem found at /dev/sdc
Unable to open /dev/sdc , fd = -1.
paul@paul-laptop:~/Desktop$ 

After running 'itfchg' with modem plugged in:


paul@paul-laptop:~$ cd Desktop
paul@paul-laptop:~/Desktop$ sudo ./itfchg /dev/sdc
Need read/write permissions for /dev/sdc .
paul@paul-laptop:~/Desktop$ 



after running 'itfchg' with no modem plugged in:



paul@paul-laptop:~$ cd Desktop
paul@paul-laptop:~/Desktop$ sudo ./itfchg /dev/sdc
Need read/write permissions for /dev/sdc .
paul@paul-laptop:~/Desktop$

---

### Post by yellowbread on 2008-02-16
Thanks. The error message you get from itfchg is just telling you that for whatever reason, it is unable to open the file /dev/sdc, it doesn't necessarily have anything to do with permissions. That helps because itfchg and changemode use the same function to open the file. If neither can open the file, the problem is not with the code in itfchg or changemode, but either a problem with your system  or a problem with the modem. On the off chance that you have access to another cdu680, you could try it and see what happens. In the mean time, I'll try to figure out how to get the open function to give us some information about why it is failing. Bear with me, this may take a while.

---

### Post by Paul86fxr on 2008-02-16
[ 2589.268000] scsi 8:0:0:0: Direct-Access     CMOTECH  Mass Storage     2.31 PQ: 0 ANSI: 6
[ 2589.272000] sd 8:0:0:0: [sdb] 135169 512-byte hardware sectors (69 MB)
[ 2589.276000] sd 8:0:0:0: [sdb] Write Protect is off
[ 2589.276000] sd 8:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 2589.276000] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 2589.284000] sd 8:0:0:0: [sdb] 135169 512-byte hardware sectors (69 MB)
[ 2589.288000] sd 8:0:0:0: [sdb] Write Protect is off
[ 2589.288000] sd 8:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 2589.288000] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 2589.288000]  sdb: sdb1
[ 2589.300000] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 2589.300000] sd 8:0:0:0: Attached scsi generic sg2 type 0
paul@paul-laptop:~$ 

This is the output of dmesg as of now.

---

### Post by Paul86fxr on 2008-02-16
Thats fine, also, it does work on fiesty without any problems, I have fiesty on a partition if you want any outputs from it running on that version.

---

### Post by yellowbread on 2008-02-16
So, at the top of the source code, there are a bunch of #include<??> statements. Add one that says 

```
#include<errno.h>
```

Then at the bottom of the file, replace the line

```
	printf("Unable to open %s , fd = %d.\n", devicename, fd);
```

with 

```
	printf("Unable to open %s , errno = %d.\n", devicename, errno);
```

Then go through the save-compile-run-post results cycle.

---

### Post by Paul86fxr on 2008-02-16
paul@paul-laptop:~/Desktop$ mv a.out changemode
paul@paul-laptop:~/Desktop$ sudo ./changemode
[sudo] password for paul:
Modem found at /dev/sdc
Unable to open /dev/sdc , errno = 2.
paul@paul-laptop:~/Desktop$

---

### Post by yellowbread on 2008-02-16
Errno 2 means no such file or directory. Could you post the results of

```
cat /proc/scsi/sg/device_strs
```

and 

```
cat /etc/mtab
```

---

### Post by Paul86fxr on 2008-02-16
paul@paul-laptop:~/Desktop$ cat /proc/scsi/sg/device_strs
ATA             TOSHIBA MK1234GA        AC00
HL-DT-ST        RW/DVD GCC-4242N        0201
CMOTECH         Mass Storage            2.31
paul@paul-laptop:~/Desktop$ 




paul@paul-laptop:~/Desktop$ cat /etc/mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0
paul@paul-laptop:~/Desktop$

---

### Post by yellowbread on 2008-02-16
I'm sorry, I should have been more specific. Could you repeat the cat /etc/mtab command both with the device mounted and with it unmounted?

---

### Post by Paul86fxr on 2008-02-16
paul@paul-laptop:~/Desktop$ cat /proc/scsi/sg/device_strs
ATA             TOSHIBA MK1234GA        AC00
HL-DT-ST        RW/DVD GCC-4242N        0201
CMOTECH         Mass Storage            2.31
paul@paul-laptop:~/Desktop$ cat /proc/scsi/sg/device_strs
ATA             TOSHIBA MK1234GA        AC00
HL-DT-ST        RW/DVD GCC-4242N        0201
paul@paul-laptop:~/Desktop$ 

unmounted 1st
unplugged second


the following is while mounted
paul@paul-laptop:~/Desktop$ cat /proc/scsi/sg/device_strs
ATA             TOSHIBA MK1234GA        AC00
HL-DT-ST        RW/DVD GCC-4242N        0201
CMOTECH         Mass Storage            2.31
paul@paul-laptop:~/Desktop$

---

### Post by Paul86fxr on 2008-02-16
Sorry about that here is mounted:

paul@paul-laptop:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0
paul@paul-laptop:~$ 

This is unmounted:


paul@paul-laptop:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
paul@paul-laptop:~$

---

### Post by yellowbread on 2008-02-16
Its the cat /etc/mtab that I need. According to the cat /proc/scsi/sg/device_strs results, the modem should be at /dev/sdc. The cat /etc/mtab results should show the modem at /dev/sdc when its mounted, no entry for /dev/sdc when its not.

---

### Post by yellowbread on 2008-02-16
So is that entry /dev/sdb1 the modem?

---

### Post by Paul86fxr on 2008-02-16
I think it has to be, its the only change between the two, I have kept everything consistant while doing this i.e usb slot used etc

---

### Post by yellowbread on 2008-02-16
Ok. Reinsert the modem, and run sudo ./itfchg /dev/sdb1from itfchg's directory. It should work. At the moment, I don't have any idea how to fix my program to account for this. At the moment, is the modem plugged into the usb hub? that could account for the modem being on /dev/sdb1 instead of /dev/sdc

---

### Post by Paul86fxr on 2008-02-16
ok, I will do it now

---

### Post by Paul86fxr on 2008-02-16
I tried it and its the same as it was before we started, I must have some kind of hardware conflict, When i first install 7.10 and add no hardware like wireless card etc, it will work with 'itfchg' /dev/sdb. then it seems to stop working for no reason other than I added a wireless card, I will wait for your reply the i will get 7.10 re-installed and not add anything other than cdu680 and see whats different.   Thanks for all the help, 
Paul

---

### Post by yellowbread on 2008-02-16
Just a thought, could you post results of cat /etc/fstab?

---

### Post by Paul86fxr on 2008-02-16
paul@paul-laptop:~/Desktop$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6b1415d7-2603-4431-ba5f-06b0c64a6ea2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c4e4645d-a66e-4c2c-a6a5-2f0cf6eac789 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
paul@paul-laptop:~/Desktop$

---

### Post by Paul86fxr on 2008-02-16
the above is with thw CMOTECH mounted

---

### Post by yellowbread on 2008-02-16
Thanks. Unfortunatley that didn't give me any ideas.

Please keep us informed with the fresh install details. I'd really like to figure out what's going on here.

---

### Post by Paul86fxr on 2008-02-16
i'm on my other box right now, i am reloading 7.10,this pig uses windows arrrgggg, anyway will post when i'm finished.

---

### Post by Paul86fxr on 2008-02-16
ok, i 'm back, I reinstalled 7.10, from live disc, no updates have been added, no network cards or anything else and i'm using the cdu680 right now, started it with sudo ./itfchg /dev/sdb then in terminal used 'execute.sh' that came with the modem, it switched and started right up: if you want me to run any code, i 'm here so ask away.

---

### Post by Paul86fxr on 2008-02-16
will be here most of the day(cold and snowy) i will check the posts regularly

---

### Post by Paul86fxr on 2008-02-16
new output 'dmesg':

[  455.200000] scsi 3:0:0:0: Direct-Access     CMOTECH  Mass Storage     2.31 PQ: 0 ANSI: 6
[  455.208000] sd 3:0:0:0: [sdb] 135169 512-byte hardware sectors (69 MB)
[  455.208000] sd 3:0:0:0: [sdb] Write Protect is off
[  455.208000] sd 3:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[  455.208000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  455.220000] sd 3:0:0:0: [sdb] 135169 512-byte hardware sectors (69 MB)
[  455.220000] sd 3:0:0:0: [sdb] Write Protect is off
[  455.220000] sd 3:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[  455.220000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  455.220000]  sdb: sdb1
[  455.232000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  455.232000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  477.412000] ttyS1: LSR safety check engaged!
[  481.704000] PPP generic driver version 2.4.2
[  481.884000] PPP BSD Compression module registered
[  482.028000] PPP Deflate Compression module registered
paul@paul-laptop:~$


new lsusb:



paul@paul-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 16d8:6843  
Bus 002 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
paul@paul-laptop:~$


paul@paul-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=899913cd-84b1-4dca-8704-d98c9404655b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c4e4645d-a66e-4c2c-a6a5-2f0cf6eac789 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
paul@paul-laptop:~$

---

### Post by Paul86fxr on 2008-02-16
--> CDU680DORA Linux Connection

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- MANUFACTURER: C-MOTECH Co., Ltd.
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
sprintconfig<Warn>: Can't open 'sprintconfig' for reading: No such file or directory
sprintconfig<Warn>: ...starting with blank configuration.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
--> Dialing...

WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT#777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT#777
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Sat Feb 16 13:47:48 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 13669
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: H(
WvDial<*1>: pppd: H(
WvDial<*1>: pppd: H(
WvDial<*1>: local  IP address 70.6.91.146
WvDial<*1>: pppd: H(
WvDial<*1>: remote IP address 68.28.145.69
WvDial<*1>: pppd: H(
WvDial<*1>: primary   DNS address 68.28.146.92
WvDial<*1>: pppd: H(
WvDial<*1>: secondary DNS address 68.28.154.92
WvDial<*1>: pppd: H(

---

### Post by Paul86fxr on 2008-02-16
Here comes the craziness I enabled the restricted driver for 'software modem driver' for eth0 I think{wired connection} and got the same errors for the usb modem and it would not switch, I disabled the driver and here i am, gonna try my broadcom 43xx for my wireless card and see what happens after a warm boot

---

### Post by spiderbatdad on 2008-02-16
was that the result of running ./changemode or ./connect?

Looks like now you need to run ```
sudo wvdialconf
gksu gedit /etc/widial.conf
``` And edit wvdial.conf to remove any semicolons at the beginning of the lines phone, username, password. I believe yellowbread pointed out in another post to put "#777" (no quotes) for the phone number and anything for username and password. You can also add the line Stupid Mode=on
After saving the file, from the terminal ```
sudo wvdial
``` should connect you, unless you have restarted and the modem is not in modem mode.

---

### Post by spiderbatdad on 2008-02-16
meh.

---

### Post by Paul86fxr on 2008-02-16
i ran 'sudo ./connect' and got 'segmentation fault core dumped' i have not tried 'changemode' though i will. I will edit wvdial.conf and see what happens. All is well using my wireless card, 'broadcom43xx' I will try the others and post.

---

### Post by spiderbatdad on 2008-02-16
if wireless is active while trying to use modem, they will compete and cause problems...I guess seg fault is a common problem with the modem...it may be settings in wvdial.conf. You will probably have better luck using a graphical frontend for wvdial...gnome-ppp should do the trick, but you will need to make sure it doesn't write semicolons into /etc/wvdial.conf. If it does, just edit them out, and include the #777, username, password entries.

---

### Post by Paul86fxr on 2008-02-16
i dont think my modem uses wvdial.conf, it seems to use its own default file posted below, wvdial.conf can be empty and it still uses this.


[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
; Phone = <Target Phone Number>
ISDN = 0
; Username = <Your Login Name>
Init1 = ATZ
; Password = <Your Password>
Modem = /dev/ttyACM0
Baud = 460800
Carrier Check= no
Stupid Mode= yes
Phone = #777
Username = sprintpcs
Password = sprintpcs



this is generated and posted on my desktop as a file called  'sprintconfig' while wvdial.conf is empty

---

### Post by Paul86fxr on 2008-02-16
I ran 'changemode' and it said 'unable to open modem' but it runs just fine with sudo./itfchg and i installed all updates and it is still working fine, looks like it was eth0 driver

---

### Post by yellowbread on 2008-02-16
If you do not use wvdial directly, there's no need to worry about wvdial.conf. The ./connect program
from franklin uses wvdial, but it writes its own config file. Is everything, modem, wireless, etc. working the way you want it to now?

---

### Post by Paul86fxr on 2008-02-16
Yes everything is working fine and my thanks go out to you for all the help. I trying now to put together a shell to run: ./itfchg, execute.sh, but i have to research the command to pause the program about 5 seconds before going to execute.sh. I 've got it down, if I could get the program to pause five second for the modem to switch then run execute.sh, i will be able to connect with one command only. Everything is working great.

---

### Post by yellowbread on 2008-02-16
Excellent! Good luck with the shell script.

---

### Post by Paul86fxr on 2008-02-16
I got it, crude but effective. Have a good weekend.

---

