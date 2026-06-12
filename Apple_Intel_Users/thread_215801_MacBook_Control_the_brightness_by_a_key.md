---
title: "MacBook: Control the brightness by a key"
date: 2006-07-14
forum: Apple Intel Users
---

### Post by alexinfurs on 2006-07-14
Hi, I wrote a simple program that allows you to control the screen brightness by a keypress.

It's based on a desrt's macbook-backlight program, so you have to install it before. Go here [http://desrt.mcmaster.ca/macbook.xhtml]("http://desrt.mcmaster.ca/macbook.xhtml") and follow the instruction to install a macbook-backlight packet.
Afetr installed it, make it executabile for all user by command :
sudo chmod u+s /usr/bin/macbook-backlight

now install my program
1) unpacking tar
2) make sure you have installed a libgtk2.0-dev and libvte-dev
 packages
3) enter into a src directory
4) execute - sudo make install
Now you have a macbook-backlight-control program into /usr/bin/
I suggest to add it to startup-application in a system-preferences-sessions menu.

Now you can lower and raise the brightness by Ctrl-F1 and Ctrl-F2

If you found any bugs, please contact me.
[email]alexinfurs@gmail.com[/email]

my blog [http://alexinfurs.blogspot.com/]("http://alexinfurs.blogspot.com/")


I have tested it only on my macbook.

---

### Post by frigaut on 2006-08-01
hi,

you also need libvte-dev

---

### Post by alexinfurs on 2006-08-07
Yes, of course! 
Thanks a lot!

---

### Post by leonedo on 2006-08-13
great work!! thanks.. is there any way to set a default value to the  brightness?? with your program or directy with the macbook-backlight packet??

---

### Post by kristof_v on 2006-12-03
hi

i compiled your app on my debian macbook.
it compiled just fine but when i run the program nothing seems to happen.
pressing ctrl-f1 or ctrl-f2 has no effect.

any ideas??

grtz

---

### Post by rigdzinthar on 2007-06-15
you might have to rebind if you are using beryl

---

### Post by Gen2ly on 2007-06-16
Ohh neat.  Light weight, seem unobtrusive.  Well done.  I assume you did research before starting this?  I heard (rumor only) this was to be a new feature in gnome 2.20, is this so?

---

### Post by ExplodingPickle.org on 2007-06-30
I am using Kubuntu and Ctrl-F# are used to switch desktops. I don't want to change the shortcut in Kubuntu, but don't see any way to configure the program, or what part of the code stores the keyboard shortcut. Can anyone tell me where this value is stored in the code, and how to change it to a different key combination?

---

### Post by kzm. on 2007-07-01
i use the fn+f1/f2. makes sense to me. follow those steps:

    ```
sudo apt-get install sysfsutils
    sudo gedit /etc/sysfs.conf
    add: module/hid/parameters/pb_fnmode = 2
    reboot
```

---

### Post by rosegarden78 on 2008-01-19
Or type the following command in a terminal:

xgamma -gamma 0.75

If that doesn't work you need to install xgamma from the repos.

I have posted my own solution here on setting it up:

[http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---

