---
title: "total noob to linux, just installed 7.04"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by devsfan1830 on 2007-10-03
I used 6.something last year briefly because a class required it. It installed no problem. Now ive come back and installed 7.04. I find it even better as things like network connections are working far easier. BUT theres one thing. The shutdown and reboot buttons are gone from the log off menu. Is there a setting that needs to be enbled to give these back? I am still on a default install, all that happened was it auto updated. So far ive been shutting down with sudo reboot and sudo shutdown. id line an easier option.

---

### Post by taurus on 2007-10-03
You don't have Shutdown or Reboot (and others) options from the red icon in the upper right corner when you click on it?

---

### Post by master_kernel on 2007-10-03
I had that problem too in Feisty after I installed Compiz Fusion, but I never fixed it.

---

### Post by Nehvrook on 2007-10-03
Have you tried right clicking your top pannel and choosing ADD. Then putting the quit button on there? That should let you do it normally

It SHOULD be there by default, but I've seem them randomly dissapear before too :P

---

### Post by Ant_Merlin on 2007-10-03
Hello, I noticed this issue, but it was before I installed the restricted drivers for my card (ATI), they came back after I installed drivers if that helps.

---

### Post by Egill Th on 2007-10-03
Hi,

I reccommend opening a terminal and use the "shutdown -h now" and "shutdown -r now" commands.

Best regards,
Egill Th

---

### Post by devsfan1830 on 2007-10-03
well i have a open door icon on mine, and when i click that and am presented with the shutdown menu u get hibernate, standby, log off and somethin else but no shutdown or reboot.
-screenshot-
[IMG]http://img128.imageshack.us/img128/994/dsc00747dv4.jpg[/IMG]



 I have a laptop that has onboard intel graphics and being a linux noob i have NO idea how to install things like that, other than using the package manager to do it for me

---

### Post by llamakc on 2007-10-03
Did you originally set up a different user when first installing it?

---

### Post by devsfan1830 on 2007-10-03
> **llamakc said:**
> Did you originally set up a different user when first installing it?
no, i installed it for me and i log in as the useri specified during install

---

### Post by Nehvrook on 2007-10-04
That's so wierd. When you log out can cho choose shutdown from the menu?

Anyway, you can make yourself a button that will shutdown for you. If you right click the top bar and choose add to pannel it'll bring up a menu. In there choose  "Custom Application Launcher"

It'll bring up a little box to make a launcher.
Under type choose application in terminal
Give it a name like "Shutdown" or "Restart"
Under command enter in the code you would use in the terminal to shut your PC down (Or restart it depending on what you want this button to do)
And add a comment if you think it's nescessary.
You can also pick an icon so you can tell what the button does easier.

Once you've entered all that in choose okay and it should add your new button to your pannel. Clicking on it should run the code you entered in. So in your case it will shut down the PC for you.

Hope this helps.

---

