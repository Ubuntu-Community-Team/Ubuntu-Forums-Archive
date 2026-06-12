---
title: "[SOLVED] Getting Hellanzb to save files on correct drive?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by kryth on 2008-02-23
For the life of me, I can't get Hellanzb to process/save files on another Harddrive.

the part of my config looks like

Hellanzb.DEST_DIR = Hellanzb.PREFIX_DIR = 'media/disk/test/done/'

but it ends up storing files in

/home/user-name/media/disk/test/done

can't figure it out

Any tips?

---

### Post by kryth on 2008-02-23
If anyone cares, it was a matter of making it like this

= '/../../media/disk/whatever'

---

