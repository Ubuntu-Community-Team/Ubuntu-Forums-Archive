---
title: "Connecting to the Internet"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2006-12-09
I went to network settings and enabled the wireless connection for me to connect to my wifi but I still wasn't able to connect to the internet. What should I do?

---

### Post by faraazs on 2006-12-09
has your wireless card been properly installed with all its drivers and configurations?

---

### Post by ardvark71 on 2006-12-09
Hi...

What can you tell us about your setup? Wireless card?

Linux support for wireless is still pretty spotty so I would imagine drivers MAY be the problem here for you as well...

One suggestion would be to go into Synaptic and install the ndiswrapper-utils package. This may help with your problem.

Best Regards...

:KS

---

### Post by wersdaluv on 2006-12-09
I do not have any idea about what "synapstic" is. Where can I find that?

---

### Post by ardvark71 on 2006-12-09
> **wersdaluv said:**
> I do not have any idea about what "synapstic" is. Where can I find that?

Click on "System"--->"Administration"--->"Synaptic Package Manager"

:KS

---

### Post by wersdaluv on 2006-12-09
How do I install the ndiswrapper-utils package?

---

### Post by ardvark71 on 2006-12-09
> **wersdaluv said:**
> How do I install the ndiswrapper-utils package?

Once you bring up the main program, click on "all" to the left, then on the list of packages to the right, scroll down until you see "ndiswrapper-utils." It should have the Ubuntu logo to the left of the name. Highlight the entry and then right click on it and then left click "Mark for installation." Then go to the top of the window and click "Apply."

:KS

---

### Post by wersdaluv on 2006-12-09
I have been searching all packages again and again but I never saw "ndiswrapper-utils" :confused:

---

### Post by ardvark71 on 2006-12-09
> **wersdaluv said:**
> I have been searching all packages again and again but I never saw "ndiswrapper-utils" :confused:

Ok. You will need to add some repositories. Just go back into Synaptic, click on "Settings" and then "Repositories." When that Window comes up, click on "Add" and then be sure all four boxes are checked, including "Community Maintained" and "Non-free." Then click OK. Synaptic will download some packages and when the main package window comes back up, ndiswrapper should be there.

:KS

---

### Post by wersdaluv on 2006-12-09
I was able to install the ndiswrapper-utils but ubuntu still cannot install my wireless lan driver. What should I do?

---

### Post by wersdaluv on 2006-12-09
I am using a RaLink RT2500 802.11g Cardbus/mini-PCI and I think Ubuntu supports it and I don't need to install the driver. 

I am not sure but maybe, I am just having an IP issue or something like that. 

What can I do?

:KS

---

### Post by unisol on 2006-12-09
try looking here;Hardware Compatibility section under networkong and wireless forum  on this forum

---

