---
title: "Nvidia or ati"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by alnhntr29 on 2007-09-02
I have a very old system. Dell pentium 2, onboard Nvidia rivia tnt, 512 mb ram.
Now, at the moment I have an ati raedon rv100 installed that works.
I dont think I am getting the performance out of it I should be getting.
The ati card was what i had in when i installed. I tried to install the nvidia just for comparison purposes, envy says it is supported but when I install x wont work.
Envy goes through a whole long process and then I get an error message when I try to start x, something about nvidia module not found. Can anybody tell me if it is worth my time to try to get the nvidia working or should i just stick with the ati since it works already? And what am I doing wrong?

---

### Post by w4ett on 2007-09-02
Try running envy from the terminal:

```
sudo envy -t
```

Select the option to remove the prior installation of the driver and then use the automatic driver installation option.

Sometimes the GUI frontend  is not as successful as the use of Envy in the terminal.

---

### Post by alnhntr29 on 2007-09-02
When I installed, it was from command line. I have to go into my bios and enable agp instead of pci to try the nvidia. When i install i get no x at all. Then i have to switch back to pci and rerun x config to go back to the ati.

---

