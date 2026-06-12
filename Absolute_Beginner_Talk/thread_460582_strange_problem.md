---
title: "strange problem"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Knightstormz on 2007-05-31
When I try to log off or shutdown my pc  I am getting a strange freeze that seems limted to the power button , applications ,places ,and system buttons. The items I have created shortcuts to on my desktop still function properly but I cannot log off or shut down unless I do a hard boot. If I try ctrl+alt+ backspace to restart xserver I am presented with an error that another panel is running and then the computer boots up to a screen with only my added desktop items showing. This only occurs when I click on the red button to log out or shut down the computer.
 Has anyone ever seen this?

---

### Post by starcraft.man on 2007-05-31
Uhhhhhhhh.... Nooooo, that ones never happened to me.

Lets try a few questions... Whats your hardware? Has this been happening every time you push the shut down button ever since you installed onto the HD or just recent? If its just recent what have you modified lately? What graphics card do you have and did you install drivers for it (some people have noticed suspend and close issues I think before drivers in)? Did you have any particular problems when installing that required particular hacks/modifications to certain files?

I think thats good enough for now, answer those... I can't say I ever heard this, if it has been since you installed and you did put in your drivers for your card... I dunno, maybe bad install?

Post back with answers, maybe someone more knowledgeable will have noticed and replied with the right fix and answers won't be needed :p.

---

### Post by Knightstormz on 2007-05-31
Hardware is as follows ,  amd 4200+ x2 , Asus mobo , 2 gigs corsair ram , nvidia 7600 gt oc ,  120 gb  sata hdd    built by me a year ago , no Ubuntu install problems at all . I installed nvidia drivers a few days ago and didnt have this problem untill last night . Ah  , I did install Envy last night so perhaps the problem lies there. I have been having a problem with my resolution and refresh settings not being saved so I  thought maybe if I had an auto driver installer it might solve that problem  . I will remove Envy in a bit and give that a try.

---

### Post by starcraft.man on 2007-05-31
> **Knightstormz said:**
> Hardware is as follows ,  amd 4200+ x2 , Asus mobo , 2 gigs corsair ram , nvidia 7600 gt oc ,  120 gb  sata hdd    built by me a year ago , no Ubuntu install problems at all . I installed nvidia drivers a few days ago and didnt have this problem untill last night . Ah  , I did install Envy last night so perhaps the problem lies there. I have been having a problem with my resolution and refresh settings not being saved so I  thought maybe if I had an auto driver installer it might solve that problem  . I will remove Envy in a bit and give that a try.

Uh, what kinda problems suddenly started happening? Just the shutdown thing and resolution trouble? And why did you install Envy after having installed the Nvidia drivers before, Envy installs the same drivers you know? You did it manually before I assume? 

I uh, don't think installing Envy itself can break anything... the program is just a shell to automatically install drivers. Hmmmm, curious... are you sure you installed the drivers properly the first time? Cuz resolution not staying properly sounds like typical problem when your on regular 2d drivers.... as well as the shutdown kinda (though more I hear that with suspend function for some reason)

---

### Post by Knightstormz on 2007-05-31
there were no other problems when I started having the shutdown prob. I did a manual install on the nvidia drivers before but  I didnt have an option to select 1280x1024 so I wanted to update to the  latest nvidia driver , 9755 I believe.  I am still having the problem with my resolution settings not being saved even with the latest driver and I saved the settings to xserver , however I have only been using Ubuntu/Linux for less than 2 weeks so I am sure its operator error . I do appreciate the effort to steer me straight. I like Ubuntu and I want to learn !!!

---

### Post by starcraft.man on 2007-05-31
> **Knightstormz said:**
> there were no other problems when I started having the shutdown prob. I did a manual install on the nvidia drivers before but  I didnt have an option to select 1280x1024 so I wanted to update to the  latest nvidia driver , 9755 I believe.  I am still having the problem with my resolution settings not being saved even with the latest driver and I saved the settings to xserver , however I have only been using Ubuntu/Linux for less than 2 weeks so I am sure its operator error . I do appreciate the effort to steer me straight. I like Ubuntu and I want to learn !!!

Hmmm, if you manually installed the driver you should have gotten your screen's max resolution right then... you are sure you switched it to the "nvidia"driver in the xorg right? Upgrading to latest build of driver shouldn't really make any difference...

---

### Post by Knightstormz on 2007-05-31
yes , I ran sudo dpkg-reconfigure -phigh xserver-xorg . Nvidia is selected.

---

