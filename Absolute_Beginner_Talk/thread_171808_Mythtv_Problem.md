---
title: "Mythtv Problem"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Smika on 2006-05-07
Hello,
 
 Now the site is back I was happy for 5 minutes, because now i have some new errors in dmesg. I have a PVR 150MCe (same as the PVR150). I have some errors in the dmesg:
 
 [4294693.735000] ivtv: ==================== START INIT IVTV ====================
 [4294693.735000] ivtv: version 0.4.4 (tagged release) loading
 [4294693.735000] ivtv: Linux version: 2.6.12-10-686 686 gcc-3.4
 [4294693.735000] ivtv: In case of problems please include the debug info between
 [4294693.735000] ivtv: the START INIT IVTV and END INIT IVTV lines, along with
 [4294693.735000] ivtv: any module options, when mailing the ivtv-users mailinglist.
 [4294693.740000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
 [4294693.740000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12
 [4294693.740000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
 [4294693.800000] tveeprom: The eeprom says no radio is present, but the tuner type 60
 [4294693.800000] tveeprom: indicates otherwise. I will assume that radio is present.
 [4294693.800000] tveeprom: ivtv version
 [4294693.800000] tveeprom: Hauppauge: model = 26559, rev = C260, serial# = 8225385
 [4294693.800000] tveeprom: tuner = LG S001D MK3 (idx = 60, type = 3
 [4294693.800000] tveeprom: tuner fmt = PAL(B/G) PAL(I) SECAM(L/L') PAL(D/K) (eeprom = 0x74, v4l2 = 0x00400e17)
 [4294693.800000] tveeprom: audio processor = CX25843 (type = 25)
 [4294693.800000] tveeprom: decoder processor = CX25843 (type = 1e)
 [4294693.800000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
 [4294693.833000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
 [4294693.833000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
 [4294693.991000] cx25840 0-0044: ivtv driver
 [4294693.991000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
 [4294694.519000] cx25840 0-0044: unable to open firmware v4l-cx25840.fw
 [4294694.576000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
 [4294694.625000] wm8775 0-001b: ivtv driver
 [4294694.625000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
 [4294694.632000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
 [4294694.648000] tda9887 0-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
 [4294694.648000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
 [4294695.302000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
 [4294695.302000] ivtv0: did you put the firmware in the hotplug firmware directory?
 [4294695.302000] ivtv0 warning: failed loading encoder firmware
 [4294695.302000] ivtv0 warning: Error loading firmware -3!
 [4294695.302000] ivtv0: Error -3 initializing firmware.
 [4294695.323000] ivtv0: Error -12 on initialization
 [4294695.323000] ivtv: probe of 0000:00:09.0 failed with error -12
 [4294695.323000] ivtv: ==================== END INIT IVTV ===================
 
 
 This is my formware:
 
 drwxr-xr-x 3 root root 4096 May 6 07:33 ..
 -rw-r--r-- 1 root root 262144 May 7 10:28 ivtv-fw-enc.bin
 -rw-r--r-- 1 root root 262144 May 7 10:28 ivtv-fw-dec.bin
 -r--r--r-- 1 root root 14264 May 7 10:29 v4l-cx25840.fw
 -r--r--r-- 1 root root 376836 May 7 10:29 v4l-cx2341x-enc.fw.orig
 -rw-r--r-- 1 root root 155648 May 7 10:29 v4l-cx2341x-init.mpg
 lrwxrwxrwx 1 root root 41 May 7 10:30 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
 -rw-r--r-- 1 root root 262144 May 7 10:42 v4l-cx2341x-enc.fw
 drwxr-xr-x 2 root root 4096 May 7 10:42 .
 
 
 Can somebody help me?
 
 Thanks a lot,
 
 Smika

---

### Post by Titus A Duxass on 2006-05-09
Sorry for the late response.
I had the same problem, if you read the ivtv webpage they give you a solution.
Shutdown, wait thirty seconds and reboot (cold reboot).

---

### Post by Smika on 2006-05-09
Thanks, everything works now!!!

---

