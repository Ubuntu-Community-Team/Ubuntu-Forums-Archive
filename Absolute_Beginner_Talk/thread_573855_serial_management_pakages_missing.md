---
title: "serial management pakages missing?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by lucat on 2007-10-12
I need to edit a kind of serial.conf file, but I didn't find it.
I have installed on my laptop Toshiba 4030 CDT the following xubuntu version:
xubuntu-6.06.1-alternate-i386.iso

 and installed the following packages:
setserial_2.17-43_i386.deb
minicom_2.2-5_i386.deb

But if I issue the command locate serial, I can not see any serial.conf file in the below answer:
could someone tell me if there is some packeges missing?

root@ubuntu:/# locate serial
/etc/pcmcia/serial.opts
/etc/pcmcia/serial
/lib/linux-restricted-modules/2.6.15-26-386/ltserial
/lib/linux-restricted-modules/2.6.15-26-386/ltserial/ltserial.mod.o
/lib/linux-restricted-modules/2.6.15-26-386/ltserial/serial.o
/lib/modules/2.6.15-26-386/kernel/drivers/char/generic_serial.ko
/lib/modules/2.6.15-26-386/kernel/drivers/parport/parport_serial.ko
/lib/modules/2.6.15-26-386/kernel/drivers/serial
/lib/modules/2.6.15-26-386/kernel/drivers/serial/8250_fourport.ko
/lib/modules/2.6.15-26-386/kernel/drivers/serial/8250_accent.ko
/lib/modules/2.6.15-26-386/kernel/drivers/serial/8250_boca.ko
/lib/modules/2.6.15-26-386/kernel/drivers/serial/serial_cs.ko
/lib/modules/2.6.15-26-386/kernel/drivers/serial/jsm
/lib/modules/2.6.15-26-386/kernel/drivers/serial/jsm/jsm.ko
/lib/modules/2.6.15-26-386/kernel/drivers/serial/8250_hub6.ko
/lib/modules/2.6.15-26-386/kernel/drivers/serial/8250_mca.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/gadget/g_serial.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/belkin_sa.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/airprime.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/cyberjack.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/cp2101.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/digi_acceleport.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/cypress_m8.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/garmin_gps.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/empeg.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/ftdi_sio.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/io_edgeport.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/hp4x.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/keyspan_pda.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/io_ti.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/ipaq.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/ipw.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/ir-usb.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/keyspan.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/ti_usb_3410_5052.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/kl5kusb105.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/kobil_sct.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/mct_u232.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/omninet.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/option.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/pl2303.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/safe_serial.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/usbserial.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/visor.ko
/lib/modules/2.6.15-26-386/kernel/drivers/usb/serial/whiteheat.ko
/lib/modules/2.6.15-26-386/kernel/sound/drivers/snd-serial-u16550.ko
/usr/share/doc/alsa-base/driver/serial-u16550.txt
/usr/share/man/man4/serial_cs.4.gz
/usr/share/cups/templates/de/choose-serial.tmpl
/usr/share/cups/templates/es/choose-serial.tmpl
/usr/share/cups/templates/ja/choose-serial.tmpl
/usr/share/cups/templates/pl/choose-serial.tmpl
/usr/share/cups/templates/sv/choose-serial.tmpl
/usr/share/cups/templates/choose-serial.tmpl
/usr/include/asm/serial.h
/usr/include/linux/generic_serial.h
/usr/include/linux/serial_8250.h
/usr/include/linux/serial.h
/usr/include/linux/serial167.h
/usr/include/linux/serialP.h
/usr/include/linux/serial_core.h
/usr/include/linux/serial_reg.h
/usr/include/asm-i386/serial.h
/usr/include/asm-x86_64/serial.h
/usr/lib/cups/backend-available/serial
/usr/lib/hal/hald-probe-serial
root@ubuntu:/#

---

### Post by renzokuken on 2007-10-12
assuming you are trying to communicate over a serial port pyserial may be of help

[http://pyserial.sourceforge.net/](http://pyserial.sourceforge.net/)

---

