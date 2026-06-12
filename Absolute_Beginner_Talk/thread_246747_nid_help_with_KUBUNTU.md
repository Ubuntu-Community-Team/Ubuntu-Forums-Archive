---
title: "nid help with KUBUNTU"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by mark610 on 2006-08-29
hi! im using KUBUNTU to program in java.. and i have problems with the .bashrc ... i nided to edit it to export some variables but it seems that im not in root mode... i dont know how to make my log in as and administrator already... is there someway to do that? thanks in advance!

---

### Post by robins_web on 2006-08-29
To edit your .bashrc file, open a console window and type:

sudo vi .bashrc (I use vi--substitute whatever editor you wish to use)

when it prompts for the password, use your regular password you log in with.

sudo is a bit more secure than su'ing to root, but you can do that if you wish. Ubuntu/Kubuntu doesn't come with the root password set. To set a root password, in a console window type:

sudo passwd root

When prompted, enter a new password for root. Be sure to remember it!

---

