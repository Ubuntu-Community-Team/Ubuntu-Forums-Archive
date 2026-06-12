---
title: "Help w/ ATI tutorial.."
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by CBTF on 2006-08-07
Figured i'd spare my n00b questions from that thread for here :mrgreen: 

Alright- i am looking to install the latest ati drivers as described in this thread: [http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

I dont get far though. 
> 
. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

How?

Also, where should I save the .run I get from that link?

---

### Post by TFX360 on 2006-08-07
You should edit:

```

sudo nano /etc/apt/sources.list

```

To remove the "#" from te repositories so you can download from them.

In Synaptic you can also change the repositories settings what should be easier for a noob. **Settings / Repositories / Tag al tags.**


Kind regards,


TFX

---

### Post by Sutekh on 2006-08-07
To enable the universe / **multiverse** repository, you will need to do some command line editing (the GUI way in Synaptic is hard to describe IMO).  Here's how.
   
First you need to backup and edit the file that contains the repository sources. Open a Terminal window (Applications -> Accessories menu) and enter the commands.
   ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list
 sudo gedit /etc/apt/sources.list
``` When the text editor opens you need to uncomment (remove the # sign) these lines.
   ```
# deb http://archive.ubuntu.com/ubuntu dapper universe
# deb-src http://archive.ubuntu.com/ubuntu dapper universe
   
   ...
   
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
``` and add **multiverse** to the end of them.
   
   They should look like this when you are done
   ```
deb http://archive.ubuntu.com/ubuntu dapper universe **multiverse**
deb-src http://archive.ubuntu.com/ubuntu dapper universe **multiverse**
    
   ...
   
deb http://security.ubuntu.com/ubuntu dapper-security universe **multiverse**
deb-src http://security.ubuntu.com/ubuntu dapper-security universe **multiverse**
``` Save the file and then refresh the repositories list using this command
   ```
sudo apt-get update
``` 

You can save the .run file wherever you like.  Your Desktop is probably easiest to keep track of things.

---

### Post by TFX360 on 2006-08-07
Newest driver is downloadble here:

Ati Linux Driver 8.27.10

32 bits driver

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-x86.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-x86.run")

64 bits driver

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.27.10-x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.27.10-x86_64.run")

---

### Post by CBTF on 2006-08-07
Thanks for the replies. For some reason the instructions are not working..

> gsf@gsf-desktop:~$ chmod +x ati-driver-installer-8.27.10-x86.run
chmod: cannot access `ati-driver-installer-8.27.10-x86.run': No such file or directory


The file is on my desktop, what now??

---

### Post by Sutekh on 2006-08-07
The problem is that you are not at the Desktop on the command line.

Your pasted code shows me this.
[quote=CBTF]```
gsf@gsf-desktop:~$
```[/quote]
It shows your username, computer name, then the location you are currently in, which is **~**. This correpsonds to your home folder; **/home/gsf**.

You can always determine what folder you are in with the **pwd **command
```
pwd
``` To change to your Desktop (with a capital D), use the** cd** command
```
cd /home/gsf/Desktop
``` Or using the ~ shortcut
```
cd ~/Desktop
``` both will work.

To check that the ATI file is there, use **ls** to list files in the folder
```
ls
``` If it is there on your Desktop, then try the **chmod** command again.  The pupose of the chmod command is to **ch**ange the **mod**e of access to the file - the permissions.  chmod +x adds execution permission to the file.

---

