---
title: "monitor issue update"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by Dale McGarry on 2005-07-08
Eariler in the day, I asked for some help with a monitor issue in kubuntu. With the help of some people on the forum, I was able to fix my problem. However, I still have some questions. The only way I could get in the /etc/X11/xorg.conf file was to go through the run command and type "kdesu kwrite /etc/X11/xorg.conf". Nothing else worked. I tried to access the file through the Konsole terminal program using both the sudo and kdesu  commands, but  they didn't work. I am very confused by all of this, can someone take the time to explain the difference between the run command and the terminal  program and when you would use them.

Also, I found some game files in a sub folder called share/opps/appfinder/apps and would like to open them up so I can use them. Can anybody help me with that?

Thanks

---

### Post by ubuntu_demon on 2005-07-13
[QUOTE=Dale McGarry]Eariler in the day, I asked for some help with a monitor issue in kubuntu. With the help of some people on the forum, I was able to fix my problem. However, I still have some questions. The only way I could get in the /etc/X11/xorg.conf file was to go through the run command and type "kdesu kwrite /etc/X11/xorg.conf". Nothing else worked. I tried to access the file through the Konsole terminal program using both the sudo and kdesu  commands, but  they didn't work. I am very confused by all of this, can someone take the time to explain the difference between the run command and the terminal  program and when you would use them.

Also, I found some game files in a sub folder called share/opps/appfinder/apps and would like to open them up so I can use them. Can anybody help me with that?

Thanks[/QUOTE]

"sudo" means superuser do. "sudo" will prompt for "Password:". Please specify user password

So whenever you can't do a command without sudo in front because you don't have those permissions put sudo in front. So you should use sudo if you do things that effect your system. You shouldn't use sudo whenever you are doing stuff on your own (user) files. 

just an example :
Most desktop applications don't effect the system. That's why their configuration files are hidden in your home directory. So whenever you should need to alter or remove those files don't use sudo.

If you have an issue with your monitor again ==>
 sudo dpkg-reconfigure xserver-xorg for the monitor
after this close all your programs and press control-alt-backspace (this restarts gdm and it should take the new xorg.conf into account)

copy back the backup if your X doesn't start anymore ;)

Can you be more specific about the game files in a seperate thread in hoary's gaming section please ?

---

