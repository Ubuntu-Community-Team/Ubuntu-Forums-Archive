---
title: "Weird noises coming from computer in Ubuntu, but not in Linux"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by BOZG on 2007-10-02
Whenever I open something in Ubuntu, there's a quiet but high pitched noise coming from my PC as if something is booting up.  I dual boot both Ubuntu and Windows and I never have the same problem with Windows.  The noise is a little irritating because it happens every time I open something.

---

### Post by dca on 2007-10-02
Is it your CPU fan?

---

### Post by BOZG on 2007-10-02
Doesn't seem to be.  It's almost like the sound of something in the internal speaker but I don't think it's from there.  

Even if it was the fan, why would it make that noise in Ubuntu but not in Windows?  It actually makes that noise even if I scroll now.

---

### Post by kellemes on 2007-10-02
Is it maybe only when you move the mouse?
Or simply opening a window and not moving the mouse also gives noise?

---

### Post by BOZG on 2007-10-02
When I move the mouse, there's no sound.  But if I use the scroll wheel, it makes the noise.

Or when I open a window, it'll make it the noise.

---

### Post by dca on 2007-10-02
If you go to System -> Preferences -> Sound -> and then click on the sound tab.  If you click on any of the sounds available from the drop-down and click 'play' does it sound like what you're hearing?  I know it's a way out test but I'm stumped...  I mean I tried running Ubuntu 64-bit on an Intel P4 HT it the fan would go nuts occassionally.  If I backed it down to the 32-bit vers or disbaled HT in BIOS it was fine...

---

### Post by BOZG on 2007-10-02
All my sounds other than Login and Logout are disabled.

---

### Post by alienexplorers on 2007-10-02
I have a simular problem that only occures while scrolling with the mouse scroll wheel.  I get a clicking and a high pitch squeal through my pc speaker.  Don't know what makes the sound though it is annoying.

---

### Post by tgalati4 on 2007-10-02
Post the output of:

>cat /proc/interrupts

Perhaps there is a shared interrupt between the mouse and the sound card that is causing one to affect the other.

---

### Post by santiagoward2000 on 2007-10-02
I don't know if this is the case, but my monitor did some really annoying noises when I tested Kubuntu Edgy. I could fix this by lowering the refresh rate.

---

### Post by BOZG on 2007-10-02
> **tgalati4 said:**
> Post the output of:

>cat /proc/interrupts

Perhaps there is a shared interrupt between the mouse and the sound card that is causing one to affect the other.

stephen@stephen-desktop:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:    2613018        290   IO-APIC-edge      timer
  1:       5142          4   IO-APIC-edge      i8042
  6:          4          1   IO-APIC-edge      floppy
  7:          1          0   IO-APIC-edge      parport0
  8:          2          1   IO-APIC-edge      rtc
  9:          0          0   IO-APIC-fasteoi   acpi
 12:     433148          2   IO-APIC-edge      i8042
 14:      38013          1   IO-APIC-edge      ide0
 16:    1739058     410428   IO-APIC-fasteoi   libata, eth0
 17:     336001          1   IO-APIC-fasteoi   libata, HDA Intel
 18:          2          1   IO-APIC-fasteoi   ohci1394
 19:          1          1   IO-APIC-fasteoi   ehci_hcd:usb1
 20:         21          1   IO-APIC-fasteoi   ohci_hcd:usb2
 21:    1018332          1   IO-APIC-fasteoi   nvidia
NMI:          0          0 
LOC:    2613266    2613262 
ERR:          1
MIS:          0

---

### Post by tgalati4 on 2007-10-02
You don't seem to have an interrupt conflict.  But you do have a Non-Maskable Interrupt (NMI).  This is normally a memory error--and it gives the location: LOC: 2613266 2613262

Have you run memtest86+ on your system?  Perhaps you need to reseat your RAM.

Also, post the output of:

>dmesg | tail -n 50

---

### Post by nowshining on 2007-10-02
by the way Linux is the Underlying Operating System while Ubuntu is the GUI.

---

### Post by avik on 2007-10-02
> **nowshining said:**
> by the way Linux is the Underlying Operating System while Ubuntu is the GUI.

Actually, GNU/Linux is the operating system, and Ubuntu is GNU/Linux plus a set of applications and other packages put together in a coherent manner so you don't have to do it yourself.

---

### Post by OliverN on 2007-10-02
> **alienexplorers said:**
> I have a simular problem that only occures while scrolling with the mouse scroll wheel.  I get a clicking and a high pitch squeal through my pc speaker.  Don't know what makes the sound though it is annoying.

I get it too. never thought about it much, though, with me it's barely discernible. I've got an ati x1400 video card.

---

### Post by nowshining on 2007-10-02
> **avik said:**
> Actually, GNU/Linux is the operating system, and Ubuntu is GNU/Linux plus a set of applications and other packages put together in a coherent manner so you don't have to do it yourself.

"GNU/Linux is the operating system," = what I said I just left out the GNU part which is referring to the License.
"GNU/Linux plus a set of applications and other packages put together in a coherent manner so you don't have to do it " = U just detailed it more than I did, however i didn't say the application part - however thst is what I meant, GNU again is the part I left out because it again refers to the License but not the Actual Operating System.

---

### Post by BOZG on 2007-10-03
> **nowshining said:**
> by the way Linux is the Underlying Operating System while Ubuntu is the GUI.

And if you'd read the first post, you'd see it was a typo. :)

---

### Post by nowshining on 2007-10-03
actually linux is not a typo, actually something wasn't working in ur brain right, in other words the CPU was at 100 percent on something else, I know because my brain gets that way too.. :P

---

### Post by BOZG on 2007-10-03
Ha ha.

---

### Post by BOZG on 2007-10-03
> **tgalati4 said:**
> You don't seem to have an interrupt conflict.  But you do have a Non-Maskable Interrupt (NMI).  This is normally a memory error--and it gives the location: LOC: 2613266 2613262

Have you run memtest86+ on your system?  Perhaps you need to reseat your RAM.

Also, post the output of:

>dmesg | tail -n 50


stephen@stephen-desktop:~$ dmesg | tail -n 50
[   16.968000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.220000] nvidia: module license 'NVIDIA' taints kernel.
[   17.472000] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   17.472000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 21
[   17.472000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   17.472000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.11  Wed Jun 13 18:21:22 PDT 2007
[   17.540000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   17.624000] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   17.624000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 17
[   17.624000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   17.832000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   18.112000] fuse init (API version 7.8)
[   18.124000] lp0: using parport0 (interrupt-driven).
[   18.164000] Adding 971924k swap on /dev/disk/by-uuid/e834c09f-2f85-4b7a-88af-ee38a51c721b.  Priority:-1 extents:1 across:971924k
[   18.284000] EXT3 FS on hda3, internal journal
[   18.432000] NET: Registered protocol family 10
[   18.432000] lo: Disabled Privacy Extensions
[   18.472000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   18.528000] NTFS volume version 3.1.
[   24.584000] Using specific hotkey driver
[   24.636000] input: Power Button (FF) as /class/input/input4
[   24.636000] ACPI: Power Button (FF) [PWRF]
[   24.636000] input: Power Button (CM) as /class/input/input5
[   24.636000] ACPI: Power Button (CM) [PWRB]
[   24.736000] ibm_acpi: ec object not found
[   24.784000] No dock devices found.
[   24.892000] pcc_acpi: loading...
[   25.068000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ processors (version 2.00.00)
[   25.068000] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0x8
[   25.068000] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xa
[   25.068000] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0xc
[   25.068000] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0xe
[   25.068000] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x10
[   25.068000] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x12
[   30.772000] ppdev: user-space parallel port driver
[   31.356000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   31.356000] apm: disabled - APM is not SMP safe.
[   31.588000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   31.676000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   31.680000] NFSD: starting 90-second grace period
[   32.932000] Bluetooth: Core ver 2.11
[   32.932000] NET: Registered protocol family 31
[   32.932000] Bluetooth: HCI device and connection manager initialized
[   32.932000] Bluetooth: HCI socket layer initialized
[   33.040000] Bluetooth: L2CAP ver 2.8
[   33.040000] Bluetooth: L2CAP socket layer initialized
[   33.108000] Bluetooth: RFCOMM socket layer initialized
[   33.108000] Bluetooth: RFCOMM TTY layer initialized
[   33.108000] Bluetooth: RFCOMM ver 1.8
[   44.308000] eth0: no IPv6 routers present



I ran memtest86+ a few days ago, didn't report anything strange.  I'll try reseating my RAM and running it again now.  

I've also noticed that periodically, the noise stops but never for long.

---

### Post by BOZG on 2007-10-03
Ok, I resat my RAM and ran cat /proc/interrupts again and it seems to have removed the NMI error anyway.

> stephen@stephen-desktop:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:      45686        288   IO-APIC-edge      timer
  1:         43          4   IO-APIC-edge      i8042
  6:          4          1   IO-APIC-edge      floppy
  7:          0          0   IO-APIC-edge      parport0
  8:          2          1   IO-APIC-edge      rtc
  9:          0          0   IO-APIC-fasteoi   acpi
 12:      11812          2   IO-APIC-edge      i8042
 14:      11155          1   IO-APIC-edge      ide0
 16:         23          1   IO-APIC-fasteoi   ehci_hcd:usb1, ohci_hcd:usb2
 17:      23110          1   IO-APIC-fasteoi   eth0, HDA Intel
 18:       1886          1   IO-APIC-fasteoi   libata
 19:          0          0   IO-APIC-fasteoi   libata
 20:          2          1   IO-APIC-fasteoi   ohci1394
 21:      13185          1   IO-APIC-fasteoi   nvidia
NMI:          0          0 
LOC:      45861      45867 
ERR:          0
MIS:          0

I did one pass on memtest86+ and beside having spent the most boring 22 minutes of my life starting at the screen, it gave me no errors.

---

### Post by tgalati4 on 2007-10-03
You are running power-stepping on your CPU:

[ 25.068000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ processors (version 2.00.00)
[ 25.068000] powernow-k8: 0 : fid 0x12 (2600 MHz), vid 0x8
[ 25.068000] powernow-k8: 1 : fid 0x10 (2400 MHz), vid 0xa
[ 25.068000] powernow-k8: 2 : fid 0xe (2200 MHz), vid 0xc
[ 25.068000] powernow-k8: 3 : fid 0xc (2000 MHz), vid 0xe
[ 25.068000] powernow-k8: 4 : fid 0xa (1800 MHz), vid 0x10
[ 25.068000] powernow-k8: 5 : fid 0x2 (1000 MHz), vid 0x12

When the CPU goes to idle, it throttles down.  When you move the mouse, it spins up again.  This can cause a noise in the crystal circuitry as it steps up and down.  If the stepping creates electronic noise, then it can get into the sound circuitry as well.

Try turning off the stepping and see if the noise goes away.

---

### Post by BOZG on 2007-10-03
I haven't noticed any problems since I resat the RAM so I'll see how it goes.  How do I turn off stepping?  BIOS menu?

---

### Post by tgalati4 on 2007-10-04
In a terminal:

>apropos powernow

Perhaps

>man powernowd

You may be able to disable it in BIOS under the power savings settings.  A forum search on powernow may give some clues.  I don't have any AMD hardware so I don't have experience with it.

If the RAM fixed it, then don't mess with it.  Or mess with it.  It is Linux and it's meant to me tinkered with.

---

### Post by BOZG on 2007-10-04
>apropos powernow comes up with:

```
stephen@stephen-desktop:~$ apropos powernow
powernowd (1)        - control the speed and voltage of cpus

```


>man powernowd comes up with:
```
POWERNOWD(1)                                                      POWERNOWD(1)

NAME
       powernowd - control the speed and voltage of cpus

SYNOPSIS
       powernowd [options]

DESCRIPTION
       This  is  a  simple  client  to  the cpufreq driver, and uses the sysfs
       interface in Linux kernel version 2.6.  You need a supported cpu, and a
       kernel that supports sysfs to run this daemon.

       The name is somewhat misleading, as any processor supported by the ker&#8208;
       nel cpufreq driver will work, not just processors supporting AMD’s Pow&#8208;
       erNow! technology.  This daemon works best with processors that support
       more then 2 frequency steps,  like  those  with  AMD’s  PowerNow!,  and
       Intel’s Pentium M family.

OPTIONS
       -h     Prints a help message.

       -d     Don’t  detach from terminal (default is to detach and run in the  
                background)

       -v     Increase output verbosity, can be used more than once.

       -q     Quiet mode, only emergency output.

       -n     Include nice’d processes in calculations.

       -m     Modes of operation, 0 = SINE, 1 = AGGRESSIVE (default), 2 = PAS&#8208;
              SIVE, 3 = LEAPS

       -s     Frequency step in kHz (default = 100000)

       -p     Polling frequency in msecs (default = 1000)

       -u     CPU usage upper limit percentage [0 .. 100, default 80]

       -l     CPU usage lower limit percentage [0 .. 100, default 20]

MODES
       There are 4 modes supported by this client:

Mode  0,  SINE,  changes the frequency as a sine wave function, raising
       the frequency by "step" Hz every time the CPU usage goes over 80%,  and
       decreases it by "step" Hz when the CPU usage falls under 20%.

       Mode 1, AGGRESSIVE, changes frequency by a sawtooth function.     Imme&#8208;
       diately jumps to the highest frequency whenever  CPU  usage  goes  over
       80%,  and decreases by "step" Hz as usage drops below 20%.  This is the
       default behavior.

       Mode 2, PASSIVE, is the inverse of  AGGRESSIVE.   Immediately  jump  to
       lowest  frequency when usage drops below 20%.  Raise by "step" Hz if it
       goes above 80%.

       Mode 3, LEAPS, immediately jumps to the highest frequency if  usage  is
       above  80%,  and  immediately jumps to the lowest frequency if usage is
       below 20%.

PHILOSOPHY
       Why another CPUFreq client daemon?

       Some other daemons are better suited for two speed states,  and  toggle
between two states based upon load.  This daemon does a better job han&#8208;
       dling intermediate steps.

       Other daemons are written in Perl, Python, or C++.  This is a simple  C
       program.

       Some other daemons rely on APM or ACPI.  The sysfs interface to the 2.6
       kernel is simple, completely sufficient, and completely portable to all
       architectures that support the CPUfreq support in the kernel.

       Some  other daemons change thier behavior based upon battery status, AC
       status, temperature, etc.  What good is having a nice  powerful  laptop
       if  you  can’t  use  it at full speed, even for a few seconds, while on
       battery power?  This daemon just measures CPU load, and bases decisions
       solely upon that.

       SMP  systems are supported, making this daemon useful for servers, too!

AUTHOR
       The powernowd program was written by John Clemens <clemej@alum.rpi.edu>

       This  manual  page was written by Bdale Garbee <bdale@gag.com>, for the
       Debian project (but may be used by others).



```

---

### Post by BOZG on 2007-10-04
The weird sound is back anyway.

---

### Post by nowshining on 2007-10-04
man and then the programs name gives the manual on how to use the named program and what commands are acceptable, and one can use. :) to exit out of the man pages or manuels (both are acceptable names) type the letter "q" on ur keyboard.

---

