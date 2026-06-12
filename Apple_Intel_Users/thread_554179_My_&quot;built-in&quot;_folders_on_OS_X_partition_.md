---
title: "My &quot;built-in&quot; folders on OS X partition have little X's on them in Ubuntu"
date: 2007-09-18
forum: Apple Intel Users
---

### Post by dmber on 2007-09-18
Dual-booting OS X and Feisty on a Macbook.

When I mount my OS X partition on Feisty, I can get access to any folder I have personally created, but my "Music" "Documents" "Movies" "Pictures" folders that OS X makes for me have little X's and won't mount.  

Is there something I can change, so that I can use my "Music" folder for both OS's?

Thanks.

---

### Post by cyberdork33 on 2007-09-18
> **dmber said:**
> Dual-booting OS X and Feisty on a Macbook.

When I mount my OS X partition on Feisty, I can get access to any folder I have personally created, but my "Music" "Documents" "Movies" "Pictures" folders that OS X makes for me have little X's and won't mount.  

Is there something I can change, so that I can use my "Music" folder for both OS's?

Thanks.
Your OSX user and linux user are different as far as the system is concerned, and by default the permissions on the files are set to not allow others users access.

You will need to boot OSX, and alter the permissions on all the folder you would like to allow other users access to.

---

### Post by dmber on 2007-09-18
in OS X, i have all the permissions set to Read and Write for each of the folders.  When I mounted them succesfully in Feisty, I could still only read the files in those folders.

do i need to change anything in "owner" (right now it's set to my OS X username)?

thanks.

---

### Post by cyberdork33 on 2007-09-18
> **dmber said:**
> in OS X, i have all the permissions set to Read and Write for each of the folders.  When I mounted them succesfully in Feisty, I could still only read the files in those folders.

do i need to change anything in "owner" (right now it's set to my OS X username)?

thanks.
write access is only available if journalling is turned off...
[http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)

---

### Post by dmber on 2007-09-18
thanks for the help!

---

