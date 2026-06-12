---
title: "apt-get upgrade: Packages kept back"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by ullal on 2006-04-05
I am switching from SuSE Linux to ubuntu. I have just installed ubuntu without any problem, logged in and tried to update+upgrade:

sudo apt-get update
sudo apt-get upgrade

Everything seems to have worked correctly but for the following message:

The following packages have been kept back:
linux-image-386  linux-restricted-modules-386

What does this message mean?

Do I have to do anything special to upgrade these packages?

---

### Post by sYs^ on 2006-04-05
yes, use sudo apt-get dist-upgrade

---

### Post by ullal on 2006-04-05
Thanks - it worked!

---

