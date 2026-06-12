---
title: "Need help deleted a folder i made in media."
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by lifewillfadeaway on 2005-07-30
I made a folder in /media called windows... (/media/windows)
however i would now like to delete it but i keep getting that i do not have the permissions to do so. Any help?  :)

---

### Post by lifewillfadeaway on 2005-07-30
well i figured it out with the terminal, but is there a way i could set my permissions to remove it without having to go into the terminal and type "sudo rm -R /media/windows" ?

---

### Post by bored2k on 2005-07-30
[QUOTE=lifewillfadeaway]I made a folder in /media called windows... (/media/windows)
however i would now like to delete it but i keep getting that i do not have the permissions to do so. Any help?  :)[/QUOTE]
 1. Execute the commands in Terminal mode (Applications -> System Tools -> Terminal)
2. sudo rm -rf /media/windows

Watchout with -rf. It's a powerful tool. 
3-. man rm

---

### Post by bored2k on 2005-07-30
[QUOTE=lifewillfadeaway]well i figured it out with the terminal, but is there a way i could set my permissions to remove it without having to go into the terminal and type "sudo rm -R /media/windows" ?[/QUOTE]
 1. sudo chmod 777 /media/windows will give full access to everyone. 
2.- man chmod

---

### Post by lifewillfadeaway on 2005-07-30
Awesome thank you very much, i suppose i could do this to any directory i frequently edit?

---

### Post by heimo on 2005-07-30
I'd probably do something like 
chgrp disk /media (now group called disk owns that directory)
chmod g+w /media (now group can write in that directory)
add yourself to disk group (System->Administration->Users and Groups)
login, logout (refreshes your rights)
groups (shows which groups you belong to)
mkdir /media/new_directory (create new directory)
rm /media/new_directory (remove it)

---

### Post by bored2k on 2005-07-30
[QUOTE=lifewillfadeaway]Awesome thank you very much, i suppose i could do this to any directory i frequently edit?[/QUOTE]
 * Not so funny laugh *

Hold your horses cowboy. If you want to keep things running without going to deep technically, stick to editing your /home directory. If you want to tamper with stuff outside $HOME, try to do this on /opt. A wrong "chmod" can render your box unconscious.

Edit: read Heimo's post, it's much more elaborate.

Off-topic: Don't remember seeing you around Heimos. And from your post count, I think I should have.. weird. Rock _on.

---

### Post by heimo on 2005-07-30
[QUOTE=lifewillfadeaway]Awesome thank you very much, i suppose i could do this to any directory i frequently edit?[/QUOTE]

not recommended - I'm sure bored2k won't recommend this either, the weight on his words was probably on the *man chmod, *learn how file permissions work and you will thank yourself one day

EDIT: :) bored2k was faster than me

---

### Post by lifewillfadeaway on 2005-07-30
Will do. *MUST NOT EDIT THINGS OUTSIDE OF HOME!!!!*  :-P

---

