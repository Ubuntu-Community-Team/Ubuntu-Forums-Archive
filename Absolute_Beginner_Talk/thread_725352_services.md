---
title: "services"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by RAJESHKSV on 2008-03-15
I HAD A PROBLEM WITH SERVICES...unknowingly  I UNCHECKED system communication bus(dbus) .as a result many applets and services(such as hibernate, sleep and many more stopped  working!!!

 I  found a soultion in one of ubuntu forums but its not working completely ....       I entered 

 sudo /etc/init.d/dbus start

 and  Then run services-admin and enabled the System Communication Bus (dbus)

thn its fine,but it is only upto that session.When I restart it again ,problems are still continuing,.......now  services window is opening(dbus is also in checked state) but still some services like hibernate,sleep are not working...Also the window 
 
 "Internal error:failed to initialise hal" 
 
 is still coming after every reboot...Everytime I switch on my lap, I have to stop the system communication bus(dbus)--uncheck it , and restart it again(through the above command from terminal)
 
 ...then hibernate and sleep are working...Isnt there a complete solution to this problem????I think due to this in recent times my lap is being stucked very often......(ofcourse config is very good del vostro 1500 model 2gb ram ;120gb harddisk;1.6ghz processor)..so plz help ,its very annoying ...............................

---

### Post by herbster on 2008-03-15
Wait, so you can't check it again in Services without starting the daemon from terminal?

---

### Post by RAJESHKSV on 2008-03-16
No,i mean to say after I found the solution in ubuntu forums and entered the command 
sudo /etc/init.d/dbus start
 and checked dbus from services,it worked fine but only upto that session..Next time I boot my lap,services window is openeing and dbus is also in checked state but still the same problems are contunuing..So what I did is 
stop dbus(by unchecking it)
run the above command from terminal
start dbus again
then all services and applets are running....So i mean 2 say every time I switch on my lap I am restarting  dbus!!!!!wt is solution to this prob?????? :confused:

---

### Post by kcramakrishna on 2008-05-04
I am facing the exact same problem. I was playing with the system and disabled dbus just to see what would happen and now I have the same issue of having to restart dbus and hal. Did you find a solution? Can you share it with me? I am running UBUNTU - kernel: 2.6.22-14 (32 bit) on a compaqAMD64

Thanks,
kc

---

