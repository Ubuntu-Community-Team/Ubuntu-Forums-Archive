---
title: "touchpad fix, really FIXED ME! Please help."
date: 2011-10-06
forum: Any Other OS
---

### Post by mrjoeyman on 2011-10-06
I read on the Mint help site that to fix my touchpad I needed to do this:

> If your touch pad can not emulate a double click by tapping on the touch pad go to the terminal and type:

sudo gedit /usr/share/X11/xorg.conf.d/50-synaptics.conf
 

then replace with:

Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        Option "TapButton1" "1"
        Option "VertEdgeScroll" "1"
EndSection

Then save the file, close gedit

go back to the terminal and type: sudo reboot

log-in and test the touch pad by tapping on it to open files

Well I saved the file that was already there into my documents. That file read like this:

> Section  "InputClass"
          Identifier "touchpad catchall"
          Driver "synaptics"
          MatchIsTouchpad "on"

So now that it was saved in my documents, I replaced it with the above and upon reboot, it only goes to a black screen with things happening, loading, unloading etc... and ends up at something like:

> laptop@mrjoeyman tty1
login:

I tried putting in "startx" but it says the server is already running or something.  Can someone help me get the first script, put back in that file please using the terminal? Or is there an easier fix?

I was a dumb @ss. In hindsight I found out I shouldnt have saved the first script to my document folder, but to the xorg.conf file. :(

Any help would be appreciated!

---

### Post by ajgreeny on 2011-10-06
At the 
```
laptop@mrjoeyman tty1
login: 			 		
```screen, login with your username and password, the latter of which will not show on screen but will be there.  Now you will be able to edit that file back to what it was with ```
sudo nano /usr/share/X11/xorg.conf.d/50-synaptics.conf

```After editing the file Ctrl+X will offer to save the file for you, and you can then just reboot with ```
sudo reboot
```

---

### Post by mrjoeyman on 2011-10-06
Thank you sooooo much! I thought I was doomed. When I saved the new script, I didnt even have to reboot, it just opened right up to x and I logged in. This is the best help site on the net. Thanks again!!!!!!!!!:KS

---

### Post by ajgreeny on 2011-10-07
Great!

Now for the touchpad problem.  What exactly is that problem, and what are you trying to change in its behaviour?

You may find that **gpointing-device-settings** from the repos is needed if you do not already have it installed, or that the **synclient** command can sort you out.  Use the command ```
synclient -l
``` to see what can be changed and your current settings, then use a command such as ```
synclient MaxTapTime=0
``` to turn off tap-for-click.

---

### Post by mrjoeyman on 2011-10-07
Wow thanks for asking! Ok what I was trying to do initially was to get the "tap" option to work on my touchpad. It works to move the cursor around, but I can't "tap" it with my finger to make it execute. I was hoping to use that script to fix that, and then find a way to disable the whole function of the touchpad when I choose not to use it. It can be kind of frustrating sometimes when typing a lot because the touchpad hits my hands and throws the focus away from the document I am working on. I will wait for you to respond since you know now more about what I was going for. This problem is on Linux Mint Debian Edition (LMDE 2011) . I post here because this forum is the best! I have Ubuntu on one puter and Mint on another. Thanks!

---

### Post by Perfect Storm on 2011-10-07
Moved to Other OS/Distro Talk.

---

### Post by ajgreeny on 2011-10-07
To turn tap-for-click off use the command i showed previously ```
synclient MaxTapTime=0
```   To turn it on again use ```
synclient MaxTapTime=180
```
You should be able to make a shell script which will turn it off, and another to turn it on, and then put launchers for those scripts in your panel or desktop, I think.  Put this in a text editor and name it taptoclickoff or taptoclickon, make it executable, and that's it;  all you do is make a launcher for that script and it should work.
```
#!/bin/bash
synclient MaxTapTime=0   #(180 to turn on)
```

---

### Post by mrjoeyman on 2011-10-07
Ok thanks, when I get off of work and get home I will try it and let you know. :)

---

### Post by mrjoeyman on 2011-10-08
Well you are off the hook :)  I was googling how to make a launcher with the script you gave me when I ran across a post where someone had encountered a similar problem to mine. The poster admitted that he had never tried to view his mouse/touchpad options built in to his linux system. I scratched my head and thought, "You mean we have some built in"? I hate to admit this (my noobiness is showing) but I had not done that either. I just figured that the "fix" that was broadcast on the default page of my new browswr was universal to all iterations of the newest LMDE Os's. Well I found out where to look and all is well afterward. I would however like to learn how to make those scripts you offered me into executables and attach them to launchers like you suggested. I read up a little bit on it, but I am still not sure about exactly how to go about it. If you have the time I would appreciate some further advice. If not then certainly I understand and appreciate very much what you have done for me to this point. Thanks again for your valuable time.

---

### Post by ajgreeny on 2011-10-08
OK, make the script as I showed you before and save as  **taptoclick.sh** file in your home.  Now make it executable, either in **nautilus, right click ->properties ->permissions** tab or with ```
chmod +x taptoclick.sh
``` Now right click on your desktop and select **Create launcher** and fill in the dialog that appears.  See screenshot.  Now double clicking that launcher should run the script and turn off or on the taptoclick.

---

### Post by mrjoeyman on 2011-10-08
Thats what I needed; where to save it. I read about the other part on google, but I thank you for showing me how to do it via the terminal too. Thanks for all the great help.

---

