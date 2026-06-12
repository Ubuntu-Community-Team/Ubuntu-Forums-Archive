---
title: "cant install"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by UK-Andy on 2006-08-25
hi i am new to ubuntu i have installed this onto a pc but it only gets to a screen for me to log in then it appears to be waiting for a command.  what command do i need ?                 i have installed  ubuntu-server-5.10-install-i386 linux  on a pentium 333 i do have some error messages      

 [  68.574661] PCI: cannot allocate resource region 9 of bgridge 0000:00:02:0  

initializing.random number generator   [fail]  
  
any help you could give me with this would be great
    Thanks 
           Andy

---

### Post by muep on 2006-08-25
Are you getting a black-and white screen with only text in it, or do you get a fully graphical login screen with working mouse and stuff?

Can you post as much information of your hardware as possible? Especially the graphics card and display models are important now. Also, how much RAM do you have in the computer?

Also, Ubuntu 6.06 has been released. It is newer than 5.10 and might work better. Have you tried it? 5.10 should work fine though, especially on older machines.

---

### Post by muep on 2006-08-25
If you are only getting the text-only screen, it means that the X server has failed to start and you have the option to log in to a command-line terminal. The graphics can probably be fixed from here, if you just be patient and ask for instructions. The help will be in the form of commands for you to write in the terminal. It's basically just copying the commands and telling the results here, so it is not very hard. It just takes patience.

---

### Post by UK-Andy on 2006-08-25
yes i get a black and white screen 
i can type help and get a list of commands but i cant see all of them 
how can i scroll up the page ?
this is an old pc with onboard graphics and sound 
i dont have any more details realy about it 
i get to put my username and password in then it appears to be waiting for me to type a command

Thanks 
       Andy

---

### Post by 3rdalbum on 2006-08-25
> **UK-Andy said:**
> i have installed  ubuntu-server-5.10-install-i386 linux

The Server installation does not include a graphical user interface. If you don't mind retrieving a couple of hundred megabytes of packages from the Internet, when you get the command-line prompt type:

```
sudo apt-get install ubuntu-desktop
```

After everything is installed, type:

```
sudo halt
```

Then start up again, and you'll get the GUI.

---

### Post by nick.burnination on 2006-08-25
I'm also having a problem installing.  I get to the splash screen on the Live CD (AMD64 Desktop) and press enter to boot/load.  The disk verifies, and goes to a screen that looks like a terminal.  I get the message that says something to the effect of "booting the linux kernel".  This took awhile, so I just left it up....overnight...and nothing happened.  I understand that all distros of linux are OSes first, and they take a minute or 5 to boot.

Here are my hardware specs:

AMD 64 X2 3800+
Asus A8N32 SLI
XFX 7800GT
Plextor and LiteOn DVD drives
2GB of Corsair XMS 3200

Primary OS is WIndows XP Professional x64-Edition

Thanks for the help

---

### Post by nick.burnination on 2006-08-25
*bump*

---

