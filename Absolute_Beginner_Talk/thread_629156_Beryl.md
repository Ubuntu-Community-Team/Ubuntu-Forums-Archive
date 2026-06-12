---
title: "Beryl"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by jordanae on 2007-12-02
I tried to install Beryl but it won't work. I've followed the directions but it won't work. I'm using Ubuntu 7.10 and the directions I was using are here: [https://help.ubuntu.com/community/CompositeManager/InstallingBeryl](https://help.ubuntu.com/community/CompositeManager/InstallingBeryl)

---

### Post by LaRoza on 2007-12-02
Ubuntu 7.10 comes with Compiz-Fusion, what Bery is now.

You can install:

```

sudo aptitude install compiz-fusion-plugins-extra
sudo aptitude install compiz-fusion-plugins-main

```

You can customize it now with these.

System->Preferences->Appearance
System->Preferences->Advanced Desktop Effects Settings

---

### Post by overdrank on 2007-12-02
> **jordanae said:**
> I tried to install Beryl but it won't work. I've followed the directions but it won't work. I'm using Ubuntu 7.10 and the directions I was using are here: [https://help.ubuntu.com/community/CompositeManager/InstallingBeryl](https://help.ubuntu.com/community/CompositeManager/InstallingBeryl)

Hi and you will need to remove the repositories from you sources list also. They will cause conflicts with compiz-fusion.

---

