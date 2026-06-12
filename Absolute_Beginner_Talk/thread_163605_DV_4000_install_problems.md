---
title: "DV 4000 install problems"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by jbcoder on 2006-04-21
I just tried to install the Dapper Flight 6 on my DV4000 laptop. Installation went without problems, but now, when I boot up, as soon as it gets to the login screen, the display goes black and looks like it turns off. I think that I may have selected the wrong screen resolution when I installed it. I don't know if thats the problem though. 

Is there any way to change the resolution via a text only log in? I've heard that there is a way to get to a text login, but I don't know how to. 

This is my first appempt at linux, so please be as descriptive as possible. 

Thanks!

---

### Post by st0kes on 2006-04-21
From your black screen, you can press ctrl+alt+f1 to bring up a login prompt. Log in, and then try: 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You can then reconfigure your monitor with a new resolution. 

After you exit from the config program, you can press ctrl+alt+backspace to restart the X server (this will try to load the graphical logon page again using your new settings).

---

### Post by jbcoder on 2006-04-23
Thanks, I got the logon screen to show up now, but the highest resolution is 1024x768. I have a widescreen laptop (res: 1280x800) and can't seem to get it to that resolution. I've tried changing/adding a "modeline" in the xorg.conf file. Any other ideas?

---

