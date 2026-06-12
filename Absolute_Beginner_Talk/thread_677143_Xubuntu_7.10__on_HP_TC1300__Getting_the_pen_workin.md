---
title: "Xubuntu 7.10  on HP TC1300 : Getting the pen working?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by foxie on 2008-01-24
I have seen the following reference on the forums quite a number of times "Uncomment the following lines in /etc/X11/xorg.conf "

# InputDevice "stylus" "SendCoreEvents" 
#InpuDevice "cursor" "SendCoreEvents"

I can navigate to "xorg.conf" via the files menu, backspace the "#", but for the life of me i have not been able to save the amended file.

Would someone please go through this process step by step so that I end up being able to use my pen after following the instructions.

It is my intention to get the pen working as a cursor first, then get as much of the tablet facilities going as possible.

The ultimate aim is to say a thankful goodbye to MS Windows. Thanks.

---

### Post by eggdeng on 2008-01-25
You need to edit the file as superuser.
Just in case, first back up the file. Open a terminal and type
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp
```
Then type
```
sudo gedit /etc/X11/xorg.conf
```
This opens the file using the gedit text editor. If you don't have gedit in Xubuntu, substitute the name of your preferred text editor for gedit.
Edit & save. You will need to log out and back in for changes to take effect.

---

### Post by foxie on 2008-01-25
Thanks eggdeng, pen now working:)

---

