---
title: "mass sms???"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by joris1977 on 2007-10-07
For a job i do i 'd like to send the same sms message to a lot of people. I have a nokia 6021. It works nice with bluetooth and gnome phone manager. But this program only allows to send sms one by one. I've been looking around and it seems kmobiletools could do what i want, but it doesn't work well with my nokia.

Maybe there is a simple solution to my problem i'm not seeing?     

Joris

---

### Post by ryanVickers on 2007-10-07
You could write a script to send a message to everyone - do you know a terminal command(s) for sending the message(s)?

---

### Post by joris1977 on 2007-10-08
Well from the gnokii site  [http://wiki.gnokii.org/index.php/User%27s_Guide#--sendsms:](http://wiki.gnokii.org/index.php/User%27s_Guide#--sendsms:) 
it looks lke this command would do:

echo "This is a test message" | gnokii --sendsms +48501123456 -r


Haven't tried it but gnocky was working nice so i think his should work as well.

I have never wrote any scripts before and was looking for a gui orientated solution, that my collegues would easily understand. 

But if it would be very simple i would like to know how i could make a script for this?

---

### Post by ryanVickers on 2007-10-08
well, if it has to be graphical (this is rally a disadvantage though) you could use zenity (see my RAR maker).


Usually I'm decent at scripting, but I know nothing about sending these messages (especially from the computer - how does that work?!?! ;)), so I don't know if I'll really be any help...

---

