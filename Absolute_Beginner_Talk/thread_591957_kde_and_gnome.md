---
title: "kde and gnome"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by mrukus on 2007-10-25
what is the difference and by switching to kde does all your setting s and drivers you have in gnome tranfer nicley, what baout files and everything

---

### Post by LowSky on 2007-10-25
google is your friend

[http://www.google.com/search?source=ig&hl=en&rlz=&q=kde+vs+gnome&btnG=Google+Search]("http://www.google.com/search?source=ig&hl=en&rlz=&q=kde+vs+gnome&btnG=Google+Search")

---

### Post by thelocust on 2007-10-25
Your setting don't tranfer over and I dont think that your drivers do it is possible (I only switched over once hehe) But your file system stays the same all your doing is adding more files.

---

### Post by mrukus on 2007-10-25
i did a little reading and wanted to try it out. i ran this command line

sudo aptitude install kubuntu-desktop

after that it all went well until the end when i got this error msg

E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/digikamimageplugins/digikamimageplugins_0.9.1-0ubuntu2_i386.deb:](http://us.archive.ubuntu.com/ubuntu/pool/main/d/digikamimageplugins/digikamimageplugins_0.9.1-0ubuntu2_i386.deb:) Error reading from server. Remote end closed connection [IP: 91.189.88.45 80]

what do i do now, or can i start from stratch by undoing whatever was done adn redoing it a different way?

---

### Post by mrukus on 2007-10-26
any suggestions anybody?

---

### Post by taurus on 2007-10-26
You can try to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from your repos.  Save it and then run

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by mrukus on 2007-10-26
no error messages but nothing happened, do i restart and then it will be there???

---

### Post by thelocust on 2007-10-26
do a ```
sudo dpkg --configure -a
``` first and if it says all is good then try to restart and at the log in window there should be options go and change the session to kdm.
 
P.S. could somebody confirm that command I am at work and I'm pretty useless with out my Tab key.

---

### Post by TeaSwigger on 2007-10-26
Don't worry, it's ok. It timed out or something trying to download a package, it happens. Open Synaptic Package Manager. Go to settings > Repositories. On the "download from" selector, pick "other," pick your country, and let it find the fastest mirror. Close it. Then update with sudo apt-get update. Then re-run sudo aptitude install kubuntu-desktop.

---

### Post by mrukus on 2007-10-26
nothing happens with that command i am going to try and just restart it and see if there is an option.

---

### Post by swoll1980 on 2007-10-26
kde on ubuntu doesn't seem to work right for some reason

---

### Post by SunnyRabbiera on 2007-10-26
you can get KDE via synaptic if you are having issues.
both KDE and gnome do about the same thing, its just a shell around a shell that allows you to look at files on your computer.
if you want to switch there is not a lot to worry about, they both work the same roundabout way.

---

### Post by mrukus on 2007-10-26
allright upon reboot, i select to open up ubuntu from the grub menu, and then it says its loading kubuntu, then it has the kubuntu login page, then it starts to load and everything is blue, then an orange ubuntu loading screen comes up, everything turns orange and gnome is loaded

---

### Post by mrukus on 2007-10-26
oh i didn't know that i could do it through synaptic which files do i select?

---

### Post by mrukus on 2007-10-26
tried it through synaptic, same things are happening.  the only difference being now there is no option to turn my computer off, the only options are standby or hibernate
is there a way to start form stratch here, like complete get ride of my gnome files and have te kubuntu files installed without having to completely re format and install again?

---

### Post by mrukus on 2007-10-26
don't want this thread to die, im poised and ready to do anything

---

### Post by thelocust on 2007-10-26
I think you need to disable your automatic login.

---

