---
title: "help with boot up manager"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by chrisblack on 2005-10-27
I've installed BUM, in order to stop my computer diailing up the internet on start-up (before login screen).... but I don't know which setting to disable...  I don't want to experiment at this stage, as I familiarise myself with linux, so anyone able to help??

Thanks

Chris

---

### Post by Dr. Nick on 2005-10-27
most likely ntp, it syncs your clock to the a timeserver

EDIT
Never used bum but you can disable ntp by using System-Administration-Services

---

### Post by Perfect Storm on 2005-10-27
And if you're not on a laptop you can disable:

pcmcia
acpi-support
apmd

---

### Post by chrisblack on 2005-10-28
Thanks

Chris

---

