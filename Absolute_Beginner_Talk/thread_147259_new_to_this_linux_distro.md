---
title: "new to this linux distro"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by plexy on 2006-03-19
Hello, I am sort of stuck on how do you install plugins for firefox. I have tryed but can not seem and have no idea what to do. I hope someone can help me. I also got a problem how do you find the command line, like to type commands etc.

---

### Post by Zeroangel on 2006-03-19
To bring up Gnome's version of the 'run' box, you just hit Alt+F2 . And type in gnome-terminal then hit enter, or you can use the menu [ Applications > Accessories > Terminal ]

As to your problems installing extensions. Are you using the default firefox that came with Ubuntu? Or are you using an updated version installed with Automatix/EasyUbuntu?

---

### Post by Zelut on 2006-03-19
To find the 'command line' you just need to open a terminal.  This is found in "Applications > Accessories > Terminal".

To install plugins/extensions for Firefox you should be able to simply go to the [Extensions page]("https://addons.mozilla.org/extensions/?application=firefox"), find the extension & click the install now button.  Most of them work with Linux.  I have only seen a few that are Windows specific.

---

### Post by NeghVar on 2006-03-19
On Gnome the Command line is at:

Applications>Accessories>Terminal

It should be the same on KDE but I don't know as Ive never used KDE.

---

### Post by TylerH on 2006-03-19
In firefox just go to Tools --> Extensions --> then click "Get More Extensions" down at the bottom of the window that pops up. Find the extension you're looking for then click "install now" on the website... firefox should handle it from there. Note that extensions require you to restart firefox for them to take effect. I recommend getting the "Restart Firefox" extension that sticks a restart option in the file menu.

As for the command console goto Applications --> Accessories --> Terminal


enjoi

---

### Post by catlett on 2006-03-19
Before you go crazy you can take the easy way out. Someone just turned me on to Automatix. This is a package that will give you Firefox 1.5 and all it's plugins. You can also get Opera and it's plugins. Plus much more very easily. Go to this link and find out more...[url]http://ubuntuforums.org/showthread.php?t=138405  .     Regards,Good luck.

---

### Post by plexy on 2006-03-19
Will thanks for everyone for helping me for finding the command thing.

I am having trouble doing a plugin in for firefox and the version is the one and latest Ubuntu has.

It says this:
To install the Plug-in Player for Linux via an install script, follow these directions:

 

- This installer is script-based and cannot be run from a GUI.

- Uncompress install_flash_player_7_linux.tar.gz.  A directory called install_flash_player_7_linux is created.  Navigate to this directory.

- From the command line, type ./flashplayer-installer to run the installer.  The installer will instruct you to shut down your browser(s).

- Once the installation is complete, the plug-in will be installed in your Mozilla browser.  To verify, choose Help > About Plug-ins from the browser's menu.

What does it mean "From the command line"? Were is the command line?

---

### Post by Cesium on 2006-03-19
The easiest thing to do is to use Automatix.  :)

---

### Post by plexy on 2006-03-19
Will can you help on. Were is the command line for installing a plugin?

---

### Post by Zelut on 2006-03-19
If you are simply trying to install flash capabilities to your browser that can be installed via Synaptic package manager (unless this is something different).  You should be able to search for "flashplayer-mozilla".

You may need to take a look at these as well..
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

...the command line you referred to is answered above.  Its also the "Terminal".

---

### Post by Zeroangel on 2006-03-19
I wouldn't recommend taking the manual install route unless you are comfortable with pulling yoru hair out. EasyUbuntu and Automatix will install all the plugins for you.

However if you do want to do it manually, the command line means the terminal. You would have to navigate to the directory where the flash installer is. Ok, lets say that your flash installer is in this folder.

/home/dave/Downloads/install_flash_player_7_linux

You would open up the terminal (it starts off in your home folder)
```
dave@ubuntu:~
``` And navigate to the folder where the flash installer is:
```
[COLOR=Silver]dave@ubuntu:~$[/COLOR] cd Downloads[COLOR=Silver]
dave@ubuntu:~/Downloads$[/COLOR] cd install_flash_player_7_linux[COLOR=Silver]
dave@ubuntu:~/Downloads/install_flash_player_7_linux$[/COLOR] ./flashplayer-installer
```

---

### Post by plexy on 2006-03-19
Ok, thanks.

What is the firefox area on my computer. Like were is the exact location for default firefox.

---

### Post by plexy on 2006-03-19
Ok I done that but it says:

ERROR: Your architecture, \'x86_64\', is not supported by the
       Macromedia Flash Player installer.



What does it mean?

---

### Post by Zeroangel on 2006-03-19
Are you using an Athlon 64 processor? If you are then I have some bad news. Some apps are not compatible with Athlon 64's because they are designed much differently then Athlon XP's and Pentiums. However, you could try looking for a version that will work with Athlon 64s.

Maybe someone who is familiar with getting Athlon 64 processors to work can help you.

---

### Post by plexy on 2006-03-19
Yes, I have an AMD 64 one. So can you still find a 64 for ubuntu? Or it does not exist yet?

---

### Post by plexy on 2006-03-19
Is they are 64bit one for firefox flash player plugin or no?

---

