---
title: "loging as root in gui"
date: 2005-05-28
forum: Absolute Beginner Talk
---

### Post by heart_reaver on 2005-05-28
hi there 

 i m new  to ubuntu i am not able to login as root in GUI. i have made root password by sudo but that is not working in gui.

when i  try sudo root to login as root then

message is 

Password:
anu is not in the sudoers file.  This incident will be reported.
xyz $ 


on gui terminal. 

also i have tried root terminal it is giving me no responc after i give user password
or root password.

---

### Post by netrattler on 2005-05-28
I highly recommend that you don't do this for security reasons but here are the steps to do it if you really like this option.

1: sudo passwd root
2: Type in your new password for root
3: Click on System -> Administration -> Login Screen Setup -> Security tab
4: Put a check by Allow root to login with GDM
5: Logout and type root for username and in the password field whatever your password is.

But I highly recommend that you try to get use to using the sudo command to do administration. If you need to sudo from the gui from Applications -> Run Application then all you need to do is type "gnome-sudo", for example : gnome-sudo nautilus .

Joe

---

