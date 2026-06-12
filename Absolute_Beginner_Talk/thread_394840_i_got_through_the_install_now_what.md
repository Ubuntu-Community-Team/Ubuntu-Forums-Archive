---
title: "i got through the install now what??"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by dippydoo on 2007-03-27
Ok here it is.... I have installed Xubuntu 6.06 using the alt cd. I loged on with my name and password and then the prompt cody@localhost:~$ came up. What do i ?do8)

---

### Post by taurus on 2007-03-27
What happens when you run this command from that prompt?

```
startx
```
If you get an error message about command not found, then you installed the server version, not the desktop version--XFce4.  Therefore, you need to run these commands to install XFce4.

```
sudo aptitude update
sudo aptitude install xubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by qamelian on 2007-03-27
> **dippydoo said:**
> Ok here it is.... I have installed Xubuntu 6.06 using the alt cd. I loged on with my name and password and then the prompt cody@localhost:~$ came up. What do i ?do8)

A couple of questions:
Did you see a graphical login screen? 
What type of install did you do (normal, OEM?)

---

### Post by dippydoo on 2007-03-27
> **taurus said:**
> What happens when you run this command from that prompt?

```
startx
```
If you get an error message about command not found, then you installed the server version, not the desktop version--XFce4.  Therefore, you need to run these command to install XFce4.

```
sudo aptitude update
sudo aptitude install xubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

When i typed "startx" i got the following: 
-bash: startx: command not found

---

### Post by dippydoo on 2007-03-27
> **qamelian said:**
> A couple of questions:
Did you see a graphical login screen? 
What type of install did you do (normal, OEM?)

No. i got the balck w/white text screen that had the following:

Ubuntu 6.06 LTS localhost tty1

loclhost login:
Password:

---

### Post by compmodder26 on 2007-03-27
Yup, you installed the server version.  Follow the instructions at the bottom of Taurus' post.

---

### Post by taurus on 2007-03-27
> **dippydoo said:**
> When i typed "startx" i got the following: 
-bash: startx: command not found

Run those these commands to install XFce4 on your machine then.

```
sudo aptitude update
sudo aptitude install xubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by dippydoo on 2007-03-27
it is going through the install now. thanks alot. I clicked on the link to download the alt desktop cd from xubuntu.com and that is y i thought i wouldnt have any problems. 

Now the next time i reboot i should have a graphical logon screen and it should bring me to the desktop right????

---

### Post by Patrick K on 2007-03-27
> Now the next time i reboot i should have a graphical logon screen and it should bring me to the desktop right????Our fingers are crossed :).

---

### Post by dippydoo on 2007-03-27
Ok guys the next problem...

I got the following errors i would like to know if they will be a problem for me:

Setting up python-gnome2 (2.12.4-ubuntu1)...
Errors were encountered while processing:
 libuniconf4.2
 libwvstreams4.2-base
 libwvstreams4.2-extras
 wvdial
 mailx

---

### Post by dippydoo on 2007-03-27
I then proceded to run the command:
```
sudo etc/init.d/gdm start
```

and then it opend a blue screen and told me there was an error with that what do i do????

---

### Post by taurus on 2007-03-27
> **dippydoo said:**
> I then proceded to run the command:
```
sudo etc/init.d/gdm start
```

and then it opend a blue screen and told me there was an error with that what do i do????

It's 

```
sudo /etc/init.d/gdm start
```
What is the exact error message?

---

### Post by dippydoo on 2007-03-27
it was an Xwindow error and now i am getting a an error that says "faild to start the X server (your graphical inerface)

---

### Post by taurus on 2007-03-27
I guess you need to reconfigure your X first then.  At the prompt, run

```
sudo dpkg-reconfigure xserver-xorg
```
If you are not sure about a question, just use the default and use **vesa** driver for your graphic card for now.  Once you have X running, then you can install a driver for it. 

When done, restart X again with

```
startx
```

---

### Post by dippydoo on 2007-03-27
i went through the config and this is what comes up:

```
Fatal server error:
could not open defult font 'fixed'
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.
```

---

### Post by thelinuxguy on 2007-03-27
```

sudo apt-get install xfonts-base

```

---

### Post by dippydoo on 2007-03-27
I am getting all sorts of different errors now. im just gunna wipe my disk clean and restart everything. i will be back on when i need help again

---

