---
title: "bad driver"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by aladdumonk on 2007-05-06
anyone know how I can uninstall an improperly installed driver. Trying to get wifi to work and I forgot to include the .sys file in with the .inf file and now I need to undo it. Any help would be great.

---

### Post by divague on 2007-05-06
try looking in /lib/firmware, there's where i found my wireless card drivers

---

### Post by aladdumonk on 2007-05-07
that's a no go, also I'm trying to use ndiswrapper to remove it and that won't work either. It says it can't find the directory even though it shows up when I request a list. Anyone out there with anything to help me would be fantastic.

---

### Post by jargoman on 2007-05-07
sudo rm -rf /etc/ndiswrapper/*

---

### Post by jargoman on 2007-05-07
/lib/firmware is where the linux native drivers are.

---

