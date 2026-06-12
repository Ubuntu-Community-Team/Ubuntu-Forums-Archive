---
title: "Fan files missing in applesmc.768 (Black Macbook Santa Rosa)"
date: 2008-05-02
forum: Apple Hardware Users
---

### Post by ShareBuntu on 2008-05-02
I load applesmc on startup to adjust the fan speed through fan1_min. However, for some some reason, all the fan files have disappeared from /sys/devices/platform/applesmc.768/. Here's what I have now:

```

calibrate                 key_at_index_name  subsystem     temp6_input
driver                    key_at_index_type  temp10_input  temp7_input
hwmon                     key_count          temp1_input   temp8_input
input                     modalias           temp2_input   temp9_input
key_at_index              name               temp3_input   uevent
key_at_index_data         position           temp4_input
key_at_index_data_length  power              temp5_input
```

Any idea how I can get it back? I added the following to /etc/rc.local:

```

echo 2500 > /sys/devices/platform/applesmc.768/fan1_min 
```

Not sure if the above has anything to do with it.

---

### Post by cocoon on 2008-06-12
This happens to me as well, some of the time. I see the following pattern: if I reboot from OS X, the fan files are missing. If I do a shutdown on OS X, then boot to ubuntu, they exist. If I reboot Ubuntu, they exist.

This is a MacBook Santa Rosa, 32 bit hardy heron, and the precompiled kernel from linux-image-2.6.24-18-generic. I'm loading applesmc in /etc/modules. I'll provide more information if necessary. Right now I'm good with always doing a shutdown on OS X.

---

### Post by cyberdork33 on 2008-06-12
> **cocoon said:**
> This happens to me as well, some of the time. I see the following pattern: if I reboot from OS X, the fan files are missing. If I do a shutdown on OS X, then boot to ubuntu, they exist. If I reboot Ubuntu, they exist.

This is a MacBook Santa Rosa, 32 bit hardy heron, and the precompiled kernel from linux-image-2.6.24-18-generic. I'm loading applesmc in /etc/modules. I'll provide more information if necessary. Right now I'm good with always doing a shutdown on OS X.
there are several "variables" and such that do not get reset if you do a reboot, you have to actually powerdown the machine. The iSight firmware loading is another example.

---

### Post by sands on 2008-08-10
Does that mean, the value of fan1_min will remain 2500 after reboot?

---

### Post by ShareBuntu on 2008-08-10
> **sands said:**
> Does that mean, the value of fan1_min will remain 2500 after reboot?
The applesmc.768 files will appear given that you shut down your computer completely, rather than a reboot. The best way to ensure fan1_min stays populated with the value you specified is to add an entry to /etc/rc.local; say "echo 2500 > /sys/devices/platform/applesmc.768/fan1_min" before the "exit 0" line. Negate the quotations, of course.

---

### Post by dkulp on 2008-08-11
I had the same issue of fan files not being found.   Also, I couldn't get pommed to read the "light" file reliably.   This is on my MacBook Pro Penryn.   I was also getting a bunch of warning messages in the syslog.

I did some debugging and it looks like the applesmc needs a "retry" in it.   When reading the light sensors, it would read the left sensor fine, but not read the right sensor at all.  If I added a retry on the right sensor, it would read it.


I ended up modifying the applesmc.c file as:

```

static int __wait_status(u8 val)
{
	unsigned int i;

	val = val & APPLESMC_STATUS_MASK;

	for (i = 0; i < 100; i++) {
		if ((inb(APPLESMC_CMD_PORT) & APPLESMC_STATUS_MASK) == val) {
			if (debug)
				printk(KERN_DEBUG
						"Waited %d us for status %x\n",
						i*10, val);
			return 0;
		}
		udelay(10);
	}

	/*
	printk(KERN_WARNING "applesmc: wait status failed: %x != %x\n",
						val, inb(APPLESMC_CMD_PORT));
	*/
	return -EIO;
}

/*
 * applesmc_read_key - reads len bytes from a given key, and put them in buffer.
 * Returns zero on success or a negative error on failure. Callers must
 * hold applesmc_lock.
 */
static int applesmc_read_key(const char* key, u8* buffer, u8 len)
{
	int i;

	if (len > APPLESMC_MAX_DATA_LENGTH) {
		printk(KERN_ERR	"applesmc_read_key: cannot read more than "
					"%d bytes\n", APPLESMC_MAX_DATA_LENGTH);
		return -EINVAL;
	}

	outb(APPLESMC_READ_CMD, APPLESMC_CMD_PORT);
	if (__wait_status(0x0c)) {
	  outb(APPLESMC_READ_CMD, APPLESMC_CMD_PORT);
	  if (__wait_status(0x0c)) {
		return -EIO;
	  }
	}
....... (more stuff in this method)     ..........


```

Basically, it shortened the timeout in __wait_status and removed the printk, then added a retry in applesmc_read_key.

With that, everything seems to work fine.   I can get the fans, the lights, position, etc....

Not sure why the retry is needed.   Maybe the device in the newer macbooks are sending more data back or something.   I don't really know.

---

### Post by cyberdork33 on 2008-08-11
> **dkulp said:**
> I ended up modifying the applesmc.c file...
You should submit these changes to the mactel-linux mailing list.

---

