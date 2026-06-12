---
title: "my administrator user doesn't work anymore"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by frischi on 2007-03-19
some how i managed to get my only account who is able to administrate users broken. the only account left is a try out account with only few permissions. 
i think i could fix it if only i had another account with administrative abilities. i'm sure that it's possible to create an account like that with the terminal and the root password. but unfortunately i didn't find the terminal command. :(

---

### Post by Respenus on 2007-03-19
Terminal is in the accesories folder.

Open it, type "sudo passwd root", write in your password, then the new root one, repeat the root again and there you go!

---

### Post by scxtt on 2007-03-19
Alt+F2
xterm

you can also boot into "recovery mode" to bypass setting up a root account, as described by the post above ...

---

### Post by frischi on 2007-03-19
i meant how u could make new accounts and edit them with terminal
i mean while found out 
it s 


usermod

and

useradd

 but thanks anyway

---

### Post by Zuuswa on 2007-03-19
Try booting into recovory mode (Grub should give you the option)
That will give you a CLI with root privilages.  The code to add a user to the admin group would be:
```
addgroup *username* admin
```
where *username* is the acount you want to give admin rights.  If that doesnt work, then you will have to add the admin group to the list of sudoers.  I believe (I am at school on a windoeze computer atm) the file is /etc/sudoers, so the code would be
```
nano /etc/sudoers
```
and make sure that this line is in there at the bottom:
```
%admin ALL=(ALL) ALL
```
then hit control+x to exit, y to save, reboot and voila!  your acount (and all users in the group 'admin') have the ability to sudo (administrative privilages)

---

### Post by scxtt on 2007-03-19
for the record (since it looks like the OP resolved the issue) you shouldn't do "nano /etc/sudoers" - you should use **visudo** - it will perform syntax checks on save ...

---

