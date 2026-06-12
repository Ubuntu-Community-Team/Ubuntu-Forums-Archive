---
title: "iMac upgrade 20.04 &gt; 20.10 graphics driver issue"
date: 2020-10-30
forum: Apple Hardware Users
---

### Post by smojo on 2020-10-30
I recently upgraded my iMac (late 2015 with Intel 6200 integrated graphics) from 20.04 to 20.10.
After installation i am greeted with a black screen.

I only seem to b able to boot with the old kernel 5.4.
Or by appending nomodeset to the 5.8 boot options.

In the failed boot report it says: 
```
gnome-shell[1960]: Failed to create backend: No drm devices found
```

I'd like to fix the problem.  
nomodeset isn't an option since my second screen isn't recognized.

---

### Post by DuckHook on 2020-10-30
Welcome to the forums, smojo.

Though we normally frown on "me too" posts, given that your error message is exactly the same as the one reported in my post [here]("https://ubuntuforums.org/showthread.php?t=2452873"), I think it highly likely that we suffer from the same problem. Hence, I doubt that it's HW-related: my system differs from yours significantly, but we are getting the same symptoms/logged errors.

FTR, my HW is PC architecture (not Apple) with AMD GPU (vs your Intel). This actually helps because it suggests that the same problem afflicts different HW, thus eliminating HW as the issue.

Referencing my linked post, does dmesg work on yours? Can you please post the results of:```
cat /var/log/syslog | egrep -i 'error|warn|fault|fatal|fail'
```
Given that we share the same problem, I obviously have no solution for you, but by pooling our efforts, perhaps we can make a start.

---

### Post by smojo on 2020-10-30
Thanks for the update DuckHook!

This is the output from syslog for one boot.
[https://pastebin.ubuntu.com/p/CnnK98H2sT/](https://pastebin.ubuntu.com/p/CnnK98H2sT/)

Maybe some relevant extra info.
I boot from an external SSD.

---

### Post by DuckHook on 2020-10-30
Hmm&#8230; your log errors are eerily similar to mine. I boot from internal SSD connected via standard bus, so that's not the source of the problem.

Please scan my thread because oldfred is helping out over there. However, for sake of good thread hygiene, let's maintain separation between your issue and mine for now.

---

### Post by smojo on 2020-10-30
I have an identical external SSD which I used to try some other distro's.  
Booting from USB for Ubuntu 20.10 installation and Manjaro also fail exactly the same way.

They both have a kernel > 5.6
On the Manjaro forums people seemed to have a similar problem.  Their fix was to add intel_iommu=on as boot option, but this doesn't seem to do anything on my installation.

---

### Post by smojo on 2020-10-30
Graphics card info (booted with kernel 5.4)

```

00:02.0 VGA compatible controller [0300]: Intel Corporation Iris Pro Graphics 6200 [8086:1622] (rev 0a) (prog-if 00 [VGA controller])
    DeviceName: Integrated Video Controller
    Subsystem: Apple Inc. Iris Pro Graphics 6200 [106b:014f]
    Flags: bus master, fast devsel, latency 0, IRQ 56
    Memory at b0000000 (64-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

```

```

  *-display                 
       description: VGA compatible controller
       product: Iris Pro Graphics 6200
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0a
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:56 memory:b0000000-b0ffffff memory:a0000000-afffffff ioport:3000(size=64) memory:c0000-dffff

```

---

### Post by DuckHook on 2020-10-30
Your HW shows no surprises. The i915 driver is quite stable by now.

Kudos to you for having the initiative to try passing the kernel parameter. When you added it, did you do so by adding to boot process interactively, or through modifying /etc/default/grub? If the later, you must remember to run:```
sudo update-grub
```

---

### Post by smojo on 2020-10-30
I passed them interactively.  
That's how i found out using nomodeset also works on 5.8
But no external monitor support and terrible screen tearing.

---

### Post by DuckHook on 2020-10-30
> **smojo said:**
> I…But no external monitor support and terrible screen tearing.
Yes. Nomodeset disables HW acceleration. That's why it often works—by falling back to a more primitive mode. It's not meant as a long&#8209;term solution but as a temporary get&#8209;by.

I'm going to be offline for a few hours. Will tinker with my setup further tonight. If I make any headway, I will alert you.

---

### Post by DuckHook on 2020-10-31
Unfortunately, my explorations have been fruitless so far. My own setup is still borked on the new kernel. Thankfully, the old kernel works, which I find to be an acceptable short&#8209;term solution for now.

One thing you might try is running a LiveUSB to see if that works. If it does, it could indicate that some inherited configuration from the old install might be the problem. The implication would then be that a fresh install might work fine.

Another option is to simply stick with Focal. If there's no pressing reason to go with Groovy, then sticking with Focal brings many benefits: Long Term Support, increased stability, larger user (ie helper) base, etc.

In my own case, I'm willing to wait and see if the next kernel update solves the problem. The problematic partition isn't my production OS, so I'm in no hurry.

---

### Post by smojo on 2020-11-01
As I stated above I tried booting of both Groovy and the lastest Manjaro, both present me with a black screen on boot. (LiveUsb)
I didn't try safe graphics which seems to set NOMODESET upon starting.

On the Manjaro forums people seem to be experiencing this problem since the 5.7 kernel.

---

### Post by smojo on 2020-11-01
I can boot again without having to set NOMODESET..... using  5.10 RC1 kernel!
Kernel 5.10 seems to fix the issue.  

I did this:

```

mkdir kernel_5_10_RC_1
cd kernel_5_10_RC_1
wget -c https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.10-rc1/amd64/linux-headers-5.10.0-051000rc1_5.10.0-051000rc1.202010291359_all.deb
wget -c https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.10-rc1/amd64/linux-headers-5.10.0-051000rc1-generic_5.10.0-051000rc1.202010291359_amd64.deb
wget -c https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.10-rc1/amd64/linux-image-unsigned-5.10.0-051000rc1-generic_5.10.0-051000rc1.202010291359_amd64.deb
wget -c https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.10-rc1/amd64/linux-modules-5.10.0-051000rc1-generic_5.10.0-051000rc1.202010291359_amd64.deb                                                                                     
sudo dpkg -i *.deb    
                     
reboot

```

---

### Post by DuckHook on 2020-11-02
Congrats! Installing an RC kernel is not for the faint of heart, but if it works for you, that's what counts. If you consider this matter solved, please mark it so by using the thread tools option in your first post and others can then benefit from their searches.

---

### Post by slickymaster on 2020-11-02
*Thread moved to **Apple Hardware Users**.*

---

