---
title: "MacG3 + Firewire HD (LaCie 500GB) = FAILURE !!"
date: 2006-08-15
forum: Apple PPC Users
---

### Post by koroshiy1 on 2006-08-15
Hi there,

first of all, thank you for taking the time to read my post/topique.
[B]
**WHAT I HAVE DONE**[/B]

I have installed ubuntu dapper server version on a Mac G3 (clen install)(blue).
I installed samba and did the apt-get upgrade update.
I made a local network share for backup purpeous.
[I]
Everything works fine.[/I]

I plugged in my LaCie 500GB external firewire HD.
After waiting for like 5 secs the console tells me this.

```
ieee1394: sbp2: Error logging into SBP-2 device - login timed-out 
```

sudo fdisk -l Gives me info on the cd-rom and the linux partitions.

There are no extra drives listed in /dev/
only hda hdc hdc1 hdc2 hdc3 hdc4

The output that dmesg gives is.

```
[ 3355.536256] sbp2: probe of 0010b9210051572a-1 failed with error -16
[ 3631.577190] pcilynx0: bus reset interrupt
[ 3631.577234] pcilynx0: SelfID process finished (phyid 1, root)
[ 3631.577247] pcilynx0: SelfID packet 0x807f8462 rcvd
[ 3631.577259] pcilynx0: SelfID packet 0x817f8c74 rcvd
[ 3631.846452] ieee1394: Error parsing configrom for node 0-00:1023
[ 3631.847339] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0010b9210051572a]
[ 3644.853332] pcilynx0: bus reset interrupt
[ 3644.853376] pcilynx0: SelfID process finished (phyid 1, root)
[ 3644.853389] pcilynx0: SelfID packet 0x807f8462 rcvd
[ 3644.853401] pcilynx0: SelfID packet 0x817f8c74 rcvd
[ 3645.123345] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0010b9210051572a]
[ 3645.124237] scsi6 : SCSI emulation for IEEE-1394 SBP-2 Devices
[ 3666.929907] ieee1394: sbp2: Error logging into SBP-2 device - login timed-out
[ 3666.941109] sbp2: probe of 0010b9210051572a-1 failed with error -16
```

****THINGS I HAVE DONE TO FIX THIS****

I looked around in many topics reguarding this kind of problems.
Many of them where Ipod problems and speed problems.
 
Shutting down en starting up ieee1394/sbp2 ?service/demon?
(worked for a guy with a Ipod)

Rebooting with HD connected to the port.
I updated my system to latest 

But in the end nothing worked.

I know there is a bug posted concerning this problem but it is for a version below 6.06. So I guess it doesn't apply on my problem...

So if anyone has got some good ideas to let this thing work...
pls respond....

---

### Post by koroshiy1 on 2006-08-16
This blows...

I have given up, so long ubuntu. :cry:

---

### Post by 3rdalbum on 2006-08-16
I hate to say this, but the only operating system that has good support for Firewire is OS X. For obvious reasons, as most PCs don't come with Firewire. Quite frankly, support for Firewire peripherals is lacking because *there is no demand*.

---

### Post by Synchro on 2006-08-17
Well, there are quite a lot of threads on here about wanting to both boot from and use FireWire, and Ubuntu just doesn't work in this department. There are numerous hacks linked to, but they're nearly all obsolete and incomplete. Wanting to boot from Firewire is a pretty normal thing to want to do, particularly on Mac hardware - it's massively preferable to booting from USB as it offers both lower latency and higher transfer rates (in practice, not theory). What's more, I suspect that in the scheme of things FireWire device support is a far smaller, easier and more important thing to fix than many other projects - what use is Compiz/XGL if you can't boot? It's also an enabling technology - doing this one small thing opens up access to many more users, and its absence is a total showstopper, as koroshiy1 demonstrates so clearly.

---

### Post by 3rdalbum on 2006-08-17
> **Synchro said:**
> Well, there are quite a lot of threads on here about wanting to both boot from and use FireWire, and Ubuntu just doesn't work in this department. There are numerous hacks linked to, but they're nearly all obsolete and incomplete. Wanting to boot from Firewire is a pretty normal thing to want to do, particularly on Mac hardware - it's massively preferable to booting from USB as it offers both lower latency and higher transfer rates (in practice, not theory). What's more, I suspect that in the scheme of things FireWire device support is a far smaller, easier and more important thing to fix than many other projects - what use is Compiz/XGL if you can't boot? It's also an enabling technology - doing this one small thing opens up access to many more users, and its absence is a total showstopper, as koroshiy1 demonstrates so clearly.

That's right, booting from Firewire is a normal thing for a Mac user to want to do, and I agree it should be given priority over XGL and Compiz.

However, developers determine what gets worked on and what doesn't. Most developers use x86 machines and have probably never seen a Firewire port on the back of a computer unless they accidentally wandered into an Apple store. So Firewire will probably never get fixed, and neither will my iMac's sound in. Drag 'n' drop support will still trail behind the Mac too, as most Linux users are former Windows users (who rarely, if ever, d'n'd).

It's sad, but that's just what you've got to expect unless you're a coder :-)

---

