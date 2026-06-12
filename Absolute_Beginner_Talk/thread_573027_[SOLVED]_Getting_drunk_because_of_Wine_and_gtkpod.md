---
title: "[SOLVED] Getting drunk because of Wine and gtkpod"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by ShadowMKII on 2007-10-11
I cannot seem to get either of these to work with me. Could someone please advise? I am using Feisty on an AMD 64 bit type with Swiftweasal installed after a rigorous workout trying to install Java and Flash myself.

When trying to install Wine I get this: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
jordi@Shadow-Slate:~$ 

I cannot get past this point. I am trying to do this so I can run .exe files as well as Snes9x. As for gtkpod, I do not know what the code history is. If someone could show me how to do these through terminal I would greatly appreciate it, as I like to learn new things. Also, if you feel like being particularily generous, I would like to know how to install a driver supported by Ubuntu for my Nvidia 8600gt 256mb video card. Again, that is just a side note and does not need to be answered. You generosity is appreciated.

---

### Post by skipbarker on 2007-10-11
Try System>Administration>Software Sources. Make sure you have Community Maintained and  Software restricted by copyright or legal issues checked. Be sure to run ```
sudo apt-get update
``` afterwards if you change anything.

After you have done this Wine should be available to install.

As for GtkPod I'm not sure what your asking for.

For your Nvidia drivers I highly recommend [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to handle setting up your drivers.

---

### Post by ShadowMKII on 2007-10-12
Thank you for responding! I ran sudo apt-get update as you said I should and I received numerous lines of code in the terminal, which indicated that a lot of stuff was being downloaded. I then tried to run sudo apt-get install wine as previously mentioned, but I got the same error message as before. Do you know what I am doing wrong?

As for the Nvidia driver, I was able to install Envy and updated it perfectly fine! Thank you for your assistance in that matter! Then only thing I have yet to find out is how to get gtkpod to work with my mp3 player and how to get wine.

---

### Post by TedGarvin on 2007-10-12
What happens when you try to use gtkPod?

---

### Post by skipbarker on 2007-10-12
You might try [this]("http://winehq.org/site/download-deb") out to get wine.

---

### Post by ShadowMKII on 2007-10-14
I tried your recommendation for installing wine the alternate way from Wine HQ, and everything seemed to download fine. I will get back to you once I have time to test it out with Snes9x.exe.

As for gtkPod, I cannot even begin to make it install properly. I tried to make it work on the second day I was running Ubuntu, mind you, but it still was a hassle. If you could help me or guide me as to how I could install it from the ground up, I would be very appreciative. 

Also, are any of you experienced in the area of DVD playback? I have gotten very close and have actually ran a DVD movie, but I was having a large amount of trouble accessing the main menu off of Totem. I believe I installed xine and gstreamer, thought I am not sure if I did it correctly or fully based on what I can remember. Again, that is just a side note and does not need to be addressed here.

---

### Post by defrex on 2007-10-14
To install gtkpod:
*sudo apt-get install gtkpod*

Of course, make sure universe and multiverse are turned on in administration>software sources.

And for DVDs, Totem won't give you menus, unfortunately. For menus *sudo apt-get install vlc*. vlc'll do menus.

---

### Post by ShadowMKII on 2007-10-15
Alright, I will try that when I get home from university, which should be in about 4 hours. XD Thank you!

---

### Post by ShadowMKII on 2007-10-17
Well, I am able to locate my iPod and Rhythmbox knows that it is there, but it is unable to play all of the files. I have not tried to extract any, but I know for a fact that m4a files are not supported, whereas mp3's are. Are there any converters that I should get, or any more installations that I should do?

As for vlc, I installed it. The only problem is that though I can view my DVD's fine now, I still cannot access any menus! They just load up and play on their own command. Is there any way around this? Thanks again!

---

### Post by ShadowMKII on 2007-10-17
As for gtkpod, forget about what I said! I got it working through installing codecs with Totem. I did not know that they were transferrable or interchangeable, but now I know! =D Thank your for your help on that! Now, on to the DVD's...

---

### Post by ShadowMKII on 2007-10-18
Nevery mind about all of that, I have solved it! Sorry for being such a bother! Thank you for all of your help and expect to see me again somewhere else on the forums! ^-^

---

