---
title: "How to change my DMA acceleration"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by Linuxmyatuk on 2006-01-07
How do I change my DMA acceleration on my /dev/hdc and /dev/hdd from off to on..

---

### Post by s6dalane on 2006-01-07
You can turn DMA ON for all devices with Automatix.
Get it here: [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by bored2k on 2006-01-07
If you want to this **yourself,** I'll quote the official wiki:

[list=1][*]See the what the settings are on /dev/hdc
          ```
sudo hdparm /dev/hdc
```
               

   [*] If you get a line like  using_dma    =  1 (on), DMA is already enabled. Skip to step 4 to see if it has been enabled at boot time.


  [*]      Enable DMA on /dev/hdc
      ```
sudo hdparm -d1 /dev/hdc
```
               

   [*] You have now enabled DMA for the drive. However, in order for the settings to be automatically applied at boot there you need to edit the /etc/hdparm.conf} script. To do this use this command: ```
sudo gedit /etc/hdparm.conf
```

Add the following to the end of your hdparm.conf
```

/dev/hdc {
dma = on
}
```
         
[/list]
**Troubleshooting**

If your drives are configured in [Cable Select] mode and while running hdparm commands you receive errors related to timeouts or drive not ready, try changing the drive to be a master or slave device depending on your system configuration. This does require opening the case and as far as I know most drives are set to Cable Select from the manufacturer.

Sometimes step 3 above can fail with a "operation not permitted" message. You can fix this by editing the file /etc/modules: For an intel cpu put the lines

```
piix

ide-core

above the line

ide-cd

```
For an amd cpu put the line
```

amd74xx

above

ide-cd

```
For a VIA Chipset put
```

via82cxxx

above

ide-cd
```

Then reboot and try steps 3-4 again....

---

