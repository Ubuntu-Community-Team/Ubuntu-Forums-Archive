---
title: "Gah!  Screen resolution help!"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-06-05
I was messing around in the Xorg config file trying to allow Composite back up -- I made a mistake and saw in the file was a sudo command to upgrade.  I did so and it downloaded and did something. 

Now my screen is set to 1024 x 768 and there isn't the option to go to my screen's higher native resolution!  The option's just disappeared!  

Help.  Everything on my screen is very big.

---

### Post by csixx on 2007-06-05
You can try manually adding your desired resolution by reconfiguring xorg.

From a terminal type:
sudo dpkg-reconfigure xserver-xorg

in one of the steps, you will be asked to select your resolutions.

---

### Post by meborc on 2007-06-05
also read this: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by aberadam on 2007-06-05
csixx, tried that and got to a point I couldn't go past -- it asked me for bus line or something but then gave no option of where to put it. 

Thanks for the link meborc, I tried the ATI-specific one and it didn't work... Or I couldn't get it to...

---

### Post by meborc on 2007-06-05
when doing "sudo dpkg-reconfigure xserver-xorg" you just answer the default answers, when not sure what to say... if you want to leave a line empty, press tab to highlight "OK" and then enter...

hope this helps

---

### Post by aberadam on 2007-06-05
I can't understand those instructions meborc... when I do what they say it just doesn't do what it's supposed to...

---

### Post by meborc on 2007-06-05
you said something about bus line... it should be the default option... just press enter, or if not able to, tab and then enter...

sorry, i probably don't understand where or why can't you go through with the reconfiguring... :)

---

### Post by aberadam on 2007-06-05
I went through the reconfigure: sudo dpkg-reconfigure xserver-xorg

At the point it asks to select resolution there's no way to select!  Just a red cursor that does nothing.  Theo nly thing to do is tab it to OK.

---

### Post by aberadam on 2007-06-05
Ahh, how do I put the asterix into the box?

---

### Post by hashimoto on 2007-06-05
> **aberadam said:**
> Ahh, how do I put the asterix into the box?

Go to box with arrow keys and select/deselect with space bar.

---

### Post by aberadam on 2007-06-05
Haha, thanks!  Selected all the options but I still can't change it in preferences > screen resolution

---

### Post by aberadam on 2007-06-05
OK restarted and it worked,  But ATI drivers are messed up -- screen's moved sideways and Nexuiz no longer works :(

Reinstalling with Envy...

---

### Post by aberadam on 2007-06-05
OK, everything seems to be working as before... but when I try Nexiuz the screen goes blank and the monitor displays a message "out of frequency range."

It worked fine before this. 

Any ideas?

---

