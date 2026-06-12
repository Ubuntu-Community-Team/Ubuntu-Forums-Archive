---
title: "Virtualbox: no more virtual machine"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by tico on 2007-07-30
For space’s sake I moved my virtual machine to another drive and changed the defaults dirs to point to the new dirs in the new drive. Now, when I open Virtualbox, there’s no virtual machine. Is there a way to fix this without moving the my virtual machine to the original dir?

Thanks.

---

### Post by vexorian on 2007-07-30
Yes.

The vdi files are actually just the hard drives. So you can always just create a new virtual machine (with the same settings) and when you are prompted for the hard drive just pick the vdi file (there's an open dialog for those)

The downside would probably be you'll have to set up some few things again like making it share clipboard with the host, and perhaps the shared folder?

---

