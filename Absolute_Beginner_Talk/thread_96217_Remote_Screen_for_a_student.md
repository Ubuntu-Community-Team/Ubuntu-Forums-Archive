---
title: "Remote Screen for a student"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by widjajayd on 2005-11-28
I am a  teacher and would like to migrate my school from windows to linux.

what I want is ALL my student(more than 10)  in class CAN SEE my screen when I demo something.

- Is it possible in Linux, in windows I am using Netsupport duo / NETOP.
- If possible what kind of software should I use (VNC / Real-VNC).

Thank you :confused: 

widjajayd

---

### Post by patrick295767 on 2005-11-28
Hi !
  
I guess that with vnc viewer it should be possible.
apt-get -f install vnc-viewer
  
let us know about ur progress !!

pat'

---

### Post by widjajayd on 2005-11-28
Thanks, do I have to Install VNC services/server in every student's workstation.?

---

### Post by patrick295767 on 2005-11-28
vnc server for the teacher
    
  
*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-
apt-get -f install vnc-client  
for the pc's of the students
  
*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-
that should work I guess ... 
  
concerning the server, i guess u'll havge to specify several sesssions
i never did it in linux... 
I am rather sure it'll work in linux 
It's so great linux

---

### Post by patrick295767 on 2005-11-28
I am wondering if there is not other program than vnc to do so ... 
If someone knows, please let us know !!

 kind regards, 

patrick

---

### Post by widjajayd on 2005-12-01
Thanks Patrick
I'll try it later 

I'll let you know if I find it's working

---

### Post by steve.horsley on 2005-12-01
For the students, the command is **vncviewer -shared hostname** where hsotname is the teacher's pc's name (or IP address). It might make sense to write a one-line script do to this.

For the teacher's PC, use the menu System -> Preferences -> Remote Desktop. You could set the student PCs to allow you to access theirs, too.

---

