---
title: "Internet on Macbookpro5,3 in Lucid"
date: 2011-09-10
forum: Apple Hardware Users
---

### Post by gotenks05 on 2011-09-10
It's been a while. Well, I decided to try Lucid again and 10.04.3 is more stable than when it was originally released. However, I have a problem. Mainly, I am making a customized version of Ubuntu, in order to run om my MacbookPro5,3, in case I need to some checks. After all, Linux has helped me find problems on other systems or recover data. Right now, I am trying to get Internet access from the remaster that I produced, but for some reason Ubuntu does not allow me to use my Macbook's wireless card. I am producing the remaster via VMware Fusion, since I don't want to wipe my mac's hard drive, at least yet, since there are not any stability issues on its currently installed OS. Before, on previous editions of Ubuntu, I only needed to install the driver, which I have done via ndiswrapper today. The drivers are bcmwl6, which is definitely what is in my computer, since that is what the restore media contained, when I loaded the disc into the Ubuntu VM. Also all other live disc images I created worked fine after being set up from VMware, no matter whether it was Ubuntu, or its direct base, Debian, since the last time I did this was with the bcmwl5 drivers, which I do not own the machine anymore.

---

### Post by gotenks05 on 2011-09-12
never mind I found the solution in the documentation, which was to install the native drivers. They seem pretty stable this time. I was using the ndiswrapper drivers, because those were more stable in the past than the driver available in the repository.

---

