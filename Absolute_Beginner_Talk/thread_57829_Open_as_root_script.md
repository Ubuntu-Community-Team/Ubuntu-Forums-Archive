---
title: "Open as root script"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by akechi on 2005-08-18
Hi all.  i created the "open as root script" and it will only show up if i open nautilus as root (which i created from another link here somewhere).  but if i right click in nautilus as a regular user i dont get that command in the menu, only if nautilus is in root mode.  anyway to fix this?  heres the script:

saved as (~/.gnome2/nautilus-scripts)

actual code:

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "gnome-open $uri" &
done

---

### Post by invalid on 2005-08-18
If you wrote the script and saved it as a root user, perhaps you need to change the file permissions to be visible/usable by non-root users, or change the owner/group of the file.

sudo chmod 777 scriptname.sh && sudo chown youruser scriptname.sh && sudo chgrp youruser scriptname.sh

Cheers,
Cb.

---

### Post by akechi on 2005-08-18
i tried your suggestion to no avail :(

---

