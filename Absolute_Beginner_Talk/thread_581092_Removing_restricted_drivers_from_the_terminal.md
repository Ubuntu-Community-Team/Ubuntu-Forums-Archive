---
title: "Removing restricted drivers from the terminal"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Fjellpower on 2007-10-19
Hi there =) 
Ive been using ubuntu for about a week and dont know any commands for the terminal.
Last night i tried to instal a restricted driver for my graphiccard, a ATI Raedon X600 256ram card.
The problem is started when i did the restart witch was required, when i got to the login screen my screen 
was all messed up. 
I cant see anything, there is a picture but its all like stretched.

The only thing i can access is the terminal so i wondered if there is any command that allows me to do a rollback to disable the restricted driver.

=) 

/Alex

---

### Post by Qwerty_ on 2007-10-19
You might beable to configure your card manually in the terminal via xorg

```
sudo dpkg-reconfigure xserver-xorg
```

I am not to sure but its worth a shot.

---

### Post by Fjellpower on 2007-10-19
Thanks for the quick reply, gonna check it out right away =)

---

### Post by Fjellpower on 2007-10-19
Thanks alot Qwerty_ =D 
It worked perfect =D

---

### Post by Qwerty_ on 2007-10-19
Not a problem Fjellpower :) I am glad to help others as I have received a fair bit of help from this forum.

---

