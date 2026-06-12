---
title: "Deleting symlink in OSX deletes target folder contents?"
date: 2012-09-04
forum: Apple Hardware Users
---

### Post by max6166 on 2012-09-04
I have a Samba share on my Ubuntu machine. The share contains some symbolic links to folders. The links were created within Ubuntu.

If I mount that Samba share on my Macbook and delete a symbolic link, the contents of the target folder of the symbolic link are also deleted. The target folder itself remains untouched.

If I delete the symbolic link from within Ubuntu, only the link is deleted. The target folder remains intact, as does its contents.

I am running Snow Leopard on my Macbook, and Ubuntu 12.04 on my desktop machine.

I have tested this numerous times. Could someone please explain why this is happening? Is there perhaps a safer way to handle links than this? :confused:

---

