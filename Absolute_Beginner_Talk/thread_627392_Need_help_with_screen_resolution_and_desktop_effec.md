---
title: "Need help with screen resolution and desktop effects"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by nileshsudon on 2007-11-24
I Have Toshiba Laptop U-300 And I Am Unable To Use Desktop Effects 

More Over My Screen Resolution Is Also Not Full..i Have A Split Screen  1024*780 And Still The Wallpaper Does Not Stretch All Over And Nither Does The Ubuntu Screen 

Please Help Me I Don`t Have Any Knowledge Of Linux So You Will Have To Let Me Know Things Step By Step

---

### Post by shamasis on 2007-11-24
> **nileshsudon said:**
> I Have Toshiba Laptop U-300 And I Am Unable To Use Desktop Effects 

More Over My Screen Resolution Is Also Not Full..i Have A Split Screen  1024*780 And Still The Wallpaper Does Not Stretch All Over And Nither Does The Ubuntu Screen 

Please Help Me I Don`t Have Any Knowledge Of Linux So You Will Have To Let Me Know Things Step By Step

You may need to reconfigure your xserver

Use this command at a terminal window:
```
sudo dpkg-reconfigure xserver-xorg
```
... and follow the steps on screen.

Be conservative while providing the input values. By that I mean, do not over-estimate your monitor or graphic card's capabilities when asked by the reconfiguration menu.

---

### Post by nileshsudon on 2007-11-30
i have no knowledge of linux and i really want to learn linux as i want to switch over from windows to linux

i have tried all the ubuntu forums and even indian ubuntu forums but no one helps .

please all experts in linux help beginners like me.

I am using a laptop  toshiba u300 -111  and i don`t have sound /interent/ no proper display as taskbar is smaller then the windows size.

and i am unable to understand how to work it out.

please all experts of ubuntu ...kindly compile a documentation from the scratch with the basis linux 

+ ubuntu and also a special chapter on how to configure sound and display for unsupported laptops.

please help.
nilesh

---

### Post by Partyboi2 on 2007-11-30
> I am using a laptop toshiba u300 -111 and i don`t have sound /interent/ no proper display as taskbar is smaller then the windows size.
What do you mean that your taskbar (panel) is smaller then the windows size?
How are you trying to connect to the internet? wireless? ethernet?
What are the error message you are getting if any?

---

### Post by Partyboi2 on 2007-11-30
There are plenty of guides out there that can help you learn and if you ever get stuck you can always use Mr Google to search out answers (which I do often) If there is something you are unsure about ask here in the forums. Remember that you will not learn linux over night. So read and read and ask questions and take one hurdle at a time.
Here are some links that might interest you.
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://ubuntuforums.org/showthread.php?t=86389&highlight=troubleshooting](http://ubuntuforums.org/showthread.php?t=86389&highlight=troubleshooting)
[http://www.linux.org/](http://www.linux.org/)
[http://www.google.com](http://www.google.com)
Hope this gets you started in the right direction. :)

---

### Post by nileshsudon on 2007-11-30
thanks a lot partyboi2 

well i am using my other laptop to excess the net

have tried everything with google and tried even forums for the sound problem no use man 

i think u will have to let me know step by step from 

nilesh@nilesh-laptop:~$ 

or please mail me at [email]sudonnilesh@yahoo.com[/email]

---

### Post by nileshsudon on 2007-11-30
i tried

sudo dpkg-reconfigure exserver-xorg

it says /usr/sbin/dpkg-re
configure: exserver-xorg is not installed

partyboi2 is it possible for you to send me ur email id or some chat id like yahoo or msn ?

---

### Post by overdrank on 2007-11-30
> **nileshsudon said:**
> i tried

sudo dpkg-reconfigure exserver-xorg

it says /usr/sbin/dpkg-re
configure: exserver-xorg is not installed

partyboi2 is it possible for you to send me ur email id or some chat id like yahoo or msn ?

Try this correct command
```
sudo dpkg-reconfigure xserver-xorg
```

---

