---
title: "Can't log in"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by hundur on 2006-01-14
Hi there, I installed Ubuntu 5.04 yesterday and everything was fine until i turned my computer on this morning. When i turn it on it loads like usual and then something like this appears 

[COLOR="DarkGreen"]"...*Checking battery state

Ubuntu 5.04 "Hoary Hedgehog" dhcppc1(my computer name on the network, I think) tty1

dgcppc1 login:     "[/COLOR]

I tried to log in with my user name(birgir) and write my password, but then this message appears:
> "Las login: Sat Jan 14 12:50:33 2006 on tty1
Linux dhcppc1 2.6.10-5-386 #1 Mon Oct 10 11:15:41 UTC 2005 i686 GNU/Linux

The programs included with the ubuntu system ar free software;
the exact distribution terms for each program are described in the individual files in /use/share/doc/*/copyright.

Ubuntu comes wit ABSOLUTELY NO WARRANTY, to the extent permittet by applicable law.
You have new mail.
birgir@dhcppc1:~$

I installed some programs (amsn) and I tried to install Firefox 1.5 but that didn't work.

Can you please help me

---

### Post by bscbrit on 2006-01-14
Well you have successfully logged in - what were you expecting?  It shows you as user 'birgir' on dhcppc1, which is the name of your machine.  I guess that you used to go straight into Gnome or KDE - right?  And now you have found yourself at the command line.

Try the following on the commandline:

gdm

---

### Post by rjwood on 2006-01-14
I suggest being careful when installing programs. One of the many differences between linux and windows is that you have to control what happens in your machine. With windows, when you install a program either from a disc or a download, the developer of the program is in control of your machine. It requires a little more scrutiny and work on your part but rather than being treated as a moron who can't do anything with your computer except point and click you are now a whole person.LOL!!!

---

### Post by hundur on 2006-01-14
[IMG]http://photos1.blogger.com/blogger/4745/727/1600/Picture%2033.jpg[/IMG]
This is webcam screenshot of the screen that comes now...


I used to go to the login screen that looks like this [IMG]http://static.flickr.com/8/11229312_8b5befa213.jpg[/IMG]

Can you tell me what to do?:O I tried to write GDM on that commandline, that doesn't work.

---

### Post by rjwood on 2006-01-14
what was the last thing you did before this happened?

---

### Post by bscbrit on 2006-01-14
I'm becoming confused - is the picture what you see _now_ or what you used to see?  If it is now, input your name, press [Enter], input your password and press [Enter] again.  What happens?

The command was 'gdm' not 'GDM'.  But it neither works then there is something else wrong....:razz:

---

### Post by hundur on 2006-01-14
I was trying to update some programs with EasyUbuntu, it never worked so i just turned the computer off and went to sleep.

The picture was just of the thing i saw, was trying to explain(thought you misunderstood me) but it seems to have gone the opposite way:p

---

### Post by rjwood on 2006-01-14
try ```
startx
```

---

### Post by Iowan on 2006-01-14
[QUOTE=hundur]Can you tell me what to do?:O I tried to write GDM on that commandline, that doesn't work.[/QUOTE]
 (My browser only showed your Ubuntu signon screen picture)
I presume you realize that "GDM" is not the same as "gdm".  I suspect you capitalized it only for emphesis... if not, try command in lower case.

[edit] I must have slow browser... beaten twice.

---

### Post by hundur on 2006-01-14
I wrote gdm (not with capital letters).

When i write startx i'm asked for password, i write my usual password but then it say's Login incorrect.

---

### Post by rjwood on 2006-01-14
you have to log-in first

---

### Post by hundur on 2006-01-14
Hmmm, i don't know why the webcam screenshot doesn't work, but here is it

[http://photos1.blogger.com/blogger/4745/727/1600/Picture%2033.jpg](http://photos1.blogger.com/blogger/4745/727/1600/Picture%2033.jpg)

---

### Post by rjwood on 2006-01-14
type 'ls' from where you are

---

### Post by bscbrit on 2006-01-14
Still cannot download it - but this is the error message! :p 

ERROR
The requested URL could not be retrieved

While trying to retrieve the URL: [http://localhost:10141/blogger/4745/727/1600/Picture%2033.jpg](http://localhost:10141/blogger/4745/727/1600/Picture%2033.jpg)

The following error was encountered:

    * Access Denied.

      Access control configuration prevents your request from being allowed at this time. Please contact your service provider if you feel this is incorrect. 

Your cache administrator is webmaster.
Generated Sat, 14 Jan 2006 16:00:24 GMT by photos2.blogger.com (squid)


COMMENT
The problem is with the URL.  Your 'localhost' is not the same as my 'localhost'.  You wiould have to use a full recognised domain name for anyone using a different computer to yourself.
/COMMENT

---

### Post by hundur on 2006-01-14
[QUOTE=rjwood]type 'ls' from where you are[/QUOTE]
I did that, and something happened ;) 
[COLOR="Blue"]
amsn_recieved      [/COLOR]                           [COLOR="Red"] firefox-1.5.tar.gz[/COLOR]
[COLOR="Blue"]Desktop  [/COLOR]                                         [COLOR="Red"]lmctl_0.3.2._i386.deb[/COLOR]
[COLOR="Red"]Easyubuntu-2.1.tar.gz[/COLOR]                        [COLOR="Blue"]lmctl_0.3.2._i386.deb_FILES[/COLOR]
[COLOR="Blue"][COLOR="Red"]Easyubuntu-2.4.beta4.tar.bz2----              logitech_applet-0.4test1.tar.gz[/COLOR][/COLOR]
[COLOR="Blue"]Easyubuntu-2.4.beta4.tar.bz2_FILES----   logitech_applet-0.4test1.tar.gz_FILES[/COLOR]


Does that help something?

---

### Post by rjwood on 2006-01-14
> **hundur]I did that, and something happened  said:**
> 
amsn_recieved      [/COLOR]                           [COLOR=Red] firefox-1.5.tar.gz[/COLOR]
[COLOR=Blue]Desktop  [/COLOR]                                         [COLOR=Red]lmctl_0.3.2._i386.deb[/COLOR]
[COLOR=Red]Easyubuntu-2.1.tar.gz[/COLOR]                        [COLOR=Blue]lmctl_0.3.2._i386.deb_FILES[/COLOR]
[COLOR=Blue][COLOR=Red]Easyubuntu-2.4.beta4.tar.bz2----              logitech_applet-0.4test1.tar.gz[/COLOR][/COLOR]
[COLOR=Blue]Easyubuntu-2.4.beta4.tar.bz2_FILES----   logitech_applet-0.4test1.tar.gz_FILES[/COLOR]


Does that help something?

OK-- so you are in your home directory.Do ```
sudo dpkg-reconfigure xserver-xorg
``` and  answer the questions. After that you will get back to the command line. Then ```
sudo reboot
``` see if that works

---

### Post by hundur on 2006-01-14
RjWood: I followed your comment and answered thos questions, did reboot and everything. After the reboot i'm back on the command line and nothing happens.

---

### Post by tokyovigilante on 2006-01-14
Reboot, login, and type the following command:

cat /var/log/Xorg.0.log | grep (EE)

exactly as it is above. Post the result, you may have to take a photo of the output.

Also post as much detail about the computer and its hardware as you can.

---

### Post by hundur on 2006-01-14
tokyovigilante: I can't do the | sign :S On this computer(windows computer with icelandic keyboard) i do ctrl+alt+<      But that doesn't work on that command line(although i have set Icelandic keyboard and can do icelandic letters in the command).

I have Shuttle An50r mainboard, with AMD processor(bought may 2004, don't know the exact type. I have Geforce 2 Titanium video card, and 1gb Corsair RAM. I have MSI cd/rw. And 3 HDD - two Seagate Barracuda and one Samsung.

---

### Post by tokyovigilante on 2006-01-14
On my US keyboard it's on the same key as backslash (ie SHIFT-\ enters a "|"). 

If you can't get it, try "startx" after logging on and post any errors you get.

Also, your GeForce 2 Ti is not supported by the nvidia-glx driver, if you have this installed. You need to install the nvidia-glx-legacy package instead, or use the nv driver.

---

