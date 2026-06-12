---
title: "MBA 11&quot; 2012 with 12.04"
date: 2012-06-18
forum: Apple Hardware Users
---

### Post by eee.c on 2012-06-18
Got the newest Macbook Air 11" with 8gb memory and wanted to report my results. 

tl;dr It is possible to install, though there are at least a few things not working.

The biggest hurdle that I encountered was the install CD halting with:
```
kernel panic not syncing timer doesn't work through interrupt-remapped io-apic
```I was able to work around by adding "nointremap" to the boot options. From what I've read about that option, it is not a good thing to use, but it allowed the install CD to work (manually edited the boot options) and it allows the OS to boot once installed.

That is, instead of:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1 resume=/dev/sda5"
```I am using:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nointremap i915.i915_enable_rc6=1 resume=/dev/sda5"
```

I have a superdrive, so I cannot speak to USB install, but I would guess that it still works.

I ran through the post-install script manually and most of it worked.  In particular, the updated wl network drivers still work for quick connectivity.

What is not working: [LIST]
[*]applesmc. Modprobe-ing that results in an input-output error. I'm not sure how big a deal that is. 
[*]Keyboard lights. I prefer them off so I have not investigated.
[*]Fn key to dim the screen (the brightness applet works). Oddly the fn key to brighten the screen does work.
[/LIST]

What is working: suspend (mouse was messed up, but that could just be me), reboot, most keyboard functions, touchpad (with synaptics), wireless, camera, sounds.

Haven't tested yet: OSX partition access, microphone, fan control, extra power saving, external monitor (I don't use one).

All-in-all, I think this is going to be an excellent Ubuntu machine :)

---

### Post by zaphod777 on 2012-06-19
How is battery life on it?

---

### Post by poliva on 2012-06-19
regarding the applesmc error, can you check if the dmi_system_id on your system matches the DMI_BOARD_VENDOR and DMI_PRODUCT_NAME set on the applesmc module? source is on linux/drivers/hwmon/applesmc.c

If unsure, please paste the output of this command:
```
 sudo dmidecode |egrep -i "(Product|Vendor)"
```

---

### Post by eee.c on 2012-06-19
```
$ sudo dmidecode |egrep -i "(Product|Vendor)"
	Vendor: Apple Inc.
	Product Name: MacBookAir5,1
	Product Name: Mac-66F35F19FE2A0D05
```

---

### Post by poliva on 2012-06-19
should be ok, it's a different problem then. Can you post the output when modprobing the module? I'd suggest adding printk's in the module and re-compile it to see how far it reaches, and where/why it fails.

---

### Post by aviromanoff on 2012-06-20
Hah, I was just Googling around and found this after commenting on a bug report for MBA not being supported with Lightum.

So I'll link to my comment there, which has the (fail) output from applesmc. [https://github.com/poliva/lightum/issues/15#issuecomment-6445369](https://github.com/poliva/lightum/issues/15#issuecomment-6445369)

I don't know much about kernel hacking, but it seems to me like the API to interface with the SMC needs some updating for the new MBAs (I've got a 13'' 5,2 model).

---

### Post by poliva on 2012-06-20
@aviromanoff: thanks for the output, the applesmc module source is here: [http://x90.es/applesmc](http://x90.es/applesmc) from the log you posted it looks like it's failing at applesmc_init() because read_smc() doesn't work (the key values are clearly wrong).

You will get more verbose information from /var/log/kern.log (because the module uses pr_info() which is not logged on dmesg). If possible, please run the following using two separate terminals:

CONSOLE1: sudo rmmod applesmc
CONSOLE2: tail -n 0 -f /var/log/kern.log
CONSOLE1: sudo modprobe applesmc
CONSOLE2: hit Ctrl+C

When done, please paste the output of kern.log.

---

### Post by aviromanoff on 2012-06-20
Thanks for the explanation & detailed instructions. I've actually just upgraded to Mountain Lion (and successfully borked my Linux install in the process), so it'll be an hour or so before I can get that output.

EDIT: Wow, one hour on the nose.

CONSOLE1: [http://paste.ubuntu.com/1050724/](http://paste.ubuntu.com/1050724/)
CONSOLE2: [http://paste.ubuntu.com/1050721/](http://paste.ubuntu.com/1050721/)

Unfortunately it doesn't look to me like there's much more info in kern.log than in dmesg.

---

### Post by poliva on 2012-06-20
ok, no luck here either.

Let's start hacking the module source then ;)

1. Install the required dependencies to build the modules:

```

sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)

```

2. Get the kernel source:
```

apt-get source linux-image-$(uname -r)

```

3. Edit applesmc.c to apply your changes:
```

cd linux-$(uname -r|cut -d- -f1)/drivers/hwmon
vim applesmc.c

```

I'd start by printing messages like this:

```

pr_warn("applesmc_whatever failed\n");

```

4. Compile the module:
```

make -C /lib/modules/$(uname -r)/build M=$(pwd) applesmc.ko

```

5. try the compiled module:
```

sudo insmod ./applesmc.ko

```

The messages you have inserted using pr_warn() will be printed in dmesg each time you insmod the module, start with the applesmc_init() function, it's like main() in a regular C program.

Good luck and let us know your progress! (I'm available via gtalk if you need any further help with this).

---

### Post by poliva on 2012-06-20
You might also want to have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096)

---

### Post by jhodapp on 2012-06-21
So I am just at the point of setting up Ubuntu 12.04 on my new MacBook Air 13". I should be able to help in these efforts to trace down these problems. I'll let you know what I find.

EDIT: eee.c, I can confirm that your technique also works for me on my 13" to get Ubuntu 12.04 installed and booted.

---

### Post by asting on 2012-06-24
I just ordered a new 13" MBA, so I'll be trying to put Ubuntu on soon.
I'm hoping to triple boot OSX, WIN7, and use [this]("http://www.amazon.com/SanDisk-Cruzer-32GB-Flash-Drive/dp/B00812F7O8/ref=sr_1_19?ie=UTF8&qid=1340582333&sr=8-19&keywords=32gb+sandisk") for my ubuntu drive (hopefully). 
I'm just tagging along to hopefully learn a thing or two and hopefully . I've used Ubuntu for about 8 years on and off, and am not a complete newbie, but still have plenty to learn.

---

### Post by agb32 on 2012-06-28
Hi,
external display is working for me... 
Except:  if I boot with the external display plugged in, the laptop screen is always blank after grub, and I can find no way of turning it on.  The display properties GUI reports the screen being present and on, and I can move windows onto it and start applications on it, but I just can't see them.

So, for now, unplug the external display while booting...

All else seems pretty good... except I can't get fvwm working with unity very well... (launch bar goes funny).

Also - usb booting works fine (I didn't test the CD boot).

---

### Post by MikaelHolber on 2012-06-28
Everything went smooth for me as well. Thank you for the information. However, are you still running with the nointremap-option? I cannot seem to get around the kernel panic without this option.

---

### Post by nkhong on 2012-06-28
I have the same problem on the MBA 5,1 11" and other graphics problems.  I installed the latest Nvidia driver.  LCD still goes black with dual monitor plugged in.  I'm not sure if the driver helps... havent had time to investigate.  But here is some info that may help:

[http://askubuntu.com/questions/65164/unity-3d-not-working-no-longer-works-after-update](http://askubuntu.com/questions/65164/unity-3d-not-working-no-longer-works-after-update)

---

### Post by agb32 on 2012-06-29
Hi,
I'm not sure the nvidia driver will do anything, because there is no nvidia chip.  Graphics are provided by the HD4000 from the ivy bridge.

I'm having an interesting problem today though - can't get wireless to connect - have powered off and back on multiple times... (its fine on osx, so not a network problem).

It was being slow and droppy yesterday, and today, no luck.

Yes, am still using the nointremap option.

Anyone got any thoughts about wireless?

Hmm - I did do a apt-get upgrade yesterday - maybe that has done it...?

---

### Post by agb32 on 2012-06-29
OK - wifi fixed by reverting back to the stock install driver.

Am having some problems with CPU lockups - possibly this is because the fans aren't being controlled properly, and so overheating?  Not sure about that.

---

### Post by minsf on 2012-06-30
i have the new (2012) MBA 13" with 4GB ram. 
i'm dual booting Lion with 12.04.

@eee.c 
* i have no superdrive, and i can confirm that booting from a usb works. (i used the amd+mac iso, converted it to img with hdiutil and used dd to copy it to the usb stick, all from the OSX Lion partition). 
* initially, i got the same kernel panic as you did(for IO-APIC)
* the nointremap parameter worked as you described. i also tried the noapic parameter (independently) and it worked too. i have not notice a difference between the two boots yet (one with nointremap and one with noapic). 
* unlike you, i have no problem with dimming the screen brightness from the fn keys. but i did notice that if i include the kernel parameter nomodeset (as suggested by some tutorials), then i cannot control the brightness of the screen anymore. i think nomodeset is trying to fight something with the nvidia drivers, so it is irrelevant to us (since we have no nvidia card). anyways, i wonder if your dimming issue is also related to some redundant kernel parameter that you added.
* you are not alone- i have the same issue with the mouse freezing after suspend. 
* same as you regarding the keyboard lights not working.
* same as you regarding wireless & sound working out of the box. 

i'll report more later.

---

### Post by fhucho on 2012-07-01
@minsf What is the power consumption (sudo powertop)?

---

### Post by minsf on 2012-07-01
> **fhucho said:**
> @minsf What is the power consumption (sudo powertop)?

[http://paste.ubuntu.com/1070561/](http://paste.ubuntu.com/1070561/)

---

### Post by eee.c on 2012-07-03
The brightness key issue eventually went away for me. I was able to resolve (mostly) the mouse-after-suspend issue. I added the following to /etc/pm/sleep.d/00_usercustom:```
    modprobe -r bcm5974 
    modprobe bcm5974 

```The whole contents of that came from one of the postinstall scripts in [https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

---

### Post by agb32 on 2012-07-04
Had several hangs using the stock kernel, so upgraded to 3.4 following:
[http://askubuntu.com/questions/142192/can-i-install-linux-kernel-3-4-in-ubuntu-and-kubuntu-12-04](http://askubuntu.com/questions/142192/can-i-install-linux-kernel-3-4-in-ubuntu-and-kubuntu-12-04)

But then wifi didn't work, so fixed that using:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/994255](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/994255)  (post #5).

System now much more stable, and with wifi.

(have also installed mate desktop with fvwm window manager - nice!).

---

### Post by digsim on 2012-07-05
I'm facing the same problems as agb32. With the nointremap option the system installs and boots but is highly unstable (at the point that it is unusable for me).
As mentioned by agb32, I tried to install the 3.4.4 quantal Kernel. The system still requires the additional boot parameter. Since I had bad luck with the nointremap option I'll try for now the noapic option.

---

### Post by agb32 on 2012-07-05
I have the 3.4.0 quantal kernel... still with nointremap - but it is now stable...

Installed from the deb packages.

---

### Post by digsim on 2012-07-05
After a full day of use with the 3.4.4 quantal kernel and the noapic boot parameter my system appears to be stable. No more freeze (at least for today). For completeness I took the approach described on [http://www.upubuntu.com/2012/06/how-to-install-linux-kernel-343-on.html]("http://www.upubuntu.com/2012/06/how-to-install-linux-kernel-343-on.html") using the dropbox scipt on [http://dl.dropbox.com/u/47950494/upubuntu.com/linux-kernel-3.4.4]("http://dl.dropbox.com/u/47950494/upubuntu.com/linux-kernel-3.4.4")
BTW I had installed the wifi driver before upgrading to the 3.4.4 kernel (I came from stock ubuntu 12.04 kernel) and did not have to reinstall anything to get the wifi working. This maybe comes from the fact that I'm not using a MBA but rather a MB 13'' last generation.

---

### Post by adamski99 on 2012-07-05
hi,
im running 12.04 on MBP 9,2 13inch, had to use the nointremap boot option, does anyone know what its caused by?


had a few freezes after a couple of hours, might try the new kernel.

Also tried to load applesmc, but read_smc() fails, did a bit of debugging if anyone interested:

```
 
 [applesmc_init_smcreg_try]("http://lxr.free-electrons.com/ident?i=applesmc_init_smcreg_try")() first calls
 [read_register_count]("http://lxr.free-electrons.com/ident?i=read_register_count")() who returns 375

 then [applesmc_get_lower_bound]("http://lxr.free-electrons.com/ident?i=applesmc_get_lower_bound")() calls

[applesmc_get_entry_by_index]("http://lxr.free-electrons.com/ident?i=applesmc_get_entry_by_index")(187) which calls

[read_smc]("http://lxr.free-electrons.com/ident?i=read_smc")([APPLESMC_GET_KEY_BY_INDEX_CMD]("http://lxr.free-electrons.com/ident?i=APPLESMC_GET_KEY_BY_INDEX_CMD"), ([u8]("http://lxr.free-electrons.com/ident?i=u8") *)&be, [key]("http://lxr.free-electrons.com/ident?i=key"), 4);

which call 
send_argument(key) that successfully sends the first 3 bytes, 

then fails after the 4th waiting on __wait_status(0x04),

status read is always 0x05.

```Does anyone know anything aboot the SMC?

cheers

adam

---

### Post by kosumi68 on 2012-07-07
Hi adamski,

thanks for looking into this. A long shot, but maybe Apple changed the argument to APPLESMC_GET_KEY_BY_INDEX_CMD, from u32 to u16 for instance. The patch below will tell.

```

diff --git a/drivers/hwmon/applesmc.c b/drivers/hwmon/applesmc.c
index 0162f55..d0eb86e 100644
--- a/drivers/hwmon/applesmc.c
+++ b/drivers/hwmon/applesmc.c
@@ -194,11 +194,11 @@ static int send_command(u8 cmd)
        return -EIO;
 }
 
-static int send_argument(const char *key)
+static int send_argument(const char *key, int keylen)
 {
        int i;
 
-       for (i = 0; i < 4; i++) {
+       for (i = 0; i < keylen; i++) {
                outb(key[i], APPLESMC_DATA_PORT);
                if (__wait_status(0x04))
                        return -EIO;
@@ -206,11 +206,11 @@ static int send_argument(const char *key)
        return 0;
 }
 
-static int read_smc(u8 cmd, const char *key, u8 *buffer, u8 len)
+static int read_smc(u8 cmd, const char *key, int keylen, u8 *buffer, u8 len)
 {
        int i;
 
-       if (send_command(cmd) || send_argument(key)) {
+       if (send_command(cmd) || send_argument(key, keylen)) {
                pr_warn("%.4s: read arg fail\n", key);
                return -EIO;
        }
@@ -219,12 +219,14 @@ static int read_smc(u8 cmd, const char *key, u8 *buffer, u8 len)
 
        for (i = 0; i < len; i++) {
                if (__wait_status(0x05)) {
-                       pr_warn("%.4s: read data fail\n", key);
+                       pr_warn("%.*s: read data fail\n", keylen, key);
                        return -EIO;
                }
                buffer[i] = inb(APPLESMC_DATA_PORT);
        }
 
        return 0;
 }
 
@@ -232,7 +234,7 @@ static int write_smc(u8 cmd, const char *key, const u8 *buffer, u8 len)
 {
        int i;
 
-       if (send_command(cmd) || send_argument(key)) {
+       if (send_command(cmd) || send_argument(key, 4)) {
                pr_warn("%s: write arg fail\n", key);
                return -EIO;
        }
@@ -255,7 +257,7 @@ static int read_register_count(unsigned int *count)
        __be32 be;
        int ret;
 
-       ret = read_smc(APPLESMC_READ_CMD, KEY_COUNT_KEY, (u8 *)&be, 4);
+       ret = read_smc(APPLESMC_READ_CMD, KEY_COUNT_KEY, 4, (u8 *)&be, 4);
        if (ret)
                return ret;
 
@@ -278,7 +280,7 @@ static int applesmc_read_entry(const struct applesmc_entry *entry,
        if (entry->len != len)
                return -EINVAL;
        mutex_lock(&smcreg.mutex);
-       ret = read_smc(APPLESMC_READ_CMD, entry->key, buf, len);
+       ret = read_smc(APPLESMC_READ_CMD, entry->key, 4, buf, len);
        mutex_unlock(&smcreg.mutex);
 
        return ret;
@@ -301,7 +303,7 @@ static const struct applesmc_entry *applesmc_get_entry_by_index(int index)
 {
        struct applesmc_entry *cache = &smcreg.cache[index];
        u8 key[4], info[6];
-       __be32 be;
+       __be16 be;
        int ret = 0;
 
        if (cache->valid)
@@ -311,11 +313,11 @@ static const struct applesmc_entry *applesmc_get_entry_by_index(int index)
 
        if (cache->valid)
                goto out;
-       be = cpu_to_be32(index);
-       ret = read_smc(APPLESMC_GET_KEY_BY_INDEX_CMD, (u8 *)&be, key, 4);
+       be = cpu_to_be16(index);
+       ret = read_smc(APPLESMC_GET_KEY_BY_INDEX_CMD, (u8 *)&be, 2, key, 4);
        if (ret)
                goto out;
-       ret = read_smc(APPLESMC_GET_KEY_TYPE_CMD, key, info, 6);
+       ret = read_smc(APPLESMC_GET_KEY_TYPE_CMD, key, 4, info, 6);
        if (ret)
                goto out;

```

Thanks!

---

### Post by adamski99 on 2012-07-07
Hi,
Thanks for the suggestion but unfortunately didnt work.

after a lot of messing around i managed to get it to load by decreasing the minimum time it waits for the status from 0x0040 to 0x0010,

```


//#define APPLESMC_MIN_WAIT    0x0040
#define APPLESMC_MIN_WAIT    0x0010


```

not sure if this has any horrible side effects..

have managed to manually change the keyboard brightness value by poking:

/sys/bus/platform:applesmc/applesmc.768/leds/smc::kbd_backlight/brightness

but dedicated buttons dont seem to work.

have tried poking the fan speed, as it doesnt seem to budge from 2000rpm, but didnt seem to change.

Cheers

adam


> **kosumi68 said:**
> Hi adamski,

thanks for looking into this. A long shot, but maybe Apple changed the argument to APPLESMC_GET_KEY_BY_INDEX_CMD, from u32 to u16 for instance. The patch below will tell.

Thanks!

---

### Post by kosumi68 on 2012-07-08
Hi adamski,

> 
after a lot of messing around i managed to get it to load by decreasing the minimum time it waits for the status from 0x0040 to 0x0010,

```


//#define APPLESMC_MIN_WAIT    0x0040
#define APPLESMC_MIN_WAIT    0x0010


```

not sure if this has any horrible side effects..


Excellent, thank you. No, the side effects should be slim. The original linear timing scheme (from 2008) had a smallest wait time of 10 us, so potentially this tweak will work on all models.

I will accumulate some more tested-by's before applying the patch, though. If I can have you full name sent to [email]rydberg@euromail.se[/email], that would be great.

> 
have tried poking the fan speed, as it doesnt seem to budge from 2000rpm, but didnt seem to change.


Did you set fanX_manual first? Careful though, check this first: [http://ubuntuforums.org/showpost.php?p=6098587&postcount=10](http://ubuntuforums.org/showpost.php?p=6098587&postcount=10)

Since the 2012 machines seem different, it would be great to accumulate a bit more information, following this post: [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096)

Thanks!

---

### Post by adamski99 on 2012-07-08
> **kosumi68 said:**
> Hi adamski,

Did you set fanX_manual first? Careful though, check this first: [http://ubuntuforums.org/showpost.php?p=6098587&postcount=10](http://ubuntuforums.org/showpost.php?p=6098587&postcount=10)



Ok, so i can set the speed with the manual setting, but it doesnt seem to regulate its self automatically.

monitoring one of the temperatures (temp16_input )  and fan1_input with  4 stress threads got the temp value to 93000 (is that deg C ??) and fan speed is still ~2000

thanks for the help

adam

---

### Post by kosumi68 on 2012-07-08
> **adamski99 said:**
> Ok, so i can set the speed with the manual setting, but it doesnt seem to regulate its self automatically.

monitoring one of the temperatures (temp16_input )  and fan1_input with  4 stress threads got the temp value to 93000 (is that deg C ??) and fan speed is still ~2000


Yep, the output is in degC * 1000 (hwmon standard).

Ok, so the 2012 models seem to belong to the (small) set of machines where using macfanctld (or similar) is recommended for now.

---

### Post by adamski99 on 2012-07-08
> **kosumi68 said:**
> 
Ok, so the 2012 models seem to belong to the (small) set of machines  where using macfanctld (or similar) is recommended for now.

So i ran the same kind of heat test in mac os x and it acted similar so i let it get hotter, the fan only started increasing at above 95/96 deg C and slowly ramped up to about ~2500rpm with the temperature stable at around 94deg C.
i the repeated and similar results in ubuntu.

Seems strange to let it get that hot...

cheers

adam

---

### Post by kosumi68 on 2012-07-11
I added an updated applesmc-dkms package for precise in the mactel-support ppa, including support for the mid-2012 macs.

---

### Post by ascii00 on 2012-07-11
I would just like to complement you on fixing this bug. I played around with the damn module for ages and couldn't figure out why. But I noticed some changes when extending the time wait.

Thanks god it was such an easy solution though! :)

I played around with the fan-control, and it seem to work automaticly here on my MBP 9,2 mid-2012.

What I can't figure out is the trackpad gestures on my gnome-shell desktop. Using ginn, it registeres the swipes and taps, but the keys aren't sent correctly to desktop/application. Any pointers would be highly appricated! I would love the 3 finger navigation/3 and 4 finger tap etc.

Also, if anyone is interested I mocked up a quick gnome-shell extension for applesmc keyboard backlight adjustment. You can find at [http://www.grimsby.us/?p=132]("http://www.grimsby.us/?p=132"). Still needs a bit of work, but still...

Cheers people, Kristian

---

### Post by poliva on 2012-07-12
> **kosumi68 said:**
> I added an updated applesmc-dkms package for precise in the mactel-support ppa, including support for the mid-2012 macs.

Great work :-)
Maybe it's time to write write a wiki page with instructions for new models...

---

### Post by beniz on 2012-07-13
Thanks for the applesmc module, it loads like a charm (with kernel 3.4.4 from the mainline kernel ppa).

Using a 11" MBA 2012, I can't get the USB ports to work. Am I the only one witnessing this problem ?
Typically, I can't locate the ehci or xhci hcd modules. Any information is warmly welcome!

---

### Post by shamusl on 2012-07-13
I'm getting one of these in a few weeks. I have the option of getting a MBA or a 2009 Macbook. I mostly want Ubuntu. What's the consensus?

---

### Post by ascii00 on 2012-07-14
> **adamski99 said:**
> Hi,
Thanks for the suggestion but unfortunately didnt work.

after a lot of messing around i managed to get it to load by decreasing the minimum time it waits for the status from 0x0040 to 0x0010,

```


//#define APPLESMC_MIN_WAIT    0x0040
#define APPLESMC_MIN_WAIT    0x0010


```

not sure if this has any horrible side effects..

have managed to manually change the keyboard brightness value by poking:

/sys/bus/platform:applesmc/applesmc.768/leds/smc::kbd_backlight/brightness

but dedicated buttons dont seem to work.

have tried poking the fan speed, as it doesnt seem to budge from 2000rpm, but didnt seem to change.

Cheers

adam

Are you experiencing problems after a while with the module?

> Jul 13 11:23:04 ascii-mbp kernel: [34906.451692] applesmc: #KEY: read arg fail
Jul 13 11:23:04 ascii-mbp kernel: [34906.571343] applesmc: #KEY: read arg fail
Jul 13 11:23:04 ascii-mbp kernel: [34906.691086] applesmc: #KEY: read arg fail
Jul 13 11:23:04 ascii-mbp kernel: [34906.810829] applesmc: #KEY: read arg fail
Jul 13 11:23:04 ascii-mbp kernel: [34906.930477] applesmc: #KEY: read arg fail
Jul 13 11:23:04 ascii-mbp kernel: [34907.050215] applesmc: #KEY: read arg fail
Jul 13 11:23:04 ascii-mbp kernel: [34907.169907] applesmc: #KEY: read arg fail
Jul 13 11:23:04 ascii-mbp kernel: [34907.289559] applesmc: #KEY: read arg fail
Jul 13 11:23:05 ascii-mbp kernel: [34907.409288] applesmc: #KEY: read arg fail

This is what I get after unknown time. The module stops working and won't load after a rmmod.

Anyone else experienced this?

---

### Post by asting on 2012-07-14
> **shamusl said:**
> I'm getting one of these in a few weeks. I have the option of getting a MBA or a 2009 Macbook. I mostly want Ubuntu. What's the consensus?
Although I can't comment on Ubuntu because I've yet to install it on my 2012 (it's on my to do list) I can comment on the specs. The 2012 macbook air is much faster and much better equipped than a 2009 macbook. Whether the difference in price is worth it is up to you, but the 2012 will undoubtedly be faster (faster/more ram, MUCH faster cpu, a hard drive that is an order of magnitude faster, much more power graphics).

---

### Post by adamski99 on 2012-07-15
hi,

> **ascii00 said:**
> Are you experiencing problems after a while with the module?

This is what I get after unknown time. The module stops working and won't load after a rmmod.

Anyone else experienced this?

i have not had that error since ive been using it (a week). What mac have u got out of interest?

Ive just been messing around with the wait value and it seems send_command() fails in a similar manner if i decrease the MIN_WAIT below ~0x0004. And it will not manage to load (even if i reinstate the higher MIN_WAIT) until after a restart. It seems once one send_command() fails the smc and driver get out of sync.


```

Jul 15 19:49:48 adam-MacBookPro kernel: [ 1547.001399] applesmc: Th1H: read cmd fail
Jul 15 19:49:48 adam-MacBookPro kernel: [ 1547.097675] applesmc: #KEY: read cmd fail
Jul 15 19:49:48 adam-MacBookPro kernel: [ 1547.193686] applesmc: #KEY: read cmd fail
Jul 15 19:49:48 adam-MacBookPro kernel: [ 1547.289393] applesmc: #KEY: read cmd fail
Jul 15 19:49:48 adam-MacBookPro kernel: [ 1547.385364] applesmc: #KEY: read cmd 
...


```
 send_argument() still works for me with MIN_WAIT right down to 0x0001.

Anywhere in the range 0x0001 to 0x0010 i occasionally get 1 read arg fail during init after which it successfully loads. (not sure the exact percentage but after doing tens of load / unload).

cheers

ads

---

### Post by adamski99 on 2012-07-15
On closer inspection it seems i can break it with MIN_WAIT = 0x0010.

wrote a script to constantly read and print  a bunch of temperatures:

ran one instance for 5mins without errors,

ran 2 instances and after a minute or so the read fails.

I separated the error checking for cmd and arg, so i can tell its the command failing

```

Jul 15 22:32:17 adam-MacBookPro kernel: [  428.307688] applesmc: TB2T: read cmd fail
Jul 15 22:32:17 adam-MacBookPro kernel: [  428.340194] applesmc: TC0J: read cmd fail
Jul 15 22:32:17 adam-MacBookPro kernel: [  428.372731] applesmc: TC0E: read cmd fail
Jul 15 22:32:17 adam-MacBookPro kernel: [  428.405269] applesmc: TG1D: read cmd fail
Jul 15 22:32:17 adam-MacBookPro kernel: [  428.437784] applesmc: TC0F: read cmd fail
...

```

the status read is always 0x0E.

after this the module fails to load until i reboot.


I tried using a different MIN_WAIT for the wait_status() and the send_command(), using 0x0080 for the send_command() and 0x0010 for the wait_status() 

```

#define APPLESMC_MIN_WAIT    0x0010
#define APPLESMC_MIN_WAIT_CMD    0x0080

```

this "seems" to improve it, have run 3 instances of the script for ~15mins without a fail yet...

---

### Post by MikaelHolber on 2012-07-19
I noticed some problems with gnome settings that might not be machine specific. I cannot turn off dim-screen or enable lock-screen. I've tried both gui-settings and using gsettings.
```
gsettings set org.gnome.settings-daemon.plugins.power idle-dim-ac false
gsettings set org.gnome.desktop.screensaver lock-enabled true
```
The desktop also doesn't save my brightness backlighting settings for screen and keyboard but are always on max after reboot or cold start.

---

### Post by MikaelHolber on 2012-07-19
I have the same problem with the applesmc failing after some time. This cause the fan control to stop working and machine gets hotter than with fan control working. Only reboot solves the problem.

> **adamski99 said:**
> 
```

#define APPLESMC_MIN_WAIT    0x0010
#define APPLESMC_MIN_WAIT_CMD    0x0080

```

this "seems" to improve it, have run 3 instances of the script for ~15mins without a fail yet...

Did you see any improvement on the stability of the module? Did it solve the problem?

---

### Post by myselph on 2012-07-23
Hi all,

I have a Macbook Pro 9,2 (13'') with Ubuntu 12.04. I also had problem with the SMC stopping working after 15-30 minutes (same problem in 12.10, by the way). What helped a lot was the following change (which is, as the module's maintainer Henrik Rydberg pointed out, more or less going back to what the code did before problems with post-2009-models):

In [FONT=Courier New]send_command()[/FONT], move the [FONT=Courier New]outb(cmd, APPLESMC_CMD_PORT);[/FONT] out and in front of the for-loop, so the port is not written to on every iteration but only once.

This is not a final solution to the problem since I still get some errors of the type [FONT=Courier New]applesmc: FS! : write arg fail[/FONT], maybe five per hour, but my SMC hasn't crashed for six hours now with macfanctld constantly accessing it, so it's at least an improvement.

Best,
    Hubert

---

### Post by adamski99 on 2012-07-23
Hi,
> **myselph said:**
> 
In send_command(), move the outb(cmd, APPLESMC_CMD_PORT); out and in front of the for-loop, so the port is not written to on every iteration but only once.


great, this indeed stops the driver from locking up, I am getting a lot of single fails though.

had a look at what status returned and when a cmd "resend" is needed.

This is what happens on my machine with the outb(cmd, APPLESMC_CMD_PORT); outside the for loop.

On a successful send_command() the status is:

```


initial status=0x04

then we send cmd: outb(cmd, APPLESMC_CMD_PORT);

status=0x0A

for a few ms then

status=0x0C and we exit the loop.


```


sometimes it fails:

```

initial status= 0x04

then we send cmd: outb(cmd, APPLESMC_CMD_PORT);

status=0x08

and it times out with status at this value


```

I have no idea what any of the status values mean, but we can reduce the number of times the cmd is sent, as this seems problematic, by only re-sending if the status == 0x08

this is what my send_command() looks like:

```

static int send_command(u8 cmd)
{
    int us;
    
    outb(cmd, APPLESMC_CMD_PORT);
    for (us = APPLESMC_MIN_WAIT; us < APPLESMC_MAX_WAIT; us <<= 1) {
       
        udelay(us);
        if ((inb(APPLESMC_CMD_PORT) & APPLESMC_STATUS_MASK) == 0x0c) {
            return 0;
        }
        else if ((inb(APPLESMC_CMD_PORT) & APPLESMC_STATUS_MASK) == 0x08) {
            /* resend the cmd as SMC is unhappy */  
            outb(cmd, APPLESMC_CMD_PORT);
        }
    }

    return -EIO;
}

```

havent tested much but it seems to be running stable at the moment.

cheers

ads

---

### Post by beniz on 2012-07-24
Even with new kernel 3.5, USB ports are not working for me.

However, I did stumble on this thread and solution, for those interested: [http://www.spinics.net/lists/linux-usb/msg67003.html](http://www.spinics.net/lists/linux-usb/msg67003.html)

I haven't tested yet.

Edit: I've found the culprit so I'm sharing it here in case it can help someone. I was booting with option 'nolapic', once removed, leaving the only 'noapic' parameter to the kernel, the USB controller was successfully recognized, ports working properly.

---

### Post by jhodapp on 2012-07-24
One thing I'm running into is that quite often, booting into Linux from rEFIt into Grub doesn't restore screen brightness, so it'll boot into Grub and then into Ubuntu with a completely darkened screen. I know that it's fully booting because I can see the screen contents if I shine a flashlight on it. I'm not quite sure what the cause of this is.

---

### Post by kosumi68 on 2012-07-24
Hi adamski,

I think you are on to something here. It would be great to find out the minimum number of return codes which choke on a command resend. If it is just one or two, this approach might also work on older machines. So, this patch might be useful:

```

diff --git a/drivers/hwmon/applesmc.c b/drivers/hwmon/applesmc.c
index 4d937a1..4e01ef7 100644
--- a/drivers/hwmon/applesmc.c
+++ b/drivers/hwmon/applesmc.c
@@ -189,11 +189,28 @@ static int __wait_status(u8 val)
 static int send_command(u8 cmd)
 {
 	int us;
+	outb(cmd, APPLESMC_CMD_PORT);
 	for (us = APPLESMC_MIN_WAIT; us < APPLESMC_MAX_WAIT; us <<= 1) {
-		outb(cmd, APPLESMC_CMD_PORT);
 		udelay(us);
-		if ((inb(APPLESMC_CMD_PORT) & APPLESMC_STATUS_MASK) == 0x0c)
+		switch (inb(APPLESMC_CMD_PORT) & APPLESMC_STATUS_MASK) {
+		case 0x08: /* resend */
+			outb(cmd, APPLESMC_CMD_PORT);
+			break;
+		case 0x0a: /* wait */
+			break;
+		case 0x0c: /* success */
 			return 0;
+		case 0x0e: /* error */
+			outb(cmd, APPLESMC_CMD_PORT);
+			break;
+		case 0x0f: /* unknown */
+			outb(cmd, APPLESMC_CMD_PORT);
+			break;
+		default:
+			pr_warn("send %d: unknown status: %d\n",
+				cmd, inb(APPLESMC_CMD_PORT));
+			break;
+		}
 	}
 	return -EIO;
 }

```

Here, only 0x0a skips the resend. If that works for you, I will test it on some older machines as well. So far, I know this works fine on an MBA3,1.

It could well be that the different status codes should have different wait times as well...

Thanks!

---

### Post by adamski99 on 2012-07-24
Hi,
> **kosumi68 said:**
> 
Here, only 0x0a skips the resend. If that works for you, I will test it on some older machines as well. So far, I know this works fine on an MBA3,1.

It could well be that the different status codes should have different wait times as well...

Thanks!

This seems to work for me as well, a couple of things i noticed:

1. With both this and the code from my last post i get quite a high error status 0x0e returned in send cmd, but seems to recover fairly quickly without a resend, the send_command() does not fail here for me.

2. I get quite a high  fail rate in the send_argument() routine. A fail every 5-10seconds when doing lots of reads. This rate falls drastically (no errors in 10mins) if i increase the min wait used in the send_command() routine to 0x0100 (separate min waits for arg and cmd). The high  error status rate in send_command() goes away as well.

Cheers

ads

---

### Post by mschinca on 2012-07-24
Hi all,
I'm running 12.04 on a 13" MBA 5,2 (Mid 2012) with 3.2.0 stock kernel and latest applesmc from PPA. I am booting with noapic parameter.
Everything looks fine, I turned keyboard backlight on manually as desribed by @adamski99.
I just want to report my temperatures after 1 hour uptime, are those values safe?
[http://paste.ubuntu.com/1109202/](http://paste.ubuntu.com/1109202/)
I'm not using manual fan control, should I?

Best regards.

---

### Post by kosumi68 on 2012-07-25
Hi adamski,

> **adamski99 said:**
> 
1. With both this and the code from my last post i get quite a high error status 0x0e returned in send cmd, but seems to recover fairly quickly without a resend, the send_command() does not fail here for me.


Ah. So it seems the resend should not be done in so many cases,
after all.

> 
2. I get quite a high  fail rate in the send_argument() routine. A fail every 5-10seconds when doing lots of reads. This rate falls drastically (no errors in 10mins) if i increase the min wait used in the send_command() routine to 0x0100 (separate min waits for arg and cmd). The high  error status rate in send_command() goes away as well.


Which could be because of the resend, if I interpret this
correctly.

I have a theory as to why we are seeing three distinctly
different behaviors, summarized in the patch below. The patch
seems to be essentially the same as yours.

It would be great to see that this one works, and I would very
much like to have your email, for proper credits. :-)

Thanks!

```

From 4aa5d755bab1690540aef9893cb35f29ee58414a Mon Sep 17 00:00:00 2001
From: Henrik Rydberg <rydberg@euromail.se>
Date: Wed, 25 Jul 2012 09:39:35 +0200
Subject: [PATCH] hwmon: (applesmc) Decode send_command() status codes

It appears as if the the way commands are sent to the smc have changed
over the years, and the mid-2012 macbooks have further accentuated
this problem. However, the most likely explanation is that we are
experiencing a timeout and a shift in smc speed.

We should first wait for the line to settle, which was the most
frequent response on the old slow machines. Then, if the smc is busy,
we need to try again later by resending the command. This was the most
likely response until 2012. Now, with a shorter wait time, we are
again most likely to poll while the smc is settling, which is why we
see such high failure rates on the mid-2012 models.

This patch takes the command status bits into account, which seems to
work for all models.
---
 drivers/hwmon/applesmc.c | 16 ++++++++++++----
 1 file changed, 12 insertions(+), 4 deletions(-)

diff --git a/drivers/hwmon/applesmc.c b/drivers/hwmon/applesmc.c
index 4d937a1..583377b 100644
--- a/drivers/hwmon/applesmc.c
+++ b/drivers/hwmon/applesmc.c
@@ -182,18 +182,26 @@ static int __wait_status(u8 val)
 }
 
 /*
- * special treatment of command port - on newer macbooks, it seems necessary
- * to resend the command byte before polling the status again. Callers must
+ * special treatment of command port - the low bits determine if we should
+ * resend the command byte before polling the status again. Callers must
  * hold applesmc_lock.
  */
 static int send_command(u8 cmd)
 {
+	u8 status;
 	int us;
+	outb(cmd, APPLESMC_CMD_PORT);
 	for (us = APPLESMC_MIN_WAIT; us < APPLESMC_MAX_WAIT; us <<= 1) {
-		outb(cmd, APPLESMC_CMD_PORT);
 		udelay(us);
-		if ((inb(APPLESMC_CMD_PORT) & APPLESMC_STATUS_MASK) == 0x0c)
+		status = inb(APPLESMC_CMD_PORT);
+		/* wait for smc to settle */
+		if (status & 0x03)
+			continue;
+		/* ready for argument */
+		if (status & 0x04)
 			return 0;
+		/* failed, resend */
+		outb(cmd, APPLESMC_CMD_PORT);
 	}
 	return -EIO;
 }
-- 
1.7.11.3

```

---

### Post by myselph on 2012-07-25
This patch also works on my MBP9,2, thanks, adamski & kosumi; there are no more send_command errors.

I still get many send_argument errors, though. Just for the sake of completeness, here's what I did yesterday to solve the problem.
I don't outb again in send_command but just return if the status is 0x08; and in read_smc(), I have
```
static int read_smc(u8 cmd, const char *key, u8 *buffer, u8 len) {
    int i;
#define SEND_CMDARG_TRIES 3
    for (i=0; i<SEND_CMDARG_TRIES; i++) {
        if (send_command(cmd)) {
            pr_warn("read arg fail %d - send_command(0x%2X) (key=\"%.4s\")\n",
                i+1, cmd, key);
            continue;
        }
        if (send_argument(key)) {
            pr_warn("read arg fail %d - send_argument(\"%.4s\")\n", i+1, key);
        } else {
            break;
        }
    }
    if (i==SEND_CMDARG_TRIES) return -EIO;
```This takes care of the (required?) command resend before again calling send_argument. I never had more than one retry with the above construction.
Best,
   Hubert

---

### Post by Notclive on 2012-07-25
Has anyone got UEFI grub working? I get a black screen, though I can get a working display by plugging in and unplugging an external monitor.

---

### Post by Notclive on 2012-07-25
It seems the 3.2.0-26 kernel works but the 3.2.0-27 doesn't. I will try a newer kernel tomorrow.

---

### Post by kosumi68 on 2012-07-26
adamski, myselph,

Thanks for the feedback. It seems all writes should be treated
the same way, which also affects what status is important during
reads. Also, as adamski pointed out several times, additional
timing is important. They way it is incorporated in the patch
below means we do not have to sacrifice general read speed.

Tested to work successfully on the MBA3,1 and the much more
tricky MBA1,1. Please give it a try. :-)

Cheers!

```

From 7f83e1bc2d41d2346c4ddc6aa5ef0cf0a9a586f6 Mon Sep 17 00:00:00 2001
From: Henrik Rydberg <rydberg@euromail.se>
Date: Thu, 26 Jul 2012 09:40:49 +0200
Subject: [PATCH] hwmon: (applesmc) Decode and act on read/write status codes

The behavior of the SMC has changed several times over the years,
causing read failures in the driver. It seems the problem can be
explained by a shift in SMC speed combined with improper action on
status codes.

We should first wait for the SMC to settle, which was the most
frequent response on the old slow machines. Then, if the SMC is busy,
we need to try again later by resending the command. This was the most
likely response until 2012. Now, with a shorter wait time, we are
again most likely to poll while the SMC is settling, and as a result
we see high failure rates on the mid-2012 models.

With the distinction between busy and failure, we can also wait longer
before retrying without sacrificing speed.  This seems to bring
failures down to virtually zero.

Tested on: MBA1,1 MBA3,1

Signed-off-by: Henrik Rydberg <rydberg@euromail.se>
---
 drivers/hwmon/applesmc.c | 66 ++++++++++++++++++++++++++++++------------------
 1 file changed, 42 insertions(+), 24 deletions(-)

diff --git a/drivers/hwmon/applesmc.c b/drivers/hwmon/applesmc.c
index 4d937a1..50b1814 100644
--- a/drivers/hwmon/applesmc.c
+++ b/drivers/hwmon/applesmc.c
@@ -55,9 +55,9 @@
 
 /* wait up to 32 ms for a status change. */
 #define APPLESMC_MIN_WAIT	0x0010
+#define APPLESMC_RETRY_WAIT	0x0100
 #define APPLESMC_MAX_WAIT	0x8000
 
-#define APPLESMC_STATUS_MASK	0x0f
 #define APPLESMC_READ_CMD	0x10
 #define APPLESMC_WRITE_CMD	0x11
 #define APPLESMC_GET_KEY_BY_INDEX_CMD	0x12
@@ -162,51 +162,64 @@ static unsigned int key_at_index;
 static struct workqueue_struct *applesmc_led_wq;
 
 /*
- * __wait_status - Wait up to 32ms for the status port to get a certain value
- * (masked with 0x0f), returning zero if the value is obtained.  Callers must
+ * wait_read - Wait for a byte to appear on SMC port. Callers must
  * hold applesmc_lock.
  */
-static int __wait_status(u8 val)
+static int wait_read(void)
 {
+	u8 status;
 	int us;
-
-	val = val & APPLESMC_STATUS_MASK;
-
 	for (us = APPLESMC_MIN_WAIT; us < APPLESMC_MAX_WAIT; us <<= 1) {
 		udelay(us);
-		if ((inb(APPLESMC_CMD_PORT) & APPLESMC_STATUS_MASK) == val)
+		status = inb(APPLESMC_CMD_PORT);
+		/* read: wait for smc to settle */
+		if (status & 0x01)
 			return 0;
 	}
 
+	pr_warn("wait_read() fail: 0x%02x\n", status);
 	return -EIO;
 }
 
 /*
- * special treatment of command port - on newer macbooks, it seems necessary
- * to resend the command byte before polling the status again. Callers must
- * hold applesmc_lock.
+ * send_byte - Write to SMC port, retrying when necessary. Callers
+ * must hold applesmc_lock.
  */
-static int send_command(u8 cmd)
+static int send_byte(u8 cmd, u16 port)
 {
+	u8 status;
 	int us;
+	outb(cmd, port);
 	for (us = APPLESMC_MIN_WAIT; us < APPLESMC_MAX_WAIT; us <<= 1) {
-		outb(cmd, APPLESMC_CMD_PORT);
 		udelay(us);
-		if ((inb(APPLESMC_CMD_PORT) & APPLESMC_STATUS_MASK) == 0x0c)
+		status = inb(APPLESMC_CMD_PORT);
+		/* write: wait for smc to settle */
+		if (status & 0x02)
+			continue;
+		/* ready: cmd accepted, return */
+		if (status & 0x04)
 			return 0;
+		/* busy: long wait and resend */
+		udelay(APPLESMC_RETRY_WAIT);
+		outb(cmd, port);
 	}
+
+	pr_warn("send_byte(0x%02x, 0x%04x) fail: 0x%02x\n", cmd, port, status);
 	return -EIO;
 }
 
+static int send_command(u8 cmd)
+{
+	return send_byte(cmd, APPLESMC_CMD_PORT);
+}
+
 static int send_argument(const char *key)
 {
 	int i;
 
-	for (i = 0; i < 4; i++) {
-		outb(key[i], APPLESMC_DATA_PORT);
-		if (__wait_status(0x04))
+	for (i = 0; i < 4; i++)
+		if (send_byte(key[i], APPLESMC_DATA_PORT))
 			return -EIO;
-	}
 	return 0;
 }
 
@@ -219,11 +232,14 @@ static int read_smc(u8 cmd, const char *key, u8 *buffer, u8 len)
 		return -EIO;
 	}
 
-	outb(len, APPLESMC_DATA_PORT);
+	if (send_byte(len, APPLESMC_DATA_PORT)) {
+		pr_warn("%.4s: read len fail\n", key);
+		return -EIO;
+	}
 
 	for (i = 0; i < len; i++) {
-		if (__wait_status(0x05)) {
-			pr_warn("%.4s: read data fail\n", key);
+		if (wait_read()) {
+			pr_warn("%.4s: read data[%d] fail\n", key, i);
 			return -EIO;
 		}
 		buffer[i] = inb(APPLESMC_DATA_PORT);
@@ -241,14 +257,16 @@ static int write_smc(u8 cmd, const char *key, const u8 *buffer, u8 len)
 		return -EIO;
 	}
 
-	outb(len, APPLESMC_DATA_PORT);
+	if (send_byte(len, APPLESMC_DATA_PORT)) {
+		pr_warn("%.4s: write len fail\n", key);
+		return -EIO;
+	}
 
 	for (i = 0; i < len; i++) {
-		if (__wait_status(0x04)) {
+		if (send_byte(buffer[i], APPLESMC_DATA_PORT)) {
 			pr_warn("%s: write data fail\n", key);
 			return -EIO;
 		}
-		outb(buffer[i], APPLESMC_DATA_PORT);
 	}
 
 	return 0;
-- 
1.7.11.3

```

---

### Post by myselph on 2012-07-26
Thanks for the code, kosumi, this works great here. I did a stress test where I perform many reads (infinite while loop with cat on temperature sensors in two terminals) and did not get any read errors (just one write error in five minutes coming from macfanctld running at the same time). So I checked on write errors, and I got write errors when performing a write stress test:
```
while [ 0 -eq 0 ]; do echo 0 > /sys/class/hwmon/hwmon0/device/fan1_manual; done
```but that's a pretty exotic test scenario. What happens on a fail is that in send_byte, the initial status goes from 0x44 to 0x40 after the outb and remains there until the loop ends. This only happens under heavy load, so I guess we can ignore it - or insert something like
```
if (!(status & 0x0f)) break;
```Just a brief note on the command resend - if it happens in the last iteration of the loop, there's no status check and an error will occur nonetheless, so maybe you could insert something like
```
        /* busy: long wait and resend */
        if ((us<<1) >= APPLESMC_MAX_WAIT) break; //last iteration;
        udelay(APPLESMC_RETRY_WAIT);
        outb(cmd, port);

```So, on my MBP9,2, your changes seem to solve all the problems I had. Thanks a lot to you and adamski!
    Hubert

---

### Post by kosumi68 on 2012-07-26
> **mschinca said:**
> Hi all,
I'm running 12.04 on a 13" MBA 5,2 (Mid 2012) with 3.2.0 stock kernel and latest applesmc from PPA. I am booting with noapic parameter.
Everything looks fine, I turned keyboard backlight on manually as desribed by @adamski99.
I just want to report my temperatures after 1 hour uptime, are those values safe?
[http://paste.ubuntu.com/1109202/](http://paste.ubuntu.com/1109202/)
I'm not using manual fan control, should I?

Best regards.

Looks ok (the 129 is actually -2). Check the mactel repo for a fresh update.

Thanks.

---

### Post by kosumi68 on 2012-07-26
> **myselph said:**
> Thanks for the code, kosumi, this works great here. I did a stress test where I perform many reads (infinite while loop with cat on temperature sensors in two terminals) and did not get any read errors (just one write error in five minutes coming from macfanctld running at the same time). So I checked on write errors, and I got write errors when performing a write stress test:
```
while [ 0 -eq 0 ]; do echo 0 > /sys/class/hwmon/hwmon0/device/fan1_manual; done
```but that's a pretty exotic test scenario. What happens on a fail is that in send_byte, the initial status goes from 0x44 to 0x40 after the outb and remains there until the loop ends. This only happens under heavy load, so I guess we can ignore it - or insert something like
```
if (!(status & 0x0f)) break;
```Just a brief note on the command resend - if it happens in the last iteration of the loop, there's no status check and an error will occur nonetheless, so maybe you could insert something like
```
        /* busy: long wait and resend */
        if ((us<<1) >= APPLESMC_MAX_WAIT) break; //last iteration;
        udelay(APPLESMC_RETRY_WAIT);
        outb(cmd, port);

```So, on my MBP9,2, your changes seem to solve all the problems I had. Thanks a lot to you and adamski!
    Hubert

Thanks for that, Hubert. I added a timeout break and your Tested-by and will push it upstream once I get a few more positive reactions. Great work, everyone. :-)

PS. I uploaded the new applesmc version to the mactel ppa.

---

### Post by barryf on 2012-07-27
> **jhodapp said:**
> One thing I'm running into is that quite often, booting into Linux from rEFIt into Grub doesn't restore screen brightness, so it'll boot into Grub and then into Ubuntu with a completely darkened screen. I know that it's fully booting because I can see the screen contents if I shine a flashlight on it. I'm not quite sure what the cause of this is.

I'm getting the same here. Doesn't happen all the time, and I have to keep rebooting/powering off until the screen kicks in. I do not even see the grub menu.

Other than that, everything seems to work great.

---

### Post by jhodapp on 2012-09-04
> **barryf said:**
> I'm getting the same here. Doesn't happen all the time, and I have to keep rebooting/powering off until the screen kicks in. I do not even see the grub menu.

Other than that, everything seems to work great.

I figured out that if you wait for a little while (~30+ seconds) in rEFIt, then the screen brightness is restored every time for me. It seems that rEFIt does some controller initialization that the Linux kernel is not doing (or shouldn't do). I'd be curious if you can confirm that this works for you too? Obviously not an ideal solution, but at least more predictable to get into Ubuntu.

---

### Post by saintdev on 2012-09-04
> **jhodapp said:**
> I figured out that if you wait for a little while (~30+ seconds) in rEFIt, then the screen brightness is restored every time for me. It seems that rEFIt does some controller initialization that the Linux kernel is not doing (or shouldn't do). I'd be curious if you can confirm that this works for you too? Obviously not an ideal solution, but at least more predictable to get into Ubuntu.

I use rEFInd and have not had any problem like this.

---

### Post by barryf on 2012-09-05
> **jhodapp said:**
> I figured out that if you wait for a little while (~30+ seconds) in rEFIt, then the screen brightness is restored every time for me. It seems that rEFIt does some controller initialization that the Linux kernel is not doing (or shouldn't do). I'd be curious if you can confirm that this works for you too? Obviously not an ideal solution, but at least more predictable to get into Ubuntu.

I'll try that next time I reboot, although with suspend/resume working so well now I rarely do that :)

---

### Post by asting on 2012-09-13
Forgive me for most of these posts went right over my head.
What is the state of this install? Is there a guide anywhere detailing what to do? I assume refit is still necessary.

Thanks for indulging a noobie.

---

### Post by sml on 2012-12-20
> **asting said:**
> 
What is the state of this install? 

i downloaded mint 14 (essentially ubuntu 12.10) .. burnt to DVD .. installed via external DVD player ... everything seems perfect except:

1. the stupid apple start-up gong sound
2. i have the start-up white screen delay for 15 seconds

---

### Post by Notclive on 2012-12-21
> **sml said:**
> 1. the stupid apple start-up gong sound
Boot into OSX and mute the sound, when you restart there will be no gong.

> **sml said:**
> 2. i have the start-up white screen delay for 15 seconds
Use [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") to install an UEFI boot loader, haven't tried on mint myself only Ubuntu 12.10.

---

