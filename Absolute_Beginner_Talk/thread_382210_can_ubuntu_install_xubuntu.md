---
title: "can ubuntu install xubuntu"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Dark-Angel on 2007-03-11
i'm just wondering if you have ubuntu 6.10 if you are able to choose to install xubuntu from that.

---

### Post by mitch707 on 2007-03-11
nope you have to download the xubuntu ISO file from the site

---

### Post by Dark-Angel on 2007-03-11
ok thanks

---

### Post by oilchangeguy on 2007-03-11
are you aware that xubuntu is a lesser version of ubuntu. why do you want to go backward? is your computer having problems with 6.10?

---

### Post by mitch707 on 2007-03-11
your welcome but if yuo have problems i recommend fedora core 6

---

### Post by qpwoeiruty on 2007-03-11
Won't "sudo apt-get install xubuntu-desktop" get you most of the way there?

Edit: I installed Ubuntu Breezy with the "server" option, updated to Edgy, and sudo apt-get install kubuntu-desktop for kubuntu. Should be the same for xubuntu if it's in the repository. Downside is that it's almost the size of the CD going from a plain server install to kubuntu so probably similar with xubuntu,

---

### Post by Dark-Angel on 2007-03-11
i'm installing on a very old computer so xubuntu would be best

---

### Post by moffa on 2007-03-11
```
 sudo apttitude install xubuntu-desktop 
``` should work

---

### Post by qamelian on 2007-03-11
> **mitch707 said:**
> nope you have to download the xubuntu ISO file from the site

Sure you can. Install the xubuntu-desktop metapackage then you can choose whether you want Ubuntu or Xubuntu on login.

---

### Post by actuary286 on 2007-03-11
Xubuntu is in no way inferior to Ubuntu or Kubuntu, the XFCE window manager just takes a more minimalistic approach. If you want to add XFCE as a desktop environment for your Ubuntu box then
```
sudo apt-get install xubuntu-desktop
```

You can then choose XFCE from under the Options menu in GDM (login).

---

### Post by jgamio on 2007-03-13
Xubuntu and Xfce are two diferent thing.

Xubuntu is a minimal distribution for Ubuntu
Xfce is a Desktop

If you install xfce in ubuntu you have the same app loaded and is almost the same speed to use gnome.

Xubuntu install small aplication and load less app in the start and use xfce because is light is better install Xubuntu direct from CD and dont install Xfce in Ubuntu.

That is if you want install a fast distribution if you only want to test Xfce go ahead in ubuntu


[IMG]http://ubuntucounter.geekosophical.net/img/xubuntu-blogger.php?user=11642[/IMG]

---

### Post by zyx on 2007-03-13
Install the xubuntu-desktop metapackage then you can choose whether you want Ubuntu or Xubuntu on login????

What is metapackage? Can you give some detail?

---

### Post by mi_were on 2007-03-13
> **Dark-Angel said:**
> i'm just wondering if you have ubuntu 6.10 if you are able to choose to install xubuntu from that.

The simple answer is yes you can. 

But if your installation is on a resource starved computer then your best bet is to start off by installing Xubuntu with the default Xfce GUI. You will be starting off on the right foot with a installation that is already geared to your situation and you don't have to go to the problem of finding and installing applications that are not that resource hunger.

I tried it both ways and can say from personal experience Xubuntu is the best option for older PCs and Laptops while still retaining the ability to install application from the ubuntu family.

---

### Post by Mikesco3 on 2007-03-13
I have been able to successfully have xubuntu-desktop, ubuntu-desktop and kubuntu-desktop all live happily on the same computer. All I had to do is open a command line and key in a couple of commands. 

   So lets imagine I have the Dapper Ubuntu desktop and I want to install either the xubuntu and/or kubuntu desktop. and you may even be able to follow this if you are already on xubuntu or kubuntu wanting to go to either one of the other. 
   Be sure to have administrative rights or sudo ability before you plan to begin. 

   Open a command line with one of either two methods:
     1) from ubuntu go to **Applications** -> **Accessories** -> **Terminal** or Konsole.
     2) else you can press **Ctrl** + **Alt** + **F2**, then login. (with your user name and password).

and once you have access to the console you can type:
for Xubuntu ```
sudo apt-get install xubuntu-desktop
```
for Kubuntu ```
sudo apt-get install kubuntu-desktop
```

or another alternative to the same command is:
for Xubuntu ```
sudo aptitude install xubuntu-desktop
```
for Kubuntu ```
sudo aptitude install kubuntu-desktop
```
   (I believe you might get a little better dependency handling with the later but I could be mainly wrong but either one should work)
then follow the instructions.

   You should be fairly safe following the defaults suggested. During the install process you will be prompted to select which will be your default graphic environment, in other words which login screen will it use (the ubuntu, kubuntu or xubuntu login screens) and then from that screen you should be able to select which desktop environment you wish to login to, by going to the bottom part of the logon screen and selecting session type. 

   A nice little tip that might come handy is creating a user for each one. In other words create 3 user names if you were to have 3 desktop environments and say name them "ubuser", "kubuser" and "xubuser" and make the respective desktops their default.

   You can select kde desktop environment and then logon as "kubuser" and then it will ask you if you want to make that his default desktop environment, to what you respond yes (as opposed to using it for this session only). :)

---

### Post by astronic on 2007-03-14
> **mi_were said:**
> But if your installation is on a resource starved computer then your best bet is to start off by installing Xubuntu with the default Xfce GUI. You will be starting off on the right foot with a installation that is already geared to your situation and you don't have to go to the problem of finding and installing applications that are not that resource hunger.
Can you elaborate on that? To my knowledge Ubuntu, Kubuntu and Xubuntu are exactly the same Linux distribution that just differ when it comes to the default package selection. And in case of Xubuntu, after installing the xubuntu-desktop metapackage you should have all packages installed on your system, that would have been installed if installing Xubuntu from a Xubuntu CD.

So there should be no need of "having to find applications". The only I reason I can think of, why Xubuntu on Ubuntu could be slower than a dedicated installation, would be that the ubuntu-desktop metapackage might set up configuration files used by both GNOME and XFCE differently. In this case, the user should just overwrite those configuration files with the version shipped with XFCE. Linux is not Windows. We should encourage users to fix their problems, not just reinstall their operating system just because they want to switch to a different desktop environment.

Oh, and please tell me about what exactly makes XFCE on Ubunutu slower than on Xubuntu. I want to have a closer look at it.

Regards,
Stefan

---

### Post by hyper_ch on 2007-03-14
> **oilchangeguy said:**
> are you aware that xubuntu is a lesser version of ubuntu. why do you want to go backward? is your computer having problems with 6.10?

Don't give any notice to that statement above...

Xubuntu is in no way inferior than Ubuntu...

I prefer Xubuntu myself as I don't need all those eye-candys provided by GNOME/KDE although my pc could handle those just fine... the only eye-candy I ever use is a desktop-wallpaper changer... that's about it :)
I see no reason why I need to bloat my system with a desktop environment which I don't need so that it just looks nice... Xfce is straight forward and that's what I value :)

Well, by installing the xubuntu-desktop you will not exactely get the same stuff and things installed as when you do a clean xubuntu install... I don't remember exactely where the differences are but there are some...

---

### Post by wishyjr on 2007-04-03
hi guys, 

am i correct in assuming that installing xubuntu will also install other stuff that will also be on my gnome installation? What im trying to say is.. Is there a way to install Xfce as a desktop environment on top of gnome? So its basically my gnome system that looks like xfce? thanks

---

### Post by Maestro23 on 2007-04-03
> **wishyjr said:**
> hi guys, 

am i correct in assuming that installing xubuntu will also install other stuff that will also be on my gnome installation? What im trying to say is.. Is there a way to install Xfce as a desktop environment on top of gnome? So its basically my gnome system that looks like xfce? thanks

Read section on "Playing Around": [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

