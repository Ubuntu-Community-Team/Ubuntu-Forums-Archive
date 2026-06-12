---
title: "I give up"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by acer56 on 2006-07-04
Ive tryed 4 times to try and install ubuntu each time after the orange progress bar finishes it says server x hasnt been detected or isnt working and it takes me to  a black screen with white writing, ive tryed to reconfigure it and nothing works.

---

### Post by evilghost on 2006-07-04
Post /var/log/Xorg.0.log, or, just summarize the crucial output of:

cat /var/log/Xorg.0.log|grep "EE"

---

### Post by acer56 on 2006-07-04
what?

---

### Post by aysiu on 2006-07-04
[QUOTE=acer56]what?[/QUOTE]
evilghost means that when you're in the black screen with white text, log in with your username and password. Then when you get to the prompt that looks like this: ```
acer56@ubuntu:~$
``` type this command: ```
cat /var/log/Xorg.0.log|grep "EE"
``` Then post back here what you see.

---

### Post by wolfmaniac on 2006-07-04
it means that to run graphical interface u have to configure your xserver properly.
juz post the output of above commands to see where the problem might be.

---

### Post by wombat20 on 2006-07-04
He's asking you to post the contents of a log file by entering the command specified at the command line.  Then people can debug it for you and give you some helpful advice.

---

### Post by acer56 on 2006-07-05
i typed in that command for the log but all it says is no such file or directory and it i typed it in correctly i tryed like 5 times, the message that it keeps telling me when i try and load ubuntu is" Failed to start the X server (your graphical interface) it is likely that it is not set up correctly would you like to veiw the x server output to digounise the problem and after that it just shows me a bunch of programming lanuage that i dont understand in the slightest.

---

### Post by IYY on 2006-07-05
You can run the following code and select 'vesa' when asked for the video card driver:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by acer56 on 2006-07-06
yeh when i type in that a blue screen comes up asking me like a thousand questions and i dont know wot to select so i just enter with whatever it has auto seleted then after it stops asking me questions it just takes me back to the black screen with sudo commands and when i restart there is no difference it still says xserver not working, but when i finish selecting options after typing in that command it sayswarning overwriting possibly-customised configuration or something just above were i can type in a sudo command.

---

### Post by AndyTPO on 2006-07-06
Hi Acer. As you can see, I am new to this too. I belive that your problem is same as I did have when trying to install. Was installing on dell gx-150 computer that have integrated video card. When I hit auto to install video driver it did vesa. However, my sistem did not work, just vertical lines on it. After reading more, i chose i380 video driver (intel chipset in comp).

That solved my problem.

Good luck, we will need it. Man, this is soooooo confusing for new guy!

---

### Post by Grim_n_Evil on 2006-07-06
Having in mind that you are using terms such as "black screen with white writing", I would suggest that you read a little more before further venturing into Linux. Don't get me wrong, I'm not trying to insult, I just want to save you a lot time and headache.  ;)

cheers

---

### Post by sanderella on 2006-07-06
:KS Acer, please don't give up! You need someone to come alongside you and help you get your install fixed. Do you know about Linux User Groups (LUGs)? You can find out where your nearest one is by typing in your county or nearest city into Google, (eg Hampshire LUG). You can take your box along and someone there will help you fix it.

If at first you don't succeed....presevere! I'm hoping our computer room will be Microsoft free this year.:)

---

