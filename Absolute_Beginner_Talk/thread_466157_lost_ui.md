---
title: "lost ui"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by banda on 2007-06-06
my pclinux installation was working perfectly with beryl for a few hours.. then due to some reason i went and changed the monitor type from the controls and now i have lost the ui
all i get when i boot is the black screen asking username and pwd

how do i get the ui back??:(

---

### Post by banda on 2007-06-06
anyone??

---

### Post by Rocket2DMn on 2007-06-06
If you can get to a command line interface / terminal, login and run the following command which will bring up a reconfiguration for the monitor/gfx card setup.  It also covers other stuff like keyboard/mouse.  Make sure you read everything, but it's pretty self-explanatory:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by banda on 2007-06-06
ok gonna try it now.. thx for replyin:D

---

### Post by banda on 2007-06-06
it says command not found

---

### Post by Rocket2DMn on 2007-06-06
Are you sure you typed it exactly as written above with the dashes and everything?
I've never heard of that command not being found with Ubuntu.

---

### Post by banda on 2007-06-06
i m running pclinux not ubuntu
their main forums were down so i posted on the temporary ones...
did not get a reply for long so posted here...

somebody on the pclinux temporary forums told me to type mcc at command prompt.. that way  i was able to select the correct monitor.. 
but i dont know the command to initialize x
and it does not run automatically on boot... so som1 plzz HELP!
temprary pclinux forum -[http://pclossupport.forumsland.com/pclossupport-post-3704.html#3704]("http://pclossupport.forumsland.com/pclossupport-post-3704.html#3704")


(by the way the main pclinux forums are up but they will take hours to validate my registeration)

---

### Post by Rocket2DMn on 2007-06-06
Ah, that explains it.  "startx" should be the command to start up the X-server.  If that doesn't get you in, I'm not really sure what to do.  You may just have to wait until the PCLinux forums are up unless anybody else here has experience with it.
Good luck man.

---

### Post by banda on 2007-06-06
when i type startx

i got error.. i m typing it here 

creating new authority file /root/.serverauth.3211
fatal server error
cannot open log file "/var/log/xorg.0.log"
giving up
xinit: connection refused (error no 111): unable to connect to xserver
xinit: no such process (error no 3):server error

---

### Post by Rocket2DMn on 2007-06-06
Hrmm, I've never had to run this command myself, it looks like you may have to run it as root:
```
sudo startx
```
type in your pw.
My bad man, hope that works.

---

### Post by banda on 2007-06-06
hey rocket2d.. thanks for trying to help me out...

but even sudo startx gave the same errors!
any other ideas??
i m minutes away from reinstalling... (i guess it will be quicker than troubleshooting furthur)

---

### Post by Rocket2DMn on 2007-06-06
I'm fresh out, sorry man.  Hope the reinstall works well.

---

