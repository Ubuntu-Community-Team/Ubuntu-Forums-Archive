---
title: "can't get into desktop!"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by jaws31415 on 2008-04-10
I was running ubuntu 7.1 with gnome.     when I boot the system it opens into a full screen terminal.   startx gives me a white screen.  in the terminal text entered doesn't show for about ten lines.  when I try to login to a user it goes blank then comes back to same terminal.  I even tried to reinstall ubuntu with a get apt command and it did the same thing

---

### Post by jaws31415 on 2008-04-10
I was running ubuntu 7.1 with gnome. when I boot the system it opens into a full screen terminal. startx gives me a white screen. in the terminal text entered doesn't show for about ten lines. when I try to login to a user it goes blank then comes back to same terminal. I even tried to reinstall ubuntu with a get apt command and it did the same thing.  I don't know anything about linux commands.. please help

---

### Post by siraf on 2008-04-10
Could you post the contents of your xorg file?
```
cat /etc/X11/xorg.conf
```

---

### Post by jaws31415 on 2008-04-10
yes, what am I looking for

---

### Post by smurphy_it on 2008-04-10
Post the entire file so that we can look at it.

The video driver part is of use in particular.

---

### Post by siraf on 2008-04-10
well, if you can't post those contents to the forums, what I'd look for are any sort of server options that definitely don't coincide with your graphics card setup. Don't change any values before backing up though! 
an easy way to backup would be:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```
and to restore (in case things go really screwy):
```
sudo cp /etc/X11/xorg.conf.back /etc/X11/xorg.conf
```

If your running hardy, I don't know how much has changed with the X11/conf structure. I'd recommend searching some other posts for some info.

Also, could you post your video card info, and your computer specs? (especially if it's a laptop)

---

### Post by jaws31415 on 2008-04-10
Toshiba satellite  a75-s231

Processor Intel Pentium 4 3.33GHZ OS ubuntu 7.1 
HD 100GB Drive DVDRW 
RAM 512MB Max RAM 1.28GB

---

### Post by jaws31415 on 2008-04-10
I can no longer view this file.  it says that it doesn't exist
cat etc/X11/xorg.conf

---

### Post by smartboyathome on 2008-04-10
Thats you problem then. Run this to get it back:
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by jaws31415 on 2008-04-10
I did this and got a message that says
"xserver-xorg postinst warning: overwriting possibly-customized configuration
          file; backup in /etc/X11/xorg.conf.20080410130922"

then it went back to the normal comand line
jaws31415@michael-laptop:~$

and it still says 'cat etc/X11/xorg.conf"   doesn't exist

---

### Post by smartboyathome on 2008-04-10
So it doesn't work, then. I would advise reinstalling Ubuntu at this point. Something borked it by removing your xorg.conf.

---

### Post by jaws31415 on 2008-04-10
that sucks.....do ya know a code to do the reinstallation?

---

### Post by opscure on 2008-04-10
you could try 
```
dpkg-reconfigure xserver-xorg
```
in the terminal and see if you can reconfigure your Xserver with the proper monitor/video/etc.

You could also give some more information such as the type of video card you are using and the contents of /etc/X11/xorg.conf

---

### Post by smartboyathome on 2008-04-10
The best way would be to reinstall Ubuntu from disk. Back up everything before you do that, though. You can backup your home folder and then reinstall, put your home folder back, and all the settings will still be there.

---

### Post by jaws31415 on 2008-04-10
this opened a rather strange menu. do you know what I should do now

---

### Post by jaws31415 on 2008-04-10
how do I do that

---

### Post by jaws31415 on 2008-04-10
so I went through the configure stuff and it went back to the terminal   so I put in 
startx   and I got this  
'fatal server error:
server is already active for display 0

                      if this server is no longer running, remove /tmp/.X0-lock
and try again.'          

   what should I do from here?

---

### Post by oldos2er on 2008-04-10
"and it still says 'cat etc/X11/xorg.conf"   doesn't exist"

 It doesn't exist, because the file you're looking for is /etc/X11/xorg.conf . You need the "/" at the beginning of the file location.

---

### Post by jaws31415 on 2008-04-10
ya that helps a bit.    but It just says default on everything or generic.  and I don't know how to scroll up to see what it went through

---

### Post by oldos2er on 2008-04-10
Then open it in a text editor: gksudo gedit /etc/apt/sources.list

---

