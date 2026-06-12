---
title: "error at boot says&quot;sync out of range&quot;"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by coolnik6 on 2008-02-19
after installing ubuntu 7.10 
when i restart n choose ubuntu to boot 
i get a black screen with a reb n blue box saying **SYNC OUT OF RANGE**
I ALSO HAVE WINDOWS XP
 but when i boot it i dont get such an error
plzzz help me

---

### Post by ashmew2 on 2008-02-19
Try opening up the Recovery Console. Do you know what Refresh Rate your monitor uses ? And which graphic card do you have ? 

Also , look if theres an AUTO button somewhere on your Monitor. Maybe Pressing that could help.Btw , How long have you been using Ubuntu ? Is it your first time ?

---

### Post by coolnik6 on 2008-02-19
i dot know the refresh rate
n i dont have an additional graphic card installed
im using pentium 4 
my monito is samsung  samtron 56v

---

### Post by MikeSz on 2008-02-19
I had the same problem.  When you start up I did this from live CD, hit F6 and enter the following as a boot option...

FB=FALSE VIDEO=VGA16:OFF

Worked for me.

---

### Post by coolnik6 on 2008-02-19
i was using ubuntu 6.10 for almost 6 months
today only i got the cd of 7.10 n hence i installed it
plzz help mee out

---

### Post by coolnik6 on 2008-02-19
i had installed ubuntu 6.10 twice  (liike 6 months back)
but i nver got such an error
only ths time when im using 7.10 im getting this problem

---

### Post by MikeSz on 2008-02-19
I take it you have no problems from the Live CD?  Usually, if the live CD works that suggest that there are no issues with your hardware although it may be worth running through the installation of the Live CD again, though start it up with the command I posted above in the F6 boot options.

---

### Post by pedro_orange on 2008-02-19
Sounds like your monitor cannot display your desktop. If it worked fine from LiveCD I presume this is a xserver-config issue. Try the following:

Press: <Ctrl + Alt + F2> when you get the out of range message.

This should bring you to a command-line interface.
Then after you've logged in enter the following command:

```
sudo dpkg-reconfigure xserver-xorg
```

Follow the onscreen steps. Ensure that when you are told to select resolutions you select ones that your monitor can display.
If this does not work, you can try booting in safe graphics mode and seeing if that lets you in.

---

### Post by SteveHillier on 2008-02-19
I had a similar situation on a recent installation at some of the higher resolutions.  I was not concerned as this is going to be a server long term but because i wanted it for other purposes I swapped the monitor and the old CRT one on that machine now works fine at higher resolutions.
This may not be a solution available to you so it may not help but as it sorted out my problem I shall probably not spend any more time investigating it.

---

### Post by erginemr on 2008-02-19
> **coolnik6 said:**
> after installing ubuntu 7.10 
when i restart n choose ubuntu to boot 
i get a black screen with a reb n blue box saying **SYNC OUT OF RANGE**
I ALSO HAVE WINDOWS XP
 but when i boot it i dont get such an error
plzzz help me

Normally, you should be able to reach the login screen after 1-2 minutes of waiting. If so, then try my howto:
[http://ubuntuforums.org/showthread.php?t=700673](http://ubuntuforums.org/showthread.php?t=700673)

Otherwise, load into the recovery console from the Grub menu and follow the same steps above, but use **nano **(as the text editor) instead of **gedit **(gnome editor) to edit the config file.

---

### Post by philinux on 2008-02-19
Install then run startupmanager it will sort this out from it's GUI.

---

