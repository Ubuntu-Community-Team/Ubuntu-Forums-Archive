---
title: "Install flash"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Stone9 on 2006-09-17
Hi guys!

I'm trying to install flash using the instructions on their website:


1. Click the "Download Now" button. A dialog box will appear asking you where to save the Installer.

2. Save the Installer to your desktop and wait for the file to download completely.

3. Unpackage the file. A directory called install_flash_player_7_linux will be created.

4. Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s).

5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

But when I open the Terminal and enter the command I get:

bash: ./flashplayer-installer: No such file or directory

I'm unfamiliar with the way the file directory is setup. If the file is on the desktop, what is the command for running the setup application for Flash?

Thanks in advance guys!!!

---

### Post by whizbaby on 2006-09-17
When you open a new terminal you start in your homedirectory, the command **cp** makes you move to other directories. So let's assume your flashplayer-installer is in *Desktop/install_flash_player_7_linux/*:
open a terminal and type
[B]cd Desktop/install_flash_player_7_linux
ls -la[/B] (to check if it is there and has an **x** in it's permissions)
if it's there and can be executed
**./flashplayer-installer**

---

### Post by LookTJ on 2006-09-17
also enable the repos "non-free"

---

### Post by hopstah on 2006-09-17
i have two suggestions - first, add the letters 'sh' before the ./flashplayer-installer.

second, start typing the name of the file and then hit the tab button.  the tab button will auto complete the file name if it exists, so you don't have to worry about misspelling or typing the whole thing out.

---

### Post by xyz on 2006-09-17
Just in case:
[http://www.ubuntuforums.org/showthread.php?t=257206](http://www.ubuntuforums.org/showthread.php?t=257206)

---

### Post by Stone9 on 2006-09-17
Great! Thanks guys!!!

---

### Post by xpod on 2006-09-17
AND of course if you fancied having an app that would allow you to easily install all the typical new requirements such as flash and java not to mention the numerous codecs you might want.
 It also has some good stuff like gdesklets,swiftfox,wine and skype and many others.
 Just thought i`d tell you as no-one else has pointed it out and it`s usually the first thing somebody points out after a request for "flash" and the likes.

Although of course it is a much better thing to be doing it all yourself without the use of automated apps like automatix or easy ubunto.
I wish i was as brave=D> :biggrin:

EDIT:..Of course the thread below is not a good advert for it but this is a rare problem i believe:rolleyes:

---

### Post by xyz on 2006-09-17
xpod...you're a very funny man!
But what else could we expext from a "Scotlands biggest region....London" guy!!!lol

---

### Post by xpod on 2006-09-17
Did you spot it then???=D>:biggrin:

---

