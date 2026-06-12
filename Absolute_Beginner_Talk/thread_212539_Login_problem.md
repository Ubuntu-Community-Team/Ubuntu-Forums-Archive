---
title: "Login problem"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by xrchris on 2006-07-10
Well booted up my PC this morning and it requested my login id and password which i thought unusual as i have this option turned off. 
No problem i thought and i entered my login and password, it then thought about it and then went back to begining of the login process. It seems stuck in a perpetual loop. 
So whenever i enter the correct login/password combo it accepts it but then goes back to the begining of the login process.

I have checked to make sure i am using the correct info. 

Any ideas on how to correct this?

---

### Post by xrchris on 2006-07-10
This is so infuriating and to be frank i am getting a little tired of the minor problems that seem to render your whole linux system useless. I can certainly see why the majority of the public will never choose Linux in any form. 

Well thats enough of the rant.

---

### Post by rdd on 2006-07-10
Don't despair. I agree that you can have problems on Ubuntu. But for my part they have been either self-induced or quickly solved. So let's solce this one.

Does the X-Server crash (i.e. screen flickers or something) after the login?

---

### Post by xrchris on 2006-07-10
To start with i am surprised the login screen comes up at all as i had disabled this. 

It gets to the login screen ok, gui type login not commandline.

It accepts the Login and PW fine and then starts to load the splash screen it is at this point that it flicks back to the Login screen. 

It never actually gets to the splash screen.

-EDIT-
The last thing i had been doing was running Half life lost coast using Crossover Office.

---

### Post by rdd on 2006-07-10
Have you tried choosing another session type (bottom-left corner menu). Try failsafe Gnome. Have you got an alternative Window Manager installed or something like that.

---

### Post by xrchris on 2006-07-10
Yes i have and none of them work. 

After i login the screen very quickly flicks to a text login screen then to the nvidia logo screen after this the screen goes back to the login screen. 

Tried to reconfigure xorg as well in safe mode and that hasnt solved anything. 

Completely stumped and have no idea how to proceed.

---

### Post by xrchris on 2006-07-10
Well it looks like i have fixed it - Booted into windows and navigated to the Steam folder in the Crossover Office files and just deleted it. 

Bit of a hack but it worked. :)

---

### Post by rdd on 2006-07-11
Glad you could fix it. But i wonder what steam has to do with your session startup. 

rdd

---

### Post by OleNOR on 2006-07-13
Hi, after upgrading to 2.6.15.26. i got the same problem as you.  Haven't seem anybody who have a good solution for this either. My setup is basic ubuntu 6 with ndiswrapper, and automatix with nvidia  driver.

---

### Post by rockprincess on 2006-07-15
i've got exactly the same problem now, the screen flickers and then goes back to the login interface.....how can I fix this?! i appreciate any help!

---

### Post by Lamar on 2006-07-15
I've had exactly the same thing happen before, but only after setting my video drivers to "vesa" in xorg.conf.

---

### Post by rockprincess on 2006-07-15
how did you fix it then?

---

### Post by rockprincess on 2006-07-15
oh by the way, the above mentioned

"CTRL + ALT + Backspace to kill/restart the x server" and "CTRL + F4" (or CTRL + E) to login and sudo restart X" didn't work for me either........

what else can I do to have full access again?!

---

### Post by Aliby on 2006-07-28
I have had this problem a number of times (Kubuntu). Until now I have brutily just reinstalled the system to get it working again. However that is not in good linux spirit and I really want to learn what is wrong and how to fix it.

My system was working fine. It seems that after upgrading the system (using apt-get) some configuration was lost and I get the **"Login Loop"**.

I expect that it is the xorg.conf that is a problem, and that it is X crashing, but I am not sure.
:confused:

---

### Post by billy bob joe jr on 2006-10-12
Hi also have the same problem i enter my login details and it loads to the desktop then flashes and goes back to the login screen im and it only happened after i downloaded the updates in useing version 6.06  could anybody help ??

---

