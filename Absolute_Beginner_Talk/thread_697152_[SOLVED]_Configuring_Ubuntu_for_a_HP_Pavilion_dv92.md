---
title: "[SOLVED] Configuring Ubuntu for a HP Pavilion dv9205us"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by jwill1515 on 2008-02-14
I recently installed Ubuntu 7.10 on a HP Pavilion dv9205us and I can't access the files from the Vista portion of the computer. They were there earlier. There was an icon on the desktop called sda1 and I could open and see the files inside. Now nothing. Also, there is a wireless button on the front of the computer that is not working and not allowing me to access wireless networks. Running Vista, you move the button to the right to activate and the light would switch from orange to blue. Now it is always orange. I believe it's broadcom.

---

### Post by Presto123 on 2008-02-14
With the wireless, check to see if the card shows up in Restricted Drivers Manager. If it shows up and you click on the box to enable it, the next window will prompt for a driver; let it download it from the internet (being connected to the internet with your networking cable).

What you will have to do is mount that drive...someone (if not me) will follow up with how to mount it, below.

---

### Post by spiderbatdad on 2008-02-14
You probably need linux-restricted-modules  to activate the broadcom driver for wireless. After installing that package from synaptic...i think you need to reboot. The System>>Administration>>Restricted Drivers Manager should offer a driver for your wireless. There may be some issues if you enable eth1 (wireless) or eth0 while ppp (dial-up) is running.  Look in Places>>Computer for your other filesystem. OR:
```
sudo apt-get install ntfs-3g ntfs-config
gksudo ntfs-config
```

---

### Post by Presto123 on 2008-02-14
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Follow the last 5 codes to get your Vista partition remounted. (Of course replacing the HDA with whatever the drive is. It seems you already KNOW it's SDA1, so you can replace it with that.)

---

### Post by jwill1515 on 2008-02-14
I tried that in the Restricted Drivers Manager and it wouldn't download. It came back with an error message. All that's in Places>Computer is the CDU680, CDdrive and file system. Only Ubuntu files in file system.

---

### Post by jwill1515 on 2008-02-14
I got the wireless now. It went this time. Thank you very much.

---

### Post by jwill1515 on 2008-02-14
It's asking to enable write support for external and internal device.

---

### Post by jwill1515 on 2008-02-14
Mounting /media/sda1 failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0

---

### Post by Presto123 on 2008-02-14
Go back into your fstab like is listed in the psychocats thing and delete out what you added, save and then type in:

```
sudo mount /dev/sda1
```

I don't know what to tell you from here, but at least you will be back to what you had before and can start from the beginning if that doesn't mount it.

---

### Post by spiderbatdad on 2008-02-14
That is the wrong guide for mounting windows on a linux system. see this instead.[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Presto123 on 2008-02-14
Pardon my error. Thank you.

---

