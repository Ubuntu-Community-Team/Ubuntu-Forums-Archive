---
title: "Making nVidia settings as default"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by corowakid on 2007-09-25
Hi all,

I used Alberto Milone's website to get my nVidia GEForce 6200-256 card installed. I then used the nVidia menu item in Ubuntu to set the resolution of the monitor to 1680x1050. So far, so good. I used "Apply" on the menu screen, assuming it would make the default 1680x1050 at bootup, but I now find that each time I boot up the screen resolution comes in at 1024x768. I can make the changes in the nVidia menu, and the system reboots at the correct settings of 1680x1050.

Can anyone advise on how to get the system to recognise the default as 180x1050? I assume it might have to do with the XConfig file (?). Have used the Terminal, but still a newbie at Linux..

Any advice really appreciated.

---

### Post by RomeReactor on 2007-09-25
Hi. That probably happened because you ran nvidia-settings as a normal user; to make sure the changes are saved (so they don't disappear after a reboot) run the command using sudo:
```
gksudo nvidia-settings
```
and make the changes; this time the system should keep them.

---

### Post by corowakid on 2007-09-25
> **RomeReactor said:**
> Hi. That probably happened because you ran nvidia-settings as a normal user; to make sure the changes are saved (so they don't disappear after a reboot) run the command using sudo:
```
gksudo nvidia-settings
```
and make the changes; this time the system should keep them.

Thanks for response. I did the settings in the nvidia GUI from the "Accessories" menu. This was installed as part of Alberto Milone's guides for installing nvidia cards.

Could you tell me the command to open the nvidia-settings file so I can see if the settings for the resolution are there (any idea what they look like?). Then I assume I use the gksudo nvidia-settings command (?).

Would appreciate a little more assistance. Thanks

---

### Post by RomeReactor on 2007-09-25
Yes, run the **gksudo nvidia-settings** command, and change the resolution as you did previously. As I said, after you make the changes this time, the settings *should* be there even after you reboot or shut down again.

Or you could use "System->Preferences->Screen Resolution" if your desired resolution appears there.

---

### Post by corowakid on 2007-09-25
> **RomeReactor said:**
> Yes, run the **gksudo nvidia-settings** command, and change the resolution as you did previously. As I said, after you make the changes this time, the settings *should* be there even after you reboot or shut down again.

Or you could use "System->Preferences->Screen Resolution" if your desired resolution appears there.

Thanks for that. I'm going to do the command line thing now. Thought I might mention that the System>Preferences>Screen Resolution fix didn't work - maximum resolution shown is 1024x768. Any clues how I might fix that? (assuming the changing the file doesn't do it?)

Thanks for prompt response

---

### Post by RomeReactor on 2007-09-25
When a resolution that I know is supported doesn't show up in "System->Preferences->Screen Resolution", I just use nvidia settings. As for adding that resolution to the resolution utility in preferences, sometimes manually modifying xorg.conf and adding refresh rates and modelines does the trick; however, I recommend you use nvidia-settings if that works for you. The less you manually alter xorg.conf at this stage, the better (in my opinion).

---

### Post by CaptainInsaneO on 2007-09-25
To make your nVidia settings stick each time you boot, do what I did to fix the same problem:

Go to System>Preferences>Sessions

Make a new startup program, name it nVidia Settings Autostart. For the command, it is ```
nvidia-settings -l
```. Save and restart X (Ctrl+Alt+Backspace) and presto, your settings are stuck like glue!:guitar:

---

### Post by corowakid on 2007-09-26
> **RomeReactor said:**
> Yes, run the **gksudo nvidia-settings** command, and change the resolution as you did previously. As I said, after you make the changes this time, the settings *should* be there even after you reboot or shut down again.

Or you could use "System->Preferences->Screen Resolution" if your desired resolution appears there.

Right again! I used the terminal, entered the command and got what looked like the System > Preferences> Screen resolution GUI menu. It showed the 1680x1050 settings already - I clicked on Save to X.org file, then Quit, did Ctrl-Alt-Backspace, and it came back as 1680x1050. thanks a lot.

---

