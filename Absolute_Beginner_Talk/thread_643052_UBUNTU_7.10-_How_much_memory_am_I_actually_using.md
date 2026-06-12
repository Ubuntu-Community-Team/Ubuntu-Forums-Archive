---
title: "UBUNTU 7.10- How much memory am I actually using"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by ghoran on 2007-12-17
I have 256 Meg of ram.
It looks like I am using a lot of ram!!

Top shows that I am using 199 meg of ram and 114 meg of swap.
System monitor shows 121 of user memory. Why the difference?
I am only running firefox and a terminal.


top - 11:39:15 up  2:30,  2 users,  load average: 1.19, 0.66, 0.39
Tasks:  97 total,   1 running,  96 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.3%us,  1.3%sy,  0.0%ni, 86.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    255940k total,   199076k used,    56864k free,     3584k buffers
Swap:   329292k total,   114340k used,   214952k free,    80460k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                      
 4871 root      15   0 88768 9952 4208 S  7.3  3.9   2:43.88 Xorg                                                                                                         
 5998 ash       15   0 83424  10m 8708 S  3.0  4.3   0:03.39 gnome-terminal                                                                                               
 5972 ash       15   0  185m  65m  18m S  2.7 26.4   5:39.83 firefox-bin                                                                                                  
 6125 ash       15   0  2360 1152  876 R  0.7  0.5   0:00.71 top                                                                                                          
 5148 ash       15   0 17800 8628 7304 S  0.3  3.4   0:08.91 metacity                                                                                                     
    1 root      16   0  2952 1064  472 S  0.0  0.4   0:01.72 init                                                                                                         
    2 root      20  -5     0    0    0 S  0.0  0.0   0:00.01 kthreadd                                                                                                     
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                                  
    4 root      39  19     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0                                                                                                  
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                                   
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 events/0                                                                                                     
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.01 khelper                                                                                                      
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                                    
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid

---

### Post by diatribe on 2007-12-17
use free -m

---

### Post by ghoran on 2007-12-17
Wow,
Looks like I need to add memory

ash@ash-desktop:/etc$ free -m
             total       used       free     shared    buffers     cached
Mem:           249        217         32          0          5         87
-/+ buffers/cache:        123        126
Swap:          321        111        209
ash@ash-desktop:/etc$

---

### Post by diatribe on 2007-12-17
512 is a good starting point, but a gb would be preferable; ram is fairly cheap also.  for instance:

             total       used       free     shared    buffers     cached
Mem:           946        928         18          0        131        589
-/+ buffers/cache:        207        739
Swap:          972          0        972

---

### Post by ghoran on 2007-12-17
I could use help determining what memory is in my machines and what they could take.
I believe they are both DDR (not DDR2).
What is the max I can go with?

---

### Post by emil.s on 2007-12-17
> **ghoran said:**
> I could use help determining what memory is in my machines and what they could take.
I believe they are both DDR (not DDR2).
What is the max I can go with?

Try "sudo lshw | less"

---

### Post by DezSP on 2007-12-17
If it's DDR, probably 1 GB, but don't quote me on that. Try using Crucial's website to identify your PC's RAM capability.

---

### Post by ghoran on 2007-12-17
I copied and pasted the command.
It cleared the terminal screen and moved the cursor to the top.
I started another terminal and I see that less is running?


ash@ash-desktop:~$ ps -fu ash
UID        PID  PPID  C STIME TTY          TIME CMD
ash       5096     1  0 09:09 ?        00:00:00 /usr/bin/gnome-keyring-daemon -d
ash       5099  4864  0 09:09 ?        00:00:00 x-session-manager
ash       5134  5099  0 09:09 ?        00:00:00 /usr/bin/ssh-agent x-session-manager
ash       5136     1  0 09:09 ?        00:00:01 /usr/lib/libgconf2-4/gconfd-2 6
ash       5140     1  0 09:09 ?        00:00:00 dbus-daemon --fork --print-address 17 --print-pid 19 --session
ash       5142     1  0 09:09 ?        00:00:01 /usr/lib/gnome-control-center/gnome-settings-daemon
ash       5148  5099  0 09:09 ?        00:00:15 /usr/bin/metacity --replace --sm-client-id default0
ash       5151  5099  0 09:09 ?        00:00:13 gnome-panel --sm-client-id default1
ash       5152  5099  0 09:09 ?        00:00:06 nautilus --no-default-window --sm-client-id default2
ash       5160     1  0 09:09 ?        00:00:00 gnome-volume-manager --sm-client-id default4
ash       5163     1  0 09:09 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
ash       5176     1  0 09:09 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
ash       5186  5099  0 09:09 ?        00:00:00 vino-session --sm-client-id default5
ash       5187  5099  0 09:09 ?        00:00:00 bluetooth-applet
ash       5194  5099  0 09:09 ?        00:00:00 update-notifier
ash       5196     1  0 09:09 ?        00:00:12 gnome-screensaver
ash       5200  5099  0 09:09 ?        00:00:00 /usr/lib/evolution/2.12/evolution-alarm-notify
ash       5203  5099  0 09:09 ?        00:00:01 trackerd
ash       5205  5099  0 09:09 ?        00:00:00 nm-applet --sm-disable
ash       5207  5099  0 09:09 ?        00:00:00 python /usr/share/system-config-printer/applet.py
ash       5210     1  0 09:09 ?        00:00:00 gnome-power-manager
ash       5227     1  0 09:09 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapping-daemon
ash       5234     1  0 09:09 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=21
ash       5338     1  0 09:10 ?        00:00:01 /usr/bin/python /usr/lib/deskbar-applet/deskbar-applet --oaf-activate-iid=OAFIID:Deskbar_Applet_Factory --oaf-ior-fd=22
ash       5340     1  0 09:10 ?        00:00:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=29
ash       5342     1  0 09:10 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=35
ash       5883     1  0 09:21 ?        00:00:01 pidgin
ash       5998     1  0 10:25 ?        00:00:05 gnome-terminal
ash       6001  5998  0 10:25 ?        00:00:00 gnome-pty-helper
ash       6002  5998  0 10:25 pts/0    00:00:00 bash
ash       6136     1  3 11:41 ?        00:03:15 gnome-system-monitor
ash       6315     1  0 13:05 ?        00:00:00 /bin/sh /usr/bin/firefox
ash       6327  6315  0 13:05 ?        00:00:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin
ash       6331  6327  3 13:05 ?        00:00:52 /usr/lib/firefox/firefox-bin
ash       6358  6002  0 13:25 pts/0    00:00:00 less
ash       6363  5998  0 13:25 pts/1    00:00:00 bash
ash       6384  6363  0 13:27 pts/1    00:00:00 ps -fu ash
ash@ash-desktop:~$

---

### Post by ghoran on 2007-12-17
The crucial website says that it needs to have Internet Explorer to determine the memory needed.

---

### Post by MangasColoradas on 2007-12-17
I have 1gb and this what I get

           ..........total                            used        free        shared    buffers     cached
Mem:          1011         852          ..159         .... 0              .....25            ..........463



seems like a lot being used/cached, is it normal?

---

### Post by rsambuca on 2007-12-17
> **MangasColoradas said:**
> I have 1gb and this what I get

           ..........total                            used        free        shared    buffers     cached
Mem:          1011         852          ..159         .... 0              .....25            ..........463



seems like a lot being used/cached, is it normal?

That is fine.  The more in the cache, the faster your machine can run.

---

### Post by ghoran on 2007-12-17
I figured out why
sudo lshw | less
seemed to lock the screen

sudo asked for a password which then ended up off the screen.

I ran it without piping it to less and copied the interesting part here.

I took the information and crucial tells me and this is what I get:

I have 2 computers:
Computer 1 can take a 1 GIG chip
Computer 2 can only take (2) 256 meg chip

Since each one has a 256Meg chip, is there any danger in taking the 256 meg chip out of computer 1 and putting it in computer 2.
I can then put a DDR 2700 1 GIG in computer 1.


Computer1:

 *-core
       description: Motherboard
       product: AK32V
       vendor: Shuttle Inc
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (05/19/2003)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 1666MHz
          width: 32 bits
          clock: 133MHz


Computer 2:
      description: Motherboard
       product: K7S5A
       vendor: ECS
       physical id: 0
       version: 1.0
       serial: 00000000
       slot: PCI2
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 07.00T (04/02/01)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.6.2
          slot: Socket-A
          size: 1050MHz
          capacity: 1200MHz
          width: 32 bits
          clock: 66MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts

---

### Post by emil.s on 2007-12-17
> **ghoran said:**
> I figured out why
sudo lshw | less
seemed to lock the screen

sudo asked for a password which then ended up off the screen.


Opps! I'm not using sudo, so i didn't thougt about it. :P Btw, you probably learned someting. ;)

But the necessary info is under the CPU part:

```
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM-1
             size: 256MB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM-2
             size: 256MB
             width: 64 bits
             clock: 266MHz (3.8ns)

```

---

### Post by SOULRiDER on 2007-12-17
RAM is always good to have. I have 1 GB and im very happy with it, im not planning on upgrading anytime soon.
> free
             total       used       free     shared    buffers     cached
Mem:       1034304    1008132      26172          0      25876     695164
-/+ buffers/cache:     287092     747212
Swap:       248996          0     248996


---

### Post by MangasColoradas on 2007-12-17
> **rsambuca said:**
> That is fine.  The more in the cache, the faster your machine can run.

Thanks, I thought that might be the case, just wasnt sure. :)

---

