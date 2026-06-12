---
title: "URGENT!!! I think I might have broke my GUI, can someone help me please"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by thecomputingexpert on 2007-07-23
Hi, I need some help I am a newbie to Ubuntu but wanted to change my resolution to something better so i followed this post: [http://ubuntuforums.org/showthread.php?t=507007](http://ubuntuforums.org/showthread.php?t=507007)

So I used this:
sudo dpkg-reconfigure -phigh xserver-xorg

I then checked a couple of resolutions that were higher than the 1024x768 one and then restarted the server.

It tried to log into the GUI and then it loaded a message saying Failed to start the X server. It is likely that it is not set up correctly.

I have then tried to do the sudo dpkg-reconfigure -phigh xserver-xorg and change the resolutions but it didnt work, i have also tried sudo dpkg-reconfigure xserver-xorg but after answering all the question as well as I can, it still fails to load. I stupidly didnt back up my configuration file so im... well a bit buggered now and i really need to use the computer as soon as possible.

Thank you in advance to any help given

My graphics card if it helps is an Intel GMA 950

---

### Post by thecomputingexpert on 2007-07-23
SORTED

I used my Live CD version of Ubuntu and copied the text of the file located at /etc/X11/xorg.conf on the CD and then pasted it into the /etc/X11/xorg.conf on the hard drive where it installed. I did however have to edit it in the terminal because the file was locked so i used sudo nano [disk]/etc/X11/xorg.conf and deleted the contents of the file and pasted the contents on the live CD version into the file. Rebooted and i was back to my old Ubuntu. Thank God

---

### Post by Jon@bayleys.org.uk on 2007-07-23
Silly question I know, but which driver are you using? Ctrl, alt and F1 will ,kill your xserver, and bring you back to a commandline, if all else fails, when you run dpkg-reconfigure xserver-xorg, select vesa as the driver, at least you can get your desktop back and start again. From there, check the forum for the release of ubuntu you're using, versus your hardware, and find out what driver you should be using, secondly, check that your monitor can support the resolution you want at the refresh rate you want. For example, many slightly older laptops won't support a resolution of 1024x768 at 60 hz. Good luck! Also, if you go and have a look at /var/log/Xorg.0.log at the end of it, it should tell you what's gone wrong, if you copy what the problem is into the forum, then chances are that a lot of people on the site can help you.

---

