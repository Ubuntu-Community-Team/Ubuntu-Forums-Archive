---
title: "Trouble deleting folder"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by bruceathome on 2006-12-28
Hi all.  My first cry for help.  I was setting up backup options using "Simple Backup Config", and through that configuration software created a new folder in my home directory to save the backups to.  Unfortunately I stuffed up somehow, and the folder just has the name 'Type name of new folder'.  I want to rename or delete this folder.

It is locked so I can't just right click on it and rename it, I can't change the permissions using chmod as it says the folder does not exist.  I can't delete it using rm -rf as it also says it doesn't exist.  However it is present even when I do an ls from the terminal.

Any ideas on how I can delete this folder???


Much thanks for any help,


Bruce

---

### Post by pseudonym on 2006-12-28
Try doing 'sudo rm -rf <name_of_folder>' . Sometimes things can only be removed when you do so as root user.

Also, if there are spaces in the name, you'll need to put the folder name in " " .

---

### Post by bruceathome on 2006-12-28
Awesome pseudonym!  That worked.

Thanks for the quick reply!



Bruce

---

### Post by pseudonym on 2006-12-28
You're welcome. :)

Just a quick follow up - use sudo only as a last resort. You should have been able to delete that folder as normal user, provided you put the name in " ".

---

### Post by shrimphead on 2006-12-28
you can also use backslashes instead of putting the name in ""

eg.

Type\ name\ of\ folder

that makes autocompletion work, so if you type Type\ and then hit tab it will fill in the rest for you.

just a useful tip :)

---

### Post by AgeingAdolescent on 2006-12-29
Yay!  Just had the same problem!  You solved it!  Than-Q!  :D

---

