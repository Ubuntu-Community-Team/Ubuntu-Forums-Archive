---
title: "wireless nic wrapper help needed"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by jhd5476 on 2007-01-20
Hello,

Since i am very new to Ubuntu and Linux and i am working from a command line detailed hand holding would be greatly appreciated.

My experience is with the other operating system you know the one that starts with a W, there i have extensive experience.

After installing Ubuntu 6.10 Server onto a HP Netserver one of my first observations is that the nic does not work, so i started down the tunnel of updating the driver or wrapper.

when reading similar questions / responses in this forum it seemed that i should use the "sudo apt-get install ndisgtk" command.

this command resulted in a initially positive response judging from the command line feed back.  however, the final line was "couldn't find package ndisgtk".

this nic is a cheap generic model made by dynex, however they did have two linux drivers / wrappers one for 2.2 and one for 2.4. so i made a cd with both of them on it however i do not know the command(s) to install it or if these are correct for Ubuntu.

this nic worked very well on WinServer 2003 however i would really like to switch to Ubuntu.

since i have several years of help desk on other operating systems i know that providing information about the system and specific input would be very helpful, but this machine is not communicating right now so please bear with me and i will type the screen response for needed feedback.

any help would be greatly appreciated.

thank you in advance

jd

---

### Post by RomeReactor on 2007-01-20
Since you installed Ubuntu server, i assume you don't have X (that you're working from terminal only), in which case ndisgtk probably won't appear on your search, since it's a graphical interface to ndiswrapper. Try:

```
sudo apt-get install ndiswrapper-common
```

or invoke Aptitude:

```
aptitude
```

to manage your installation from there.

---

### Post by jhd5476 on 2007-01-21
Thank you for the input, 

FYI - command sudo apt-get install ndiswrapper-common produced the same behavior as sudo apt-get install ndisgtk, couldn't find package ndisgtk

the aptitude command responded with the expected gui.  allowing further configuration, the admin install was apparently successful however i failed at installing the linux driver provided by the manufacturer.

somehow i am failing to find instructions for installing drivers or wrapper using the ubuntu server documentation either the html or pdf version.  

this is not a complaint, i wanted to know if instructions for aptitude -> admin are in the server manual.  having searched the internet it did not provide me with very much information for using aptitude to install the driver / wrapper.

again i thank you for your attention

---

### Post by RomeReactor on 2007-01-22
Sorry for answering so late. In case you still have trouble with your wireless:

Did you manage to install ndiswrapper? Also, i don't know if it handles linux drivers; i think it only helps you installing windows drivers on linux, so if you have the win drivers for your card, then check the [NdisWrapper]("http://ndiswrapper.sourceforge.net/") page for instructions and a list of supported cards. Again, sorry for not providing you with more specific help.

---

