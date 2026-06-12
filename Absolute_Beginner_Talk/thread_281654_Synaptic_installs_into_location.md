---
title: "Synaptic installs into location?"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by jkvv_1973 on 2006-10-21
First of all Ubuntu is great...cant complain one bit--although im still a newbie


My problem is that I Install through Synaptic...

I realized that some programs are installed but I cant see it in app menu...I recently installed vsftpd but I cant see the program anywhere except in synaptic saying it is installed...

I need help to figure this out...Ive searched around the forum but I wasnt so  good at finding the answer...:(

---

### Post by taurus on 2006-10-21
Do you want to configure vsftpd?  The config file should be in /etc/vsftpd/vsftpd.conf and the binary should be in /etc/init.d/vsftpd...

---

### Post by moeFinley on 2006-10-21
Open up the terminal and type vsftpd

This should open the application.

---

### Post by jkvv_1973 on 2006-10-21
> **moeFinley said:**
> Open up the terminal and type vsftpd

This should open the application.

500 OOPS: vsftpd: must be started as root (see run_as_launching_user option)


this is what happened...anymore suggestions? just typed it plainly..."vsftpd"

---

### Post by gustolove on 2006-10-21
sudo vsftpd

^^type that in a terminal... it should run then

---

### Post by thornomad on 2006-10-21
vsftpd is not a GUI program ... as I understand it ... it runs in the background as a FTP server ... to configure it, go to edit /etc/vsftpd.conf to restart it after [configuration]("http://www.damontimm.com/blog/how-to-install-configure-ftp-server-vsftpd-on-ubuntu-linux/"), run: sudo /etc/init.d/vsftpd restart

I don't think it is a program you will ever "see", however.  I use it and I see nothing.

---

### Post by jkvv_1973 on 2006-10-21
> **thornomad said:**
> vsftpd is not a GUI program ... as I understand it ... it runs in the background as a FTP server ... to configure it, go to edit /etc/vsftpd.conf to restart it after [configuration]("http://www.damontimm.com/blog/how-to-install-configure-ftp-server-vsftpd-on-ubuntu-linux/"), run: sudo /etc/init.d/vsftpd restart

I don't think it is a program you will ever "see", however.  I use it and I see nothing.

oh really...I didnt know that...I was assuming it was a GUI based ftp client...thanks for the info guys...seems like Ive changed my mind...do you suggest any other program that is gui based???? Im windows centric and I am used to cuteftp...right now Im using filezilla...its gui based and it seems to do the job...let me know if theres better...again thank guys!

---

### Post by tubasoldier on 2006-10-21
Kbear, gFTP, KFTPGrabber, are all GUI clients, of course you can always use a filemanager as an ftp client in linux. In Konqueror just type in the address.

---

### Post by rfruth on 2006-10-21
gFTP has a nice GUI and works well for me (Gnome here)

---

### Post by catlett on 2006-10-21
BTW..If you still want a way to see all installed packages.
There is a 'Debian Menu' that can be installed in your gnome menu (the menu on the top panel). Ubuntu is based on Debian linux but for some reason the ubuntu developers leave out the debiam menu. I like the debiam menu because it displays all your applkications instaled by synaptic (actually all packages installed through apt. synaptic is the gui for apt)
To enable it, enter these commands
```
sudo apt-get install menu
```
```
sudo apt-get install xdg-menu
```
```
killall gnome-panel
```
```
update-menus
```
After all that, it should be under Applications
P.S. The first 2 commands install the packages needed to display the menu. The next one restarts the gnome panel which holds the gnome menu that we want to add the debian menu to. The last command refreshes all the menu lists. This is to just make sure the debian menu has everything listed.

---

### Post by CatKiller on 2006-10-21
Actually, I was using FileZilla in Windows. Worked OK for me. My other half seemed to get on OK with it after I uninstalled CuteFTP. Haven't needed to use a dedicated FTP client since I switched to Ubuntu.

---

