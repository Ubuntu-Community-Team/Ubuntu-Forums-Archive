---
title: "Screen issue after login"
date: 2009-03-21
forum: Apple Hardware Users
---

### Post by alien0101 on 2009-03-21
I have installed Ubuntu 8.10 on VirtualBox on MacOSX 10.6. It was working fine few days back. Now I am having issue. It boots fine , I can see login screen.
After entering username and password I can login. After the I can see desktop icons also. But soon after that screen goes weird . I cannot see anything on desktop. I am not sure what happened wrong. Any suggestions to resolve this.?
Screenshot is at location :[http://imagebin.ca/view/WeR2_i.html](http://imagebin.ca/view/WeR2_i.html)

Is it possible to restore screen settings?

I dont want to reinstall as it contains important stuff and it will take lot of time to configure it again.

I am not sure what could be the reason. Is it possible that this is due to image corruption?

---

### Post by cyberdork33 on 2009-03-21
when the VM is booted up, use CTRL+ALT+F1 to change to switch to a console. You can edit config files and such from there. If you have the same graphics issue when at the console, then it might just be a problem with VirtualBox or it's settings. If not, then you need to change the xorg driver.

---

### Post by alien0101 on 2009-03-22
I am able to go to console and it works fine but I dont have any idea how to configure xorg driver. 

Can you give some pointers?

My concern here is it works fine before login. I can see login screen and also desktop icons after logging in.
I think after logging in it initializes some new settings that causes this screen.

---

### Post by cyberdork33 on 2009-03-22
> **alien0101 said:**
> I am able to go to console and it works fine but I dont have any idea how to configure xorg driver. 

Can you give some pointers?

My concern here is it works fine before login. I can see login screen and also desktop icons after logging in.
I think after logging in it initializes some new settings that causes this screen.
maybe it is trying to enable the desktop effects.

edit your xorg.conf to use the fbdev driver temporarily and you should be able to get to a desktop at least.

---

### Post by ronocdh on 2009-03-22
> **alien0101 said:**
> I am able to go to console and it works fine but I dont have any idea how to configure xorg driver. 

Can you give some pointers?

My concern here is it works fine before login. I can see login screen and also desktop icons after logging in.
I think after logging in it initializes some new settings that causes this screen.
The command **sudo dpkg-reconfigure -phigh xserver-xorg** will generally set things right by auto-correcting your xorg.conf. It'll even make a backup, too, should things go wrong.

---

### Post by alien0101 on 2009-03-23
Hello 

I tried this and its still not working. I have attached image of xorg.conf file.

Are there any files that I can delete so that when I login again my desktop settings get restored?

Like xsession , setting specific to user , something like that.

I think this should be easy but I am not very expert.

---

### Post by cyberdork33 on 2009-03-23
In the device section, add:
```
Driver    "fbdev"
```

then try again.

I think the issue might be that compiz is trying to start and is not quite working correctly.

---

### Post by alien0101 on 2009-03-23
I just did that 

Adding Driver  "fbdev" to device section of xorg.conf
and restarted but it didn't work.

This time it was not able to go to GUI mode.

Do I need to do something after adding "fbdev"

Any idea if I can disable compiz

---

### Post by cyberdork33 on 2009-03-23
> **alien0101 said:**
> I just did that 

Adding Driver  "fbdev" to device section of xorg.conf
and restarted but it didn't work.

This time it was not able to go to GUI mode.

Do I need to do something after adding "fbdev"

Any idea if I can disable compiz
no. fbdev is the framebuffer driver. If it is not working, then vbox doesn't support it, and I don't know what to tell you.

Have you tried to install the Vm tools?

---

### Post by alien0101 on 2009-03-23
Okay, I found the solution.

I deleted the .kde folder in home directory and restarted again.


Its working fine.The issue was in user profile files.:)

---

