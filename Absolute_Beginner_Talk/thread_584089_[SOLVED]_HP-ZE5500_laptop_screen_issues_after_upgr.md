---
title: "[SOLVED] HP-ZE5500 laptop screen issues after upgrade from Feisty to Gutsy"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by ag65151 on 2007-10-20
I have an HP ZE5500 laptop with the ATI IGP 340m card. I upgraded from Feisty to Gutsy today and lost the ability to see anything on the screen. I think it is the screen refresh rate that is messed up, but it seems to happen before X is loading. I was wondering if there is a way to "step" through the boot process so I can see exactly what the command is that is flaking out my display. I can see everything fine from POST through grub and even the first third (or so) of the boot process, but then the display blinks and when it comes back it is unreadable, though I can tell that it is still going through the boot process. I just can't make out any letters. I just know what the lines look like.

Quick help would be much appreciated.

---

### Post by RomeReactor on 2007-10-20
Hi. You might want to look in /var/log/Xorg.0.log for errors:
```
cat /var/log/Xorg.0.log
```
Have you installed the drivers  yet? you might also want to do a reconfigure of your display:
```
sudo /etc/init.d/gdm stop
```
then
```
sudo dpkg-reconfigure xserver-xorg
```
accept all the defaults the dialog presents you, except when it asks which driver to use for your video card, select **ati**. Once the process is finished:
```
sudo /etc/init.d/gdm start
```
if your display doesn't start automatically after that:
```
start X
```

---

### Post by ag65151 on 2007-10-20
Thanks for the quick reply, but I can't see anything on my screen. I am using my wife's M$ machine to read this forum. I can't see Xorg.0.log even if I wanted to. I tried to go by guess through the dpkg-reconfigure, but I couldn't tell if I selected ATI or something else. The display is just too garbled. 

My question is whether I can step through the init sequence one at a time (perhaps a n00b question, but like F6 used to do after POST on a M$ system) so I can tell exactly what command is killing the display. Then I should be able to correct it. It might be gdm, but gdm stop did not give me a readable display. Any other suggestions?

---

### Post by RomeReactor on 2007-10-20
When you turn on your system, you'll be presented with a text screen that says something like "Press ESC to load Grub", with a 3 second counter. Press ESC then, and select "Safe Graphics Mode" or "Failsafe Mode" (can't remember the exact terms, sorry).

---

### Post by ag65151 on 2007-10-20
But even "Safe Graphics Mode" has a corrupted display. Whatever it is that happens right before the display garbles is just happening too fast for me to read. I need to slow the init process down enough to watch the steps. Any suggestions?

---

### Post by ag65151 on 2007-10-20
FYI - it is during the "Loading Hardware Drivers" portion of the boot process that I lose the display. It says something about "Radeon" (3 lines worth) and then becomes completely unreadable. Apparently it has chosen the wrong driver or a bad refresh rate. How can I modify without being able to see the change? I could probably get an editor up and use a "find and replace" function if I knew exactly what I was looking for and what I needed to change it to. 


Thanks again for the help.

---

### Post by RomeReactor on 2007-10-20
Try pressing CTRL+ALT+F1 to switch to a terminal after your system has finished booting; this should give you a black screen with white text that *should* be perfectly readable if the problem is not hardware related. Once in the terminal, login if asked to, and follow the commands on my first post.

---

### Post by ag65151 on 2007-10-20
CTRL+ALT+F1 took me to a black screen with unreadable white letters on it. I found on another thread to try switching the video driver to VESA through "dpkg-reconfigure xserver-xorg" So, I guessed at which driver was VESA in the reconfigure and got it right. I now have my display back and I will play with getting a better driver installed when I have more time (i.e., not tonight). Thanks for your help. Hopefully this will help someone else.

---

