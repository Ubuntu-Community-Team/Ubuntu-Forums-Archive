---
title: "resolution and problems at first startup"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by nightkillerkiller on 2006-09-12
hi all

i heard someone say that installing ubuntu is a piece of cake. well here is my expierience:
first of all, i cannot change the screenresolution from beeing 640x480. so the windows displayed when trying to install are bigger than the desktop. so i cannot see the buttons at the lower window. and using that move-thing all the time is really a pain in the a..!
during startup there is the possibillity to change the resolution, but that has no effect at all! having a pc with sli and 2 nvidia graphics cards and then i have to see 640x480? i meen what year is this? 
i am disapointed as hell. and with this shit happening, i dont dare to install. i wanted to use both windows xp and ubuntu. and had hoped that there is some kind of boot-manager with ubuntu. but with this start problem, i cannot continue. cause what will happen? is the rest of the installation the same uncompleted shit or what. 
i must say i am disapointed!!!

---

### Post by Anonii on 2006-09-12
> **nightkillerkiller said:**
> hi all

i heard someone say that installing ubuntu is a piece of cake. well here is my expierience:
first of all, i cannot change the screenresolution from beeing 640x480. so the windows displayed when trying to install are bigger than the desktop. so i cannot see the buttons at the lower window. and using that move-thing all the time is really a pain in the a..!
during startup there is the possibillity to change the resolution, but that has no effect at all! having a pc with sli and 2 nvidia graphics cards and then i have to see 640x480? i meen what year is this? 
i am disapointed as hell. and with this shit happening, i dont dare to install. i wanted to use both windows xp and ubuntu. and had hoped that there is some kind of boot-manager with ubuntu. but with this start problem, i cannot continue. cause what will happen? is the rest of the installation the same uncompleted shit or what. 
i must say i am disapointed!!!
About your resolution problem:
Try this first:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)
and if it doesnt work, try this:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)


One or the other should fix this.

---

### Post by nightkillerkiller on 2006-09-12
nice of you to suggest some solution. tried it but still the same. :mad:

---

### Post by Anonii on 2006-09-12
wtf, really?
Did you also enable the other resolutions from the "sudo dpkg-reconfigure xserver-xorg" ? Did the configure, detect your monitor? Are you sure, you just didnt pass by every option hitting the default one, and you checked them, especially the ones concerning the resolution.

---

### Post by Najand on 2006-09-12
Press Ctrl+Alt+Backspace to refresh (better to say restart) the X. Sometimes it is enough and works.

If it was not the solution, login to Ubuntu with your uuser ID, Click on Applicaton -> Accessories -> Terminal
A new page with a command prompt like MS-DOS will appear... 
You  need to write down the following command:
```

sudo dpkg-reconfigure xserver-xorg

```
and press Enter.
You need to enter your Password and wait for a moment...
A blue page will appear with guidence on it... 

use the following steps:
1. Let the wizard autodetect your  video hardware.
2. At the next page it will ask you for the X server driver... As far as you can see graphics, it must me Ok... without changing anything, continue
by pressing Enter
3. Press Enter to continue (several times) until the page it asks you for:> 
 "select the video modes you would like the X server to use."
Select your desirable resolutions (Multiple) by pressing Space, Move with Arrow key (Up and Down) and when you are finished press Enter
4. Press Enter again at  the  next page.
5. Select medium and Enter
6. At "please select your monitor's best video mode" select the option best matches your Monitor; for frequency you  may check your monitor documentations. When you are done, press Enter
7. Press  Enter until finish the wizard... 

Type "exit" in the terminal and log out (System->Quit->Log out).
When you found yourself at gdm (theplace you logged in) Press Alt+Ctrl+Backspace to restart  your X and then see if your probllem is  solved or not... I wish you good luck

---

