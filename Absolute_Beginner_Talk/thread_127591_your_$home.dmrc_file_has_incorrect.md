---
title: "your $home/.dmrc file has incorrect"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by whitehawk on 2006-02-09
Hello  
Hope I am in the right spot for this ?
when I login to ubuntu after giving user name and password I got a error that says  (  your $home/.dmrc file has incorrect permission and is being ignored this pervents the default session and language from being saved  file should be owned by user and have a 644 permission ) I tryed  from a terminal window something I found from a post but did not help what I tryed was this

sudo chown (your user name) /.dmrc
 
asked for password but won't let me type password  so I hit enter  and got message 
sorry try again 
still no luck putting password in 
 so I hit eniter and took  me back to where I started  in terminal window 
 thanks for the help if any one can help me

---

### Post by markd on 2006-02-09
You could try deleting the file:
```
rm -f ~/.dmrc
```

Then when you log out, saving your settings should create a new one.

---

### Post by carlosqueso on 2006-02-09
BTW...it is letting you type in your password, it just doesn't show anything so that no one can see how long your password is.  Just type it and press enter next time you need to enter it.

---

