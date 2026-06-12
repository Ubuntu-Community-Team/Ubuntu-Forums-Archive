---
title: "Failed to start the x server..."
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by MrPhen on 2007-08-05
"Failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagonose the problem?" 

i've tried the sude command but still did not seem to work or maybe i didn't do it correctly?

by the way i am on a dell e1505, please help me :(

---

### Post by overdrank on 2007-08-05
> **MrPhen said:**
> "Failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagonose the problem?" 

i've tried the sude command but still did not seem to work or maybe i didn't do it correctly?

by the way i am on a dell e1505, please help me :(

Hi, could you tell us what your graphics card is? and did you tried the command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then reboot your system?

---

### Post by sameer.iitg on 2007-08-06
Hi I am getting the same problem. I followed the instructions given on [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

I have ATI drivers

thanks in advance
Sameer

---

### Post by LinuxGEEK7288 on 2007-08-06
Hey, i have the exact same problem i have a dell Inspiron e1505 and i was running ununtu 6.10, which worked fine and i wanted to upgrade to 7.04 so i spend the hour and a half doing the upgrade, and now it i get that "failed to start the x server" so i went to the xorg.conf file and it told me to run "sudo dpkg-reconfigure -phigh xserver-xorg" and then it asked me to pick a video driver, which i did........it still dosn't work......whats the deal???

PLEASE HELP

---

### Post by MrPhen on 2007-08-06
> **overdrank said:**
> Hi, could you tell us what your graphics card is? and did you tried the command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then reboot your system?

yes that is the command i tried and i believe i have the 'CARD (CIRCUIT), GRAPHICS, 128MB, M52, I6400 (ATI X1300)'.  that is what i found when i looked.'

---

### Post by MrPhen on 2007-08-06
also i was trying to use the 7.04, i have not used any other versions.

---

### Post by overdrank on 2007-08-06
> **MrPhen said:**
> yes that is the command i tried and i believe i have the 'CARD (CIRCUIT), GRAPHICS, 128MB, M52, I6400 (ATI X1300)'.  that is what i found when i looked.'

Hi if you use the command posted and select the vesa driver and hopefully this will get you to the desktop and then you can enable the restricted drivers that seemed to help other with similar problems. Hope this works.

---

### Post by MrPhen on 2007-08-06
> **overdrank said:**
> Hi if you use the command posted and select the vesa driver and hopefully this will get you to the desktop and then you can enable the restricted drivers that seemed to help other with similar problems. Hope this works.

ok, where is the place i enter that command and how do i get there? (so i know i'm at the correct place). and what restricted driver? the x server?

---

### Post by overdrank on 2007-08-06
> **MrPhen said:**
> ok, where is the place i enter that command and how do i get there? (so i know i'm at the correct place). and what restricted driver? the x server?

Sorry, Ok when you get the xserver error just click ok and it will bring you to the command prompt with the login screen. Then you login user name and password then enter the command 
```
sudo dpkg-reconfigure xserver-xorg
``` answer the questions and if you dont know the answer leave the default  given. This command is a little different than before because the first command auto configures you xorg and the command just given in this post will let you choose the vesa driver.

---

### Post by MrPhen on 2007-08-06
> **overdrank said:**
> Sorry, Ok when you get the xserver error just click ok and it will bring you to the command prompt with the login screen. Then you login user name and password then enter the command 
```
sudo dpkg-reconfigure xserver-xorg
``` answer the questions and if you dont know the answer leave the default  given. This command is a little different than before because the first command auto configures you xorg and the command just given in this post will let you choose the vesa driver.

i don't get a thing to login, it just gives some basic pop ups about the error, i choose OK on them from using the right arrow as i cannot us my mouse to click and then it just leaves a command line about boot but does not go any farther.

---

### Post by overdrank on 2007-08-06
> **MrPhen said:**
> i don't get a thing to login, it just gives some basic pop ups about the error, i choose OK on them from using the right arrow as i cannot us my mouse to click and then it just leaves a command line about boot but does not go any farther.

Ok when you reach that last point then use the keys at the same time ctrl, alt,F1 and this shoule bring you to the command prompt.

---

### Post by leo_rockway on 2007-08-06
[http://ubuntuforums.org/showthread.php?t=516835](http://ubuntuforums.org/showthread.php?t=516835)

that's the solution for an ati mobility x1400... it probly works for x1300 as well.

---

### Post by MrPhen on 2007-08-06
> **overdrank said:**
> Ok when you reach that last point then use the keys at the same time ctrl, alt,F1 and this shoule bring you to the command prompt.

so i try that sudo thing, and after i'm done it says something about "something@ubunutreboot" so then i do "startx" and it gives me an error about connection reset by peer.

---

### Post by MrPhen on 2007-08-06
> **leo_rockway said:**
> [http://ubuntuforums.org/showthread.php?t=516835](http://ubuntuforums.org/showthread.php?t=516835)

that's the solution for an ati mobility x1400... it probly works for x1300 as well.

whenever i'm done writing the file it says  "Error Writing /ect/X11/xorg.conf:No such file or directory" and i cannot do control + x, it just beeps at me.

---

### Post by overdrank on 2007-08-06
> **MrPhen said:**
> so i try that sudo thing, and after i'm done it says something about "something@ubunutreboot" so then i do "startx" and it gives me an error about connection reset by peer.

Ok, Is ubuntu installed on the system or are you still using the live cd?

---

### Post by MrPhen on 2007-08-06
> **overdrank said:**
> Ok, Is ubuntu installed on the system or are you still using the live cd?

i first got this problem when i tried the live cd, so then i installed it so i'm using the installed version.

---

### Post by MrPhen on 2007-08-06
[http://ubuntuforums.org/showthread.php?t=414194]("http://ubuntuforums.org/showthread.php?t=414194")

i was looking at that, i'm not sure if i install it from the live cd that it will overwrite everything i have for windows though.

---

### Post by overdrank on 2007-08-06
> **MrPhen said:**
> [http://ubuntuforums.org/showthread.php?t=414194]("http://ubuntuforums.org/showthread.php?t=414194")

i was looking at that, i'm not sure if i install it from the live cd that it will overwrite everything i have for windows though.

Hi you can do that from the command line but from the error you stated previously  
"Error Writing /ect/X11/xorg.conf:No such file or directory"
This poses a problem, that is why I asked if you were using the live cd. I am at a lose to be able to help but if you can get to command line after the xserver error the by all means use the sticky you posted. That has seem to help others like in this thread
[http://ubuntuforums.org/showthread.php?t=489477&highlight=ATI+X1300](http://ubuntuforums.org/showthread.php?t=489477&highlight=ATI+X1300)
Good luck! :(

---

### Post by MrPhen on 2007-08-06
> **MrPhen said:**
> i first got this problem when i tried the live cd, so then i installed it so i'm using the installed version.

> **overdrank said:**
> Hi you can do that from the command line but from the error you stated previously  
"Error Writing /ect/X11/xorg.conf:No such file or directory"
This poses a problem, that is why I asked if you were using the live cd. I am at a lose to be able to help but if you can get to command line after the xserver error the by all means use the sticky you posted. That has seem to help others like in this thread
[http://ubuntuforums.org/showthread.php?t=489477&highlight=ATI+X1300](http://ubuntuforums.org/showthread.php?t=489477&highlight=ATI+X1300)
Good luck! :(

after the xserver error and after i click all the OK's and such it just leaves at 
* Running local boot scripts (/ect/rc.local)  [OK]
and doesn't go any rather.

---

### Post by leo_rockway on 2007-08-06
> **MrPhen said:**
> whenever i'm done writing the file it says  "Error Writing /ect/X11/xorg.conf:No such file or directory" and i cannot do control + x, it just beeps at me.

it's /etc not /ect...

---

### Post by MrPhen on 2007-08-06
> **leo_rockway said:**
> it's /etc not /ect...

oh maybe that was it, stupid noob error :oops:

---

### Post by MrPhen on 2007-08-06
ok i tried that again, but when i tried to enter the "sudo apt-get install xorg-driver-fglrx"
i got this error "E: Couldn't find package xorgdriver-fglrx".

---

### Post by leo_rockway on 2007-08-06
are you connected to internet on ubuntu?

you may need to decoment some lines in the /etc/apt/sources.list file... i dont remember if certain repositories were necessary for the driver.

---

### Post by MrPhen on 2007-08-06
> **leo_rockway said:**
> are you connected to internet on ubuntu?

you may need to decoment some lines in the /etc/apt/sources.list file... i dont remember if certain repositories were necessary for the driver.

not sure if i am connected to the Internet or not, and i probably wont be able to figure that out as i am a noob and will have no idea what i'm doing.

---

### Post by leo_rockway on 2007-08-07
> **MrPhen said:**
> not sure if i am connected to the Internet or not, and i probably wont be able to figure that out as i am a noob and will have no idea what i'm doing.

are you wire connected or wifi connected normally? if you are wifi connected i recommend connecting the cable to your network card... ubuntu should recognize your wired connection.

if you were wire connected... then maybe you need to decomment some lines in /etc/apt/sources.list

i'll let you know how to do that if the wire connection fails.

---

