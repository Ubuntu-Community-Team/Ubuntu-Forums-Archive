---
title: "update-alternatives on multiple fies at once"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-04-27
Is it possible to use the update-alternatives one multiple files at once? For my directory
/usr/lib/jdk1.6.0_01/bin , I want to use the update-alternatives on all the executables in there like this:

update-alternatives --install /usr/bin/<file_name> <file_name> /usr/lib/jdk1.6.0_01/bin 300
update-alternatives --auto <file_name>

is it possible to do this?

---

