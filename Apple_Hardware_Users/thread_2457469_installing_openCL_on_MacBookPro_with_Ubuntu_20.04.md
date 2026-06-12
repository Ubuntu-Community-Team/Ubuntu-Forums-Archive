---
title: "installing openCL on MacBookPro with Ubuntu 20.04"
date: 2021-02-02
forum: Apple Hardware Users
---

### Post by frueter on 2021-02-02
Hi all,

I am new to Ubuntu and am having to get OpenCL to work in order to run [RecFusion]("https://www.recfusion.net/index.php/en/").
Since I need this on the run, I installed a brand new Ubuntu 20.04 on my MacBookPro as a dual boot option.
I then installed [FONT=Helvetica]intel-opencl-icd via[/FONT]:
```
[FONT=Helvetica]sudo apt install intel-opencl-icd[/FONT]
```
I also installed ocl-icd-libopencl1 via:
```
sudo apt install ocl-icd-libopencl1
```

However, the output of clinfo still shows no compatible platform and RecFusion still complains about missing OpenCL components.
Previously I had Windows 10 installed as a dual boot option which allowed me to run RecFusion, so I know the required hardware is there.

Since I am a 1-man-band and all self-taught out of necessity when it comes to IT any advise would be hugly appreciated.

Cheers,
frank

---

### Post by wildmanne39 on 2021-02-02
*Thread moved to **Apple Hardware Users for a more appropriate fit**.*

---

