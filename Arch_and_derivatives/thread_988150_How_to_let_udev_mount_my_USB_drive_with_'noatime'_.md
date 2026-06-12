---
title: "How to let udev mount my USB drive with 'noatime' mount option?"
date: 2008-11-20
forum: Arch and derivatives
---

### Post by kpkeerthi on 2008-11-20
Is it possible to (have udev auto-)mount an external drive with certain mount options?

My backup drive is USB, JFS formatted. I just need it auto-mounted with 'noatime' mount option. I read the instructions [here]("http://wiki.archlinux.org/index.php/Udev#Auto_mounting_USB_devices") but its way over my head. 

Currently, I'm working around this issue with an FSTAB entry and mounting the partition manually:
```

<UUID>     /media/Backup     jfs     defaults,user,noatime,noauto    0   0

```
* If I leave out noauto, it get boot time warning that reads 'partition does not exist'.

I'd really like udev auto mount it. Any help is much appreciated.

---

### Post by cammin on 2008-11-20
> 
ACTION=="add", KERNEL=="sd[a-z][0-9]", PROGRAM=="/lib/udev/vol_id -t %N", RESULT=="vfat", RUN+="/bin/mount -t vfat -o rw,noauto,flush,quiet,nodev,nosuid,noexec,[size=3]**noatime**[/size],dmask=000,fmask=111 /dev/%k /mnt/usb%n", OPTIONS="last_rule"


From the wiki you linked to.

---

### Post by fwojciec on 2008-11-20
This one is a hal policy -- so it should work if you use hal to automount drives.

No idea if this will work, but it might -- I just changed a ntfs policy that I had on my system, I don't actually have any jfs hotpluggable filesystem to test it on.  It needs to go somewhere in /etc/hal/fdi/policy (as something like 10-jfs_usb.fdi).  You'll need to restart hal (and remove the entry you created in fstab).

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
    <device>
        <match key="volume.fstype" string="jfs">
            <match key="@block.storage_device:storage.hotpluggable" bool="true">
                <append key="volume.mount.valid_options" type="strlist">noatime</append>
            </match>
        </match>
    </device>
</deviceinfo>

---

### Post by kpkeerthi on 2008-11-20
Thanks fwojciec for the pointer. I didn't knew it is HAL thought it'd be udev. I'll find out more about this.

EDIT: Searched for HAL in the wiki and found [it]("http://wiki.archlinux.org/index.php/HAL"). Thanks again.

---

### Post by kpkeerthi on 2008-11-20
> **cammin said:**
> From the wiki you linked to.

Thanks. But that didn't make any sense to me.

---

### Post by kpkeerthi on 2008-11-22
Following the guidelines at [http://wiki.archlinux.org/index.php/HAL](http://wiki.archlinux.org/index.php/HAL), I created a file /usr/share/hal/fdi/policy/10osvendor/10-custom-mount-options.fdi with the following content:
```

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
        <device>
                <match key="block.is_volume" bool="true">
                        <match key="@block.storage_device:storage.hotpluggable" bool="true">
                                <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
                        </match>
                        <match key="@block.storage_device:storage.removable" bool="true">
                                <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
                        </match>
                </match>
        </device>
</deviceinfo>

```
And then restarted HAL. Even tried reboot. But my drives still won't mount with noatime. Any help is much appreciated?

(Asked around in official arch forums. The forum seems pretty much dead :()

---

### Post by kpkeerthi on 2008-11-25
[:bump:]

---

