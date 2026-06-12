---
title: "can't adjust my video setting"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by bonjun on 2005-08-17
i have an nvidia 16mb video card (Vanta),, ubuntu detected it but it has only 800x600 setting as maximum and I can't adjust the setting to a higher resolution, please help...

---

### Post by rmrf on 2005-08-17
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf

In this file, there is a section called "Screen". This is a sample of that section:

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation Vanta, etc, etc."
        Monitor         "<YOUR MONITOR>"
        DefaultDepth    24
SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

As you can see, there are subsections of "Screen" called "Display". There is a seperate subsection for each depth, including the resolution that certain depth can handle. Based whatever settings you've had it at before, just enter them into this file (after making the backup using the command above). Afaik, when you set a default depth, it automatically uses the highest resolution, or "mode" available. So just make sure the default color depth is set, and then enter the resolution you want to use.

Once you have your resolutions set, you can go to 'System -> Preferences -> Screen Resolution' for a gui to change your resolution settings.

hope this helps :cool:

---

### Post by heimo on 2005-08-17
Pointers:
[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by rmrf on 2005-08-17
heh, I guess *I* should have done a search.

---

### Post by heimo on 2005-08-17
[QUOTE=rmrf]heh, I guess *I* should have done a search.[/QUOTE]

Oh, not directed at your good advice at all. Your instructions are to the point and appreciated - but of course the best thing would be if original poster would have found these instructions easier - especially to the wiki pages. On another thought: best would be if these problems didn't exist in the first place, let's hope next release, Breezy Badger, will fix this. Very common problem.

---

### Post by rmrf on 2005-08-17
I agree, these are the types of problems that put a bad taste in the mouth of non-regular linux users. I have come to live with the fact that after installing **any** OS, you are going to need to tweak it a little. This is just one of those things I "programmed" myself to do after an install (not that I need to reinstall that often ;))

I am still on Hoary, and haven't made the jump to Breezy Badger testing yet. Is it good enough for an experienced user to make the jump, or would you wait until a more official release it out?

---

### Post by heimo on 2005-08-17
[QUOTE=rmrf]
I am still on Hoary, and haven't made the jump to Breezy Badger testing yet. Is it good enough for an experienced user to make the jump, or would you wait until a more official release it out?[/QUOTE]

It's getting better. Definitely not for newbies or avarage users, but for experienced user with knowledge of shell, apt-get and dpkg - it's fun. I'm using it as my main desktop at home, made a fresh Breezy install lately from 13th August install CDs and with minor tweaks it was perfectly usable. It's getting better every day. One important milestone, X modularization should be already over (state: implemented): [https://wiki.ubuntu.com/BreezyGoals](https://wiki.ubuntu.com/BreezyGoals)

---

### Post by bonjun on 2005-08-18
[QUOTE=rmrf]heh, I guess *I* should have done a search.[/QUOTE]

allow me to say this,,,:)

thanks guys for the help....

---

