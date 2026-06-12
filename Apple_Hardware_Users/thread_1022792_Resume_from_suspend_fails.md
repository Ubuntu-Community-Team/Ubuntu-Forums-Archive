---
title: "Resume from suspend fails"
date: 2008-12-27
forum: Apple Hardware Users
---

### Post by hanzomon4 on 2008-12-27
When ever I attempt to resume from suspend I hear the machine coming back to life but the screen remains dark and the keyboard is totally unresponsive(caps key won't even light up). I've actually had this problem across distros(fedora). I'm running Intrepid on a 3,1 MacbookPro... even though the wiki says that it should just work it doesn't. I've tried adding ath9k to acpi-support and fiddling with some of the options in there.... and nothing.

---

### Post by cyberdork33 on 2008-12-28
> **hanzomon4 said:**
> When ever I attempt to resume from suspend I hear the machine coming back to life but the screen remains dark and the keyboard is totally unresponsive(caps key won't even light up). I've actually had this problem across distros(fedora). I'm running Intrepid on a 3,1 MacbookPro... even though the wiki says that it should just work it doesn't. I've tried adding ath9k to acpi-support and fiddling with some of the options in there.... and nothing.

if you read the info in the acpi-support file, you'll see that it is depreciated. It does not do anything unless you change the power manager that you are using back to the old style.

---

### Post by hanzomon4 on 2008-12-29
So what file should I be editing?

---

