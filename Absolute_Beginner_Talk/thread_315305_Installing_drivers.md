---
title: "Installing drivers"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2006-12-09
I reformatted my laptop with Ubuntu 6.10. I wasn't able to connect to the internet so I tried installing the recovery cd of my laptop. Unfortunately, when I tried to run the installer of my wireless lan, an error window popped up stating that "(there is) no application suitable for automatic installation is available for handling this kind of file." My laptop was bundled with linpus linux that is why I expected that the drivers are also compatible with linux. What should I do?

---

### Post by riven0 on 2006-12-09
> **wersdaluv said:**
> I reformatted my laptop with Ubuntu 6.10. I wasn't able to connect to the internet so I tried installing the recovery cd of my laptop. Unfortunately, when I tried to run the installer of my wireless lan, an error window popped up stating that "(there is) no application suitable for automatic installation is available for handling this kind of file." My laptop was bundled with linpus linux that is why I expected that the drivers are also compatible with linux. What should I do?

If you have a broadcom card, I would suggest first trying ndiswrapper. Go to the synaptic package manager, search for *ndiswrapper* and install the files from there. It may just work.

---

