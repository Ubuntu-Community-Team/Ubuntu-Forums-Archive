---
title: "Installing Ubuntu 7.04 without an internet connection"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Stanverr on 2007-10-19
I have installed the above on a PC which does not have an internet connection nor does it have Windows. Everything works except for all programs relating to sound and vision (Totem Movie Player 2.18.1 and Ryythnox 0.10.0). The error message for the audio side of things indicates that I need to obtain GStreamer extra plug ins and that for the video I need gxine, libdvdcss2, libdvdnav4, libdvdplay0 abd libdvdread3. Using another PC I have been able to locate these applications and save them to a memory stick but I have no idea how (and if) I can install them from the memory stick to the PC. That's the query really - can I and if so how do I go about it (and I really do need an idiot's guide for this, words of one syllable without assuming any knowledge!!). Finally is there anything else I need to make audio and video work? I know I am asking a lot here but I am assured Linux users are a friendly lot keen to share knowledge so I'm hoping for the best (you can tell I bought the [recent Computer Active Guide to Getting Started with Linux and its cover disc can't you?). Thanks in anticipation of your help!!!!

---

### Post by mikeyphi on 2007-10-19
Try this guide: [http://www.psychocats.net/ubuntu/installingsoftware#deb](http://www.psychocats.net/ubuntu/installingsoftware#deb)

There's also something about Apt on CD - [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by onelife151 on 2007-10-19
As far as the flash drive. plug it in to the computer ubuntu should recognize the flash drive and open a window for it. the easiest method is to go to the terminal change directories to that fllash drive. if you can't figure out what directory that is type the mount command and it will show you all mounted devices. anyways change to the directory of the flash drive and do a dpkg -i *.deb and it should install all the .deb files you downloaded.

---

### Post by Stanverr on 2007-10-20
Thanks for your help. I will try both and see how I get on

---

