---
title: "xserver-xorg problems"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by cebobbitt on 2006-06-18
when I boot in safe mode and type in dpkg-reconfigure xserver-xorg it goes to this wizzard that aks a lot of questions.  Well everything goes fine untill it get to the 24bit color part.  When I select 24 bit color, I get a warning at the bottom of the screen say I am overiding a previous configuration and it asks me for a command prompt. I don't know what to put here and it want let me procede any further.  I have tried a lot of stuff, but can't get pass this prompt.  Any help would be much appreciated.

---

### Post by catlett on 2006-06-18
What happens if you just press "enter" at the prompt without putting anything in?
What happens if you put 16bit in or another color level other than 24?

---

### Post by cebobbitt on 2006-06-18
when I hit enter, it just goes on to another prompt, nothings happens, I have try to go back to enter other answers, but as soon as I get to the screen asking me for what bit color, it goes to the bottom of the screen tell me this may over ride current configs. It then asks for a command prompt, but I don't know what to apply.  I have tried y I have tried accept, nothings seems to let me get to the log in screen for my desktop. Every thing was working fine untill I let it update some stuff, then I went off in its own ways.Any help here is much apprecieated.

---

### Post by catlett on 2006-06-18
Is there more than one listing for Ubuntu in grub when you start up? If you get a choice of more than one entry from the menu at startup, try one of the other entries. Hopefully you got a new kernel during the update and it is having issues. If that is the case, you should be able to boot into your system with the older kernel.
Try another listing if it is there./ I'm going to find the xserver file in my machine and see if editing that will help.
I'll check back in a litle bit.

Actually I found it a litle faster than I thought. Next time through see if you can enter this cammand ```
 sudo nano /etc/X11/xorg.conf
``` If it brings up that text, try editing it. Look for the screen section and put 24 in if it is another value. It's worth a try. It will look like this and the red is where you want to make the change.
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "CPD-G410R"
        [COLOR="Red"]DefaultDepth    24[/COLOR]
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "$        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "$        EndSubSection

```

EDIT: Good point by Hegenious. Have you been able to boot in normally? And if so, did you try dpkg-reconfigure... from the terminal? If you can get in a backup is smart to do. Run this if you can ```
sudo cp sudo nano /etc/X11/xorg.conf sudo nano /etc/X11/xorg.conf_backup
``` That creates a backup.

---

### Post by hegenious on 2006-06-18
dunno, perhaps it's because you are in safe mode and it restricts you from making some changes.
try booting normally and run 'sudo dpkg-reconfigure xserver-xorg'

in the first screen accept the option to have the xserver autodetected. If that succeeds, most questions the wizard asks will be pre-answered.

If you don't know what to answer, just accepting the default is your safest bet.

important: before you begin, make a safety copy of /etc/X11/xorg.conf

that way, if you made some mistake in the wizard and the system won't start X anymore or let you login, you could restore your safety copy from the command line after booting in recovery mode.

---

### Post by cebobbitt on 2006-06-18
ok, I tried the sudo nano/ect/x11/xorg.conf.  and it brought up a screeen that had a flashing cursor and stuff at the bottom about changing the text and stuff like that, but there was no info there to edit.  I have been searching everywhere in the forums looking for a solution, but so far , no good. I apperciate you guys trying. I have reinstalled the desktop version back to the hard drive. I now have a working version of ubuntu, just now it has less disk space than it did before.  I hope to figure out how I get the other one working, but untill i do, I will just not update the one I have now.  Thanks again to all for helping

---

### Post by catlett on 2006-06-18
[QUOTE=cebobbitt]ok, I tried the sudo nano/ect/x11/xorg.conf.  and it brought up a screeen that had a flashing cursor and stuff at the bottom about changing the text and stuff like that, but there was no info there to edit.  I have been searching everywhere in the forums looking for a solution, but so far , no good. I apperciate you guys trying. I have reinstalled the desktop version back to the hard drive. I now have a working version of ubuntu, just now it has less disk space than it did before.  I hope to figure out how I get the other one working, but untill i do, I will just not update the one I have now.  Thanks again to all for helping[/QUOTE]
Did you enter the exact path to the document /etc/X11/xorg.conf? If you did and nothing was there, you have a real issue. That is the dociment that holds the entire configuration of your x window session. Without it you can't get into a x window system i.e. gnome or kde etc.

What has happened recently that changed your system if anything? Do you only have a server install? Maybe that is it. Enter this at the prompt next time ```
sudo aptitude install ubuntu-desktop
``` That will install the ubuntu desktop i.e. the x window system and gnome. Maybe somehow it isn't installed and you only have the server instal at the moment. Casn't hurt to try. If it is already installed it will leave it alone

---

### Post by cebobbitt on 2006-06-18
I had a working system untill I allowed it to make the updates it wanted me to do.  I installed the updates and it told me to reboot and thats when I got the xserver message.  I have reinstalled the cd again and this time I will not update it untill I can figure out what I did wrong last time. I have already done the sudo aptitude install ubuntu-desktop. I says it can't find it or something to that effect. After reinstalling the cd I have be able to respond to the forum through my working version of Ubuntu. I really appreciated all the help

---

### Post by catlett on 2006-06-18
Your not the only one to have problems with an upgrade through the update manager. I know what it's like to have a perfectly running system and then have it hosed by the update manager. [http://www.ubuntuforums.org/showthread.php?t=178903](http://www.ubuntuforums.org/showthread.php?t=178903)

P.S. Since I had to reinstall I made a home partition and next time I'm going to upgrade with the cd and just leave my home partition unformatted. This way root gets updated to the new system but my home and anything I have in it doesn't get touched.

---

