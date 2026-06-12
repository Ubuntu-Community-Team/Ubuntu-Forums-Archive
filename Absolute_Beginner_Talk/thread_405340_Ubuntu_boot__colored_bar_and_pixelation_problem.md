---
title: "Ubuntu boot : colored bar and pixelation problem"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by noxxer on 2007-04-09
I recently downloaded Ubuntu 6.10 burned the ISO to a CD.
I insert the liveCD and start the machine, I got to the main menu and selected, "Start or install Ubuntu." When I would do so, it would show the logo with the progress bar, it would complete and go to the next screen, but instead of the desktop it would be many colorful bars, they would just sit there. If I were to click or to press buttons sometimes they would change and pixelate. Wondering if this was a video issue, I turned off the machine and when the main screen came back up, I pressed F4 for "VGA", I selected "1024 x 768 x 32" Then again selected to start Ubuntu. This time after the progress bar was finished, to my surprise, Ubuntu actually worked!
There was still a problem, I could not see my cursor, assuming this was a video driver problem I started installing Ubuntu to my hard drive (mainly by pressing enter and tab since I could not see the mouse cursor), figuring I would install the drivers afterwards and all would be well.
After the installation was finished I restarted the machine, and selected to start Ubuntu on the OS selection screen. After selecting Ubuntu, (there was no option to select the resolution like I did on the liveCD/install), and I think it did the progress bar again, I came to what was suppose to be the desktop, and once again, colored bars and pixelating colors! Arg!

I looked at some of the other posts about nVidia driver installing, but I thought that was AFTER you had access to the desktop.

Is there something I must edit in the boot options for Ubuntu to force some kind of different video or resolution option? Has anyone experienced this before, does anyone know what I am doing wrong? Help? (Excuse my excessive amount of questions, I'm sorry haha.)
If this is indeed not a driver issue and something else, I would be glad to know.

Thank you.

**Some of my Specs**

AMD 64 3400+
A 20gig HD
Nvidia GeForce 6600

---

### Post by prizrak on 2007-04-09
Hit Ctrl+Alt+Backspace once you get to the mess of lines. This restarts X which sometimes helps. If it's still like that hit Ctrl+Alt+F1 this *should* take you to terminal where you can log in text mode. Type in
```
sudo vim /etc/X11/xorg.conf
```
Find this part 
```
Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce Go 6200/6400]"
    Driver         "nvidia"
EndSection

```
Obviously the card name will be different and stuff. What you want to do is edit the part that says "Driver". Change whatever is in there (if you are using nVidia card it is likely to be "nv") to look like this.
```
Drver "vesa"
``` (It's case sensitive and I don't remember if it's supposed to be lower or upper case, if X doesn't start just change the case.)
This is a generic display driver that should allow you to get to the graphic part. Once there you can get the official nVidia driver from Synaptic you will need to enable extra repositories though. Then hit Ctrl+Alt+F7 to get back to the graphical console and hit Ctrl+Alt+Backspace to restart X. Alternatively you can type in
```
sudo reboot
```
to restart your computer w/o going to X at all.
Another thing you might want to try is grab 7.04 Beta it works quite well in my experience or just wait until the 19th when 7.04 becomes final.

---

### Post by noxxer on 2007-04-09
Update :
Well.. it's a no go, I tried  the Ctrl Alt Backspace, it just changed the colors (wee, pretty colors :P)
After trying, Ctrl Alt F1, it changed to what appeared to be a text terminal, but it was black, with purple blocks, when I pressed enter it moved the black down, as would text do if I could see it.

I believe I'll try your suggestion and download 7.04, is it just all around better with nVidia, or includes more drivers?
I surely hope something works, I loved the liveCD, but it hurts not being able to use to OS. :(

---

### Post by noxxer on 2007-04-09
I tried 7.04 and am still having this problem.

Would booting in "recovery mode" be something to try?
There is a terminal where I can input commands such as you said if I do boot in it, and I can read them since I do not actually start X by doing recovery mode...

---

### Post by noxxer on 2007-04-09
Excuse my doub-- triple posting. :-P

But I figured it out!! :D

I first booted in recovery mode.
Then backed up the Xorg file.
Then I used the "sudo nano" command to edit the Xorg file, edited it as you said, and it's fixed!

Thank you so much! :)

---

### Post by prizrak on 2007-04-12
You are welcome, sorry for the long delay in response for some reason the subscription didn't notify me. Glad it is working for you :)

---

