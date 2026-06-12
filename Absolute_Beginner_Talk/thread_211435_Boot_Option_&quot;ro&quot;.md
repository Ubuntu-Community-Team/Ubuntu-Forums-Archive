---
title: "Boot Option &quot;ro&quot;"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by diepruis on 2006-07-08
Could someone tell me what this boot-option does? Is it at all important?

---

### Post by Dr. Nick on 2006-07-08
Where are you seeing this at? I think "ro" usually means "read only"

---

### Post by diepruis on 2006-07-08
It seems this option mounts your root filesystem read-only, so it can be safely checked. Can I remove this option, or isn't that recommended? I'm only asking because my kernel (686) doesn't seem to recognise it.

---

### Post by ifokkema on 2006-07-08
> **diepruis said:**
> It seems this option mounts your root filesystem read-only, so it can be safely checked. Can I remove this option, or isn't that recommended? I'm only asking because my kernel (686) doesn't seem to recognise it.
What kind of kernel are you running? All standard Ubuntu kernels support the 'ro' option, as far as I know.

---

### Post by diepruis on 2006-07-08
I'm running the 686 kernel. It boots fine without the "ro" option, or with the "single" option.

---

### Post by ifokkema on 2006-07-08
If you have a standard Ubuntu kernel, how do you know it doesn't support 'ro'? Do you get an error message of some kind?

---

### Post by diepruis on 2006-07-08
I had an error message to that effect. It doesn't matter anymore though, as the real problem was actually a misbehaving driver. Thanks anyway.

---

