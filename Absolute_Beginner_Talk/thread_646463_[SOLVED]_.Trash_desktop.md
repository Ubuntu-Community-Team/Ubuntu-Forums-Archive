---
title: "[SOLVED] .Trash desktop"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2007-12-21
I have installed a second copy of 'Gutsy' on a slave drive. For some reason the desktop shows up as .Trash Desktop in File browser, and will also not accept paste or drag/drop onto it. The screenshots attached show the file browser showing (.trash)(desktop), the second one shows the error logo when attaempting to paste something onto the desktop.
Weird EH! Can someone help out with this problem.
Thanks and regards
** apologies for not reducing the second screenshot.

---

### Post by mmcmonster on 2007-12-21
Kind of strange.

Try this:
```
sudo mv ~/.Trash/Desktop ~/
```

---

### Post by Sbarton on 2007-12-21
Thanks for your reply mmcmonster, however it was not successful. I have attached a screenshot with the result.
Now strangely I have found a FOLDER called Desktop which seems to be the real Desktop.
Now if I save to the Desktop it will appear in this folder. Weird eh!
I have attached a screenshot of this as well.
Any other suggestions?
regards

---

### Post by Sbarton on 2007-12-21
Seems I attached the same screenshot twice. The other one is below.
regards

---

### Post by mmcmonster on 2007-12-21
Maybe one of these is a symbolic link or hard link?
What does this look like?
```
ls -l ~/ | grep Desktop && ls -l ~/.Trash | grep Desktop
```

---

### Post by mmcmonster on 2007-12-21
You may also want to take a look at [this]("http://ubuntuforums.org/showthread.php?t=373057") thread.

---

### Post by Sbarton on 2007-12-21
This is the output!See attachment
regards

---

### Post by Sbarton on 2007-12-21
Hi! having tried both suggestions none seem to be the answer. Pity!!
It seems that if I save anything to Desktop it goes into the 'FOLDER' Desktop, strange!!
Now, I can deal with this, but it is not right! Something has gone wrong! The quetion now is 'HOW'! Any other suggestions to try?
regards

---

### Post by seventhc on 2007-12-21
If you look in your trash do you see a folder 'Desktop' there??

---

### Post by Sbarton on 2007-12-21
Yes seventhc!
regards

---

### Post by seventhc on 2007-12-21
:) good thing you didn't empy the trash :D

---

### Post by Sbarton on 2007-12-21
So, seventhc what is the significance of that and can I get back to normal?
regards

---

### Post by seventhc on 2007-12-21
well, i would open your home folder, then open your trash. make it so you can see both, then just drag your desktop folder back in to your home folder. or copy and paste but not sure if that will wok without an error.

---

### Post by Sbarton on 2007-12-21
Thanks , but I had tried that and it does nothing. Thanks for the suggestion anyway.
regards

---

### Post by seventhc on 2007-12-21
oh..sorry, I thought you would be able to put it back. Have you tried creating a Desktop folder in your home directory?

---

### Post by seventhc on 2007-12-21
I deleted my desktop and it shows the same as yours but I am able to put it back into my home folder. you don't try to put it on your desktop, you click on 'Places'>'Home folder' and put it in there.

---

### Post by Sbarton on 2007-12-21
Thanks, but do not apologise each suggestion is welcome. I have the FOLDER Desktop installed and I can work with this, but it is not right and would like it as nornal. I will keep ontrying. Thanks so much for your time.
regards

---

### Post by jken146 on 2007-12-21
I would try emptying the trash, leaving just one Desktop directory (the one in your home directory).  You may need to log out and in again after doing this.

---

### Post by seventhc on 2007-12-21
You might want to look here.
[http://ubuntuforums.org/showthread.php?t=581498](http://ubuntuforums.org/showthread.php?t=581498)
this looks like it would fix it.
I recreated this problem as best I coukd, then followed the first post

```

sudo gedit ~/.config/user-dirs.dirs
```
2. Look for this entry: XDG_DESKTOP_DIR. Make it like this: XDG_DESKTOP_DIR="$HOME/Desktop"
3. Now log out and log back in. For me, this caused a Nautilus crash - i.e. the desktop disappeared and the nautilus browser wasn't working. So continue:
4. Open up System>Administration>System Monitor and in Processes, look for Nautilus. Stop it completely. If it does not exist, run Nautilus through Terminal (it should not have any effect, don't sudo it) and then stop it.
5. Run Nautilus via Terminal and it should be working furever.

everything seems to work fine now. I didnt even have to log out.

---

### Post by Sbarton on 2007-12-22
Hi seventhc, thanks for your input. I changed and followed the suggestion outlined in your post. The result is that the trash desktop icon has gone, but I still have a desktop screen which is not the desktop.When I save anything to desktop it goes into the 'FOLDER- Desktop' and not onto the desktop screen I see in front of me. Weird eh!
The mouse will not do anything accept move on screen (no right click function etc)
I have attached a screen shot of the config file which seems to be correct now.
This is proving to be a patience problem but I will stick at it. There has to be a answer to it.
Thanks for your time.
regards

---

### Post by seventhc on 2007-12-22
Here is mine and it looks the same accept for the PICTURES directory and PUBLICSHARE
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```When i tried recreating the problem the same thing was happening like if i put something onto my desktop it just disappeared  but I found it in another folder. After I tried this fix everything went back to normal.
Strange, I'm sure it's like one little thing we are missing, but I'm very curious as to what this fix will be.

p.s
You did end nautilus too??

---

### Post by Sbarton on 2007-12-22
Thanks seventhc, Yes I did end nautilus but no luck. I had another look in 'System monitor' and found 2 entries for nautilus, 1 running, 1 sleeping. When I hover the mouse over the running one I see the following (nautilus --no-default-window--sm-client-id default2). The second (sleeping)one when hovering over it I see(nautilus -- no-desktopfile:///home/harry). This last one I think points to the fact that when going into Menu/Places and clicking home file, nautilus does not respond at all to show home file.
Annoying is'nt i!!
I did boot into recovery mode and the system loads fine, but i believe this is a root system.
Desktop items I should normally have in normal bootup desktop screen I can see on the desktop in recovery mode.I don't know what to try next. Looks like a trying day ahead.
Thanks and regards

---

### Post by seventhc on 2007-12-22
I looked at this post
[http://ubuntuforums.org/showthread.php?t=443088](http://ubuntuforums.org/showthread.php?t=443088)
and basically they went into ```
gksudo nautilus
``` and saw the Desktop folder was missing, so they recreated it and everything was fine. But honestly I am not sure if this is what you need or not, but it can't hurt to look.

...completely baffled...
](*,) :???: :-k

---

### Post by Sbarton on 2007-12-22
Hi seventhc, Firstly let me thank you for all your time and input.
Secondly regrettably I made the decision to reinstall (the quick answer to maost probs). Having spent 3 days trying to solve the problem I felt it was time to go along another avenue. In a perverse way it is sometimes worth having these type of problems as you learn a lot in the process, by your own research, and those people who take time to offer their advice/experience. Once you know how to solve problems it becomes easier to help others.
Sorry, that I did not solve the problem, but all the effort was not in vain due to learning in the process.
Thanks once again and let me wish you festive greetings and have a good New Year
regards

---

### Post by seventhc on 2007-12-22
Reinstall fixes everything :D...but why not just create another user and delete the troubled one?? But to late to try that I think ;)
Happy Holidays to you too. :)

---

### Post by dekrit on 2008-04-07
I saw this thread was not actually solved. 
I ran through the same problem some time ago, and all I did was to remove (rename to something else to be safe) the directory ~/.gnome/gnome-vfs.

Like this
$ mv ~/.gnome/gnome-vfs ~/gnome-vfs.BAK

That's all. Hope this would help someone else with the same problem.

Regards,

dekrit.

---

