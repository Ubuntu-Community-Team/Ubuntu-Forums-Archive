---
title: "Deleted file doesn't free up space"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by feap on 2007-01-03
I deleted a 4.4GB DVD iso and emptied my wastebasket, but didn't get any free space on my HDD. I checked /home/user/.trash directory as sudo nautilus and it's indeed empty. I also searched for the filename under file system to no avail. Any other place it might hide or another explanation?

---

### Post by nunomiguelmota on 2007-01-03
try to search for hidden file or folders in the directory you erase the file.

next time use shift+del

---

### Post by feap on 2007-01-03
Found the problem: the iso was still mounted when I deleted it. I rebooted and the space was freed up.

---

