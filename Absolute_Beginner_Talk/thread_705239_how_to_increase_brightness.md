---
title: "how to increase brightness??"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by RAJESHKSV on 2008-02-23
i am using ubuntu gutsy sibbon7.10..everything is ok except brightness.it will be  very low when i am watching any videos(only video will not be visible properly-little bit darkened).i have tried many vidoes and and many  media players...ofcourse no problem with normal screen-its brightness is high..only when watching videos it will be problem..only the video will be dark but remaining screen will be proper...i am unable to enjoy videos..plz help me!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Kosimo on 2008-02-23
> **RAJESHKSV said:**
> i am using ubuntu gutsy sibbon7.10..everything is ok except brightness.it will be  very low when i am watching any videos(only video will not be visible properly-little bit darkened).i have tried many vidoes and and many  media players...ofcourse no problem with normal screen-its brightness is high..only when watching videos it will be problem..only the video will be dark but remaining screen will be proper...i am unable to enjoy videos..plz help me!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Could you please tell us witch videocard are you using?

---

### Post by zakirs on 2008-02-23
hey open with totem player and try preferences ...  there in the videos tab  find options for colour and brightness

---

### Post by sayakb on 2008-02-23
Try this:
Open a terminal and type:
```
sudo apt-get install vlc
```

Note: Do this only if VLC is not installed.

Now open VLC player. Goto settings -> Preferences.
In the preferences window, check the "Advanced options" checkbox at bottom right of the Window. Now in the left panel,expand the "Video" option and click on Output modules. Towards the right side, select "X11 Video Output" in the drop-down menu and press the "Save" button. Exit VLC and restart it. Run your video in VLC.

---

### Post by linux phreak on 2008-02-23
If you are using totem player go to preferences and click default on the video preferences.

---

### Post by RAJESHKSV on 2008-02-23
Thank you very much for your valuable suggestions.As u directed I selected the output module in vlc and it has been improved:)bt wt abt in other players???

---

### Post by montres on 2008-02-23
most players have some means of adjusting brightness, contrast, etc. Some call it "equaliser", some "video options" etc.
In any case, I think VLC will be more than enough for your needs, It's really a very good media player.

---

### Post by sayakb on 2008-02-23
VLC plays almost all media formats except for real media. Get the real player for linux from here:
[www.real.com/linux](www.real.com/linux)

Dave Smith
New Delhi ;)

---

