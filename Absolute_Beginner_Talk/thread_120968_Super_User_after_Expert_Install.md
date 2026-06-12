---
title: "Super User after Expert Install"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by fcendejas on 2006-01-24
Hi all, first day with Ubuntu!  I read that when you do an expert install, as I did for a dual boot, the first user you make is not a super user.  I don't like that much... it means I can't use the file system as easily, I can't install updates, etc.  Can I restore full rights to my first user?  I am not setting up other users on my computer.

-fcendejas

---

### Post by manicka on 2006-01-24
You're first user should have Super User rights. Just use the sudo command instead of su and use your username and password to complete root commands.

---

### Post by fcendejas on 2006-01-24
well i know for sure my first user, my only user, doesn't have expert privileges.  i did check other posts first ([http://ubuntuforums.org/showthread.php?t=120276](http://ubuntuforums.org/showthread.php?t=120276)) since other people did have the same problem.  it seemed to confirm that the problem i was having was because i didn't have super user rights on my user.  discrepency?

[http://ubuntuforums.org/showthread.php?t=120276&highlight=expert+user](http://ubuntuforums.org/showthread.php?t=120276&highlight=expert+user)

---

### Post by carlosqueso on 2006-01-24
When you did an expert install, did you set up a user called root?  If you did, to use a terminal command, you need to type "su" (no quotes) and the user's password to be able to do stuff as root.  Be warned, however, that you can really screw up your computer if you get too crazy when doing stuff as root.

---

### Post by fcendejas on 2006-01-24
[QUOTE=carlosqueso]When you did an expert install, did you set up a user called root?  If you did, to use a terminal command, you need to type "su" (no quotes) and the user's password to be able to do stuff as root.  Be warned, however, that you can really screw up your computer if you get too crazy when doing stuff as root.[/QUOTE]
no, just a personal username.  i had to make a user named root?

---

### Post by Titus A Duxass on 2006-01-24
If you do an expert install you do not get the chance to add the root user.
If you do a server-expert install, you get the opportunity is add the root user first.

---

### Post by carlosqueso on 2006-01-24
hmmmm...what happens when you type ```
sudo apt-get update
``` in a terminal?

---

