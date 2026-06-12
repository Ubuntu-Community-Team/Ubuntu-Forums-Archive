---
title: "only DVI , No VGA"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by djcoom on 2007-12-30
Dear friends, Hope for help.

I've installed Ubuntu 7.1 and when it goes to grafical mode( no matter live cd ,alternative or even on safe grafical mode) the VGA screen goes black (I have an onboard intel 915 Chipset with one DVI output and I'm using an adaptor to VGA) It works fine on DVI monitor.

---

### Post by ^rooker on 2007-12-30
Hm...
If I understood you correctly, you're connecting a VGA monitor to your DVI output (using an adaptor?) - so obviously your XServer disables the analog output of the DVI. :(

Could you please post your /etc/X11/xorg.conf?

---

