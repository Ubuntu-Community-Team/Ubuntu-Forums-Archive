---
title: "startup application on xfce ?"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by Googler on 2006-05-13
how to add/remove application from startup on xfce?

---

### Post by 5-HT on 2006-05-13
Easiest way would be to close any applications you do not want run and open any applications you do want run on startup, and just save the session on logout.

If you have a non-graphical application you want to get rid of you can check what they are by a ```
ps aux 
``` and either kill them by* ```
killall <name of app>
``` or a* ```
kill <PID of app> 
``` 
*Do not add the < & > in 




Another way to get applications to run on startup is to add their executable (or a symlink to it) in ~/Desktop/Autostart (there are lots of threads around discussing this).

Note: Dapper's Xubuntu has a nice graphical tool for managing startup applications (though Dapper is still in development so use at your own risk).


Hope that helps

---

### Post by Googler on 2006-05-13
thank you very much
this command was very helpful, i use it to kill applications
but actually i have some applications that loaded on startup and i need to remove it (prevent them from being loaded at logging in)

any ideas about that

---

### Post by Tortanick on 2006-05-13
I'd get BUM (boot up manager) 

[http://ubuntuforums.org/forumdisplay.php?f=75](http://ubuntuforums.org/forumdisplay.php?f=75)

---

### Post by Googler on 2006-05-13
i installed BUM but it doesn't do what i want
i didn't find my apps in its list

---

### Post by Googler on 2006-05-13
finally i made it !! :D 
i srarted xfce menu **system>system monitor** and browse through Processes tab and end up any unwanted process then save session when logging out

thanks all for respondind

---

