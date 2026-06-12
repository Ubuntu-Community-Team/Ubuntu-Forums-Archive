---
title: "Connect to Ubuntu Remotely from OSX"
date: 2007-12-08
forum: Apple Intel Users
---

### Post by amsingh on 2007-12-08
Hello all.

I am trying to connect to Ubuntu (feisty fawn) form OS X Leopard.

I have enabled it through system preferences on ubuntu, and I'm using Chicken of the VNC on my mac, but I keep getting an "Authentication Failed" error.  Does anyone have any tips on have to fix this?

Thanks a lot.

---

### Post by xeth_delta on 2007-12-08
I am afraid I can not offer help in the VNC field, but I come with a suggestion. Have you considered trying ssh. Would it be enough for what you need?

Xeth

---

### Post by vincentzhu on 2007-12-11
How to use openssh in Mac OS X, I've searched by google, but got no results.


> **xeth_delta said:**
> I am afraid I can not offer help in the VNC field, but I come with a suggestion. Have you considered trying ssh. Would it be enough for what you need?

Xeth

---

### Post by cyberdork33 on 2007-12-11
enable "remote login" in the sharing options of System Preferences (Network?)

---

### Post by uc50_ic4more on 2007-12-11
Hello -

I administer around a dozen Ubuntu systems from my Macbook Pro. I have installed the openssh-server on the Ubuntu machines, and use either the terminal with this command:

ssh [username]@[machine name or IP]

... Or any FTP program that sports SFTP. Both the terminal method and the SFTP method simply open a SSH tunnel to the Ubuntu machines via port 22. I use the terminal to do software updates and troubleshooting, and the FTP programs to transfer files.

For accessing the screens on Ubuntu machines, Leopard also has a "Screen Sharing" program built into it that uses VNC. To enable the VNC server on the Ubuntu machines, System -> Preferences -> Remote Desktop. To access the Ubuntu machine's screen, simply choose Go -> Connect to Server in Finder and type vnc://[machine name or IP]. I am greeted each and every time with a warning about the Ubuntu machines not supporting keystroke encryption. 99.9% of the time I am accessing someone's screen, I am simply showing them where something is, so this is of no consequence to me. If, however, security is an issue, you may want to browse these forums for VNC via SSH or using FreeNX instead.

I hope that helps!

---

### Post by cyberdork33 on 2007-12-11
> **uc50_ic4more said:**
> ssh [username]@[machine name or IP]

Oh, yes, I stated how to start a server on OSX, not connect to another computer...

---

