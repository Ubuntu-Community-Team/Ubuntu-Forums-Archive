---
title: "Trying to move to Ubuntu"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by TomParker on 2006-07-27
After all this stupid WGA problems and frequent BSOD's its time to say bye to Windows i've had enough so I ordered my copy of draper got it all installed started playing with it but noticed my screen resolution was at 1024x768 hmmm its abit too big for my liking, so I set out to try and change it I tried following guides and stuff to change the resolution but I really do not have a clue i've managed to kill 3 installs of ubuntu in about 2 days I rea;;y cant see what I am doing wrong!

My monitor is a fairly old large square box thing (Eizo FlexScan F56) running on a Geforce 2 MX, I really don't have a clue what I am supose to be doing i've followed this [http://doc.gwos.org/index.php/ChangeResolution#How_to_edit_xorg.conf_file](http://doc.gwos.org/index.php/ChangeResolution#How_to_edit_xorg.conf_file)

but all I keep doing is killing the xorg.conf file and reinstalling to start all over again :( 

Stuff like this:
```
# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz Modeline 1024x768_75.00" 81.80 1024 1080 1192 1360 768 769 772 802 -HSync +Vsync
```

makes absolutly no sense so I am now going to reinstall my 4th copy of ubuntu, bye :(

- Tom

---

### Post by Paerez on 2006-07-27
There is a much easier way to choose your resolutions. Go to a terminal and type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
(if that doesnt show the resolutions, remove the -phigh)
You can hit enter for anything you don't understand and it will put in the default. At one point, you can put Xs next to the resolutions that you want. Then just restart your xserver and you should be at your top resolution.

Once logged in, you can change your personal resolution from the System->Preferences->Screen Resolution menu item.

---

### Post by rck_hitokiri on 2006-07-27
try this might help you out.. 
console:
sudo dpkg-reconfigure xserver-xorg 
         You can usually safely accept the defaults until you come to the monitor configuration select "medium" not "simple" Doing this allows you to choose a monitor that supports your desired resolution, That should fix it all for you.you can also edit your display properties through here. you can check 800x600 ... etc....

---

### Post by TomParker on 2006-07-27
Yay thats done it! now my next question whats the best msn client which also has webcam functonality?

Thanks guys!

---

