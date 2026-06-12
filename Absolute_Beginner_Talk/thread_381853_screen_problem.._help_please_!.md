---
title: "screen problem.. help please ?!"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-11
you guys rock, very supportive.. i need one more help.. i just switched to ubuntu yesterday.. my screen is so stretched out vertically.. how do i fix it.. i used to have xp.. it was clear and fixed.. can any one help me please

---

### Post by Kobalt on 2007-03-11
> **HunkieChan said:**
> my screen is so stretched out vertically.. 
What do you mean exactly, is it a problem of resolution ?

---

### Post by HunkieChan on 2007-03-11
> **Kobalt said:**
> What do you mean exactly, is it a problem of resolution ?

i guess it is.. like for example.. the pictures.. it looks bad.. seems some one is stretching it.. its not normal .. like i was used to..is there anyway i can fix it

---

### Post by Kobalt on 2007-03-11
Yes there is : you should know which resolution you want your screen to have. When you know it, check if it's avaliable in System > Pref. > Screen Resolution and select it if it's present. If you can't pick the resolution you want (if it's not in the list), open up a Terminal (Applications > Accessories > Terminal) and enter this command line : 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want to be able to pick **by pressing the spacebar**, then quit with Enter. Finally, restart your X server with Ctrl+Alt+Backspace, and voilà :) 
Your resolutions will now be avaliable in the list...

---

### Post by HunkieChan on 2007-03-11
any one ?

---

### Post by HunkieChan on 2007-03-11
> **Kobalt said:**
> Yes there is : you should know which resolution you want your screen to have. When you know it, check if it's avaliable in System > Pref. > Screen Resolution and select it if it's present. If you can't pick the resolution you want (if it's not in the list), open up a Terminal (Applications > Accessories > Terminal) and enter this command line : 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want to be able to pick **by pressing the spacebar**, then quit with Enter. Finally, restart your X server with Ctrl+Alt+Backspace, and voilà :) 
Your resolutions will now be avaliable in the list...

 thanks a lot.. hey on a side note.. before whenever.. i pressed cntrl alt backspace... it took me to a black screen... how do i get out of a black screen ? thankx

---

### Post by HunkieChan on 2007-03-11
[[IMG]http://img504.imageshack.us/img504/2602/screenshotog9.th.png[/IMG]](http://img504.imageshack.us/my.php?image=screenshotog9.png)

thats what it says ..what do i do now ?

---

### Post by HunkieChan on 2007-03-11
oh now it worked... thanks bro.. okay i have another problem.. when i try to minimize a page.. it leaves a trail behind of black square boxes.. staring from big to small.. how do i get rid of it ?

---

### Post by Kobalt on 2007-03-11
Well it seems your actual screen resolution is to small to go get the Terminal to display properly : to avoid this, write down the command lines I gave you then in a Terminal enter :
```
sudo /etc/init.d/gdm stop
```
Log in if it asks you so. 
This will get you to a non graphical terminal (in a way...) from which you will enter the commands I gave you before. 
And once you've validated, enter this command line to get back to the graphical login screen.
```
sudo /etc/init.d/gdm start
```

---

### Post by Kobalt on 2007-03-11
Ok so forget about my previous post :)
I think you will need to install the proper drivers for your graphic card : which one is it ?

---

### Post by HunkieChan on 2007-03-11
> **Kobalt said:**
> Ok so forget about my previous post :)
I think you will need to install the proper drivers for your graphic card : which one is it ?

as far as i remember.. its nvidia.. is there anyway i can check it ???.. i used to have problem with it.. my screen used to lag whenever i scrolled. but someone told me reinstall and gave me direction from here.. and it was fixed.. but the minimize .. it still frustrates me

---

### Post by HunkieChan on 2007-03-11
bro where did you go ?

---

### Post by HunkieChan on 2007-03-11
any one ? please help me

---

