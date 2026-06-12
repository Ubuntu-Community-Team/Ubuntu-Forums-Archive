---
title: "[SOLVED] Wine 9.39 problem"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by WebSiteGuru on 2007-08-09
Hi everyone,

I am a new Linux user. I am trying to install wine 9.39 so I can start loading PC Programs to my Ubuntu. I had installed the version of wine that come with the distro. But everytime I try to install any .exe from CD it will freeze up (or at least I think it did). 

I read some where in the forum and follow instruction to try to install wine 9.39 (since it is a version that will work correct as I understood.

But everytime I try to install the new version. It will not show Wine under Applications. PLZ HELP! I had been fighting with this problem at least a week now. thanks in advance!

---

### Post by MenZa on 2007-08-09
It won't show Wine because Wine is not a GUI application you open; to run a .exe file with Wine, open a terminal and type 'wine *file.exe*', obviously substituting *file.exe* with the name of your file.

I'd try to install the latest version of Wine (0.42) from their own [repositories](http://www.winehq.org/site/download-deb). Assuming you run Feisty, you can do so by running the following commands:

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update && sudo apt-get install wine

```

---

### Post by WebSiteGuru on 2007-08-09
Thanks, I'll try that tonight when I get home. :)

---

### Post by davidsrsb on 2007-08-09
If you install a program with wine, to run it you need

wine .wine/drive_c/Program\ Files/directory/program.exe

note that .wine is a hidden directory

---

### Post by splintercellguy on 2007-08-09
*~/.wine..., because you might not be in your home directory when you run it :).

---

### Post by WebSiteGuru on 2007-08-09
Cool! I'll keep those suggestion in mind. :D

---

### Post by WebSiteGuru on 2007-08-10
OK! It looks like I got wine under control. I had to run the command line to install .exe file through terminal. So far that is fine with me. But for some reason or other it will not install the .exe file correctly from the CD-ROM. It started the installation program, but when I click on install. It stop at the progress bar. :confused: I am confused.

Is this because of the hardware or CD-ROM driver issue?

---

### Post by MenZa on 2007-08-10
Check the application in the [Wine AppDB8](http://appdb.winehq.com).

---

### Post by WebSiteGuru on 2007-08-10
> **MenZa said:**
> Check the application in the [url=http://appdb.winehq.com]Wine AppDB8/url].

I did check it, the site said that somone had sucessfully installed it. And it should work. :confused:

---

### Post by Jofaba on 2007-08-12
> **MenZa said:**
> It won't show Wine because Wine is not a GUI application you open; to run a .exe file with Wine, open a terminal and type 'wine *file.exe*', obviously substituting *file.exe* with the name of your file.

I'd try to install the latest version of Wine (0.42) from their own [repositories](http://www.winehq.org/site/download-deb). Assuming you run Feisty, you can do so by running the following commands:

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update && sudo apt-get install wine

```

I'm trying to install wine, and everytime I try to add that apt key nothing happens. I copy the text into terminal, press enter, and it sends me to a blinking cursor. I continue with the installation and am told that I don't have the key. Any suggestions? 

EDIT: I'm not deleting this in case anyone else has a similar problem. BE PATIENT! I left the terminal window open while searching for a fix and when I went back to it, the key had been added. For some reason, it just took some time. So I think I'm set personally, but maybe my impatience will help someone else out one day =P

---

### Post by WebSiteGuru on 2007-08-17
OK! It seem like some of the programs on CD I can install, other seem to sit at install. I could be the CD-ROM that can not read the files. I'll see if I can do that with the external CD-ROM I just brought, to see if it still have the same problem.

---

### Post by TeaSwigger on 2007-08-17
In the event that some strange funky and unfathomable quirk is cursing wine when trying to install from your CD drive, you can also copy the entire CD to your hard drive, then mount it, and install from there. There are simple GUIs to mount 'em if you prefer, for instance gmount. I used this method to install from my Macromedia Suite 8 CDs.

---

### Post by WebSiteGuru on 2007-08-18
> **TeaSwigger said:**
> In the event that some strange funky and unfathomable quirk is cursing wine when trying to install from your CD drive, you can also copy the entire CD to your hard drive, then mount it, and install from there. There are simple GUIs to mount 'em if you prefer, for instance gmount. I used this method to install from my Macromedia Suite 8 CDs.

Thanks, I'll keep that in mind. :D

---

