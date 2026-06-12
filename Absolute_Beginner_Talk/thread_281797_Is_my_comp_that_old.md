---
title: "Is my comp that old?"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by Lt.Ross on 2006-10-21
I recently installed ubuntu 5.10 for Intel x86 based system onto my Compaq presario 100c series computer which has a 433Mhz celeron processor, 256 MB SD RAM(originally came with 64 MB SD RAM and this computer is almost 6 years old), 40 GB hard disk, using the install CD which my friend got through Shipit.
The system also has a windows xp sp2 os installed on other partition. 

Now the problems:
.Any operation on ubuntu is taking a lot of time.
.There is only one user for ubuntu OS and that is me but i couldn't open many applications and there were error messages saying that i don't have the permission to do that operation.So i tried to login as the root but there comes the exact problem,
during installation i don't remeber being asked to provide a root password, i think it asked me only to provide the username for the default user and its password and this is the same username and password using which i logged in before.
.The next main problem is on entering any text using the keyboard.
On a single keystroke i get many echos of the entered character
This problem usually goes when i restart the system.

Please help me out.I very dearly want to work in linux using ubuntu but i am afraid that my old system is not compatible with the OS or is it because of any other problem?

---

### Post by raul_ on 2006-10-21
your computer is fine.
You're not supposed to login as root. If u want to run applications try running them by the terminal (don't be afraid of it, nor to search/post your doubts) 
About the time and the keyboard problem..did u try searching for similiar problems here in the forums? It sounds like the kind of problem other people would have, so i'm pretty sure it has been posted :)

---

### Post by guysmiley25 on 2006-10-21
I'll try to help the best I can

Any operation on ubuntu is taking a lot of time.

I'm running ubuntu 6.06 LTS on a simlier system and it is really slow as well.

There is only one user for ubuntu OS and that is me but i couldn't open many applications and there were error messages saying that i don't have the permission to do that operation.So i tried to login as the root but there comes the exact problem,
during installation i don't remeber being asked to provide a root password, i think it asked me only to provide the username for the default user and its password and this is the same username and password using which i logged in before

With ubuntu 6.06 LTS the root password is the same as the one when you setup the first user. I would expect it do be the same with your version. In ubuntu insted of using the root account to make changed to the system you use
```
sudo command
```
eg
```
sudo shutdown -r now
```

The next main problem is on entering any text using the keyboard.
On a single keystroke i get many echos of the entered character
This problem usually goes when i restart the system.

Not sure about this. Have you tryed a other keyboard?

---

### Post by Sef on 2006-10-21
> Compaq presario 100c series computer which has a 433Mhz celeron processor, 256 MB SD RAM

Your processor is a slow for Ubuntu.  It would run better under Xubuntu which is made for older hardware.

---

### Post by Engnome on 2006-10-21
> **Sef said:**
> Your processor is a slow for Ubuntu.  It would run better under Xubuntu which is made for older hardware.

Xubuntu would be slugish with that hardware to. To slow for me atleast. Have a look at the suggestions here: [http://https://help.ubuntu.com/community/Installation/LowMemorySystems]("http://help.ubuntu.com/community/Installation/LowMemorySystems") IceWm or maybe even fluxbox would be more suitable. Maybe a little tougher for the beginner to set up but that machine would be a good web browser computer.

---

### Post by Bloch on 2006-10-21
I ran puppy linux on a 400 MHz with 96MB ram and it was great. Go to an internet cafe and burn an iso of it. 

I suppose the advantage of running xubuntu would be that you would get a lot of extra hardware compatibility - more kinds of printers, monitors, keyboards etc will be supported, the other advantage is the very active forum here.

But if puppy works (try the live disk) then you'll probably stick with it.

---

### Post by raul_ on 2006-10-21
Or DSL

---

### Post by redDEADresolve on 2006-10-21
> **raul_ said:**
> Or DSL

He means damn small linux

[http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)

---

### Post by gn2 on 2006-10-21
> **Lt.Ross said:**
> I recently installed ubuntu 5.10 for Intel x86 based system onto my Compaq presario 100c series computer which has a 433Mhz celeron processor, 256 MB SD RAM(originally came with 64 MB SD RAM and this computer is almost 6 years old), 40 GB hard disk, using the install CD which my friend got through Shipit.
The system also has a windows xp sp2 os installed on other partition. 

Now the problems:
.Any operation on ubuntu is taking a lot of time.
.There is only one user for ubuntu OS and that is me but i couldn't open many applications and there were error messages saying that i don't have the permission to do that operation.So i tried to login as the root but there comes the exact problem,
during installation i don't remeber being asked to provide a root password, i think it asked me only to provide the username for the default user and its password and this is the same username and password using which i logged in before.
.The next main problem is on entering any text using the keyboard.
On a single keystroke i get many echos of the entered character
This problem usually goes when i restart the system.

Please help me out.I very dearly want to work in linux using ubuntu but i am afraid that my old system is not compatible with the OS or is it because of any other problem?


Surely can't be slower than XPsp2 on the same hardware?

---

### Post by Sef on 2006-10-21
> Surely can't be slower than XPsp2 on the same hardware?

Well could be.  Depends on the hardware.

---

### Post by Lt.Ross on 2006-10-22
It seems that whenever the system boots on ubuntu 5.10 [COLOR="Magenta"]normally[/COLOR], i.e without the keyboard problem that i mentioned ,the response time seems pretty okay when compared to the windows xp that i've loaded in my comp.So i am comfortable with the speed for the time being and that is not the main problem right now.

.In my first post i forgot to mention that i tried :[COLOR="Blue"]sudo[/COLOR], at the terminal but the feedback was:
[COLOR="Blue"]unable to lookup 'whatever name i used as the user' via gethostbyname()[/COLOR]

.After booting a message is displayed saying this:
[COLOR="Blue"]couldn't lookup internet address for 'whatever name i used as the user' and this could prevent GNOME from operating correctly and that adding 'whatever name i used as the user' to /etc/hosts will may correct it [/COLOR] 

.When i tried to open up and add 'whatever name i used as the user' to this file it opened in [COLOR="Blue"]read only mode [/COLOR]and a message was displayed which said [COLOR="Blue"]i am not the primary user.[/COLOR]
 And for this matter whichever file i tried to open, opened in [COLOR="Blue"]read only mode.[/COLOR] 

Can anyone help me out once more??

---

### Post by CatKiller on 2006-10-22
It's possible that your /etc/hosts file is malformed in some way, possibly by direct fiddling. I know I managed to bugger mine up so that I couldn't sudo anymore. And the 'whatever name i used as the user' isn't your user name at all. **Don't** put user names in your hosts file. It's the **machine name** that goes in /etc/hosts, and it must be the **same** name that's in /etc/hostname, otherwise other things will break.

If you can use sudo, you should edit your hosts file to make it not broken. If you can't use sudo, you should boot from the live cd, mount your linux partition and then edit your hosts file to make it not broken.

---

