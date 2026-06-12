---
title: "nvidia repo driver different to latest one?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by Dinerty on 2006-08-15
I installed my nvidia driver from [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper), however when I came to install xgl/compiz it says install the driver from the repo?

When I tried to edit my xorg config I notice some of the "Module" section is not in my version, due to me installing the driver manually?

Should I just overwrite the driver with the repo one?

Thanks

---

### Post by tzulberti on 2006-08-15
If you see at the version of the nvidia driver (apt-cache show nvidia-glx), you should notice that there is the same version of the drivers. I can not tell, so there must not be any difference.

---

