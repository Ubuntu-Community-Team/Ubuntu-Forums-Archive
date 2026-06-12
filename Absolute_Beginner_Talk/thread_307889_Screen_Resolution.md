---
title: "Screen Resolution"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by zeke67 on 2006-11-27
I am very new to Linux.  I installed Ubuntu on an old computer. Initially it worked fine.  I could change screen settings to 1024x780 without any problem.  
Then I went to play a game and the whole system froze.  Nothing I did could get it to get back to the ubuntu screen so I turned the system off and then rebooted.  When I got back to ubuntu everything worked except I could only increase the screen resolution to 800x600.  I tried installing nvidia drivers from instructions from other posts and now can only get 640x400 resolution!
My graphics card is a Geforce 3 Ti200.  
Should I just reinstall ubuntu or does anyone have any other suggestions?
Thanks!

---

### Post by LLRNR on 2006-11-27
No, don't bother reinstalling... it's not worth it. If you use Dapper, I hope you installed the drivers form [here](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29), otherwise, if you use Edgy, I hope you installed the drivers form [here](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29).

If this is what you did, you can try to reconfigure you X Server. This will modify your xorg.conf file, so better do a backup, just in case:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Then
```
sudo dpkg-reconfigure xserver-xorg
```

You'll get through a series of questions, just answer them as close as you can get and when you're done restart X by hitting Ctrl+Alt+Backspace.

BTW, welcome to Ubuntu ! :)

LLRNR

---

### Post by zeke67 on 2006-11-27
Thanks for responding.  Like I said I am brand new to linux so not sure what dapper is but when I click on your link that was the instructions I followed.
I will try your instructions tonight when I get home. Will keep you posted on what happens.
Thanks!

---

### Post by FreakShow! on 2006-11-27
Hi.

I'm having similar problems. I did the little walkthrough and have been able to up the resolution, but the refresh rate has stayed at 60Hz. I think the issue is me not knowing enough about the refresh rate bit. Am I needing to change horizontal or vertical refresh rate and do they need to change relative to each other?

TIA :)

---

### Post by LLRNR on 2006-11-27
> **FreakShow! said:**
> Hi.

I'm having similar problems. I did the little walkthrough and have been able to up the resolution, but the refresh rate has stayed at 60Hz. I think the issue is me not knowing enough about the refresh rate bit. Am I needing to change horizontal or vertical refresh rate and do they need to change relative to each other?

TIA :)

Hi, 

I haven't had the time to look at [this](https://help.ubuntu.com/community/FixVideoResolutionHowto) throughly, but I think it might be an idea to check it out.

HTH,

LLRNR

---

### Post by zeke67 on 2006-11-28
Well, I went to boot into Ubuntu last night to try the fix mentioned above and got an error that the x-server was disabled and therefore I could not boot into ubuntu.  I then went ahead and did a reinstall.  I can now boot into ubuntu but I am still having problems with the screen resolution.
I can only increase the screen resolution to 1024X768 and 60hz.  
I can look into the info LLNR mentioned in his second post but my other question is whether the the video drivers are installed.  How do you install video drivers? I have a Geforce 3 Ti200.  The other question is whether this card uses nvidia legacy or regular drivers.  I read in two different posts two different answers on this.  I would appreciate any help.  Thanks for the help so far!

---

### Post by twrock on 2006-11-28
Have a look at this thread: [http://www.ubuntuforums.org/showthread.php?t=157235](http://www.ubuntuforums.org/showthread.php?t=157235)

If you haven't yet tried editing your xorg.conf file, I think that is the place to start. Simply adding "1280x1024" to the beginning of each line of resolutions did the trick for me (even before I got the nvidia drivers working). Later I installed the nvidia driver. I have installed the nvidia driver using the instructions available in the Multimedia & Video forum (sticky posts: [http://www.ubuntuforums.org/forumdisplay.php?f=138](http://www.ubuntuforums.org/forumdisplay.php?f=138) ) and using Automatix2. Both methods worked well for me.

---

### Post by jefferson101 on 2006-11-28
I think I'm having a similar problem.  My computer can run at 1280x800, but its currently displaying only 1024x768.  I tried changing the screen resolution via System->Preferences->Screen Resolution, but when I click on the arrows to drop down the menu, nothing happens.  It's like 1024x768 is the only option.  When I open the xorg.conf file, the only resolution that shows up is 1280x800!  Could it be that it is trying to do 1280x800, but can't for some reason, and so it settles for 1024x768?

---

### Post by bubkusjones on 2006-11-28
I'm having the same problems with my Geforce 7900 GT PCI-E. I've tried apt-getting the driver as well as using the most recent version downloaded from the nvidia website.

The thing is, is that I could get 1280*1024 using the default "nv" driver, but I can only get a max of 1024*768 with the accelerated driver.

---

### Post by jefferson101 on 2006-11-28
I was able to fix the 1280x800 resolution very easily using the advise from post 2 of [this post]("http://www.ubuntuforums.org/showthread.php?t=190237"), hopefully it helps someone else here.

---

### Post by bubkusjones on 2006-11-28
Unfortunately, 915resolution only works with Intel graphics chipsets

---

### Post by zeke67 on 2006-11-28
LLNR has it right. If you go to this link: [http://https://help.ubuntu.com/community/FixVideoResolutionHowto]("http://https://help.ubuntu.com/community/FixVideoResolutionHowto") and manually change the refresh rates and resolutions this worked for me.

---

### Post by zeke67 on 2006-11-28
Sorry I messed up the link, here it is again: [https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

### Post by bubkusjones on 2006-11-29
Still no dice for me.

Hell, for some reason, even though I only have 1280*1024 and 1024*768 listed, I still get 800*600 and 640*480 in the menu.

---

