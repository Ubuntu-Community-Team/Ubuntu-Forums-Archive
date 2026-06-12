---
title: "HFS+ in Lucid no werk!"
date: 2010-05-05
forum: Apple Hardware Users
---

### Post by platinumlolita on 2010-05-05
I'm trying to use an HFS+ formatted external hard drive, but in Lucid it doesn't even mount. I ran "df -h" and it's not on the list there...

I could have sworn it worked in Hardy, maybe even Jaunty. Never tried in Karmic. Maybe it's the HAL thing they changed?

What do?

---

### Post by srs5694 on 2010-05-05
You probably need to install the relevant HFS+ support package(s). I'm not sure precisely which ones are required, but try hfsplus and hfsprogs.

---

