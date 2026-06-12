---
title: "rootpassword"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by degsart on 2006-12-28
Terminal keeps asking for my root password. I don't remember it so how can I access it?"

---

### Post by meng on 2006-12-28
There's isn't a root password enabled by default. There's a user password if your user has admin privileges. What are you trying to do?

---

### Post by degsart on 2006-12-28
I have just installed ubuntu 6.06 from CD and I am trying to get it to recognise my internal modem (data fax 5000). When I paste in command script for it to do this I am asked for my root passward. I tried using my login password but it won't accept it.

---

### Post by meng on 2006-12-28
What is this command you are pasting in?

---

### Post by deadgobby on 2006-12-28
Your password should be the same as your log in password at the splash screen. If you need to change your pass word.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_set.2Fchange.2Fenable_root_user_password](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_set.2Fchange.2Fenable_root_user_password)

---

### Post by degsart on 2006-12-28
This is the command I am pasting in

wget -c [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz) 
gunzip -c scanModem.gz > scanModem 
chmod +x scanModem
sudo ./scanModem 
gedit Modem/ModemData.txt

---

### Post by meng on 2006-12-28
Type each line in one at a time (you can still cut and paste, but you must do it one at a time).
It will ask for a password after the sudo command, type your user password.

I think what's happening now is that you're typing everything in and it executes each command serially, but needs a password after the sudo command, and what it is receiving as the entered password is:
gedit ...... [then your password]

See?

---

