---
title: "Help with tarballs"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by drisco on 2007-04-30
[B]Hello I am currently running Ubuntu 6.06 LTS with GNOME 2.14.3 and I have read three different links on how to install tarballs and I just can't figure it out.  If someone could give me a push in the right direction that would be very greatly appreciated.

I tried this one [http://tech.cybernetnews.com/2007/04/17/how-to-install-tarballs-on-linux/](http://tech.cybernetnews.com/2007/04/17/how-to-install-tarballs-on-linux/)
and this one [http://www.newlinuxuser.com/howto-install-deb-rpm-and-source-code-files/](http://www.newlinuxuser.com/howto-install-deb-rpm-and-source-code-files/)

and if someone could give me some step by step instructions on how to do it that would be soooo great.

P.S. Im a complete linux noob and this is my first time running it and I'd really like to learn more about linux and so far i love it.
[/B]
-drisco

---

### Post by confused57 on 2007-04-30
Maybe this will help:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by AscendedDaniel on 2007-04-30
Usually, .tar.gz is the source code of the program. There are steps that work in general, but each program is different. If you have specific questions, feel free to ask them, but in general, I'd encourage you to read the README and INSTALL files included with the tarball or the instructions on the website. Are you trying to install a specific program?

---

### Post by TwistesdTexan on 2007-04-30
[PHP]1. Click the "Download Now" button. A dialog box will appear asking you where to save the Installer.
2. Save the Installer to your desktop and wait for the file to download completely. 
3. Unpackage the file. A directory called install_flash_player_7_linux will be created. 
4. Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s).
5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.
Get answers about Adobe Flash Player privacy practices, licensing, Macromedia Flash content development, and more in our list of Frequently Asked Questions (FAQ). 
For more information on Adobe Flash Player and privacy, please read about Adobe Flash Player privacy settings and the Adobe Flash Player Settings Manager , or view the Macromedia privacy policy. [/PHP]

I saved this to a doc file for me to reference when I need to download and install a tar file.

---

### Post by drisco on 2007-05-01
**Im trying to install mythtv and beryl and i searched around and everytime I type in the command from this website [http://tech.cybernetnews.com/2007/04/17/how-to-install-tarballs-on-linux/](http://tech.cybernetnews.com/2007/04/17/how-to-install-tarballs-on-linux/) the terminal says "Error package not found".  Im at school right now and I'll be home in about 2  hours and I'll try the link confused57 posted and see if that works.**

-drisco

---

### Post by drisco on 2007-05-01
*Build it with ./autogen.sh --prefix=/usr && make && sudo make install[/B]*

[B]This was in the README file of the file i want  to install.  And I type in ./autogen.sh and I don't know which variables I change to what and what order to type all of it into the terminal in...help?

*Build it with ./autogen.sh --prefix=/usr && make && sudo make install[/B]*

-drisco

---

### Post by drisco on 2007-05-01
*Build it with ./autogen.sh --prefix=/usr && make && sudo make install*

**This was in the README file of the file i want  to install.  And I type in ./autogen.sh and I don't know which variables I change to what and what order to type all of it into the terminal in...help?**

-drisco

---

### Post by confused57 on 2007-05-01
> **drisco said:**
> *Build it with ./autogen.sh --prefix=/usr && make && sudo make install*

**This was in the README file of the file i want  to install.  And I type in ./autogen.sh and I don't know which variables I change to what and what order to type all of it into the terminal in...help?**

-drisco
I'm no expert, but after you extract the tarball & cd to the extracted directory, you could enter the entire line as it is or one line at a time:
```
./autogen.sh --prefix=/usr
make
sudo make install
```

---

