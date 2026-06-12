---
title: "How can I check if the Proprietary nvidea drivers are being used?"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by n00bWillingToLearn on 2006-05-19
I just installed the proprietary Nvidea driver, restarted and tried some screensavers and I don't notice any difference. How can I check that they are being used instead of the open source ones?

---

### Post by Jason_25 on 2006-05-19
```

cat /var/log/Xorg.0.log | grep driver

```
```

glxinfo

```

---

