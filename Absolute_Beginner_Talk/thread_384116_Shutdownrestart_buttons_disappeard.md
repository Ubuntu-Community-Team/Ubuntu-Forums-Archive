---
title: "Shutdown/restart buttons disappeard"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by KsR on 2007-03-14
hello,

this is just a small nuisance but I just wanted to find out why this happend...

I wanted to restart my pc so clicked on the Systems menu -> Quit option... but the Quit window didn't have any options for Shutting down or restarting the system!!??

The only options it contains is , log out, Hibernate, Lock screen and switch user.
  This was quite puzzling since I was getting the Shut down and restart buttons before.
Any ideas on how they just suddenly..disappeared?
Where can a find the folder which contains all this data?

Thanks

---

### Post by EdThaSlayer on 2007-03-14
I don't know what happened to your computer. But you can create a shortcut icon so all you have to do is shut down by clicking on that icon. 

So below are the steps on how to shut down or restart your pc until you can get that error fixed.

_**Restart icon**_
Steps:
1.On the top panel right-click and select add-to panel
2.Click on "Custom Application Launcher"
3.In the command section paste "sudo shutdown -r now"
5.Select "run in terminal"
6.You can choose a icon if you want 

_**Shut down icon**_
Steps:
1.On the top panel right-click and select add-to panel
2.Click on "Custom Application Launcher"
3.In the command section paste "sudo shutdown -h"
5.Select "run in terminal"
6.You can choose a icon if you want 
This is the only alternative I know.

---

### Post by KsR on 2007-03-14
thanks a lot.. its actually much easier now  :) 
maybe there's a way i can add the shutdown and restart options back into the System->quit option..will check it out
thanks again

---

### Post by AtrejuT on 2007-03-14
are you using beryl (and xgl)?
That usually makes the buttons disappear.
A solution can be found here:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

atreju

---

### Post by eytan on 2007-03-14
Howdy, I am a newbie too but also had the same problem a couple of weeks ago. Turns out that enabling accessible login kills the power options. Go to System -- > Login Window -- > Accessibility and disable the accessible login. Don't know why but it worked me. Smooth sailing.

---

