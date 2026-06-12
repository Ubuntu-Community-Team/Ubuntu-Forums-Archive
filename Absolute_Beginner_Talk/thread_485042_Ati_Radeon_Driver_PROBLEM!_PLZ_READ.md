---
title: "Ati Radeon Driver PROBLEM! PLZ READ"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by proplaya23 on 2007-06-26
I have Ubuntu 7.04 amd64 installed, and i also have an Ati Radeon x800 Crosffire Edition.

Heres My problem, i downloaded the new Ati Drivers for linux_x86_64 from ati.amd.com and when i double click it it says "Could not open the file ati.........blah blah" in gedit

any help would be appreciated as i am a total Linux NumNUB :D

---

### Post by Rocket2DMn on 2007-06-26
In what format is the file?  You might need to set it as executable, I don't imagine you want to open it in a text editor unless you're trying to access the install directions.

---

### Post by w4ett on 2007-06-26
Did you read this sticky on fglrx install:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

It gives pretty concise and clear instructions.

---

### Post by proplaya23 on 2007-06-26
the file is a shell script

---

### Post by proplaya23 on 2007-06-26
> **w4ett said:**
> Did you read this sticky on fglrx install:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

It gives pretty concise and clear instructions.

yes i have read this sticky and dont really know were to put those lines of code in??

terminal??

---

### Post by Rocket2DMn on 2007-06-26
Then make sure the file is executable and run
```
cd /path/to/file
./filename.sh
```

These commands are run in terminal

---

### Post by proplaya23 on 2007-06-26
i right clicked the file and went to properties and checked the execute file box and it doesnt give me the error no more but nothing happens when i double click it.

---

### Post by w4ett on 2007-06-26
> **proplaya23 said:**
> yes i have read this sticky and dont really know were to put those lines of code in??

terminal??
  All commands are from the command prompt in the terminal

---

### Post by proplaya23 on 2007-06-26
> **w4ett said:**
> All commands are from the command prompt in the terminal

ok thx i will try out the commands from that sticky and get back to you guys.


thx for quick responses:D

---

### Post by proplaya23 on 2007-06-26
i did everything said in the ati x**** sticky and then tried to reexecute the file but still no luck if u need a screen shot of the error i will post it?

---

### Post by proplaya23 on 2007-06-26
here it is

---

### Post by Rocket2DMn on 2007-06-26
Try running these commands in terminal:
```
cd /home/moe/Desktop

chmod +x ati-dr[press tab here to autofill]

./ati-dr[tab here]
```

if it doesn't let you run the file, try using "sudo" at the beginning of the line - you will be prompted for your PW

---

### Post by proplaya23 on 2007-06-26
> **Rocket2DMn said:**
> Try running these commands in terminal:
```
cd /home/moe/Desktop

chmod +x ati-dr[press tab here to autofill]

./ati-dr[tab here]
```

if it doesn't let you run the file, try using "sudo" at the beginning of the line - you will be prompted for your PW

moe@moe-desktop:~/Desktop$ ./ati-driver-installer-8.38.6-x86.x86_64.run 
Created directory fglrx-install.C20168
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.38.6..........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 7.1 and later releases 64-bit
Removing temporary directory: fglrx-install.C20168

thats what happened i guess it worked....should i reboot now?

---

### Post by Rocket2DMn on 2007-06-26
Cool, you probably need to restart the xserver now.  You can either reboot your computer or just close all your apps and use Ctrl+Alt+Backspace and you will be taken back to the login screen (assuming everything worked).
In the case that the driver installed fails and the Xserver doesn't reload, run this command from the command line (it's all you will have):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Write that command down, you will see it a lot when people have video problems.

---

### Post by proplaya23 on 2007-06-26
> **Rocket2DMn said:**
> Cool, you probably need to restart the xserver now.  You can either reboot your computer or just close all your apps and use Ctrl+Alt+Backspace and you will be taken back to the login screen (assuming everything worked).
In the case that the driver installed fails and the Xserver doesn't reload, run this command from the command line (it's all you will have):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Write that command down, you will see it a lot when people have video problems.

thank you so Much man I am starting to love this forum and to love Ubuntu. Thanks Alot ill give it a try

---

### Post by proplaya23 on 2007-06-26
when i rebooted i got a little poop up windown on the top right of my screen saying ubuntu is using unrestricted drivers or something...... then i enabled the ati accelerated driver and it asked for a restart ....,did i do something wrong?

---

### Post by Rocket2DMn on 2007-06-26
Nope, it's because you installed a driver from a different source than Ubuntu's respositories.  Did it function OK after the restart?

---

### Post by proplaya23 on 2007-06-26
IM gona restart right now........o and also everytime i reboot i have to edit the boot line with noapic nolapic VGA=791 for it to not go blank screen i will get back to you and that later

this always used to happen its not from the ati diver installation

---

### Post by proplaya23 on 2007-06-26
ok i have restarted and everything went fine, but i have noticed that my desktop effects dont work and when i click on desktop effects from system TAB it says The Composite extension is not available

---

### Post by Rocket2DMn on 2007-06-26
That's not surprising, I think desktop effects are still in Beta or some such thing (I'm not at home to check my computer on that).  Glad the drivers are working though.

---

### Post by proplaya23 on 2007-06-26
THX rocket , u have helped me beyond enough ... i have one quick question that u might answer quickly if you can. when i reconfigure the driver with the "sudo dpkg-reconfigure -phigh xserver-xorg" commmand which one do i pick ati,vesa, etc..............

---

### Post by Rocket2DMn on 2007-06-26
Probably the "ati" driver, this should be the generic driver for ati cards and should at least give you your display back, though perhaps without complete functionality.  I'm not sure if it will give you a choice to use the driver you just installed, but I doubt it.  This command is generally used as a fall-back for when installing newer/better drivers fails.

---

### Post by proplaya23 on 2007-06-26
how do i go back to the original driver the one from ati

---

### Post by Rocket2DMn on 2007-06-26
Probably just by re-running that file you downloaded and executed, or by putting the correct name into the /etc/X11/xorg.conf file

---

### Post by proplaya23 on 2007-06-26
> **Rocket2DMn said:**
> Probably just by re-running that file you downloaded and executed, or by putting the correct name into the /etc/X11/xorg.conf file

Alright i Got everything Set,  Thank you for your great support......:D

---

