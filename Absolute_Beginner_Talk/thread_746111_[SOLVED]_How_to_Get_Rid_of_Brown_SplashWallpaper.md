---
title: "[SOLVED] How to Get Rid of Brown Splash/Wallpaper?"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by fallenshadow on 2008-04-05
When I log in a light brown wallpaper splashes up for a few seconds, how can I get rid of this?

For everyones information I am not a beginner, I have been using Ubuntu for about a year. I decided to post this in the beginners section as I feel it must not be too hard to fix. 

Please note I am not afraid of the command line. I know it is not the login screen colour as it is black or the no wallpaper colour either.

---

### Post by northern lights on 2008-04-05
Are you running compiz?

There's most likely two applications drawing to the root of the screen. What happens if you run ```
metacity --replace
``` Does the wallpaper become that brownish one? Then it's easy: Change it here to the same or whatever you want and restart compiz.

---

### Post by fallenshadow on 2008-04-05
I am not running Compiz or Compiz Fusion or Beryl. The brown wallpaper did not show up after using your command.

Here is a screenshot as Gnome was starting up.

---

### Post by FreewareFan on 2008-04-05
I believe this is the solution you are looking for.  

To change that background color during start-up, do this:

Start a terminal, and enter:

```
sudo gedit /etc/gdm/PreSession/Default
```

When that comes up, look for the section that has '#Default value' (should be almost at the bottom)  and change the  line that has BACKCOLOR to a color value that you like.  For example, #000000  would give you a color of black.

Save, then exit gedit.

When you reboot, you should see a black screen, instead of that brown one.

Hope this helps you!

---

### Post by Thanoulis on 2008-04-05
Edit your */etc/gdm/PreSession/Deault* script. (You'll need root access)
Close the end of file, you'll see a BACKCOLOR="#dab082" variable under *Default value* session.
Change the hex into quotes to match  the color you want and save the file.
Reboot if you want to see the changes...:)

FreewareFan, you catch me! :(

---

### Post by fallenshadow on 2008-04-05
Thanks Freeware fan you are the one that got the answer. I checked #dab082 in GColour2 and it was the light brown colour so I changed it to black.

Also no reboot was needed only a logout.

---

### Post by FreewareFan on 2008-04-05
Great, glad it solved your problem.  You might consider marking your thread as Solved now, for the benifit of other users who might have the same question as you do.

---

