---
title: "Display and operating problems."
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by GeorgiaBoot on 2007-11-14
I just have now been getting in the world of Ubuntu and like it so far but I just need to figure out some problems.

1) When I boot It goes to the normal Ubuntu loading then after that it turns black and says "Cannot Display this Video Mode" for about 10 seconds. After that it goes to the regular login screen and everything works. The problem with this is it takes allot longer to load with this thing popping up all the time. 



2) I decided to try out the effects with the virtual desktops and the window froze. I was able to close it but when I did the whole screen flickered and the small Icons on the taskbar got all garbled(turn off comp, network,sound icons etc...). 
So I went to try to place them back were they were originally but could not move the internet connection one, so I accidentally deleted it. 

I can't get it back. How do I get it back? I don't know the exact name of it but it had two monitors over lapping I think, It showed the internet connection and I was able to enable or disable the internet. I tried adding to the panel but the icon was not on the list.



3) I have had a bunch of freezing while messing with stuff and would like to know what is the equivalent to windows on Ubuntu to ending a process or closing the windows?


My specs are~P4 @3ghz, 3gb of ram, ati graphics card, LCD monitor
Thanks and all the help is appreciated.

---

### Post by Inxsible on 2007-11-14
If you restart your system, your taskbar should be alright. and the name of the network manager is nm-applet

---

### Post by GeorgiaBoot on 2007-11-14
I did restart and it did not show back up. Where can I find that so I could put it back on the bar?


Thanks for responding.

---

### Post by Inxsible on 2007-11-14
press Alt + F2. type in nm-applet and hit enter. That should bring it up.

---

### Post by GeorgiaBoot on 2007-11-14
I am on my windows HD at this moment but when I switch over I will try that. I am sure it will work and thanks for the help.

---

### Post by GeorgiaBoot on 2007-11-14
I just tried that and it did nothing. Nothing popped up. When I went to system monitor it showed nm-applet running.

Next the thing that messed the icons up in the first place (Desktop Effects) does not work at all. I wanted to see if it would even go on but when I clicked it the window popped up and I turned them on and nothing happened, it just froze. So I had to log out. 

Thanks

---

### Post by Inxsible on 2007-11-14
I see you have an ATI card, but which one exactly?

you will probably need to install xserver-xgl too.

---

### Post by jerrynewt on 2007-11-14
Right click on the bar where the applet was and choose Add to Panel. Scroll down and choose the Network Monitor applet and it will show back up  in the pane.

---

### Post by GeorgiaBoot on 2007-11-15
I have a ATI Radion x300 128mb.

I already have network monitor on the taskbar, it was some other network Icon where I could enable and disable the internet. It also showed it connecting or not. I don't know the name of it though.

Thanks

---

### Post by alienexplorers on 2007-11-15
Try going to this link to see if there is anything there that might help.
> [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

---

### Post by CatKiller on 2007-11-15
I don't think it's the network manager that you've lost at all. I think you've removed the notification area.

---

### Post by CatKiller on 2007-11-15
Oh, and you can terminate programs with the **kill** command. You can either run **ps ax** to get the number (**pid**) of the process and then enter **kill *pid*** or, if you know the name of the process, use **killall *programname***.

---

