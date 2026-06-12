---
title: "&quot;Unknown&quot; Format"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by Wigginz on 2006-06-14
I am trying to install Ubuntu. 
I want to have it set up with Windows XP and Ubuntu on my computer, so i partitioned my drive so that i had a 10GB partition for installing Ubuntu on and a 256 mb partition for "swap".
When i try to format the partitions inside of the Ubuntu installer, It formats them to "Unknown" regardless of what format i tell it to use (NTFS).
I tried formatting them inside windows to NTFS and running it that way. The Ubuntu installer recognizes the formatting when Windows does it, but when it trys to install, it finds "errors" on the disk and quits the installer.
I got on the #Ubuntu channel on freenode, but I couldn't even get anyone there to respond to "Can you see this?" let alone my question, so I came here :D.

Does anyone know what I can do to resolve this issue? Or even where I can look to potentially find a solution? Thank you :)

---

### Post by atomicSpatule on 2006-06-14
You can't use a NTFS partition to install linux on it, it is totally illogical, try a ext3 or reiserFS instead

---

### Post by Wigginz on 2006-06-14
I'm a total Linux newbie, so i was not aware of that. Thank you :)

---

