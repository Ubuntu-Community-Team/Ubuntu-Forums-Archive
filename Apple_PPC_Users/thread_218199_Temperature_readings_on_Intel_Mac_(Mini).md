---
title: "Temperature readings on Intel Mac (Mini)"
date: 2006-07-18
forum: Apple PPC Users
---

### Post by guardian_de on 2006-07-18
Hi,

I'm trying to read temperature information for the CPU cores of my Intel Mac Mini - Core Duo 1,66 GHz.

Lmsensors' sensor-detect find an i2c-i801, but sensors tells me "No sensors detected!".

Any hints on how read the CPU's temperature?

---

### Post by chasisaac on 2006-07-23
> **guardian_de said:**
> Hi,

I'm trying to read temperature information for the CPU cores of my Intel Mac Mini - Core Duo 1,66 GHz.

Lmsensors' sensor-detect find an i2c-i801, but sensors tells me "No sensors detected!".

Any hints on how read the CPU's temperature?


Did you find a solution for this?

---

### Post by ubuntu-geek on 2006-07-23
You might give this thread a read.. [http://ubuntuforums.org/showthread.php?t=191997&highlight=i2c-i801](http://ubuntuforums.org/showthread.php?t=191997&highlight=i2c-i801) the last point might help.

---

### Post by apollo1900 on 2006-07-24
I think the Power Mac G5 is the only Mac with temp sensors, and accessing them would be a heck of a job.

Basically all of these computer temp things are for PCs designed to run windows. Macs just aren't made like those.

---

### Post by Seq on 2006-07-24
> **apollo1900 said:**
> I think the Power Mac G5 is the only Mac with temp sensors, and accessing them would be a heck of a job.

Basically all of these computer temp things are for PCs designed to run windows. Macs just aren't made like those.

My MacBook has at least 3 thermal sensors. 2x CPU thermal sensors, and one HDD sensor (accessed via SMART). I would expect the Mini to be similar, and would not be surprised if additional sensors existed (Heat is not a windows-only problem, after all).

From memory, my iBook had five sensors.

I think within the context of your posting you are not denying the existance of the sensors, but rather the method of access. The thread linked to above seems to have some ideas on that.

---

### Post by guardian_de on 2006-07-25
The Mac Mini (Core Duo) has at least those three sensors: CPU core 1 and 2 and harddrive. There are tools for OS X which display their readings (Temperature Monitor or CoreDuoTemp as examples).

I was hoping that the Mac Mini's Hardware was so main-stream that lm-sensors could access the sensors. The harddisk's sensor can be read by smartmontool's smartctl or hddtemp.

What made me thinking is that the harddisk's temperature is 7°C hotter under Linux than under OS X. I suspect OS X handles the fan management differently than Linux. That's why I wanted to check if the CPU core's temperature is higher also.

---

