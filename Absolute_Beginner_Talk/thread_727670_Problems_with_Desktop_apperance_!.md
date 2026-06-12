---
title: "Problems with Desktop apperance !"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by WILL_CHAN on 2008-03-18
-Yesterday I've just did some change with my resolution screen from the default 640-480 -> 800-600. It worked pretty fine until I shut it down. Today when I turn Ubuntu on, I only can see the first screen ask me to log in and my pw. When I go the main screen, everything is just dot and dot, everything seems presented on the desktop but it's impossible to see it as well as click on the right direction to change it back.
-And I think this one is actually the main reason which leads my desktop to this issue.
-Also I tried to changed my font from this topic :
> [http://ubuntuforums.org/showthread.php?t=416570](http://ubuntuforums.org/showthread.php?t=416570) I wonder does it make my desktop impossible to see or the reason that I mention above ?
Now, I can't see anything on my desktop to changed it back to the default resolution ? So what should I do ? I have a whole bunch of stuff for my class and a lot of codes that I just wrote, I don't really want to reinstall everything, that really drive me crazy. 
-The other solution that I think of it directly fix it through the terminal from the main screen ( I means some options on the right at the bottom on the log-in screen ). But I just guess, because I'm still new to Ubuntu. So could you guys help me out. I'd appreciated that a lot and a lot. I really love Ubuntu, I just start learning shell script programming and kernel lately, I'm dying to learn Linux system. I can't give up this time. :( 
- I'm currently run Ubuntu 7.10, 32-bit ? Thanks !

---

### Post by WILL_CHAN on 2008-03-18
-First sorry for my poor English, second if I didn't give enough information, just let me know I will edit as much as I can. Because that all the things that I know so far on Ubuntu. Once again, thanks !

---

### Post by kpkeerthi on 2008-03-18
From GRUB, boot into **Recovery Mode**. At the prompt, type 
```

dpkg-reconfigure -phigh xserver-xorg
```
and choose the driver and resolution you monitor **supports**. If you are not sure what driver to choose, select **vesa**.

Type **reboot** and start in Normal Mode.

---

### Post by WILL_CHAN on 2008-03-18
Thanks ! I will tried that solution now T_T !

---

### Post by WILL_CHAN on 2008-03-18
It worked now T_T ! Thanks a lot kpkeerthi, I do appreciate it. Actually I only did 
> dpkg-reconfigure -phigh xserver-xorg But when I type vesa, it told me this one is not a command...But then I rebooted and it worked. But, if you have a little time, could you explain it a little bit for me. I would love to know this kind of stuff, because If I can understand it, I will learn more about Linux system.
I currently learn shell-script programming and kernel programming on Linux. But I'm not sure is it a good way to learn how to start learning programming on Linux or some other ways ? I knew C/C++ already. Would you giving me some recommendation ? Thanks a lot T_T !
Edit : my screen is still a little bit to the right, it lost some space on the left side :( ? I tried to find the place that I move the screen back to the middle but I couldn't find it ? Could you help me this time too ? Thanks !

---

### Post by kpkeerthi on 2008-03-18
Glad it worked for you.

Actually, I told you to select 'vesa' from the list of drivers it displays after you run that command. I think you typed vesa in command line.

As for programming I have no knowledge of C/C++ or kernel development or any kind of linux programming. Check out [www.linuxcommand.org](www.linuxcommand.org) and the links in my signature. I know linux commands and shell scripting and became proficient with it over time as I continued to stick with Linux. Some of the books I use and find invaluable are

1. [http://www.amazon.com/Practical-Guide-Commands-Editors-Programming/dp/0131478230](http://www.amazon.com/Practical-Guide-Commands-Editors-Programming/dp/0131478230)
2. [http://www.amazon.com/How-Linux-Works-Brian-Ward/dp/1593270356](http://www.amazon.com/How-Linux-Works-Brian-Ward/dp/1593270356)
3. [http://www.amazon.com/Linux-Cookbook-Second-Michael-Stutz/dp/1593270313/ref=pd_bxgy_b_text_b](http://www.amazon.com/Linux-Cookbook-Second-Michael-Stutz/dp/1593270313/ref=pd_bxgy_b_text_b)
* None are ubuntu or any distro specific.

dpkg-reconfigure command is used to configure an installed package. Here, we used it to configure **xorg** which is the the 'X' implementation used in Ubuntu. The **-phigh** options instructs the command to prompt for options that don't have a reasonable default (in this case, the driver and resolutions). For more information, type this command in a terminal window
```
man dpkg-reconfigure
```

If you are using a CRT, there should be a reset button or some control in it to correct the alignment.

---

### Post by WILL_CHAN on 2008-03-18
Thanks a lot ! I really appreciate this T_T ! I will look for those books !
> If you are using a CRT, there should be a reset button or some control in it to correct the alignment. What is CRT ? Sorry if it's such a silly question! But I really don't know what is it. I changed it back to 800-600 and then I restart, it show me some message that ask me to show with lowest quality of screen and some other stuff. I could just say no, and then when I've already on my desktop, I changed it back to 800-600 and now it worked fine, no more extra space on the left hand side. I think before I restart just change back to 640-480 then change it back when I'm already on Desktop. Is it a good way to handle this or it might have some affections later ?

---

### Post by kpkeerthi on 2008-03-18
[CRT monitors]("http://images.google.com/images?hl=en&q=CRT+monitor&btnG=Search+Images&gbv=2")

[LCD monitors]("http://images.google.com/images?gbv=2&hl=en&q=LCD+monitor&btnG=Search+Images")

:)

---

### Post by WILL_CHAN on 2008-03-18
Thanks a lot for your great knowledge and your enthusiasm T_T !

---

