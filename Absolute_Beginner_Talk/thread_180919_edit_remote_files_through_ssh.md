---
title: "edit remote files through ssh"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2006-05-23
when i double click a file in a remote folder i access through ssh, i cansee the content in gedit but i cant edit.

how can i go around or fix this problem?

---

### Post by harisund on 2006-05-23
I believe the latest version of gedit in Dapper can do that. Otherwise you will have to simply download the file, edit it and upload it back.

---

### Post by richbarna on 2006-05-24
Have you tried it as root?
You could use the terminal to navigate to the file and "sudo gedit name-of-file"
Or you could Alt+F2 to get the run dialogue "Gedit" click options "run-as-different-user" choose root, open Gedit and open the file.
Not sure if theses are possible but you normally have to be root to edit most docs.
Hope it helps
Good Luck

---

### Post by pedrotuga on 2006-05-24
mmm... i will check it out... now i am at home using windows...

thank you both...

downloading the file and upload it is the method i am using at the moment... its not practical at all.

---

### Post by dmizer on 2006-05-24
i can edit text documents in ssh via sudo nano, but nano doesn't work without su permissions.

but if you need to make changes to config files, nano should do the trick in ssh.

---

