---
title: "56k serial modem help needed"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by LEDZO on 2007-05-20
I have a creative blaster serial 56k modem plugged and I know its all hooked up right but ubuntu won't autodetect it and I don't know really know how to find it or if linux is even seeing it. can anyone tell me what I should do.

---

### Post by Bachstelze on 2007-05-20
```
sudo wvdialconf /etc/wvdial.conf
```

is your modem detected ?

---

### Post by LEDZO on 2007-05-21
no it's not detected, it says I should make sure it's configured with setserial and I don't know how to do that. there is a faq for setserial, Ill look there

---

