---
title: "problems using sudo"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by samuelkarush on 2006-06-07
I mistakenly changed permissions of the file /var/run/sudo to 0777. Now when I use the sudo command to change permissions back, or for any other purpose, I get this error:

sudo: /var/run/sudo writable by non-owner (040777), should be mode 0700

So, how do I reverse my mistake?
sam

---

### Post by xXx 0wn3d xXx on 2006-06-07
[QUOTE=samuelkarush]I mistakenly changed permissions of the file /var/run/sudo to 0777. Now when I use the sudo command to change permissions back, or for any other purpose, I get this error:

sudo: /var/run/sudo writable by non-owner (040777), should be mode 0700

So, how do I reverse my mistake?
sam[/QUOTE]
> sudo chmod 0700 /var/run/sudo
Please check that that is the correct path of the file.

---

### Post by samuelkarush on 2006-06-07
yes, as far as a i can tell, that is the correct file path

---

### Post by xXx 0wn3d xXx on 2006-06-07
[QUOTE=samuelkarush]yes, as far as a i can tell, that is the correct file path[/QUOTE]
Ok then it should work. :)

---

### Post by samuelkarush on 2006-06-07
well, yes it should. That is the problem, i get the error i posted earlier, and permissions arent changed. Sudo isn't working at all, from what I can tell

---

### Post by xXx 0wn3d xXx on 2006-06-07
Try 
sudo chmod 777 /var/run/sudo

---

### Post by samuelkarush on 2006-06-07
the same error message appears after any and all sudo commands:

sudo: /var/run/sudo writable by non-owner (040777), should be mode 0700

---

### Post by glotz on 2006-06-07
Boot in **recovery mode**, then you can **sudo chmod 0700 /var/run/sudo**

---

### Post by steve.horsley on 2006-06-07
You need to boot into recovery mode, which gives you a root privilege prompt. Then you can change the file permissions.

---

### Post by samuelkarush on 2006-06-07
how do i boot in recovery mode?

thanks for quick replies and patience all!!
sam

---

### Post by glotz on 2006-06-07
Reboot. By default your GRUB menu will include a recov mode entry (or entries, any will do)

---

### Post by samuelkarush on 2006-06-07
well,
in recovery mode, I am told the file does not exist. I'm quite sure it does, as i used the same path i specified to change the permissions in the beginning.
 now ubuntu wont boot properly. I began having these problems when i installed dapper. I'm going back to the last version for a test.

---

### Post by glotz on 2006-06-07
I thought your problems began when you chmodded that file...

---

### Post by samuelkarush on 2006-06-07
yes, they did.
 I just hadn't ever gotten myself into this position with the last version, and I had altered permissions there. Never that particular folder, though. I guess I learned to stay away from that one.!

---

### Post by glotz on 2006-06-07
I too learned, to not sudo nano some of the files in /proc...

As of today, I have no clue... :)

---

### Post by samuelkarush on 2006-06-07
UNfortunately, I need to be able to write to /var/www to add files to apache2. Or I need to edit an apache conf. file to point apache to a folder i have permission to write to.

---

