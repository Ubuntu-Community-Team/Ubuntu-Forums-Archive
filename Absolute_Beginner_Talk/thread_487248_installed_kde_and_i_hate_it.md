---
title: "installed kde and i hate it"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-06-28
i want my gnome back, does anybody know of a way to mass delete? i installed kde-desktop on top of ubuntu so don't worry but if i install gnome-desktop will that take it's place and remove it? 

also, since i installed kde-desktop my shutdown option has disappeared. i click on the power button and all i get is suspend and hibernate. and ideas? like a command?

---

### Post by milton1 on 2007-06-28
installing gnome-desktop will not remove kde. Best option is probably to search for kde in synaptic and choose purge for all the components. this will still leave several programs and libraries, but following up with "sudo apt-get autoremove" will uninstall anything not in use. You wont get rid of everything, but most of it will go. To really get rid of everything kde-related, you may need to do a clean install.

---

### Post by overdrank on 2007-06-28
> **rickycodie said:**
> i want my gnome back, does anybody know of a way to mass delete? i installed kde-desktop on top of ubuntu so don't worry but if i install gnome-desktop will that take it's place and remove it? 

also, since i installed kde-desktop my shutdown option has disappeared. i click on the power button and all i get is suspend and hibernate. and ideas? like a command?

Hi you still should have gnome just logout and then select session and select gnome. And you can make it your default the go to the terminal and use the command ***sudo apt-get remove kubuntu-desktop***

---

### Post by milton1 on 2007-06-28
> **overdrank said:**
> use the command ***sudo apt-get remove kubuntu-desktop***

This will only remove the metapackage. The kde components will remain.

---

### Post by kpkeerthi on 2007-06-28
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by rickycodie on 2007-06-28
thanks, i still need help with the shutdown thing though.

---

### Post by milton1 on 2007-06-28
> **rickycodie said:**
> thanks, i still need help with the shutdown thing though.

Is this problem appearing even in your gnome sessions? Or is it just in kde? If it is just in kde, the problem will go away with kde.

---

### Post by txHarleyMan on 2007-06-28
Here you go:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by rickycodie on 2007-06-28
the shutdown thing occurs only in gnome, i did the psychocats link and thanks, but  it still does it.

---

### Post by sonofusion82 on 2007-06-28
> **rickycodie said:**
> also, since i installed kde-desktop my shutdown option has disappeared. i click on the power button and all i get is suspend and hibernate. and ideas? like a command?

well, I personally like KDE. ;)
So solve your shutdown problem, you can configure the login manager in KDE to allow normal user to shutdown.
[http://docs.kde.org/stable/en/kdebase/kcontrol/kdm/index.html]("http://docs.kde.org/stable/en/kdebase/kcontrol/kdm/index.html")

---

### Post by VanHammersly on 2007-06-28
Click on Control+Alt+Backspace to get to the login screen.  From there you should be able to switch your session from KDE to Gnome.  GDM should still be your login manager.  Just make Gnome default.

---

### Post by rickycodie on 2007-06-28
no no no i must be wording this wrong......i am removing kde completely as a bootable option, if that means completely then fine.


i have no option to shut down in gnome.

---

### Post by greg_g on 2007-06-28
Here is the guide I just finished writing in fact.

[https://help.ubuntu.com/community/FromUbuntuToKubuntu](https://help.ubuntu.com/community/FromUbuntuToKubuntu)

Skip down to the "To Remove Kubuntu-Desktop in Fiesty" part.

Yes, that is the correct list, I just did the same thing, only I made sure to keep track of what packages synaptic installed with kubuntu-desktop.

Good luck,

greg

---

### Post by tarek on 2007-06-28
About the shutdown problem, are you using compiz/beryl?

---

### Post by swoll1980 on 2007-06-28
after you remove kubuntu use 
sudo apt-get autoremove
to remove the 40 or so programs that will be left behind by your kde install/uninstall

---

### Post by swisscow on 2007-06-29
Shutdown command:

```
sudo shutdown now
```


or to reboot

```
sudo shutdown -r now
```


Not actually sure if you need the sudo but it seems to work :D

---

### Post by rickycodie on 2007-06-29
i used the auto remove command and the shut down option came back.

thanks all!

---

### Post by kotek_14 on 2007-06-29
I was fooling around sometime age and removed something recently and lost my "shutdown" option, I just went to terminal/konsole and typed in "sudo halt" and it shutdown and powered off

---

### Post by rickycodie on 2007-06-29
thanks, much easier to remember!

---

