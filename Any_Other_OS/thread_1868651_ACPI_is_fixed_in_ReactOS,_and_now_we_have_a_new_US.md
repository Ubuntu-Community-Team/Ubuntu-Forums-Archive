---
title: "ACPI is fixed in ReactOS, and now we have a new USB."
date: 2011-10-24
forum: Any Other OS
---

### Post by Lucradia on 2011-10-24
Well, this means it should start working more: [http://reactos.org/forum/viewtopic.php?f=2&t=9657](http://reactos.org/forum/viewtopic.php?f=2&t=9657)

---

### Post by forrestcupp on 2011-10-24
Wow. Looks like it's not perfect yet, but this is a huge step.

---

### Post by kaldor on 2011-10-24
This is actually pretty cool.

---

### Post by Dr. C on 2011-10-24
ReactOS is very cool concept. A GPLed Microsoft Windows clone.

---

### Post by Lucradia on 2011-10-25
> **Dr. C said:**
> clone.

ReactOS is written mostly in C / C# and C++ and Python. There is no core part written in newer versions Visual Basic or .NET.

That means it does not have the same vulnerabilities as windows. But with enough patience, you can install viruses, it's just they won't do anything unless it has access to the same files as it did in Windows, which it doesn't.

Most of ReactOS' core is build on files that end with .c or .h, etc. Not really DLLs or INIs.

---

### Post by PaulInBHC on 2011-10-25
Interesting idea.

I don't get them using FAT, and IDE drives. I have SATA HDD and DVD drive.

All I want is a free or low cost OS that uses RAM and HDD larger than the limits is every Windows OS, and the ability to play 3D DirectX games.

---

### Post by Lucradia on 2011-10-26
ReactOS also doesn't bundle in drivers. Just enough drivers to allow for core compatibility. You will not have printer drivers installed at all in ROS by default, nor gaming devices, etc.

Just basic VGA Drivers, CD Drivers, Keyboard drivers, etc.

Nothing fancy. This is why Windows is so heavy.

---

### Post by PaulInBHC on 2011-11-02
FYI anyone that wants to see this on Windows, I have XP and found a program called MobaLiveCD. I downloaded the live cd version of ROS, ran MobaLiveCD and set the right click association to the iso. You can then run the live cd on your windows screen in qemu without have to do anything else.

---

