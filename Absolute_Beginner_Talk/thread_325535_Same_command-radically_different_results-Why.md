---
title: "Same command-radically different results-Why?"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by Odyssey1942 on 2006-12-25
After rebooting my computer I ran the command:
```

dmesg | grep -i usb
```


and got the following result:

>  [17179573.392000] SLOT KBC0 MSE0 PWRB USB4 USB1 USB2 USB3
[17179578.532000] usbcore: registered new driver usbfs
[17179578.532000] usbcore: registered new driver hub
[17179578.536000] USB Universal Host Controller Interface driver v2.3
[17179578.536000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus nu mber 1
[17179578.536000] hub 1-0:1.0: USB hub found
[17179578.612000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.640000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus nu mber 2
[17179578.640000] hub 2-0:1.0: USB hub found
[17179578.744000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus nu mber 3
[17179578.744000] hub 3-0:1.0: USB hub found
[17179578.852000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus nu mber 4
[17179578.856000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 D ec 2004
[17179578.856000] hub 4-0:1.0: USB hub found
[17179578.960000] ohci_hcd 0000:02:0a.0: new USB bus registered, assigned bus nu mber 5
[17179578.984000] ehci_hcd 0000:02:0a.3: new USB bus registered, assigned bus nu mber 6
[17179578.984000] ehci_hcd 0000:02:0a.3: USB 2.0 started, EHCI 1.00, driver 10 D ec 2004
[17179578.984000] hub 6-0:1.0: USB hub found
[17179579.088000] hub 5-0:1.0: USB hub found
[17179580.064000] usb 5-1: new low speed USB device using ohci_hcd and address 2
[17179580.412000] usbcore: registered new driver hiddev
[17179580.532000] input: Logitech USB Optical Mouse as /class/input/input1
[17179580.532000] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb -0000:02:0a.0-1
[17179580.532000] usbcore: registered new driver usbhid
[17179580.532000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver


A few minutes later, following execution of several shell commands (trying to learn how to use some of them to find my hard drive), I ran the identical command (as above) again and got no output whatsover. I reran it a couple of times to reconfirm and got the exact same (no) result.

Why the different results?

---

### Post by pay on 2006-12-26
Maybe you accidently unmounted it:confused:

---

### Post by Odyssey1942 on 2006-12-26
Unsure I understand. Unmounted what? dmesg is a kernal boot log file, no? Are you thinking the USB mignt have been unmounted? If so, would that change the content of the boot message file?

I am perplexed by the lack of response. Is this just uninteresting or is that no one has any idea? If either of these, does anyone know of a forum that might get more response? If not these, what please?

All ideas gratefully received.

---

### Post by jeffathehutt on 2006-12-26
Well, dmesg is not just a boot log.  It is more of a "kernel events" log.  The usb stuff usually would come up right after the boot process.  My guess is there were new events between the time you entered the two commands, and the usb part had been pushed out of the log.

---

### Post by astoltz on 2006-12-26
From Wikipedia:

> dmesg (for "diagnostic message") is a command on Unix-like operating systems that prints the message buffer of the kernel. This buffer contains a variety of important messages from those printed during boot to those used for debugging software. This information may also be stored to disk via a logging daemon, such as syslog.This is purely a guess, but maybe the buffer has been overwritten with more recent activity?  I'd guess that a similar command using the syslog would show your USB stuff.

---

### Post by Odyssey1942 on 2006-12-27
Jeff, this makes sense.

astoltz, I have tried:

```
syslog | grep -i usb

```

with and without sudo, but the command was not recognized and there is nothing in the man pages on syslog. Is this the right command structure? Thanks

---

### Post by jeffathehutt on 2006-12-27
syslog is just a plain text file on your computer.  It is located at /var/log/syslog.  You can either open it in your favorite text editor, or use a command such as 'cat /var/log/syslog | grep -i usb' if you know what word you are looking for.  cat is a command that will display a text file in the terminal, and grep is used to search for a specific word in that file.

---

### Post by Odyssey1942 on 2006-12-28
Jeff, thanks for yours, That is as I understood it.

Comparting the two:
dmesg and syslog are both text files

dmesg | grep -i usb is the same syntax as

syslog | grep -i usb

but the former yields results, while the latter does not. Is my syntax wrong for the latter?

Also 'cat /var/log/syslog | grep -i usb' does not yield results either.

---

### Post by olnir on 2006-12-28
-i means ignore.
Should it not be :  
cat /var/log/syslog |grep  usb

---

### Post by amo-ej1 on 2006-12-28
-i doesn't mean ignore.

quoting the grep manpage:

```

       -i, --ignore-case
              Ignore case distinctions in  both  the  PATTERN  and  the  input
              files.

```

---

### Post by ckempo on 2006-12-28
> **Odyssey1942 said:**
> Jeff, thanks for yours, That is as I understood it.

Comparting the two:
dmesg and syslog are both text files

dmesg | grep -i usb is the same syntax as

syslog | grep -i usb

but the former yields results, while the latter does not. Is my syntax wrong for the latter?

Also 'cat /var/log/syslog | grep -i usb' does not yield results either.

Nearly. dmesg is a command, that displays a log - it appears to you that it is a text logfile, but what you are seeing isn't actually a file at all.  syslog, on the other hand, is exactly that, a system log, and as such you can view it as you could any other file - just open /var/log/syslog whichever way you please.

---

