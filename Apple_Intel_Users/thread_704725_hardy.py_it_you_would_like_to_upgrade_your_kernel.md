---
title: "hardy.py it you would like to upgrade your kernel"
date: 2008-02-22
forum: Apple Intel Users
---

### Post by lex1 on 2008-02-22
Here is a hardy.py for the lastest kernel
I did not write it all glory goes to the guy named in the script
just make it exe chmod +x and  then
python hardy.py

lex1

---

### Post by NightwishFan on 2008-02-22
I just installed the kernel using the original thread today. It worked well but I still cannot recover when I suspend. :(

---

### Post by cyberdork33 on 2008-02-22
> **NightwishFan said:**
> I just installed the kernel using the original thread today. It worked well but I still cannot recover when I suspend. :(what do you mean by recover? As in, it doesn't wake up?

did you try to make these edits in /etc/default/acpi-support: ```
SAVE_VBE_STATE=false 
POST_VIDEO=false
```

---

### Post by NightwishFan on 2008-02-22
Thank you for helping. I will be sure to inform you if I bring about a resolution.

EDIT: No, When I intend to truly crack this problem I will look up more information. I assumed the suspend would work with the new kernel, as it does with my test machine on hardy (but did not on gutsy).

---

### Post by lex1 on 2008-02-23
Please forgive my ignorance but what advantanges are there of useing this kernel in gutsy/

lex1

---

