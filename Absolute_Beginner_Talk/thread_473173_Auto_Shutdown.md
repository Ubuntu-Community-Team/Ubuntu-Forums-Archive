---
title: "Auto Shutdown"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Chemist on 2007-06-13
Is there a command I can run in the terminal or download a program to shut down my ubuntu box automatically??

---

### Post by Inxsible on 2007-06-13
what exactly do you mean automatically ?
The terminal command is 
```
shutdown now
```

---

### Post by inque_54 on 2007-06-13
I think the OP was asking for a suggestion on how to set a timer in UBUNTU for it to shut down in a specified time.

 I too am looking for a software solution that does this or a command or a script or something 8)

---

### Post by Inxsible on 2007-06-13
> **inque_54 said:**
> I think the OP was asking for a suggestion on how to set a timer in UBUNTU for it to shut down in a specified time.

 I too am looking for a software solution that does this or a command or a script or something 8)
well you can then create a script which you can call whenever you want. Like I suggested earlier, you can use the shutdown command again.

shutdown -r  will reboot
shutdown  +m 20 will shutdown after 20 mins -- i think is the correct syntax.

or shutdown hh:mm uses a 24 hr clock to shutdown after specified time.

---

### Post by EyeBaller on 2007-06-13
> **inque_54 said:**
> I think the OP was asking for a suggestion on how to set a timer in UBUNTU for it to shut down in a specified time.

 I too am looking for a software solution that does this or a command or a script or something 8)

Woohoo.. I can help someone!
I use an app called GShutdown for this. It's right in the add/remove section in applications. Make sure you have "all available software" selected in the top right drop down, then search for "gshutdown" and you can install it.

I'm pretty sure this is what you guys need right?

---

### Post by inque_54 on 2007-06-14
Hey guys thanks for the replies 

I looked into Gshutdown but the problem is it lacks the feature which I really need the most. To schedule computer shutdown at a certain time of the day and this should be for everyday. 

Thanks again

---

### Post by deadlikeoscar on 2007-06-14
try opening a terminal and typing **crontab -e**

Go to a line underneath what is already written in the file and type like this example.

30 2 * * * /sbin/shutdown -h now

The 30 is the minutes and the 2 is the hour. So at 2:30AM (24 hour clock time) the computer will shutdown. The three asterisks are unimportant since you want this to happen every day. After you type this hit Ctrl +O to save the file and hit enter to accept the filename. Then press Ctrl + X to exit. Then just wait and see if it works.

---

### Post by inque_54 on 2007-06-14
Thanks for the suggestion, but unfortunately it didn't work 8( 

Any more tips?

---

### Post by Nikron on 2007-06-14
It would be sudo crontab -e, your user doesn't have the permisssions to shut down.

---

### Post by inque_54 on 2007-06-14
Ok that worked! 

Thanks everybody!!!

---

### Post by Chemist on 2007-06-14
cheers guy

---

### Post by vasiauvi on 2008-03-09
A good linux tutorial for begginers: [http://www.linux.org/lessons/beginner/l5/lesson5a.html](http://www.linux.org/lessons/beginner/l5/lesson5a.html)  here is and the auto shutdown. :)

---

### Post by QwUo173Hy on 2008-03-15
Thanks dealikeoscar, that was really helpful. 

Why is there no Thankyou button beside your name that I can click on?

---

