---
title: "[SOLVED] Setting a Command to an Icon"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by azurepancake on 2008-04-14
I've been curious about something for a bit now.. Recently I've got my Nintendo Wiimote to sync with my media server and with a little tinkering I got it to work pretty well. But the thing is that every time I reboot my computer I have to retype a command to start the Wiimote synchronization. And if I am going away from my computer for a prolonged amount of time, I like to shut my Wiimote off to conserve battery power, hence needing to enter the command next time I'd like to use my Wiimote with my computer.

This is only a small nuisance and personally, to me the command isn't that large and I've basically memorized it already. But I'd like to make it easier for fellow friends and family who'd like to use my media center. 

So my question is if there is someway to create an icon that is linked with that command? Almost exactly like .bat files in Windows. If anyone knows how I could pull this off, I'd greatly appreciate any tips.


Thank you!

---

### Post by groupmsl on 2008-04-14
If you just right click on the desktop, then click "create launcher". Then select "Application in terminal". and pop your command into the "command" box. Simple!

This will only work if your command is one line long though :(

---

### Post by anewguy on 2008-04-14
Just do the following:

(1) Right-click on a blank area of your desktop

(2) click "Create Launcher"

(3) Click on the arrow at the end of "Type:" and click on command in terminal

(4) Put a name in - this will show on the icon on your desktop

(5) Put in the command in the "Command:" area.  If a path is needed to get to the command, be sure to specify it (ex:  ~/some folder/mycommand  )

(6) The default icon is shown in the upper left in a box.  Clcik on the box to select another icon if you want.

(7) click "OK"


your command should now show on your desktop.  In addition, if this is something you'd like run everytime you boot Ubuntu, read some of the info on the init process and you will find you can specify it run at startup.

Hope that helps!  :)

---

### Post by anewguy on 2008-04-14
> **groupmsl said:**
> If you just right click on the desktop, then click "create launcher". Then select "Application in terminal". and pop your command into the "command" box. Simple!

This will only work if your command is one line long though :(

Love the reference to binary!  When I was younger (I'm 52 now) and just had started out in the mainframe arena, hexadecimal and binary dumps were the thing of norm.  We even made up some t-shirts with a common extremely vulgar phrase done in binary.  We figured if someone could actually read them, they couldn't help but laugh!

---

### Post by azurepancake on 2008-04-14
Ugh.. I feel like an idiot now! That was just what I needed and a lot simpler to set up then I thought it would be. 

I will read up on the init process because there are a few things I'd like to boot at start-up. Cool.

And to the binary reference. I'm afraid I didn't catch it, could you explain? I want to be part of the fun! Is it maybe because binary is written in one line? 

Thanks again!

---

### Post by forrestcupp on 2008-04-14
If it happens to take more than one command, you can make a script.  Open up your text editor and make a script like this:
```
#!/bin/bash
[i]command 1
command 2
command 3[/i]
```
substituting your commands.  Then save the file wherever you want with whatever name you want, and open a terminal and type
```
chmod +x */path/filename*
```
substituting the path to the file and the correct filename.  That makes your script executable.

Then you can follow the instructions others gave you to make a launcher, and in the launcher's command, just point it to the script you made.

---

### Post by groupmsl on 2008-04-14
Binary is a combination of 1's and 0's which make up everything that a computer does (it can only understand 1's and 0's) so the number 10 in binary means 2. Thats what the joke is!!

Andy :)

---

### Post by azurepancake on 2008-04-14
Even better. 

Thanks Forest!

Ahha, I didn't catch your signature. I thought the joke was somehow embedded within your comment. That explains it.

---

### Post by forrestcupp on 2008-04-14
As far as the boot up process goes, you can add this to your startup by going to System->Preferences->Sessions.  In the Startup Programs tab, just click Add and it will add it to the list of startup programs.  Just enter a name, and in the command section, either enter your command, or the script you made.

Then it will run that every time you boot.

---

