---
title: "Password freezes"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by frappe987 on 2007-07-19
Hello very new to Ubuntu.  I have Ubuntu 5.10 running through VMPlayer.  When it asks for my password while in Terminal window it freezes.  I cannot go back or anything if I press enter it says that my password is wrong but it wont allow me to type anything in.  Thanks for any help.  How do I register to be the "sudo" administrator.  Thanks.

---

### Post by w4ett on 2007-07-19
When you type your admin password into the terminal, the characters are not echoed on the screen as an additional security measure.

Just type the password  in normally, and press <enter>

---

### Post by KyleBrandt on 2007-07-19
Chances are you are actually typing in whatever you set the password too, it just doesn't show what you are typing for security reasons (Someone could see how many characters your password is by looking over your shoulder).  By default the root account doesn't exsist, and you wouldn't be able to create it unless you are logged in.  If you are logged in, and just one to type commands with sudo privilages just type sudo -i.

---

### Post by ubanchaos on 2007-07-20
just type the password and hit "enter"

---

