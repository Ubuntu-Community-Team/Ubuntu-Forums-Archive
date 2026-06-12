---
title: "more generic advice needed xorg"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by kristiaan_d on 2007-11-01
hi need some help i followed a tutorial on here to try and manually ammend my video res to 800 X 600 and now i cannot login at all.

this is what i followed i got upto the part where you start up KDE again and that was the end of that 

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

i am now trying to rename the backup file from the console but cannot seem to achieve this i have tried sudo rename xorg.conf xorg.conf1 but that gives me some crazy error that nasa would have a hard time working out.

can someone tell me how i now rename the xorg.conf_backup file to the proper file please. 

and how i setup the res so that its 800X600  its running in parrallels on my macbook 13" BTW its 6.06 LTS

---

### Post by kristiaan_d on 2007-11-01
ok i have got that working and restored the backup i made, but its STILL not working..... 

when i try and login i just get a drum beat and back to the login screen thats all of it. i really dont want to have to spend more time reinstalling and if thats the only option ill stick to OS x and windows...

---

### Post by nick_h on 2007-11-01
Restoring the backup was in the guide:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
What errors did you get when you tried to restart KDE?

---

### Post by kristiaan_d on 2007-11-01
did not get any errors that i can see, when i try to login using the GUI login screen it logs in goes to a terminal window for a few secs plays the drum beat sound and i am back at the GUI login screen

---

### Post by nick_h on 2007-11-01
Which bit of the guide did you follow?

---

### Post by lbthrice on 2007-11-01
well your first mistake was buying a macbook...apple is notorious for locking down their hardware...Steve Jobs is all about proprietary licensing schemes...he has recently sent a 9 year old girl a cease and desist letter for doing a 3rd grade project on how to improve the ipod nano...

anyhow...hopefully an ubuntu guru will come and post about the xorg configuration 

my advice...for whatever it is worth...is to get you hands on some old and unused hardware...a desktop pc of mac that has been sitting in one of your friends basements unused...or maybey your place of work has some old hardware laying around they they don't use because of the inefficiency of the operating systems that you mentioned...and install your favorite flavor of Linux on one of those machines...so that you have a sandbox to play in and familiarize yourself with the Linux environment... 

in this way you will not slow your productivity while you learn to use free software
this is an awe-inspiring community effort that has been spearheaded by alot of smart people

also not something that can learn in 24 hours

so anyway...that is my advice...good luck! don't be discouraged!

---

### Post by kristiaan_d on 2007-11-01
i did not get that far i got to this point in the tutorial (the forth code window down)

To start Gnome/KDE again:
Code:

sudo /etc/init.d/gdm start (or kdm for KDE)


that got me back to the login screen and thats all i have got since then.

---

### Post by nick_h on 2007-11-01
When you say "i got upto the part where you start up KDE again and that was the end of that " what exactly happened?

---

### Post by kristiaan_d on 2007-11-01
well i know it sounds like i am repeating myself and i appologise for it but, after i typed in Sudo /etc/init.d/gdm start KDE which started up the GUI again which then asked me for my username, i re entered that and my password. it then momentaraly goes back to the command prompt flicks to the ubuntu desktop wallpaper ( no menu bar) plays the sound effect and then i am back at the username GUi prompt

all of this happens with no errors, warnings or messages anywhere in the process, there are no popup errors in the GUi and nothing on the command line i can see for the brief second or two its there.

---

### Post by nick_h on 2007-11-01
Are you using KDE or Gnome?

For Gnome you need:```
sudo /etc/init.d/gdm start
```
For KDE use:```
sudo /etc/init.d/kdm start
```

---

### Post by Arthur Archnix on 2007-11-01
Can you post your xorg.conf file. Maybe toss in this too:
```
lspci | grep Display
```

Actually, wait. At the login screen can you choose a failsafe login and use that? It sounds like your xsession has been pooched.

---

### Post by kristiaan_d on 2007-11-01
hi i have tried all the login options avaliable none of them get me into the system the only one working at the moment is the failsafe terminal, 

in regards to the KDE or Gnome i have no idea i just typed in what it asked me to and i assumed as normal i was using KDE ( to be honest thats the only one i have ever heard of.


in regards to the "lspci (cannot type that on my mac) Display" nothing happens , although the line charector does turn up in the linux system when i type the command.

my next question is how do i post the conf file ?? i cannot figure out how to copy the contents of the file from the terminal and paste it here...

i just typed nano xorg.conf and there seems to be no way to select all the file or copy it...

please lads remember this is all new to me..

---

### Post by nick_h on 2007-11-01
One way to do it is to run:
```
cat /etc/X11/xorg.conf
```
Then highlight the text, then Edit->Copy.
Then you can Edit->Paste into the browser.

(Forget what I said earlier about X starting OK)

---

### Post by nick_h on 2007-11-01
> **kristiaan_d said:**
> in regards to the "lspci (cannot type that on my mac) Display" nothing happens , although the line charector does turn up in the linux system when i type the command.

Just type:
```
lspci
```
and paste to line to do with your video card.

---

### Post by jaybombalous on 2007-11-01
how is he gonna highlight? he is at a failsafe terminal, he needs to use nano, right???

I dunno

---

### Post by nick_h on 2007-11-02
Sorry, I was assuming that he was able to access a good configuration.

I don't use nano myself so I can't help there.  I don't know if the OP is using a text based browser to post or using a different computer.  If using a different computer I suggest redirecting the output of the command to a file as follows:
```
cat /etc/X11/xorg.conf > file.txt
```

As Arthur Archnix said the xorg.conf would be helpful.

Looking in the log file /var/log/Xorg.0.log would also be a good idea.  Look for lines stsrting "(EE)".

---

### Post by Arthur Archnix on 2007-11-02
EDIT: Sorry, I've erased the comment that was here. It was meant for another thread.

---

