---
title: "Getting a TL-WN321G v4 (rt2870) working"
date: 2012-09-06
forum: Any Other OS
---

### Post by JungYongHwa on 2012-09-06
> Hi,

Wanted to summarize how to do this in case someone else had the same issue.

I have Lucid 10.04 LTS (32-bit) installed on a compaq F500. Some time ago the wireless switch gave up so I bought a usb wireless thingy. It was a TP-LINK TL-WN321G v4.

So to get this to work I

Downloaded ndiswrapper 1.56 (google ndiswrapper-1.56.tar.gz)
Added 

 wstdcall void* WIN_FUNC(MmGetSystemRoutineAddress,1)
 (struct unicode_string *name)
 {
 struct ansi_string ansi;
 if (RtlUnicodeStringToAnsiString(&ansi, name, TRUE) ==
 STATUS_SUCCESS) {
 WARNING("MmGetSystemRoutineAddress: %s", ansi.buf);
 RtlFreeAnsiString(&ansi);
 }

 return 0;
 }

To ntoskernel.c (this solves ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress')

Patched the ndiswrapper with patch -p0 < iw_ndis.c.diff. Patch is provided below but feel free to google it.

 diff --git a/iw_ndis.c b/iw_ndis.c
 index 434260e..3f5e12c 100644
 --- a/iw_ndis.c
 +++ b/iw_ndis.c
 @@ -1591,6 +1591,12 @@ static int iw_set_auth(struct net_device *dev,
  		if (wrqu->param.value)
  			deauthenticate(wnd);
  		break;
 +	case IW_AUTH_MFP:
 +	        if (wrqu->param.value == IW_AUTH_MFP_DISABLED ||
 +                    wrqu->param.value == IW_AUTH_MFP_OPTIONAL)
 +		        break;
 +		WARNING("MFP not implemented");
 +		return -EOPNOTSUPP;
  	case IW_AUTH_TKIP_COUNTERMEASURES:
  	case IW_AUTH_DROP_UNENCRYPTED:
  	case IW_AUTH_RX_UNENCRYPTED_EAPOL:

This solves ndiswrapper (iw_set_auth:1602): invalid cmd 12

Made the ndiswrapper with make and then make install (as root)

By default ndiswrapper is in /lib/modules/2.6.32-30-generic/kernel/ubuntu/ndiswrapper/ however the install will put it in misc so make a softlink copy or whatever.

Got the drivers for Windows XP TL-WN321G_v4_100611.zip
unzipped and went to the Windows 2000_XP directory

ndiswrapper -i rt2870.inf

And bob should be you uncle

Iain

Dear
bibble235

I've got tp-link tl-wn321g v4, but can't get it works for linux mint 10 (maverick), maybe you can help me? I've been searching, and tried, but get no success way, thanks in advance.

Best Regards,
JungYongHwa

---

### Post by chili555 on 2012-09-06
I'm sure bibble235 is long gone. Do you mind if I try? Please insert the device, open a terminal and run and post:```
uname -r
lsusb
```Thanks.

---

### Post by Perfect Storm on 2012-09-06
Split & Moved to Other OS/Distro talk.

---

### Post by JungYongHwa on 2012-09-19
Dear
[chili555]("http://ubuntuforums.org/member.php?u=35909")

Thanks for the reply

uname -r
2.6.35-22-generic

finance-G41MT-S2PT finance # lsusb
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
Bus 001 Device 004: ID 04a9:1746 Canon, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Best Regards,

---

### Post by chili555 on 2012-09-19
Here is a pretty good procedure: [http://ubuntuforums.org/showthread.php?t=2038083](http://ubuntuforums.org/showthread.php?t=2038083)

The various places he adjusted for the 12.04 kernel, here:> Browse to DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/include/os and search for all references to "usb_alloc_buffer" and "usb_free_buffer" within rt_linux.h, there should only be two. Update them to "usb_alloc_coherent" and "usb_free_coherent".
You should *NOT* have to do.

Before you compile the driver, be sure you have the appropriate build tools installed:```
sudo apt-get install build-essential linux-headers-generic
```Post back if you get stuck.

---

### Post by JungYongHwa on 2012-09-21
the driver has been removed from that link, T_T

---

### Post by chili555 on 2012-09-21
I suggest you try the later version here: [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

If it won't compile because it's too new for your older kernel, I may have an older version on my harddrive.

---

### Post by JungYongHwa on 2012-09-21
I choose older kernel because when i use linux mint 13 ( pangolin precise) my printer printing so slow, but its print normally at older kernel, that's why i install linux mint 10 (maverick meerkat)
May you help me how to set the printer so it won't print so slow at precise?

---

### Post by chili555 on 2012-09-22
The first thing I suggest is to check the printer driver being used:```
sudo system-config-printer
```Right-click the printer icon, select Properties and check the driver. Often, more than one driver is available and often one works better than the other. Try the others.

Make sure the proper driver package is installed. If you want to use the brute force approach:```
sudo apt-get install printer-driver-all
```These suggestions are appropriate to Ubuntu; I'm not totally sure about Mint.

Please see attached.

---

### Post by JungYongHwa on 2012-09-24
Dear
Sir

After I tried 12.04 i found that 12.04 run slower than 10.10, so I decided to get my wn321g work on 10.04. May you help me to get the older driver that may work for me please, thanks for your kindness.

Best Regards,
JungYongHwa

---

### Post by chili555 on 2012-09-24
Did you try to compile the driver I suggested in post #7? Didn't it work? What went wrong?

---

### Post by JungYongHwa on 2012-09-24
I get an error while trying to compile the driver, T_T

---

### Post by chili555 on 2012-09-25
It will be very helpful if you can tell me what the error is. I am away from my 10.04 machine for about three weeks so I can't try it for myself.

---

