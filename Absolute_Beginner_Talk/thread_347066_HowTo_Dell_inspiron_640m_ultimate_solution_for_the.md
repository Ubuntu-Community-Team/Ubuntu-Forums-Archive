---
title: "HowTo: Dell inspiron 640m ultimate solution for the xserver problem"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Mba7eth on 2007-01-26
Finally i got it worked ;-)  

I have been for two days trying different things to get ubuntu to identifiy my intel 945G graphic card on this dell aspiron laptop.

Any how most of the things here are said elsewhere.
I assume are runnuing the ubuntu 6.10 liveCD and now you are at the prompt:
 
```
$sudo -s
#nano /etc/apt/source.list    > remove every # from every non-comment line. 
#aptitude update
#aptitude install 915resolution
[COLOR="Red"]#startx[/COLOR]

```
now you have the xserver in 1440x900 resolution. install ubuntu. open a shell and type ```
#reboot
``` 
now you'll notice that you have no GUI back to the same point. the same error at the beginning is comming again 8-) 
just the same steps as you performed before installing and reboot then we are done.
:guitar: 
You'll notice that the boot time is longer. I really don't know why ! please if you know why please share it with me . 


Before i used to reconfiger the xserver right after installing the 915resolution and that's what is everybody says.  But it look like that the 915resolution modify the xorg.conf file once it is installed. 
Any how Special thanks to this forum and everybody. I really learned alot about linux and specially ubuntu with only 3 weeks. 
Thanks all again :)

---

