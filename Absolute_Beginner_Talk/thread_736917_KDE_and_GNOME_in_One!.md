---
title: "KDE and GNOME in One!"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by smartygoldenfish on 2008-03-27
I have recently installed ubuntu and love its stability, but when i saw Kubuntu i became a fan of its looks. I have read that KDE and Gnome are nothing but Desktop environments for the something called **X WINDOW MANAGER**, if  its so, can i run both of them, like a app asks when i log in **What do u want to use? GNOME Or KDE...it would be nice naa?**

And i have my Kubuntu 7.10 CD plz tell a way that i dont have to use the internet to donwload KDE! We in India have limited download limits restricted to 400 MB/month in my case so i download as less as possible!

---

### Post by kesman on 2008-03-27
Yeah, you can install KDE into Ubuntu, and after installing, you can select either one in the log-in window.
I think you only need to install kubuntu-desktop, to do this, run
```

sudo apt-get install kubuntu-desktop

```
in terminal and you're done.

---

### Post by smartygoldenfish on 2008-03-29
well i want i from my cd 
not from net

---

### Post by tubasoldier on 2008-03-29
You could order a Kubuntu disk and then add it to your repository list.

---

### Post by aysiu on 2008-03-29
> **smartygoldenfish said:**
> well i want i from my cd 
not from net
Is it the Alternate CD or the Desktop CD?

---

### Post by tubasoldier on 2008-03-29
This thread got me to thinking. What is the real difference between Gnome and KDE?

The Gnome panel vs. the KDE kicker.
Nautilus vs. Konqueror.

Other than that does it really matter? You can run all available applications in either desktop. It just loads the libraries for those programs to run.

Just out of curiousity I decided to start KDE's kicker while in Gnome. Very interesting. It starts up, runs fine, and everything in my systray in the gnome-panel is available in the kicker systray. So for those who can not get compiz to work in KDE this may be an alternate option. Start the kicker in Gnome, and use it as if it is KDE.

After all they aren't that different when it comes down to it.

---

### Post by jeffinhedon on 2008-03-29
OK 
I've run the install command 
and activated KDE desktop
But How do I get back to Gnome desktop
At boot up in Kubuntu the system boots up into command 
and I have to log on in command mode to get a desktop (kubuntu)
I want Gnome back which just boots up by way of a graphic sequence
which allows me to input my name and password
Can anyone help please
:(

---

### Post by ROJIRU on 2008-03-29
Hi Tubasoldier, Ive got a kubuntu disk, How do I add it to my repository. Many thanks Rojiru

---

### Post by zvacet on 2008-03-29
@ **ROJIRU**

Copy your iso from Cd to HDD.Install [this.](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html) when is ois mounted type in terminal

```
sudo synaptic --add-cdrom /media/iso/
```

You will replace** /media/iso/** with mountpoint you choose in previous step when you mounted iso. If all goes well and it should you are just added iso to the synaptic.To install kubuntu desktop type in terminal

```
sudo apt-get install kubuntu-desktop
```

I hope it will work for you.

---

### Post by mrpixels0 on 2008-03-29
> **ROJIRU said:**
> Hi Tubasoldier, Ive got a kubuntu disk, How do I add it to my repository. Many thanks Rojiru

from Gnome go to System->Administration->Synaptic

enter your password (root) and when synaptics window comes up choose Edit and from the list that drops down choose add cdrom place the disk in the drive, when it is done and asks if you would like to add another cdrom choose no and your done.

now you should be good to go :)

MP0

LOL zvacet beat me to it :)

---

### Post by smartygoldenfish on 2008-03-31
i really appreciate the responses but 
suppose my country has NO INTERNET connection and i want to add KDE to my ubuntu
then how will i do it?
How to make Synaptic download and install KDE from packages ALREADY from the Live CD.
I have the Kubuntu 7.10 Beta Live CD

please help!

---

### Post by philinux on 2008-03-31
Post number nine or edit your sources list to add another cd rom

---

