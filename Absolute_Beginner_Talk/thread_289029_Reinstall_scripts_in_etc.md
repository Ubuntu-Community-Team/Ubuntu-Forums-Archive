---
title: "Reinstall scripts in /etc"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by RafRaf on 2006-10-30
Hi,

I did some changes to my acpi scripts in Dapper to make suspend work. Now I have upgraded to Edgy and these changes do no longer work (e.g. changes in /etc/acpi/lid.sh

..and I did not backup.

Is there a way to get the default scripts for Edgy back (e.g. by reinstalling acpi?) ?


thx

---

### Post by castrojo on 2006-10-30
try:

sudo apt-get install --reinstall acpi-support

---

### Post by RafRaf on 2006-10-30
thx, seams to work fine! :)

---

