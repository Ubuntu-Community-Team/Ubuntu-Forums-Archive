---
title: "[SOLVED] I Suck At Linux"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by capozziatc on 2008-02-28
alright this is my 3rd post in a matter of 2 days.   if i knew linux as well as i knew windows i could fix my user errors in seconds.  but i dont cause im a noob, and if i cant suddenly just figure out linux in the next few days im just going to go back to my vista.  yes u herd me i said it. :-/

ok new issue  how do i install nvida drivers?
instructions tell me to use terminal and type "sh NVIDIA-Linux-x86_64-169.12-pkg2.run"
but every time i do it it says "sh: can't open NVIDIA-Linux-x86_64-169.12-pkg2.run"

i am assuming i am having this error because terminal isnt in the directory that the file is placed on.  (which is the desktop)

i really, really need one of those Ubuntu for dummies books. :-(

Please Help!!!

---

### Post by oldos2er on 2008-02-28
cd Desktop

sh NVIDIA-Linux-x86_64-169.12-pkg2.run

---

### Post by amazingtaters on 2008-02-28
make sure the .run file is set as executable. Left click on the file, go down to properties, hit the permissions tab, and tick the box that says "Allow executing file as program"

then cd /Desktop or wherever the file is

post here again if that doesn't solve it

---

### Post by Crooksey on 2008-02-28
> **oldos2er said:**
> cd Desktop

sh NVIDIA-Linux-x86_64-169.12-pkg2.run

```

sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```

Or just use synaptic and search for Nvidia.

---

### Post by zephyrcat on 2008-02-28
To navigate around directories use the cd command. For example, if you are in your home folder (/home/username/) and you wanted to navigate to your desktop, you would type cd desktop.

Alternatively, in my expierience, most nVidia graphics card drivers can be installed automatically from the Restricted Drivers Manager, which is located under System -> Administration -> Restricted Drivers Manager.

---

### Post by Therion on 2008-02-28
You install and run [Envy](http://albertomilone.com/nvidia_scripts1.html); then kick back and let it do the work for you.

---

### Post by crjackson on 2008-02-28
```
sudo /etc/init.d/gdm stop
```

```
cd Desktop
```

```
sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```

then to restart X:

```
sudo /etc/init.d/gdm start
```

---

### Post by crjackson on 2008-02-28
> **Therion said:**
> You install and run [Envy](http://albertomilone.com/nvidia_scripts1.html); then kick back and let it do the work for you.

I use this myself these days...

---

### Post by Martin Witte on 2008-02-28
> **crjackson said:**
> 
then to restart X:

sudo /etc/init.d/gdm start

<CTRL><ALT>< Backspace> works as well to restart X

---

### Post by getaboat on 2008-02-28
Envy+1 here. I have nviidia on both my Fiesty and Dapper box. Envy has never let me down through a number of kernel updates (it is most useful when you have to run it from the command line)

---

### Post by capozziatc on 2008-02-28
> **oldos2er said:**
> cd Desktop

sh NVIDIA-Linux-x86_64-169.12-pkg2.run

it says directory doesnt exist

> **Crooksey said:**
> ```

sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```

Or just use synaptic and search for Nvidia.

when i did that it found the .run file but it said "sh cant open it" (it did make me input user name and password tho)

> **zephyrcat said:**
> To navigate around directories use the cd command. For example, if you are in your home folder (/home/username/) and you wanted to navigate to your desktop, you would type cd desktop.

Alternatively, in my expierience, most nVidia graphics card drivers can be installed automatically from the Restricted Drivers Manager, which is located under System -> Administration -> Restricted Drivers Manager.

when i type "cd desktop" or any "cd place" it says directory does not exist.  as for the restricted driver maneger it installs a driver but its not the right one it puts me to some really small resolutions 640 x 480 to be exact.

> **crjackson said:**
> sudo /etc/init.d/gdm stop

cd Desktop

sh NVIDIA-Linux-x86_64-169.12-pkg2.run

then to restart X:

sudo /etc/init.d/gdm start

i have no idea what just happend i did that and it loaded a black screen (simaler to basic dos) and it would give me ">" symbols but when i typed what u said to type the machine just didn't respond.

---

### Post by stchman on 2008-02-28
> **capozziatc said:**
> alright this is my 3rd post in a matter of 2 days.   if i knew linux as well as i knew windows i could fix my user errors in seconds.  but i dont cause im a noob, and if i cant suddenly just figure out linux in the next few days im just going to go back to my vista.  yes u herd me i said it. :-/

ok new issue  how do i install nvida drivers?
instructions tell me to use terminal and type "sh NVIDIA-Linux-x86_64-169.12-pkg2.run"
but every time i do it it says "sh: can't open NVIDIA-Linux-x86_64-169.12-pkg2.run"

i am assuming i am having this error because terminal isnt in the directory that the file is placed on.  (which is the desktop)

i really, really need one of those Ubuntu for dummies books. :-(

Please Help!!!

Installation of Nvidia video drivers is very easy.  You can enable the restricted drivers or install Envy and install the Nvidia drivers. Very easy.

To enable the restricted drivers go to System--->Administration--->Restricted Driver Manager and enable the Nvidia driver.  To use Envy go to [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by zephyrcat on 2008-02-28
Try typing "ls" in the terminal and post what you get. That will display all the files and folders in the directory you are in, so you can get an idea what directory you are in.

Also, when you tried the Restricted Drivers Manager did you try changing the resolution by going to System -> Prefrences -> Screen Resolution to see if it will let you use a higher resolution?

---

### Post by k33bz on 2008-02-28
woooooooooooo, whats envy?

---

### Post by Therion on 2008-02-28
I'll say it one more time.  Just use [Envy](http://albertomilone.com/nvidia_scripts1.html).

Why re-invent the wheel??

---

### Post by capozziatc on 2008-02-28
> **zephyrcat said:**
> Try typing "ls" in the terminal and post what you get. That will display all the files and folders in the directory you are in, so you can get an idea what directory you are in.

Also, when you tried the Restricted Drivers Manager did you try changing the resolution by going to System -> Prefrences -> Screen Resolution to see if it will let you use a higher resolution?

Yes i did try going to "System -> Prefrences -> Screen Resolution" and it gives me even lower resolutions than what i said previously

as for the "ls" command it says "desktop documents examples file: music pictures public templates videos"
i dont know what directory that is

---

### Post by philinux on 2008-02-28
> **k33bz said:**
> woooooooooooo, whats envy?

ENVY

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by capozziatc on 2008-02-28
> **Therion said:**
> I'll say it one more time.  Just use [Envy](http://albertomilone.com/nvidia_scripts1.html).

Why re-invent the wheel??

i am using it right know but im a noob at this. im a computer tech and i understand thinks when im told what thay are. however i dont know crap about linux.  so basicly i need to know how to do this type of stuff cause ive also got to get the drivers for the on board sound card.  ^_^ 

envy didnt work.  it decided to keep this 640 x 480 MAX resolution

---

### Post by zephyrcat on 2008-02-28
> **capozziatc said:**
> as for the "ls" command it says "desktop documents examples file: music pictures public templates videos"
i dont know what directory that is

OK, so you are in your home directory.  Type "cd" and then the exact name of one of the folders the "ls" command shows, so for example try typing "cd desktop" or "cd documents." I know you may have tried this before, but it really should work. (Capitalization may matter.)

---

### Post by crjackson on 2008-02-28
> **capozziatc said:**
> i am using it right know but im a noob at this. im a computer tech and i understand thinks when im told what thay are. however i dont know crap about linux.  so basicly i need to know how to do this type of stuff cause ive also got to get the drivers for the on board sound card.  ^_^ 

envy didnt work.  it decided to keep this 640 x 480 MAX resolution

Okay, you are a computer tech.  I'll break it down a little better for you.

1st of all, I'll ASSUME you have the correct driver for your system, and all other methods have failed. 
i.e. Restricted driver manager failed
i.e. Synaptic package manager failed
i.e. Envy failed..

**_[COLOR="Red"][SIZE="4"]PRINT THIS PAGE BEFORE YOU START!!![/SIZE][/COLOR]_**

This command will stop your Graphical Desktop Manager and drop you to a command line interface (like DOS)
```
sudo /etc/init.d/gdm stop
```

If you are in your Home directory, this will take you to your Desktop where you said the file is located.  The "D" in desktop must be uppercase.  CLI is case sensitive.
```
cd Desktop
```

This command will give you root priviliges (sudo) and then execute the driver binary.
```
sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```


This command will re-start your Graphical Desktop Manager (take you out of command line interface back to Desktop GUI)
```
sudo /etc/init.d/gdm start
```

---

### Post by capozziatc on 2008-02-28
> **zephyrcat said:**
> OK, so you are in your home directory.  Type "cd" and then the exact name of one of the folders the "ls" command shows, so for example try typing "cd desktop" or "cd documents." I know you may have tried this before, but it really should work. (Capitalization may matter.)

MWHA!!!!!!

i am so blind its not "cd desktop"   its "cd Desktop"  with a capital D  i knew it was case sensitive but i guess i just was so frustrated i forgot that little fact.  thank you know the driver installs yes.  and it actually is listed as a 8800 GM in the "system>administration>screen and graphics preferences.

but it didn't totaly solve the problem.  go down for further details.

> **crjackson said:**
> Okay, you are a computer tech.  I'll break it down a little better for you.

1st of all, I'll ASSUME you have the correct driver for your system, and all other methods have failed. 
i.e. Restricted driver manager failed
i.e. Synaptic package manager failed
i.e. Envy failed..

**_[COLOR="Red"][SIZE="4"]PRINT THIS PAGE BEFORE YOU START!!![/SIZE][/COLOR]_**

This command will stop your Graphical Desktop Manager and drop you to a command line interface (like DOS)
```
sudo /etc/init.d/gdm stop
```

If you are in your Home directory, this will take you to your Desktop where you said the file is located.  The "D" in desktop must be uppercase.  CLI is case sensitive.
```
cd Desktop
```

This command will give you root priviliges (sudo) and then execute the driver binary.
```
sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```


This command will re-start your Graphical Desktop Manager (take you out of command line interface back to Desktop GUI)
```
sudo /etc/init.d/gdm start
```


just to see if your way would work i uninstalled the driver and did it as u have it pasted here.  and it worked but also it didn't totally solve the problem.  btw im using my desktop to view this thread so i didn't need to print it.


ok i solved 1 problem and now i need to solve this 1024 x 768 max resolution.  i played around with
the "screen and graphics preferences" options.  and by selecting a different monitor driver. (in my case ive selected generic>LCD Panel 1024 x 768 its the highest one that works).  this monitor can to 1280 x 800 at 60 Hz.  ive looked all over the dell site and i cant find linux drivers forthis particular lcd screen.  maybe someone has an idea where i can get drivers for this monitor? (btw it was set to plug and play)

---

### Post by crjackson on 2008-02-28
> **capozziatc said:**
> MWHA!!!!!!

i am so blind its not "cd desktop"   its "cd Desktop"  with a capital D  i knew it was case sensitive but i guess i just was so frustrated i forgot that little fact.  thank you know the driver installs yes.  and it actually is listed as a 8800 GM in the "system>administration>screen and graphics prefrences.

but it didnt totaly solve the problem.  know i can bring the resolution up to 800 x 600






just to see if your way would work i uninstalled the driver and did it as u have it pasted here.  and it worked but also it didn't totally solve the problem.  btw im using my desktop to view this thread so i didn't need to print it.


ok i solved 1 problem and now i need to solve this 800 x 600 max resolution.  i played around with
the "screen and graphics preferences" options.  and by selecting a different monitor driver. (in my case ive selected generic>LCD Panel 800 x 600 its the highest one that works).  this monitor can to 1280 x 800 at 60 Hz.  ive looked all over the dell site and i cant find linux drivers forthis particular lcd screen.  maybe someone has an idea where i can get drivers for this monitor? (btw it was set to plug and play)

Good, glad it worked...

Now try this
```
sudo nvidia-settings
```

This should start your driver's built in settings manager

---

### Post by crjackson on 2008-02-28
Hopefully your settings manager will let you change your settings to what you need.  I'm at work and have to run now, so if this doesn't get you to the finish line, I'm sure some other kind soul will jump in at this point and take it there...

Before I go...  If the settings manager doesn't do the trick, you can edit you xorg.conf file and put the settings there yourself.  Just do a search on the forums for changing resolution etc...

---

### Post by capozziatc on 2008-02-28
want to know whats funny though?  if i start up the live cd it defaults to the correct video card driver and monitor (1280 x 800)



im starting to think ubuntu isnt the os for me.  im going to try one more thing (see if the live cd can automatically install the right drivers after ive specified which ones thay are)

---

### Post by Therion on 2008-02-28
Okay so you've got the correct video driver.  To correct the monitor resolution you need to open your xorg.conf file and change the default resolution ```
sudo dpkg-reconfigure xserver-xorg
```

Use the Tab button to move around, and highlight in red, the defaults for everything until you come to the part about Monitor Resolutions.  Look closely here...  There will be a little window with all the screen resolutions you can choose from, even though you'll only see about six or eight in the window (you can scroll up for higher resolution choices).   

Choose three resolutions here by using the spacebar to put an "*" in the ones you want to be able to use -- *the HIGHEST RESOLUTION you choose here will be the new default screen resolution.*  

Use Ctrl+X to overwrite the file with your changes, Save and Exit.  

Cross your fingers for good luck.

Use Ctrl+Alt+Backspace to restart X.

---

### Post by glennric on 2008-02-28
Whew, I am glad that the problem of you sucking at linux has been solved.

---

### Post by crjackson on 2008-02-28
> **glennric said:**
> Whew, I am glad that the problem of you sucking at linux has been solved.

Dude... That's too funny... :)

---

### Post by crjackson on 2008-02-28
> **Therion said:**
> Okay so you've got the correct video driver.  To correct the monitor resolution you need to open your xorg.conf file and change the default resolution ```
sudo dpkg-reconfigure xserver-xorg
```

Use the Tab button to move around, and highlight in red, the defaults for everything until you come to the part about Monitor Resolutions.  Look closely here...  There will be a little window with all the screen resolutions you can choose from, even though you'll only see about six or eight in the window (you can scroll up for higher resolution choices).   

Choose three resolutions here by using the spacebar to put an "*" in the ones you want to be able to use -- *the HIGHEST RESOLUTION you choose here will be the new default screen resolution.*  

Use Ctrl+X to overwrite the file with your changes, Save and Exit.  

Cross your fingers for good luck.

Use Ctrl+Alt+Backspace to restart X.

Good advice...  +1

---

