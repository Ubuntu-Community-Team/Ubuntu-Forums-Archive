---
title: "[SOLVED] Unable to save resolution via nvidia control panel and editing x's config"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Lokanna on 2007-07-24
First off, I'd like to thank everyone who has ever tried to help anyone on these forums.  I spent a few days lurking, reading, and deciding to dual boot and use Ubuntu.  

My first install was smooth, in fact, smoother than most windows installs go.  I was up and running, browsing sites, reading and replying to emails, and I'd even managed to listen to some old mp3's.  Google+ubuntuforums.org have helped me immensely, so thank you!

Unfortunately, on day1, I was annoyed at the low resolution that gnome was using and decided to try and get my nvidia card up and running.  The mistake I made was I failed to google or read up about how to do this first and I think I "broke" x-server.  

The first step I did was go to restricted drivers and enable the nvidia card listed there.  Upon reboot I could not get into the GUI.  I booted back into my Windows and googled the issue. 

I tried first to dpkg xconfig (or something equivalent).  I was able to select various resolutions doing this and set up my video card.  However, as soon as I selected the color bit's, it crashed (for a lack of the knowledge of proper terminology) back to the CLI.  I tried all options for color bits but I continually crashed and make multiple xorg.conf.########## files.  

I was finally able to reinstall the GUI and was back up and running.  I then envy'd the nvidia drivers and everything installed and ran fine -- until I tried to save the resolution to the X configuration file! 

When I did that, I received the error message: Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'. 

So, being the stubborn, curious individual I am, I tried to open the directory it was in and just move it to the trash.  No luck.  The OS said: Unable to move to trash:Access denied.  Needless to say, it was time to fire up the CLI and just rm the file, right?

Wrong.  Apparently I can't get into the X11 directory in my /etc directory. 

Long story short (I know, too late!), I'm past this newb's level of tolerance.  While I can manually set the resolution every time I reboot, it's fairly annoying.  I've essentially completely migrated from Windows (and in under 48 hours no less) with the exception of some games.  I'm quite fond of the Wesner game I grabbed from the ubuntu programs, so I've actually not used Windows since yesterday's driver issue.

Can someone please point me in the direction on how to resolve this issue?  I just want to be able to save the x configuration file (via nvidia, CLI, anything) so that I can continue to learn this new OS.  

As I stated previously, thanks again though.  I've already utilized these forums immensely in the past 40 hours or so, and I wanted to give thanks!

---

### Post by sad_iq on 2007-07-24
Have you tried using ```
gksu gedit /etc/X11/xorg.conf
``` to edit the file??? Also to remove the file in /etc/X11/xorg.conf you have to use sudo: **sudo rm /etc/X11/xorg.backup**. If you still get in trouble post the model of your nvidia card and your xorg.conf!!!

---

### Post by benx009 on 2007-07-24
the reason you are probably constantly getting the "access denied" error message is because you are not browsing as root.  are you familiar w/ the command "sudo su"?  it will grant you the permissions you need to edit virtually anything in ubuntu.  why don't you try saving the your xorg.conf file as root and see what happens?  use "sudo" only when you need it though, and try to be wary and what you are editing (make sure you're doing things right the first time) or you might just end up "crashing" your system again.  i can say that from experience:)

---

### Post by TheAmazingDave on 2007-07-24
When you run the xconfig utility, the color bits setting is the last setting in the utility. After you select color bits, the utility autosaves the xorg.conf file and closes without prompting you.

---

### Post by Lokanna on 2007-07-24
> **benx009 said:**
> the reason you are probably constantly getting the "access denied" error message is because you are not browsing as root.  are you familiar w/ the command "sudo su"?  it will grant you the permissions you need to edit virtually anything in ubuntu.  why don't you try saving the your xorg.conf file as root and see what happens?  use "sudo" only when you need it though, and try to be wary and what you are editing (make sure you're doing things right the first time) or you might just end up "crashing" your system again.  i can say that from experience:)

I was unfamiliar with the sudo su command.  I was finally able to remove the xorg.conf.backup file, however, the control panel can't create a new one.  

>  	Have you tried using
Code:

gksu gedit /etc/X11/xorg.conf

to edit the file??? Also to remove the file in /etc/X11/xorg.conf you have to use sudo: sudo rm /etc/X11/xorg.backup. If you still get in trouble post the model of your nvidia card and your xorg.conf!!!

No, I have not tried that command until I read your post.  I'm sorry, but I was unaware of it's existence and was impatient, I apologize for not discovering it sooner. 

That said, I did use the command and gedit, however, as I'm weary of completely destroying this file once again, I'm hesitant to edit.  I guess I may as well live and learn.. 

> When you run the xconfig utility, the color bits setting is the last setting in the utility. After you select color bits, the utility autosaves the xorg.conf file and closes without prompting you.

Now there's some info I didn't know either.  Thanks for the tip! However, now I'm even more confused.  If what you're saying is true, why won't the gui save the resolution, especially considering it's saving correctly?  

Thank you all for the responses.  I'm off to try and get this thing worked out.

---

### Post by Lokanna on 2007-07-24
Using gedit, I was able to preview the control panels output and manually enter the info into the xorg.conf file.  I rebooted and my resolution is sticking.  

Thanks for the responses, I really appreciate the info.

---

### Post by jaygo on 2007-08-12
Posting for posterity ...
The reason it wasn't saving to your xorg.conf from the nvidia-settings applet is that you weren't running the applet as root. (I just found this one out myself). You can launch (apparently) any applet you need to, as root, by using 'gksudo'. 'sudo' will launch things as well but doesn't seem to give the GUI version. In your case, you would have wanted to use (in the terminal)
```
gksudo nvidia-settings
``` to run the applet as root or
```
gksudo gedit /etc/X11/xorg.conf
``` to edit it manually.
One note, closing the terminal seems to take down the launched applet (gedit or nvidia-settings) with it, so leave it open until you're done.

---

### Post by itisbasi on 2008-06-09
That's great. It worked for me. Thanks a lot. I guess that's one of the problems of being a newb in linux, haha something as simple as opening the application as root.... :(

---

