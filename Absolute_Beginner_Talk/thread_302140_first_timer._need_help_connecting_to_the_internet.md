---
title: "first timer. need help connecting to the internet"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by sickace on 2006-11-18
hi all.
im completely new to linux.
have been a windows user all my life. partly because i found it easy to use and didnt feel the need to look for something else.
recently a friend of mine convinced me that im missing out on a whole different world and i need to switch to Linux.
i surfed around and read people comments on different pakages and decided Ubuntu is what i want to start with.
i know absolutly nothing about linux (im sorry if this is a bad thing) except of what i read and tried the past 2 days.

im trying to connect to the internet. i need a VPN connection.
i understood that i need to install connection-manager and some sord of addition for vpn.
problem is. i have no idea how to install this thing. i read around. but couldnt understand much. i tried the add/remove program from the menu. but when i try to choose the connection-manager it says i cant do that since the pakage is not intended for my computer.
altough on some forums people with computers like mine were able to install it in this manar.
so i thought i need to update the list in my add/remove list. but here again. i need an internet connection to do so.

what can i do?
is there a manual way to do this?

my computer is a Toshiba Satellite with an Intel P-M processor.
im using a Lan network (with DHCP) to connect to a VPN server.
and i installed Ubuntu 6.10 using the LiveCD 
(my other OS is WinXP if that is relevent at all)

sorry for the long msg and the complete ignorance.
 i apreceiate any sort of or and advice.
thank you all.
sickace

---

### Post by localuser on 2006-11-18
See if this helps.  I found it by doing a search in the forums for "vpn server"

[http://www.ubuntuforums.org/showthread.php?t=298017&highlight=vpn+server](http://www.ubuntuforums.org/showthread.php?t=298017&highlight=vpn+server)

If its not exactly what you're looking for, try the search again.  There were a lot of hits that may help.

---

### Post by huygens on 2006-11-18
Ouch, this is going to be complicated. The Add/remove program mistakenly tells you that there is no such a program for your architecture. I had a similar problem after installing Ubuntu because I did not have at that time internet. However, since I got my DSL line, I have reloaded the package information, and the error message vanished.

Therefore, as you need the file to get internet, it is going to be complicated. The best thing would be that you boot on Windows and download the software, or that you use a friends computer to do that.
So you will need to download the following packages (I hope I do not forget any, perhaps some are already installed, but it is a bit hard for me to guess).
So to install network-manager, you need (N.B. I assume that you are using the 32bit version of Edgy Eft for Intel or AMD):[LIST]
[*]dbus[/LIST][http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_0.93-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_0.93-0ubuntu3_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_0.93-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_0.93-0ubuntu3_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/d/dbus-glib/libdbus-glib-1-2_0.71-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dbus-glib/libdbus-glib-1-2_0.71-1ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/d/dbus-sharp/libdbus-1-cil_0.63.git.20060719-2ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dbus-sharp/libdbus-1-cil_0.63.git.20060719-2ubuntu1_all.deb)[LIST]
[*]dhcdbd[/LIST][http://archive.ubuntu.com/ubuntu/pool/main/d/dhcdbd/dhcdbd_1.14-2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dhcdbd/dhcdbd_1.14-2ubuntu2_i386.deb)[LIST]
[*]hal[/LIST][http://archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7.1-0ubuntu17_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7.1-0ubuntu17_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7.1-0ubuntu17_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7.1-0ubuntu17_i386.deb)[LIST]
[*]wpasupplicant[/LIST][http://archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.5.4-5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.5.4-5_i386.deb)[LIST]
[*]and finally network-manager[/LIST][http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.3-2ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.3-2ubuntu6_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util0_0.6.3-2ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util0_0.6.3-2ubuntu6_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib0_0.6.3-2ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib0_0.6.3-2ubuntu6_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl/libnl1-pre6_1.0~pre5+svn21-2ubuntu2_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl/libnl1-pre6_1.0%7Epre5+svn21-2ubuntu2_i386.deb")

Download all of those files by right clicking on them and selecting "Save link as..." and put them all inside the same directory I would advise /tmp (meaning you go at the root of your file system and there you will see a tmp directory).

To install them all at once, the better would be to use the command line. You go to the Applications menu and under Accessories, select the Terminal application. Now you are on the command line, if you have downloaded all the above files under /tmp, here are the instructions that you need to type:
```
cd /tmp
sudo dpkg -i *.deb
```When you see something like "Password:" the system is asking you for your user password (the one you are using to login). Then I hope it is working, follow the on-screen instructions.

You might want the GNOME front-end for it, but this would probably require a bunch of other dependency... Anyway, you could try it, but in case the installation does not work, simply ignore it. The GNOME front-end for Network Manager is downloadable here: [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager-gnome_0.6.3-2ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager-gnome_0.6.3-2ubuntu6_i386.deb)

Now, you have Network-Manager installed. You can launch it by using once again the command line, or simply by login out and login in again. For the command line, you just have to type:```
nm-applet --sm-disable
```OK, so now you have network-manager installed. You need to follow the advice you have found to configure your VPN. Checking the [Ubuntu wiki page]("https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-691ab1f191007294d3bf039bd627131628b40410"), I have found that there are possible other files to download for the VPN stuff. Please refer to the link for more information.

Hope this help :-)

Huygens

---

### Post by sickace on 2006-11-18
thank you so much for the explenation. 
im downloading the files + every other thing i can find related to pptp/vpn (just incase i need any ov it while im on linux).

going to try it now. hope i dont hit too many problems :)

---

### Post by sickace on 2006-11-18
ok. i u gave me all i needed. i had no problems at all installing the network-manager/
thank you.

but now. im lost again. i need to install pptp to have my vpn connection.
i tried sereaching for older questions about this. but all refare to updating the source list and using apt-get. i cant do that.
i need to download and install it manualy.

but i cant find the files i need (or an explenation of what files i need)
and this switching between OSs is driving me crazy :s

anyone can refare me to a more specific area of what i need here? 
thank you again.


PS: from one of the forums i found a link to 3 files that are supposed (acording to the msg) to be an update for the pptp pakage which then i can install. there where 2 rpm files:

pptpconfig-20060821-1.fc5.noarch.rpm
pptp-1.7.1-3.i386.rpm

and one .deb file:
pptp_1.5.0+20040809-0_i386.deb


i tried the .deb file as instructed to do with the ones b4. but it didnt work.
and the other 2 files. i dont know what to do with.
it said i need to convert them on the same forum page. but i dont know how to do that either.

(brain having trouble)

[COLOR="Red"]
-edit- 
as it seems the pptp IS installed (aparently).
but now i need the pptp-config.
i cannot use the update since i dont have an internet connection yet.
can anyone tell me plz where to find it and how to install it?
again thank you all. and sorry for the unclear questions. my brain is a toast by now.
[/COLOR]

---

### Post by sickace on 2006-11-19
sorry to bump this up.
but i could use any sort of help.

i finaly got the network manager and pptp installed and running.
LAN is 100% ok
VPN connection gives me an MS-Chap error.

i searched for the exact error on google. and i found out that the sign "%" might be problematic in the user name adn i have to encrypt it in the config file.


how would i do that?

(please help. panic mode is on :( )

--edit--
the error msg i have is:

MPE required, but MS-CHAP[v2] authentication not performed
--

but a wierd thing. i tried to mess around with the setting and user name/pass. and it passes PAP and fail when the details are wrong.
so im assuming it DOES get to a point where it authenticat the user/pass.

but then what goes wrong?

---

### Post by huygens on 2006-11-19
I only knew about NetworkManager, but for VPN I have no particular experience. I hope someone can go on with you and help you.

Anyway, I went on pptp web site and found something related to your problem:
[http://pptpclient.sourceforge.net/howto-diagnosis.phtml#mppe_bmanp](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#mppe_bmanp)

There is a solution, perhaps you will understand it (I do partially only) and it might help you.

All the best and perhaps, if no one answer you in the coming days, you should try to open a new thread in the [network forum section]("http://www.ubuntuforums.org/forumdisplay.php?f=136"). There might be more people able to help than in the current section. :-)

Huygens

---

### Post by sickace on 2006-11-22
thanks man.
ive already went over that page, and i googled the hell out of this thing.

it just wont work.

thanks for the effort.

---

### Post by pliumbum on 2007-01-24
i have used your instruction as well, because the problems seemed to be very similar to these. it looked like the installation worked, but when i write nm-applet --sm-disable, i get bash: nm-applet: command not found.. what is wrong? when i restart my computer, the manager doesnt work as well..

---

