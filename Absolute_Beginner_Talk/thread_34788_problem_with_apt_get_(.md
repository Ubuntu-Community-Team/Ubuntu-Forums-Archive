---
title: "problem with apt get :("
date: 2005-05-16
forum: Absolute Beginner Talk
---

### Post by hiptrop on 2005-05-16
getting this error everytime i try to download something ( with apt get ) 

root@xxxx:/home/xxxx # sudo apt-get install acroread
E: Konnte Lock /var/lib/dpkg/lock nicht bekommen - open (11 Die Ressource ist zur Zeit nicht verfügbar)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

:( can somebody please help me out here ? 

thanks alot !

---

### Post by kvidell on 2005-05-16
Do you have aptitude or Synaptic running in the backgorund?
- Kev

---

### Post by Stormy Eyes on 2005-05-16
Do you have Synaptic open, by any chance?

---

### Post by mtron on 2005-05-16
hi! 
first: you don't need to become root to install packages in ubuntu. the "sudo" before apt-get makes you superuser (sudo = Super User DO)

when you get the "permission denied" error it can mean that you are running the update manager or Synaptic Manager at the same time as using apt-get -> not working, if i am not wrong synaptic is only a graphical frontend for apt-get. 

try closing synaptic or update manager, then start a normal terminal 
Applications - System Tools - Terminal

and try again "sudo apt-get update" and "sudo apt-get install acroread"

---

### Post by N'Jal on 2005-05-17
Also as far as i am aware Acroread isn't in the repo's anyway, but yeah i having another copy of apt in any form (synaptic, aptitude Ubuntu update manager etc) causes the second copy to "lock out".

---

### Post by hiptrop on 2005-05-17
ok i guess i had synaptic running ! :P 

stupid me :) 

and i had to add the multiverse repo ! 

thanks again for helping me out ;)

now i got another problem :( 

when i try to start acroread .. nothing happens :( no error ...)

wheni try it in the terminal  i get this error : 

root@xxx:/home/xxx/Desktop/ti # acroread u6.pdf
/usr/bin/acroread: line 12: /usr/lib/Acrobat5/bin/acroread: file or directory not found  

??

---

### Post by hiptrop on 2005-05-17
figured it out :) thanks to this thread : 

[http://ubuntuforums.org/archive/index.php/t-1832.html](http://ubuntuforums.org/archive/index.php/t-1832.html)

;)

---

