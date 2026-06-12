---
title: "Help, I need a gui (server edition)"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by penduboy on 2007-09-30
Hi

I am very new to Ubuntu/Linux

I just installed my Ubuntu 7.04 server last night

I can only see the black screen with some command prompt. How I can get it to Graphical Interface like windows.

Please help.

Pendu

---

### Post by overdrank on 2007-09-30
> **penduboy said:**
> Hi

I am very new to Ubuntu/Linux

I just installed my Ubuntu 7.04 server last night

I can only see the black screen with some command prompt. How I can get it to Graphical Interface like windows.

Please help.

Pendu

Hi and welcome, but as you can see by the previous post by bodhi.zazen this is not a good place to get support. You have installed a server edition which has no GUI (desktop) Please install the desktop version found here. 
[http://www.ubuntulinux.org/](http://www.ubuntulinux.org/)

---

### Post by penduboy on 2007-09-30
Thanks for your reply

But how I can uninstall the server edition and also the changes in my boot sequence.

Could you please let me know where should I post my simple questions.

Regards,

Pendu

> **overdrank said:**
> Hi and welcome, but as you can see by the previous post by bodhi.zazen this is not a good place to get support. You have installed a server edition which has no GUI (desktop) Please install the desktop version found here. 
[http://www.ubuntulinux.org/](http://www.ubuntulinux.org/)

---

### Post by bodhi.zazen on 2007-09-30
> **penduboy said:**
> Thanks for your reply

But how I can uninstall the server edition and also the changes in my boot sequence.

Could you please let me know where should I post my simple questions.

Regards,

Pendu

Feel free to post here or in General help.

You can either :

```
sudo apt-get install ubuntu-desktop
```

Or re-install Ubuntu / Kubuntu / Xubuntu. The install is very similar, just install over the top of the server edition.

In the end, are you trying to run a server ? In that case, keep the server install. In this case you could consider a lighter desktop such as Fluxbox ...

If you want a desktop + a few server apps, go the second route and add the apps you need.

---

### Post by Seisen on 2007-09-30
I would also recommend fluxbox because it is lightweight and if you are running a server you don't need openoffice or any of the other software that is loaded with Ubuntu or Kubuntu. Check out this link to it my come in handy if you wan to use fluxbox

[https://help.ubuntu.com/community/Fluxbox]("https://help.ubuntu.com/community/Fluxbox")

---

### Post by RedSquirrel on 2007-10-01
The links in my signature might help if you decide to go with Fluxbox.

Here are two links to help you install a GUI:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

These guides are mainly for people who want to install a minimal system, but the information on installing the graphical interface might help.

---

