---
title: "MacBookAir 1,2 wakes too easily from suspend"
date: 2012-08-26
forum: Apple Hardware Users
---

### Post by uncommonname on 2012-08-26
Hi, I've got 12.04 with rEFIt installed on my MacBookAir 1,2, and I'm having a problem with suspend.

If I suspend the machine and leave it alone (say on a desk), it's totally fine.

If I jostle the machine too much (for example, placing it in my bag and riding my bike to work), it wakes up (and overheats in my bag).

I don't think it's related to the wake on USB bug I've seen mentioned elsewhere, as it seems to be movement-related, and I've tested it bu plugging and unplugging USB devices without the machine waking up.

But if I pick up the machine and give it a physical bump, it wakes up.

Any ideas on how to solve this?  It's a pretty painful bug to deal with.

---

### Post by philcolbourn on 2012-09-01
I don't know, but does it behave same using OS-X - is it just as easy to wake-up?

My MBP uses magnets to indicate that lid is closed - I guess MBA is same. Perhaps yours are not positioned correctly or have moved.

---

### Post by kosumi68 on 2012-09-01
> **uncommonname said:**
> Hi, I've got 12.04 with rEFIt installed on my MacBookAir 1,2, and I'm having a problem with suspend.

If I suspend the machine and leave it alone (say on a desk), it's totally fine.

If I jostle the machine too much (for example, placing it in my bag and riding my bike to work), it wakes up (and overheats in my bag).

I don't think it's related to the wake on USB bug I've seen mentioned elsewhere, as it seems to be movement-related, and I've tested it bu plugging and unplugging USB devices without the machine waking up.

But if I pick up the machine and give it a physical bump, it wakes up.

Any ideas on how to solve this?  It's a pretty painful bug to deal with.

It is probably the built-in accelerometer in combination with a wakeup event in the kernel. Having such a device is a good thing in machines with spinning hard disks, since it is possible to lock the drive before the machine hits something, for instance.

To fix it, you need to find out which subsystem is receiving the event (applesmc, usb, acpi, whatnot) and either ignore the event or change some setting so that the wakeup event is not sent.

---

### Post by uncommonname on 2012-09-01
@[philcolbourn]("http://ubuntuforums.org/member.php?u=12167") no, it works totally fine under OSX. Under OSX I can take my laptop for a bike ride and be sure that it will be asleep when I get to my destination.  It's software, not hardware.

> **kosumi68 said:**
> It is probably the built-in accelerometer in combination with a wakeup event in the kernel. Having such a device is a good thing in machines with spinning hard disks, since it is possible to lock the drive before the machine hits something, for instance.

To fix it, you need to find out which subsystem is receiving the event (applesmc, usb, acpi, whatnot) and either ignore the event or change some setting so that the wakeup event is not sent.

@[kosumi68]("http://ubuntuforums.org/member.php?u=592679") that sounds promising but can you help point me in the right direction a little more? N00b over here.

---

### Post by philcolbourn on 2012-09-01
Is there a pattern? If it is your accelerometer in combination with some wake event, then this should be easy to test by simulating a bike-ride.

My old MBP (and I assume newer models) keep USB ports powered. Do you have any USB devices plugged in?

Regarding a wake event, does anyone know of such a thing that would be on by default or easy to enable?

---

### Post by uncommonname on 2012-09-02
> **philcolbourn said:**
> Is there a pattern? If it is your accelerometer in combination with some wake event, then this should be easy to test by simulating a bike-ride.

My old MBP (and I assume newer models) keep USB ports powered. Do you have any USB devices plugged in?

Regarding a wake event, does anyone know of such a thing that would be on by default or easy to enable?

Yes, my MBA does provide power to USB ports when suspended.

I've tested plugging and unplugging USB devices, that doesn't cause the unwanted wakeup events, and I don't ever keep USB devices plugged in during transport (this is the old design MBA with the drop down USB hatch).

The pattern I'm seeing is consistent with either accelerometer causing wakeup or possibly overly sensitive lid opening event.

The easiest test is to close the lid (or manually tell the machine to suspend) and then physically agitate the machine a bit - it wakes up every time.

---

### Post by philcolbourn on 2012-09-02
You seem to be describing a sensitive lid switch.

I very much doubt an accelerometer is involved - since sleeping hard drives (if you have one) have parked heads and are in no danger of hitting disks.

So, either OS-X has some hysteresis, or it wakes and goes back to sleep without you knowing.

When running OS-X, can you similarly make it wake up?

A possible test: see if you can locate actual lid switch using ifixit pictures or Google search. Get a small piece of an old hard-drive magnet and tape it down over the spot. Your MBA should go to sleep. Close lid and see if you can wake it up, or go for a bike ride.

On my MBP4,1 it is near RHS USB port. On a PowerBook G4 it is below trackpad.

---

