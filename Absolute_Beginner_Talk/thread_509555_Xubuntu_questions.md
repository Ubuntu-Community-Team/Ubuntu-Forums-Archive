---
title: "Xubuntu questions"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by slymi2005 on 2007-07-25
I'm new to Xubuntu so I'm just starting to get the hang of things. I recently downloaded a theme but i have no idea how to install it. I've tried dragging it into the themes menu but that doesn't work and I've tried extracting it to users/share/themes but it says that I do no have permission. I've been look around for answers but none seem to help. I read somewhere that you should extract it to ~/.themes but I have no idea what that means. 

My second question is about my cdrom drive, when I first installed Xubuntu the drive would lock any time I put something in there so I would have to right click it and click eject volume rather than just pushing the button, so I changed it but now I don't remember how I changed it and I would like to change it back so that it locks again because it opens by itself every time put a cd in.

I'm also wondering about quicktime videos and if there is any player that plays those because I can't play them. I know in windows real player would be an alternative but I'm not sure.

One last question, sometimes Firefox stops responding and I was just wondering how you close a program that isn't responding. I read about xkill but I haven't tried that yet, is that the best way?

Thank you so much for your help and I apologize if these questions have been asked countless times but the search feature hasn't given me the results I've wanted and neither has Google. Sorry it's so long.

---

### Post by rax_m on 2007-07-25
I can help you with your themes query.. but possibly not the others. 

When you see a ~ in Linux it means the same as /home/<yourusername>
So if your user is slimy2005 then you need to extract your theme that you downloaded into the directory:
[code]/home/slimy2005/.themes[code]

If you then reload your theme switcher it should show up in there. 

BTW You can play quicktime movies on Linux.. you have to just download the correct codecs.. Unfortunately I can't remember which ones.. sorry.

---

### Post by Vague on 2007-07-25
> **slymi2005 said:**
> I'm also wondering about quicktime videos and if there is any player that plays those because I can't play them. I know in windows real player would be an alternative but I'm not sure.

One last question, sometimes Firefox stops responding and I was just wondering how you close a program that isn't responding. I read about xkill but I haven't tried that yet, is that the best way?

Thank you so much for your help and I apologize if these questions have been asked countless times but the search feature hasn't given me the results I've wanted and neither has Google. Sorry it's so long.

Not totally sure on the others, but I'll give these a shot.  I'm pretty sure VLC will play QuickTime.  It's in the Universe repository, so you'll have to have that enabled.

There's a process manager in Xubuntu under Applications>System>Process manager.  If you go in, you should be able to right click on any process and kill it.  Also, generally when Firefox freezes on me I can just right click on the taskbar entry for it and close it from there.

---

### Post by slymi2005 on 2007-07-25
So would I use Xarchiver and click extract to and type in "[code]..." and what does code mean? Do I have to create a folder?

---

### Post by Celegorm on 2007-07-25
> **slymi2005 said:**
> So would I use Xarchiver and click extract to and type in "[code]..." and what does code mean? Do I have to create a folder?
It only says [code] because the tags got messed up. Just type the stuff between the [code] tags. And no, you won't have to create a folder, since you home folder already exists and .themes is a file. The dot at the beginning makes it a hidden file, by the way.

There's a sticky in this forum describing how to enable multimedia: [http://ubuntuforums.org/showthread.php?t=413624]("http://ubuntuforums.org/showthread.php?t=413624")

As for xkill, that is a good way to kill runaway processes. In the terminal, you can also type "kill <PID>", where <PID> is the process identifier of the offending process. "ps aux" will give you a list of all running processes with PID's. The list is usually quite long, alternatively you can type "top" which will give you a shorter, constantly updated list. Press 'q' to get out of top. In case you have never used the terminal before, note that you must press enter after each command before it will take effect, and you can open a terminal from Applications->Accessories->Terminal. One final trick, in case X (the windowing system) itself should freeze or become unresponsive, you can press ctrl-alt-F1 to get to the terminal, and ctrl-alt-F7 to get back to X.

---

### Post by ugm6hr on 2007-07-25
> I'm new to Xubuntu so I'm just starting to get the hang of things. I recently downloaded a theme but i have no idea how to install it. I've tried dragging it into the themes menu but that doesn't work and I've tried extracting it to users/share/themes but it says that I do no have permission. I've been look around for answers but none seem to help. I read somewhere that you should extract it to ~/.themes but I have no idea what that means. 

I've just discovered themes.  If they are XFCE themes, extract the theme (double-click on it) to wherever, and rename the folder to something that you will recognise the theme by.  Then use the command *gksudo thunar* and copy the folder to *usr/share/themes*.  It must contain a folder xfwm4 within the main folder, with various icons.  Then, to try the theme out, go to Applications->Settings->Window Manger Settings, and it should appear in the list under the Style tab.  GDM themes (for login screen changes) are easier - just go to Applications->Settings->Login Window, and click on Add in the Local tab, and select the tar (compressed) file.  For Splash themes: [http://xfce-diary.blogspot.com/2005/03/xfce-splash-screen-crash-course.html](http://xfce-diary.blogspot.com/2005/03/xfce-splash-screen-crash-course.html)  

Some good places to get themes: [http://www.xfce-look.org/](http://www.xfce-look.org/) [http://themes.freshmeat.net/](http://themes.freshmeat.net/)
This is the Terminal method: [http://ubuntuforums.org/showthread.php?t=227416](http://ubuntuforums.org/showthread.php?t=227416)

> I'm also wondering about quicktime videos and if there is any player that plays those because I can't play them. I know in windows real player would be an alternative but I'm not sure.
I use VLC (just search for it in Synaptic package manager).

> One last question, sometimes Firefox stops responding and I was just wondering how you close a program that isn't responding. I read about xkill but I haven't tried that yet, is that the best way?
Applications->System->Process Manager

---

### Post by slymi2005 on 2007-07-25
Thank you guys so much I was able to install a theme, i can play quicktime videos, and i now know how to close a non responding program, you guys are awesome. If anyone knows how to lock the cd drive though that would be the cherry on top.

---

### Post by slymi2005 on 2007-07-27
Ok so no one responded to my last question but thats ok because I have another set of questions lol. So I was using Xubuntu this morning and I restarted the computer and the dual boot menu showed up and I selected WIndows ME and it wouldn't load (an error message popped up) I ended up having to restore the computer but I was able to keep my files and xubuntu, now I just have to reinstall everything (on windows xubuntu was not affected). Anyway I just got to thinking that maybe it's time to leave behind windows for good since it's krap anyway (I've been using Xubuntu for less than 2 weeks). FIrst though I needed to know how to do certain things before I leave windows behind.

My biggest issue is applying settings to all users rather than having to do each one at a time. For example i had to install flash player for firefox on each user, also installing things like themes and cursors have to be done individually. 

I also don't know how to change a users password, i know where to go but I don't have permission to change it, not even my own. Does this have to do with what group I'm in because all the users have admin privelages, should they be in root group or admin group?

Also, when I download things how do I install them? Or is it only possible to install through add/remove, synaptic, etc?

In my previous post I was introduced to the process manager and I noticed that there are a lot of running applications, even though I'm only using firefox, is this normal or should I close some? If so how do I stop them from starting up everytime?

And of course, if anyone knows how to lock the cd drive please let me know.

Another problem is disk space, I only have a 20 gig hd and I don't know how to increase the disk space for xubuntu and decrease it for windows. Will i have to reinstall xubuntu?

Thanks to all who responded in the past and to all who do respond, I don't know what I'd do without you.

---

### Post by ugm6hr on 2007-07-27
> My biggest issue is applying settings to all users rather than having to do each one at a time. For example i had to install flash player for firefox on each user, also installing things like themes and cursors have to be done individually. 
For plugins, install flash from Synaptic (flashplugin-nonfree) after activating Multiverse / Universe repositories.  I think that should install for all users.  As for themes - I think that has to be done individually (I think it does in Windows too).

> I also don't know how to change a users password, i know where to go but I don't have permission to change it, not even my own. Does this have to do with what group I'm in because all the users have admin privelages, should they be in root group or admin group?
Haven't tried this, but it must be possible from System->Users/Groups, surely?

> Also, when I download things how do I install them? Or is it only possible to install through add/remove, synaptic, etc?
Depends on what they are. *.deb* are easiest (e.g. from [http://www.getdeb.net/](http://www.getdeb.net/) - just double-click (like an .exe in Windows).  Anything else: [http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

> In my previous post I was introduced to the process manager and I noticed that there are a lot of running applications, even though I'm only using firefox, is this normal or should I close some? If so how do I stop them from starting up everytime?
Most things running are necessary - just as in Windows the process manager has a load of system processes running, Xubuntu has some too.  If you kill/term them, you might find that the desktop disappears etc...

> And of course, if anyone knows how to lock the cd drive please let me know.
If you are re-installing - try and leave the CD settings as it is to start with.  Linux does not recommend you use the eject button - you should get used to ejecting from the desktop.

> Another problem is disk space, I only have a 20 gig hd and I don't know how to increase the disk space for xubuntu and decrease it for windows. Will i have to reinstall xubuntu?
Either reinstall (I thought you were doiing that anyway), or use the GParted LiveCD to shrink / delete the Windows partition, and extend the Xubuntu partition: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Enjoy Xubuntu - it's way better than Windows ME.  I've got an old laptop with only 10GB HD that has a 5GB Xubuntu and 4.5GB data partition that has been recovered from ME.

---

### Post by slymi2005 on 2007-07-27
I tried system>users/group but it says that i do not have root permission. And actually I'm not reinstalling everything, that was just for windows but I guess thats always an option I just hoped that I could lock the cd drive again. I'll have to get gparted though and I'll try the others later. I'll be sure to repost if anything goes wrong. thank you ugm6hr.

---

### Post by slymi2005 on 2007-07-28
bump?

---

