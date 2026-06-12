---
title: "Feisty problems - Monitor sync and root password awal"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by cogvos on 2007-07-02
Dear all,

I thought I'd give 7.04 a bash (Feisty) on my AMD 64 box. I have two drives an IDE master with windows and an SDA which is Linux. For various reasons I don't let grub overwrite the MBR on the windows disk and installed it on hd2, which on my box is the sda.

Now the box allows you to select the drive to boot on, Selecting the sda switches it's drive number to 0, meaning that grub now cannot find it (grrr) I can edit the menu manually and after setting the root to be hd0 all boots OK.

Now the problems.

1. In order to make this permanent I need to edit the menu entry in Grub. But I can't as I do not have the su or indeed root passwords. I was not given the option to set these in the install and have no idea what the default is. Could someone tell me how to either set the root/su passowrd in the 7.04 install or what the default is.

2. Selecting 'logoff' from the shut down menu, so that I could have a bash at guessing the above pushed the display outside my monitor's scan range. Result a message on the screen telling me this and then a black screen. 
How do I force the display to stay on the same res/scan? the Monitor is an HP w2007v wide screen LCD on an Nvidia display card.

Hope someone can help, I'm stuck.

J.

---

### Post by Raineer on 2007-07-02
For the password, check out [this]("http://scottledyard.wordpress.com/2007/02/25/resetting-ubuntu-password-is-easy/") link.

---

### Post by cogvos on 2007-07-02
> **Raineer said:**
> For the password, check out [this]("http://scottledyard.wordpress.com/2007/02/25/resetting-ubuntu-password-is-easy/") link.

Many thanks, but there is something really odd. Tailing the passwd file only showed one user (me) no root. 
So I created a root password by doing passwd root and giving a password. 
Now in a terminal window  su root <ret> password gets me into the su account :D

But!

1. Ubuntu won't let root log on at the start
2. The system is telling me that the administration password is not the root one! In gnome if I try to install another package I am prompted for 'The password you use for administration activities.' If I enter the root password I get told its not the right one!! :(

So, I guess back to the first question. I have just installed 7.04. How the hell do you set the admin password , which is apparently different from root's  password if the install does not prompt you for it???! What is the default, please, anyone?

J.

---

### Post by Raineer on 2007-07-02
It should be *your* password. sudo takes the user's password to gain administrative access, this is the same thing you'd enter when Gnome asks you for the password when you first login.

If something is goofed up with that, try running:
```
sudo passwd
```
in a terminal and entering your user password instead.

oh, one edit:  Yes, ubuntu will not let you login as "root", you can expect that. You are to login under your username, and then you can "become root" if you want by entering
> sudo su
Although it isn't recommended to stay that way for long, the only real purpose would be if you're going to be running a lot of root commands in a row and want to save yourself the trouble of typing sudo that many times.

---

