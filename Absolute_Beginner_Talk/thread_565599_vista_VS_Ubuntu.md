---
title: "vista VS Ubuntu"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by fung1223 on 2007-10-02
Hi all, I have just installed Ubuntu a month ago. I really learn a lots from just this few month. I am very enjoy the apt-get funtion!!! But, what I am facing is my current job is using native WindowsXP + vista.... so...I still thinking of changing back to Windows Vista or not. As I need to work at home most of the time, but some function can not perform in Linux..
1) Change to Exchnage server- I have tried Evolution for Exchnage but not success. It ask me to install a connector on exchange server...but... I am not the admin of exchange server..

2) the format of Outlook web access in Firefox is changed a lots and very difficult to use

Actually, the reason why I use ubuntu without dual boot is I would like to push myself to use linux..... try my very best to fix the problem on my own. Lucky, I have fixed severl problem form net and quite happy on it, such like:

1) VPN
2) connect AP with WPA
3) Beryl

But, there is some pending problem that no fixed yet:
1) Firefox display chinese fonts is very ugly
2) can not play *.mov file
3) can not change the icon

I just would like to know any recommendation from you, In my situation, will you change back to Vista???I am really massing on this issue

---

### Post by dca on 2007-10-02
I hate to say this but it sounds like you need two systems.  One configured to do your job with and one to fiddle with at your leisure until you get used to it.  I know on my Ubuntu installs, I had to install the 'mstcorefonts' package to get my firefox to look the way I like it versus the default look after Ubuntu install.  The other thing is the installation of proprietary codecs to get the DVD video and other media files to play.  That can be done by using the Applications -> Add/remove function, then selecting 'all' then activating 'all available applications/repos' from the drop-down menu.  Look for 'gstreamer'...

---

### Post by Incense on 2007-10-02
You may want to also consider a virtualization solution like Virtual Box or VMWare to run windows inside of Ubuntu. I use virtual box to run win2K for some school apps I can't get working on Ubuntu, and it's fantastic. The new seamless mode makes it feel like your running native linux apps.You can then run IE and Outlook web access looks and runs much better then in firefox.

---

### Post by sdowney717 on 2007-10-02
I use mplayer and mplayer plugin for mov video.

A test site is apple movietrailers.
[http://www.apple.com/trailers/](http://www.apple.com/trailers/)

---

### Post by rjs82vette on 2007-10-02
Install virtual box and run windows XP/vista, unless you need video this works for the limited windows access that I need.

---

### Post by mivo on 2007-10-02
I ditched Windows completely, but I only really need one Windows application for my job, and it fortunately works flawlessly in Wine. In your case, I think you may have to dual-boot for work reasons. It is not a perfect solution, but I think in time there will be better solutions. Just bridge over the time with dual-booting. It is hard to get back to Windows if you experienced something like the Debian packaging system / apt-get, and the snappy performance of Ubuntu. :)

You could also talk to your administrator at work, perhaps they can install what is needed for Evolution to work better. As for the Chinese font in Firefox, I have to try this. I only need the Japanese font and it doesn't really look different than in Windows.

---

### Post by vinutux on 2007-10-02
for problem 2 go to add/remove programs and find gstreamer plugins check and install all gstreamer plugins           now u can view .mov files or any of the commonly used media files 

if it is not work ty alternative apps like vlc ,mplayer or xine


 ....................................

for changing icons and theames go to System-->Preferences--->theam
and change whatever u want

...............................................

for first problem try to change encoding settings in firefox or inststall correct fonts ...........

:guitar:

---

### Post by LetThereBeRawk on 2007-10-02
I am pretty new to Linux myself, and I followed the sticky here in the beginner forum to get Ubuntu to play well with multimedia.

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

To connect to a wireless network or access point using WPA, install the wpa-supplicant package. If you're running 6.06 or earlier maybe try the following HowTo. By the way, it's installed by default in my Ubuntu 7.04.

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

No experience with Beryl here and I've learned to live with Firefox's display quirks.

---

