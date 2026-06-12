---
title: "Assorted Issues and Quirks with 12.10 on a MacBook Pro 8,2 (and paranoia)"
date: 2013-02-21
forum: Apple Hardware Users
---

### Post by tm222 on 2013-02-21
Hello there! I am currently running Ubuntu 12.10 on a 15-inch MacBook Pro (the Early 2011 model, aka "8,2"). I absolutely love Ubuntu on my Macbook, but I have been experiencing some issues and noticing little quirks. Firstly, when I click on the Dash icon and it opens to the "Home" tab, nothing shows up in the area of the Dash which usually shows content. Could this because of my "Privacy" settings, with the recording of activities disabled? Usually at least some recent applications/files are shown. [s]Secondly, when I boot up, the keyboard backlight and screen brightness are always set at the maximum, even though my /etc/rc.local contains lines which are supposed to prevent this. My rc.local is attached. Thirdly, sometimes my WiFi suddenly ceases to work, and requires me to disconnect and reconnect. Is there a known issue with the driver, or is there a fix for this issue?[/s] And to conclude this paragraph/section, a question about battery life. I installed cpufreq and am often using the "ondemand" governor. Should I be using "powersave", or is there not too much of a difference? Also, is there anything else I should be doing to improve my battery life?

Now forth into the paranoia. While installing Ubuntu, I had to turn off FileVault and let it decrypt my drive so I could shrink my OS X partition and make a new one for Ubuntu. I haven't encrypted it again because I wanted to be able to access this partition read-only from Ubuntu (for at least a bit). I'm assuming that there is no support for encrypted HFS+ volumes yet (and there probably won't be), is this correct? Also, is it possible for me to encrypt my entire Ubuntu partition after the installation, or would I have to reinstall? I also use a VPN (with DNS leak prevention) on both OS X and Ubuntu. What should I be doing to ensure full security and privacy from within Ubuntu? I went through the "Privacy" settings pane and changed whatever I could to achieve the most privacy (to me), but is there any guideline or anything for what I should be doing to ensure the MOST privacy?

Thank you very much for your help, and I am very sorry for the long post with all of the questions.

EDIT: I have fixed the issues with screen brightness and keyboard backlight. I will be uploading my new rc.local soon for anyone that is interested. Also, it seems that my WiFi issues are gone.

---

