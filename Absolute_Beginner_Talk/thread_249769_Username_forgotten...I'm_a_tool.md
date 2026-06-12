---
title: "Username forgotten...I'm a tool"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by hawk6773 on 2006-09-03
Ok, so about a month ago, I installed Ubuntu on my test machine at work. It's the first version of Linux I've used and I love it.

That being said, I feel like a complete moron. I'm installing Ubuntu desktop on an old machine at home to setup as a test webserver. 

I was paying more attention to the poker game I was playing on my other machine while Ubuntu was installing and can't remember the username I set up.  

Yes, I know...brilliant =D> 

Is there an easy way for me to see what the username is? Or can I at least login as root?

---

### Post by LKRaider on 2006-09-03
Boot into recovery mode or from a livecd and type in this command on the console:
```
cat /etc/group | grep 1000
```[SIZE="1"]*you'll need to change the path of /etc/group to where you mounted your system hd if booting from a livecd[/SIZE]

It should display the username you have chosen to the default user.

---

### Post by aysiu on 2006-09-03
You can also boot into recovery mode and type ```
cd /home
ls
```

---

### Post by LKRaider on 2006-09-03
Heh, true! way easier :-P

But, err.... with my alternative... hmm... he learns... something... I forget what... 

err :-P

---

### Post by hawk6773 on 2006-09-03
Thanks!

Got it back up and running.

---

