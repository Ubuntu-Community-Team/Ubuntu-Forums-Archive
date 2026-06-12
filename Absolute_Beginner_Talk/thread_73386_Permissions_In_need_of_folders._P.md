---
title: "Permissions? In need of folders. :P"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by Moonstruck on 2005-10-08
Back again with another nub question... Figured out the internet thing, rather, it figured out me... I assume that it was just my connection acting up. :)

Anyway, perhaps this is just a Breezy issue, but after installing, I don't have permission to modify anything outside of my home folder. When I installed Hoary I had the basic access to these functions (and more) that the root user has from the get-go. Any idea how to modify my privs so i can actually do something as simple as create a folder? Having no skins for XMMS is beginning to grate on my nerves.

Thanks in advance.

---

### Post by SilentCacophony on 2005-10-09
Hello. 

> Anyway, perhaps this is just a Breezy issue, but after installing, I don't have permission to modify anything outside of my home folder.

That is as it should be in a linux system. The only folder you should have write permissions in is your home folder, or perhaps a storage partition mounted with RW access. If you absolutely need to make folders elsewhere, you would generally use **sudo mkdir <path>**. See this page for more info on **sudo**: [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

> When I installed Hoary I had the basic access to these functions (and more) that the root user has from the get-go.

That is unusual, and generally considered dangerous. ;)

> Any idea how to modify my privs so i can actually do something as simple as create a folder?

Yes, but seriously not advisable. No need to, really. **Sudo** and **gksudo** should suffice for that.

> Having no skins for XMMS is beginning to grate on my nerves.

You should be able to install XMMS skins into *~/.xmms/Skins* (~/ = your home dir.) Similarly, other themes generally go into ~/.themes, etc...

---

