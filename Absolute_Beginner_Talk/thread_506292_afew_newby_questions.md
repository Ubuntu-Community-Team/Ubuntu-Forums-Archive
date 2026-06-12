---
title: "afew newby questions"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Phone33 on 2007-07-21
so i just pgot ubuntu 7.04 running on my computer. i did an online update i have installed VMware server console and beryl.i am also running a dual monitor system w/ my NVidia Quadro graphics card

so here are my problems
first this is a dual boot machien i have an 80 gig HD that has windows on it. what i want to do is use VMware server to boot that copy of windows. i dont know if i can do that or if i have to reinstall window on that HD using VMware. 

i installed beryl just fine and my restricted drivers manager says the my Nvidia accelerated graphics driver is working fine but when i run sudo beryl i get his error

Reloading options
beryl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
beryl: Plugin 'dbus':initDisplay failed
beryl: Couldn't activate plugin 'dbus'
Couldn't initialise dbus. This should not happen!

it seems to be working, or at least it goes into cube mode but no other effects work
any idea what is wrong there?

also my nvidia twinview is work i think. but i have t turn it on every time i boot up also it dose to recognize the live between my two monitors so when i hit maximize it stretches the window out across both.

also whenever i boot it says im connected to a wired network which i should be however i have no  internet so i just switch to wireless. which works. any idea how i can trouble shoot my internet connection or how i can make wireless my default connection.

also can any one seggest good Linux programs to replace 

Winamp
DvDdecriptor
DvDshrink

also are there any how to guides on how to move my outlook base school email to evolution mail?

i know this is alot but any input would be great. also i am day one newb to this linxu thig so please assume i know nothing (because i actually do know nothing)

---

### Post by ddrichardson on 2007-07-21
> **Phone33 said:**
> so i just pgot ubuntu 7.04 running on my computer. i did an online update i have installed VMware server console and beryl.i am also running a dual monitor system w/ my NVidia Quadro graphics card

so here are my problems
first this is a dual boot machien i have an 80 gig HD that has windows on it. what i want to do is use VMware server to boot that copy of windows. i dont know if i can do that or if i have to reinstall window on that HD using VMware. 

i installed beryl just fine and my restricted drivers manager says the my Nvidia accelerated graphics driver is working fine but when i run sudo beryl i get his error

Reloading options
beryl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
beryl: Plugin 'dbus':initDisplay failed
beryl: Couldn't activate plugin 'dbus'
Couldn't initialise dbus. This should not happen!

it seems to be working, or at least it goes into cube mode but no other effects work
any idea what is wrong there?

also my nvidia twinview is work i think. but i have t turn it on every time i boot up also it dose to recognize the live between my two monitors so when i hit maximize it stretches the window out across both.

also whenever i boot it says im connected to a wired network which i should be however i have no  internet so i just switch to wireless. which works. any idea how i can trouble shoot my internet connection or how i can make wireless my default connection.

There are lots of tools available at the command line that can help here - ping will tell you if packets are being transmitted, ifconfig will tell you what interfaces are available and up. If the GUI flicks your switch System/Administration/Network Tools is great.

> 
also can any one seggest good Linux programs to replace 

Winamp

Amarok under KDE is outstanding.

> DvDdecriptor
DvDshrink

DVD::Rip

> 
also are there any how to guides on how to move my outlook base school email to evolution mail?

You can export your mail from Outlook to pst or csv and import into Evolution.

i know this is alot but any input would be great. also i am day one newb to this linxu thig so please assume i know nothing (because i actually do know nothing)[/QUOTE]

---

### Post by irish_flu on 2007-07-21
I use "Rhythmbox" as my music player, it's pretty cool.

As far as running already-installed Windows in VMWare, I'm not sure VMWare can do that.  As far as I know (and I might be wrong) the "build" needs to be done BY VMware in order to make it work in VMWare.

---

### Post by Phone33 on 2007-07-22
ok most of the things above i have worked out but right now my 3 big problems are

whenever i maximize a window it jumps both monitors

beryl makes my windows or wallpaper black sometime

whenever i restart my comp i have to setup my twinview

---

### Post by kvonb on 2007-07-22
Why are you running Beryl as sudo?

That's why it can't find any screen to attach to, root is NOT the current user, well it shouldn't be anyway!

The easiest way to run Beryl is to press alt-f2 and type:

beryl-manager

then run it.

You can set that to run on login with the "sessions" option in System->Preferences (assuming you are using Gnome).  It will load the manager each time you login, and will save it's last state, ie if you had Beryl selected as the current window manager on logout, it will be there when you come back.

---

### Post by Phone33 on 2007-07-22
ok that worked for beryl but it is still streching across both monitors

---

### Post by kvonb on 2007-07-23
> **Phone33 said:**
> ok that worked for beryl but it is still streching across both monitors

erm, yeah, that's what twinview does, it makes one big screen out of the 2 monitors! :rolleyes:.

Have a look at this thread that I found by simply using the search button on the forum's main page:

[http://ubuntuforums.org/showthread.php?t=221174&highlight=nvidia+twinview](http://ubuntuforums.org/showthread.php?t=221174&highlight=nvidia+twinview)

It might help you :).

---

