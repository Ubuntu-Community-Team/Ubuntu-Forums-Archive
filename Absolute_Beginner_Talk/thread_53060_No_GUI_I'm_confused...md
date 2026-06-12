---
title: "No GUI? I'm confused.."
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by confustrated on 2005-07-30
I would think this question has been asked before but after bout 30 min searching the forums, I can't find the answer. I'm using a G4 cube and I installed Kubuntu for the first time. Now, granted I really know jack about Linux, I was expecting some sort of graphical login after the installation, but alls I get is a command version. The installation went fine, except at the very beginning I had to type in "install video=ofonly" to get it to continue with the installation right. As it is right now, I can login via the command prompt and I get this little new mail message and thats it. Is there some kinda command I'm supposed to know to get into KDE er somethin? I'm clueless, help me out... PLZ   :neutral:

---

### Post by heimo on 2005-07-30
You could try:

 ```

sudo apt-get install kubuntu-desktop
sudo /etc/init.d/kdm start

``` 
First one makes sure that you have kubuntu-desktop (basicly KDE and all the relevant applications) installed, next one starts kdm, graphical login manager, which should start automaticly when kubuntu-desktop is installed. As a normal user, you should get straight to desktop by entering *startx* command on command line (also called shell / console).

---

### Post by aysiu on 2005-07-30
Well, something's clearly wrong. Have you tried typing *startx*?

---

