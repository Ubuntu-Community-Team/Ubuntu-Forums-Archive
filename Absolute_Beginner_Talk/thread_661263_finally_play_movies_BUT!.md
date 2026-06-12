---
title: "finally play movies BUT!"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by maineman2 on 2008-01-07
I can finally play movies after trying 3 times to get the software loaded I finally found an easy way to do it here   [http://ibeentoubuntu.blogspot.com/2007/10/worried-about-how-to-play](http://ibeentoubuntu.blogspot.com/2007/10/worried-about-how-to-play)
 It was real easy but now when I try to play the  movie extras disc i get the message could not demultiplex stream does not have the appropriate plugin then when  I click on it it takes me to a list of plugins any help would be great Thanks Dan

---

### Post by RomeReactor on 2008-01-07
Hi. What program are you using to watch DVDs? Try totem-xine:
```
sudo apt-get install totem-xine libxine1 libxine1-gnome libxine1-ffmpeg
```

---

### Post by maineman2 on 2008-01-07
Im using Totem movie player Dan

---

### Post by houstonbofh on 2008-01-07
I use ogle GUI to play movies.  Full functionality and menus.

---

### Post by RomeReactor on 2008-01-07
If you're using totem-gstreamer (the default), try switching to totem-xine (see above).

---

### Post by maineman2 on 2008-01-07
I started to download the plugins after I entered my password the program started to download then seemed to stop after awhile at my dell name and a prompt  any help


              Thanks Dan

---

### Post by maineman2 on 2008-01-07
The totem xine file seemed to have stopped and I accidenally closed the terminal window now when I try to download the files again I cant type in my password at the prompt Thanks Dan

---

### Post by maineman2 on 2008-01-07
Now when I play the extras dvd it starts to play then stops and says are you trying to playdvd without libdvdcss Thanks Dan

---

### Post by RomeReactor on 2008-01-07
Is your internet connection working properly? are you able to browse? do you get error messages in the terminal when trying to install the packages? when you say that you can't enter your password, do you mean that it appears that it is not being written, or you get an error?

---

### Post by maineman2 on 2008-01-07
I restated and now am able to type into the terminal what do I do at this point


Reading package lists... Done
Building dependency tree       
Reading state information... Done
totem-xine is already the newest version.
libxine1 is already the newest version.
libxine1-gnome is already the newest version.
libxine1-ffmpeg is already the newest version.
The following packages were automatically installed and are no longer required:
  libsdl-net1.2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
medan@dell:~$

---

### Post by RomeReactor on 2008-01-07
You already have the packages installed. Does the DVD still show the error message when you try to watch the extras?

---

### Post by maineman2 on 2008-01-07
yes it says the source seems to be encrypted and cant be read are you trying to play an encrypteddvd without libdvdcss It starts to play then stops

---

### Post by chandru.in on 2008-01-07
Intalling gstreamer plugins worked for me without having to switch to xine.  Look at these packages,

gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

---

### Post by suomalainen on 2008-01-07
I like Automatix [http://www.getautomatix.com/](http://www.getautomatix.com/) 

When I install it then everythnig works for me.

I think it's magic....

---

### Post by RomeReactor on 2008-01-07
Make sure these packages are installed:
```
sudo apt-get install libdvdnav4 libdvdread3 libdvdplay0
```
afterwards, run the following:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by suomalainen on 2008-01-07
I use a AUTOMATIX [http://www.getautomatix.com/](http://www.getautomatix.com/) and then all my problems/issues seem to disappear.

---

### Post by maineman2 on 2008-01-07
now i get couldnt find package libdvdplayo Dan

---

### Post by chandru.in on 2008-01-07
it is dvdplay0 [zero].

---

### Post by maineman2 on 2008-01-07
It plays now thanks Dan Where dose it say where the totem player controls are? Thanks dan

---

### Post by RomeReactor on 2008-01-07
> **maineman2 said:**
> It plays now thanks Dan Where dose it say where the totem player controls are? Thanks dan

I'm not sure what you mean by this; is totem not displaying the controls?

---

### Post by maineman2 on 2008-01-07
I cant seem to figure out how to scroll across the screen to choose chapters or start the movie im stuck watching the title screen

---

### Post by maineman2 on 2008-01-07
I got it figured out Thanks for all your help

---

