---
title: "How do I enable audio from Flash player?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by baylorbear on 2006-08-15
My network has been if-y at best the past couple of days... sorry if this is a duplicate :(

I'm trying to figure out how to get sound to work from flash files playing in Firefox.  Sound on everything else works just fine...  any suggestions?

---

### Post by basilwatson on 2006-08-15
Same problem . anyone help with this . I have installed BUMP and everything else seems to work 

Stephen

---

### Post by gerbman on 2006-08-15
Try installing the 'alsa-oss' package. Fixed the same problem for me.

---

### Post by baylorbear on 2006-08-15
Tried that but still won't play any sound.  :(

---

### Post by mcneely.mike on 2006-08-15
try installing gstreamer0.8-swfdec
??

---

### Post by niallabrown on 2006-08-16
I hope this isnt too nieve being a newbie, but I found that EASY UBUNTU fixed a lot of problems for me regarding flash, video and audio playback.  It can be found at: [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

You just paste the text it provides you in the terminal, put in your pass, then you just tick what you want it to install.... Easy enough even I can do it.

---

### Post by 3rdalbum on 2006-08-16
Try installing the "esound-clients" package, then run Firefox by using the following command:

```
esddsp firefox &
```

If that doesn't work, try turning off ESD in the Sound control panel and restarting Firefox, or try turning off all other programs that are likely to use sound (including GAIM and Skype)

---

### Post by baylorbear on 2006-08-16
I've was playing around and loaded firefox from the shell with "aoss firefox" and it worked.  While I can change the icon in the gnome panel to make it load aoss at every click, it's not a perm. fix. 

Any ideas what this means or how to give a permanent fix?


Thanks!!!

---

### Post by wh0rd on 2006-08-16
1. Install **alsa-oss**:
> sudo apt-get install alsa-oss

2. Edit **firefoxrc**:
```

gksu gedit /etc/firefox/firefoxrc

*(Changing it to: FIREFOX_DSP="aoss")*

```

::Happy Ubuntuing::;)

---

### Post by baylorbear on 2006-08-16
> **wh0rd said:**
> 1. Install **alsa-oss**:


2. Edit **firefoxrc**:
```

gksu gedit /etc/firefox/firefoxrc

*(Changing it to: FIREFOX_DSP="aoss")*

```

::Happy Ubuntuing::;)

Fixed it -- Thank you!!!

---

### Post by DrMilo on 2006-08-25
> **wh0rd said:**
> 1. Install **alsa-oss**:


2. Edit **firefoxrc**:
```

gksu gedit /etc/firefox/firefoxrc

*(Changing it to: FIREFOX_DSP="aoss")*

```

::Happy Ubuntuing::;)



I've tried several things but they didn't work. This worked. Thank you!

---

### Post by DrMilo on 2008-04-04
And then with a new computer and many hours of frustration later I found the solution again! Thanks again!

---

### Post by DrMilo on 2008-04-04
And here's something else worth noting. By doing this I have solved a number of sound problems with many other  applications and files.Audio, video, movie player and Rhythrmbox.

I wonder how many posts and threads on here to do with sound problems are to do with this simple problem?

---

