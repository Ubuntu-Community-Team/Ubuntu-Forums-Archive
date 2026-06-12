---
title: "6 very different questions."
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-07-14
1. Why can I only get a max resolution of 1024*768, when in Windows I can get upto 1280*1024. Yes my monitor supports it.

2. Can someone tell me the command, to change bootoptions. Example, change the time it takes to choose operation system, and make it so Windows boots first instead of Ubuntu (Or the other way around).

3. Is there any way to show "Computer" on the desktop?

4. How can I acces the /usr folder. (Please not in Terminal)

5. Is there any way to make all your hidden folders, not hidden? Eksampel, all the ones with the "." infront of them when you acces the home folder.

6. Is there any way to use the ctrl+c and ctrl-v commands in terminal, instead of using the mouse to copy and paste?

Thanks.

---

### Post by Jagot on 2006-07-14
1)
Try:

```
sudo dpkg-reconfigure xserver-xorg
```

2)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

3)
Hit alt+f2 then type:

```
gconf-editor
```

Navigate your way through to apps -> nautlilus -> desktop

Now click the box next to 'computer_icon_visible'.

4)
Not sure if I know what you mean with this one, but go to 'Places', then 'Computer'.  Now you can navigate your way through: Filesystem -> usr.

If you want to access it with root privileges then hit alt+f2 and type:

```
gksudo nautilus /usr
```

5)
When you're in the directory hit ctrl+h

6)
In Terminal you need 1 more key:

To copy in Terminal: ctrl+shift+c
To paste in Terminal: ctrl+shift+v

---

### Post by Kilz on 2006-07-14
> **jincast90 said:**
> 1. Why can I only get a max resolution of 1024*768, when in Windows I can get upto 1280*1024. Yes my monitor supports it.

2. Can someone tell me the command, to change bootoptions. Example, change the time it takes to choose operation system, and make it so Windows boots first instead of Ubuntu (Or the other way around).

3. Is there any way to show "Computer" on the desktop?

4. How can I acces the /usr folder. (Please not in Terminal)

5. Is there any way to make all your hidden folders, not hidden? Eksampel, all the ones with the "." infront of them when you acces the home folder.

6. Is there any way to use the ctrl+c and ctrl-v commands in terminal, instead of using the mouse to copy and paste?

Thanks.
1. Have you installed the binary driver for your graphics card?
2. Yes ```
gksudo gedit /boot/grub/menu.lst
```will let you edit the list that shows up and rearange the order, be careful, if you mess it up you could make your sytem not boot.
3. Open the places menu, click on the computer icon, and drag it to the desktop.
4. Click Places > Computer > filesystem > usr
5. open your home folder, click edit, then preferences, click the box by show hidden and backup files to put a chek in it, click close, close the home folder and open it again.
6 Im not sure about copy, but Shift+Insert will paste into it.

---

### Post by arkangel on 2006-07-14
1.  go to  /etc/X11 andas su  edit xorg.conf 
in the section "screen" add the resolution modes 
for example 
SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "800x600" "640x480"
	EndSubSection

2. go to /boot/grub/ and as su  edit  menu.lst
look for  the line timeout  and change it to the value you  wish (10 sec by default) then  look for the line default (0 by defualt )  and put the number of your windows boot menu 

3  assuming you are using gnome as it comes in the default installation ,  and you have a menu called places in the task bar ,  drag and drop

4.  make a bookmark in nautilus , if i get ur question clearly :S

5. in nautilus  crtl+H  or >>view>>show hidden folders

6. no idea

---

### Post by jincast90 on 2006-07-15
Ok thanks guys, I got it all working.

Exept the first. Gotta look a little more into that one.

---

