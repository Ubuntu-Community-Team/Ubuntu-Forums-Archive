---
title: "trying to set up internet... help!"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by ieszu on 2007-07-05
I recently set up Kubuntu, trying to set up the internet to see what updates and other good stuff I can add to it (heard good things about Wesnoth... want to try it).

Here is the problem. I have a cable modem, no router, and I when I plug it in, it seems like it is acquiring the IP address, then says it is connected.. but when I open up Konqueror, it will not access the internet... how do I solve this problem? :)

---

### Post by Joakim Stokland on 2007-07-05
Hello and welcome! :)
Do you use KDE or Gnome? You can select your network settings in System > Network in KDE (Don't remember exactly where it is in Gnome, but if you start terminal (Alt + F2, type i.e. 'gnome-terminal') and type

gksu network-admin

you'll get the same app.

You'll find your modem there. Click it and select properties. After you've saved your settings, you should uncheck the box in front of your modem, and then check it again to activate the modem with the new settings.

Good luck with ubuntu! :)

Joakim

---

### Post by Joakim Stokland on 2007-07-05
Ah, in Gnome you should find 'Network' under Desktop > Administration.

And in case you didn't know, gksu does the same thing as sudo - gives you root powers - except it's intended for graphical applications.

Joakim

---

### Post by rickycodie on 2007-07-05
joakim read the post. i recently uninstalled the kde desktop from my ubuntu, and it was because of things like this.  you need to get to another computer and down load the kde wireless/wired network gui, it will aid in connecting. then put the packages on a usb drive or a cd and install it on the problem computer. if that doesn't work then reinstall the kde internet packages. if that doesn't help then do this

sudo apt-get install gnome desktop

and remove kde, then use gnome for a while, it's much easier to navagate.

---

### Post by xpod on 2007-07-05
Something tells me their using Kubuntu;)

EDIT:zzzzzz

---

### Post by Joakim Stokland on 2007-07-05
Oh, sorry, I misunderstood the question. Thought it was dial-up... :(

---

### Post by ieszu on 2007-07-05
> **xpod said:**
> Something tells me their using Kubuntu;)

EDIT:zzzzzz
Yes, I am using Kubuntu.... tried setting up to automatically get the IP address.... doesn't seem to work.

I can access the network manager just fine, how do I know what the static IP, default gateway,etc. should be if I manually type it in?

Oh, and I am using KDE... can I even swith to GNOME if I have no internet to get programs through the add/remove prgorams prompt?

---

### Post by Rui Pais on 2007-07-05
> **rickycodie said:**
> joakim read the post. i recently uninstalled the kde desktop from my ubuntu, and it was because of things like this.  you need to get to another computer and down load the kde wireless/wired network gui, it will aid in connecting. then put the packages on a usb drive or a cd and install it on the problem computer. if that doesn't work then reinstall the kde internet packages. if that doesn't help then do this

sudo apt-get install gnome desktop

and remove kde, then use gnome for a while, it's much easier to navagate.

sorry but thats terrible advices...
change the desktop interilly for using an app is too much. 
And you can install and use tools from one DE on another.
And if he don't have a connection he cant apt-get :( nothing

The problem is a connected and detected cable modem that can not navigate.

I suspect the usual ipv6 and/or dns issues:
check [this post]("http://ubuntuforums.org/showpost.php?p=2950371&postcount=3") for suggestions.
Instead of gksudo gedit use kdesu kedit or kdesu kate.

---

### Post by ieszu on 2007-07-05
:popcorn:

Solved the problem..... realized I had to be set as DHCP, then set konqueror to use auto-proxies... thanks everyone.... now to get more familiar with Kubuntu and ask some real questions =)

---

