---
title: "adding a sh file to the gnome desktop panel"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Mikeee on 2007-04-11
Hi all,

ive wrote a basic .sh file. I want to be able to add it to the gnome panel so when i click it it executes straight away without having to be ran from a terminal by going sh script.sh

i know this is probably very basic but without creating a sh file before i dont know how to do it.

Thanks

---

### Post by Jussi Kukkonen on 2007-04-11
1. make the file executable (chmod +x filename). Make sure the first line of the script is "#!/bin/sh".
2. Create a custom launcher:
right click on panel, "Add to panel", "Custom app launcher", fill in the details.

---

