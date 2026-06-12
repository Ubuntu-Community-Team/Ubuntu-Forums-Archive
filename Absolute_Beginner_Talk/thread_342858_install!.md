---
title: "install!"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2007-01-20
ok, i am trying to install lkl......my parents want a key logger type program...and i am giving them one....so...i dont have ANY experience in proper installs....and the install thing is really confusing....please help

---

### Post by Sniper99 on 2007-01-20
i tried to do a ./configure command but it didn't do anything

---

### Post by meng on 2007-01-20
Enable universe repositories: [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
sudo aptitude install lkl

Done!

---

### Post by an.echte.trilingue on 2007-01-20
```
sudo aptitude update
sudo aptitude install lkl
```

Take care,
-mat

---

### Post by christhemonkey on 2007-01-20
Try typing:
```
sudo apt-get instal lkl 
```

Then the command to run is this:
```
sudo lkl -k /usr/share/lkl/keymaps/us_km -o /home/`echo $USER`/Desktop/log.log -l 
```

(replacing us_km with a different one if you dont have a standard english keyboard)

---

### Post by Sniper99 on 2007-01-20
thank you so much......i got it pretty quick, and its actually really easy.....i just need to get some experience...thanks again....i tried it...and it only logged a little bit....do i need to like have an activation command to start logging or is it just automatic

---

### Post by Sniper99 on 2007-01-20
alright, so it logs all the stuff i type in the terminal...but none of my internet stuff.....so it just stops randomly

---

### Post by christhemonkey on 2007-01-20
You can start the keylogging with that command.
If you want to use the terminal after run it like this:
```
sudo lkl -k /usr/share/lkl/keymaps/us_km -o /home/`echo $USER`/Desktop/log.log -l &
```

If you want, add it startup programs by creating a bootup script like this:

```
sudo -i `echo "lkl -k /usr/share/lkl/keymaps/us_km -o /var/log/lkl.log -l" >> /etc/init.d/lkl & update-rc.d -n lkl multiuser 99` 
```
That will start and stop it automagically on boot up and shutdown, with a log file appearing at /var/log/lkl.log

EDIT:
Just did a quick check, and when i ran:
```
sudo lkl -k /usr/share/lkl/keymaps/us_km -o /home/`echo $USER`/Desktop/log.log -l & 
```
Then went to firefox and opened up gmail, it then logged all my keypresses.

> <Ret>
Sat Jan 20 22:44:34 2007
<Ctrl>tgmail<Ret>
Sat Jan 20 22:44:41 2007
helloubuntuforums<Shift>!<Alt>NULLNULLNULLNULLNULLNULL

---

### Post by Sniper99 on 2007-01-20
thanks christthemonkey......much appreciated

---

### Post by christhemonkey on 2007-01-20
No problem.
If there any further issues, just let us all know.

---

