---
title: "I can't get ./setup to run"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Paddy060906 on 2006-12-02
I'm trying to install Evermore Integrated Office 2007 (EIO2007) in Xubuntu, my first foray into any Linux distro.  

I do the following, and nothing happens;
[INDENT]1. I mount the cd
2. I start terminal and type "sudo -i" and enter password
3. I go to /media/cdrom/linux and type "gksudo ./setup" to run the install file.
4. I enter my password, and that's it.  No install dialogue appears.  Nothing.[/INDENT]

No doubt I'm doing something stupid. Your help appreciated.

---

### Post by taurus on 2006-12-02
What does 

```
ls -la /media/cdrom/linux
```
look like?

And instead of becoming root, why not run it as

```
sudo /media/cdrom/linux/setup
```

---

### Post by Paddy060906 on 2006-12-02
Thansk for quick response.

I tried run sudo /media/cdrom/linux/setup and ./setup.  Was told 
[INDENT]sudo: /media/linux/setup: command not found
coleman@Coleman-desktop:~$ sudo /media/linux/./setup
sudo: /media/linux/./setup: command not found[/INDENT]

ls -la /media/cdrom/linux returns the following

[INDENT]total 40829
dr-xr-xr-x 1 root root     2048 2006-10-20 11:12 .
dr-xr-xr-x 1 root root     2048 2006-10-20 11:13 ..
dr-xr-xr-x 1 root root     2048 2006-10-20 09:28 assocaiate
-r-xr-xr-x 1 root root      523 2006-10-19 12:01 config.eni
-r-xr-xr-x 1 root root       75 2006-10-19 12:01 dispose.ini
-r-xr-xr-x 1 root root   995107 2006-10-19 12:02 dispose.jar
dr-xr-xr-x 1 root root     2048 2006-10-20 09:28 font
-r-xr-xr-x 1 root root      521 2006-10-19 12:01 InstallInfo.ini
dr-xr-xr-x 1 root root     2048 2006-10-20 09:28 instdata
-r-xr-xr-x 1 root root 40526675 2006-10-19 12:01 Jre.zip
-r-xr-xr-x 1 root root     7155 2006-07-26 10:54 linkscript
-r-xr-xr-x 1 root root      933 2006-10-20 11:13 README IMPI INSTALL.txt
-r-xr-xr-x 1 root root     2853 2006-10-19 12:01 Readme.txt
-r-xr-xr-x 1 root root    23333 2006-10-19 12:01 setup
-r-xr-xr-x 1 root root   183656 2006-10-19 12:01 setup.bmp
-r-xr-xr-x 1 root root    55135 2006-10-19 12:01 start.jpg
[/INDENT]

---

### Post by Paddy060906 on 2006-12-02
OK.  Spotted error after last post.  Got the address right, but "permission denied" when trying to run setup.
P

---

### Post by taurus on 2006-12-02
```
cd /media/cdrom/linux
sudo ./setup
```
Otherwise, what does the "README IMPI INSTALL.txt" say?

```
more "README IMPI INSTALL.txt"
```

---

### Post by Paddy060906 on 2006-12-02
Still getting "Permission Denied" for sudo ./setup

IMPI README is as follows;
Start the computer. Enter the UI as a temporay user. You will need to log in as 
the root user however to install EIOffice.

Step 1. Click System Menu ->Console Login

Step 2. After you enter the Console mode,the install interface will appear. Ente
r &#65533;&#65533;root&#65533;&#65533; and the password in the command line.

Step 3. Input command &#65533;&#65533;startx&#65533;&#65533;, and enter. This will allow you to become the r
oot user.

Step 4. Insert the EIOffice disk into the CD-Room. Enter the Disk directory, if 
you fail in entering the directory, imput the following commands. mount /dev/cdr
om /mnt/cdrom (enter)

Note: although the install procedure may appear on the screen you can only use t
he above command to install EIOffice. IT appears to be a problem with the IMPI p
rogram not EIOffice.

Step 5. Enter the Disk directory, double-click on the &#65533;&#65533;setup&#65533;&#65533; and start the installation follow th
e on-screen instructions.

---

### Post by taurus on 2006-12-02
What if you copy everything on the CD to your harddrive before you install it?

```
sudo mkdir /opt/temp
sudo cp -R /media/cdrom/linux/*  /opt/temp
sudo chmod -R 755 /opt/temp
cd /opt/temp
sudo ./setup
```

---

### Post by Paddy060906 on 2006-12-02
That did the trick.  Thanks for your help Taurus.

P

---

### Post by taurus on 2006-12-02
You're welcome.

---

### Post by Paddy060906 on 2006-12-03
POSTSCRIPT:

First time you run EIOffice you must launch it using sudo so that when you enter the CD-Key the software can write to the relevant file.  "sudo /usr/bin/eio"

Once the CD-Key is entered successfully, just launch the program without sudo.

---

