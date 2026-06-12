---
title: "Crash during update, now black screen after login  :-("
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by DutchKid on 2006-09-17
Hello,
I'm fairly new to Ubuntu and Linux in general. I have a rather old P4 laptop I wasn't using and I thought it would be interesting to install Ubuntu (Dapper Drake) on it. At first everything went well, everything seemed to be working. Now, this laptop has one problem: it tends to get very hot occasionally. When using Windows, it sometimes suddenly shut down. Not often, though, perhaps once a month or less.
Anyway, I decided to run the Ubuntu update and it found lots of updates. When installing the updates, the laptop suddenly shut down (I think due to overheating). Now Ubuntu doesn't work anymore :( 
I can login but after that I don't get to see the desktop - there's just a black screen and the cursor. I tried booting from the live cd but it's not working... I CAN however boot from my Windows cd. I don't want to, but I feel my only option right now is to re-install Windows :-(
Unless anyone can help? Please?

---

### Post by buffy^ on 2006-09-17
Press ctrl alt F1 and let me know if yuo get a login screen, if you do you should be able to login with your normal username and password.

---

### Post by DutchKid on 2006-09-17
Thanks for your help! In the meantime, however, I think I fixed it myself. I found out there's the possibility to start a failsafe terminal session. This did work. I updated everything again through apt-get update and everything seems fine again :)

---

### Post by buffy^ on 2006-09-17
Ahh well done, what was it you did to get the option?

---

### Post by DutchKid on 2006-09-17
In the login screen, if you press F10 you get a menu (you probably know this already). Then you can choose to start a failsafe terminal session (or GNOME session but this didn't work for me). I did this and entered *sudo apt-get update*. It returned a message saying something was wrong and I had to manually enter a command (something like *dgkp --configure -a*, hmmmm I forgot the exact words #-o ). After that installing went smoothly and then I could login again and everything worked just fine. 
I'm sure I sound like an absolute newbie, but well... I am! O:)

---

### Post by General Skanky on 2006-09-17
I too have this problem.

I am brand new to Ubuntu, ie, today.

Did the update and have exactly the same error.

What exactly is the command please?

---

### Post by DutchKid on 2006-09-17
Okay, this is what I remember:
1. At the Ubuntu login screen press F10
2. The second option in the menu is Choose session or something like that. Click it.
3. Choose: start failsafe terminal session
4. You should be able to login; afterwards you see a terminal screen
5. Type: sudo apt-get updates

Now, if you do have the exact same problem, you'll get a message saying there's a problem and you have to manually enter a line of code. I'm sorry I don't remember the exact command, but it should be listed in your terminal window. Otherwise, I guess you've got a different problem...

---

### Post by General Skanky on 2006-09-17
Thanks very much. Instead of F10, I saw the options icon in the bottom left hand corner of the log in page. Same reslut I believe.

My laptop was on batt power which had run down when it shut down and interupted the update.](*,) 

Live and learn.:rolleyes:

---

### Post by DutchKid on 2006-09-18
It worked, then? Good :-)

---

