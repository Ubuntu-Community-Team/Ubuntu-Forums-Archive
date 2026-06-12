---
title: "Installing a .deb?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by PartyTaco on 2007-05-12
Ok so I downloaded a .deb from my windows laptop, put it on a usb drive, transfered it to my ubuntu 7.04 desktop and tried to run the command after logging in as root:

dpkg -i bcm43xx_compwiz18.1-all.deb

I am 100% sure the file name is correct. But it just tells me it cannot find the package....


Any ideas?

---

### Post by Perfect Storm on 2007-05-12
You can doubleclick the .deb file.
If you use the commandline make sure to **cd <distination>** or else it can't find it.

---

### Post by Dev'olution on 2007-05-12
1) try sudo dpkg -i and then tabbing as u type the name... that will confirm the file name

2) Make sure it has fully copied and you can see it on the desktop.

3) Or what AI said.

---

### Post by PartyTaco on 2007-05-12
1. where would I put cd? or for that matter, is it a command? How do I use cd. Please use an example.

2. What does tabbing mean, and how do I do it?


Edit: I feel silly, I just double clicked it. It brought up the install screen. I am still trying to get used to linux after using windows since windows 95. So...Thanks!

But if you really feel like it, please explain questions 1 & 2.

:] Thanks!

---

### Post by Dev'olution on 2007-05-12
> **PartyTaco said:**
> 1. where would I put cd? or for that matter, is it a command? How do I use cd. Please use an example.

2. What does tabbing mean, and how do I do it?


Edit: I feel silly, I just double clicked it. It brought up the install screen. I am still trying to get used to linux after using windows since windows 95. So...Thanks!

But if you really feel like it, please explain questions 1 & 2.

:] Thanks!

1. Go to terminal

2. type 'cd Desktop'

3. type in 'dpkg -i blah.deb' where blah is the file name...

4. Tabbing is pressing the tab key on ur keyboard

:popcorn:

---

### Post by ramjet_1953 on 2007-05-12
1. If the file is on your desktop, go to 3, otherwise, Open your File Browser

2. Navigate the tree, until the file you want to install is in view.

3. Right-click on it

4. Select "Install with "GDebi Package Installer"

Regards,
Roger 8)

---

### Post by Jussi01 on 2007-05-12
Just for your future use and hoping you understand clearly, cd is a command (cd = change directory) so when you open your terminal, it automatically opens in your home directory. (ie. /home/username) so as mentioned earlier, to get to your desktop you need to change the directory you are in. This means that you issue the command: cd Desktop this will take you to the desktop and you can run your dpkg command. you can also go back down a directory by using cd .. 

hope this helps

Jussi

---

### Post by iPirates on 2007-05-12
cd means "change directory".

when you open up a terminal, the default directory it starts in is your home directory.
so when you try to run the deb file using dpkg in the terminal, it'll look for it in the directory you're currently in.  If you put the .deb file on your desktop, it wont be in your home directory, however it will be in the folder called "Desktop" in your home folder.

So you have to either do:

sudo dpkg -i /home/"Your user name"/Desktop/whatever.deb

or 

cd Desktop

and then

sudo dpkg -i whatever.deb

Here's a good site for learning how to navigate around in the terminal:  
[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)


EDIT - or what he said just above... that's what i get for leaving for a few before posting.   still, check out the site, it helped me a great deal.

---

### Post by Vixis on 2007-05-12
Explanation of the most often used commands in terminal: [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

### Post by alienexplorers on 2007-05-12
I use the GDebi Package Installer.  All you have to do is double click on the .deb file and the installer opens and you select Install package.

---

