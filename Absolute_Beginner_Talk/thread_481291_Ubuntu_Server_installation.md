---
title: "Ubuntu Server installation"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by siegfried drews on 2007-06-22
Need your help to install server. Have advanced up to inserting username and password but am now confronted with command line prompts I am not familiar with. My only past server experience is with Windows Server and I had expected an installation process with ubuntu which leads to a GUI interface and from there to install the various server elements as I had experienced in windows. 

Questions: Does ubuntu server have a GUI interface at all or is the whole installation process command line driven?
                 Can I expect any similarity to Windows Server with regard to user friendliness or is this a totally unrealistic                 expectation?

I have no past experience with Linux and as the desktop version install went very smoothly and I instantly liked what I saw,  I thought to also try the server version. Is this where the similarity in ease of installing stops and I better go back to the old or is it worth pushing on. I certainly am too old to learn all that command line stuff.

Thanks for your help.

---

### Post by p_quarles on 2007-06-22
No GUI for the server edition. If you need one, though, you can use the regular edition and then install whatever server software you need. 

The reason for this is that GUIs seriously slow down a machine's performance, so if the server is doing a lot of work it's kind of self-defeating to install the GUI. If you just want one machine that can make all the others talk to each other, though, just install Ubuntu and get Samba and whatever else you need.

---

### Post by Happy_Man on 2007-06-22
Um... a server version will basically use the command line to install a command-line interface on your computer. Sure, you can get a GUI afterwards. But if you just want a basic install, the Desktop version is the way to go.

---

### Post by lazyart on 2007-06-22
You can install the GUI onto the server by doing```
sudo apt-get install ubuntu-desktop
```You'll usually not run a GUI on the server because it steals cycles away from it's main task... which is serving!

Admittedly I did install xubuntu-desktop on my webserver and I jump into it once in a while.  When I'm done I log out of the X session, leaving it at the command line.  There is also Webmin that lets you configure all the server stuff from another machine on the network and it's exposed via http on port 10000.

---

### Post by siegfried drews on 2007-06-22
Thanks guys, certainly a quick and positive response. You may get me interested in command line stuff yet! Followed lazyart advise but got answer: ubuntu-desktop package not foun/available. Where do I go from here? Can I intall Firefox get on the internet and find desktop package somewhere to install?

Thanks again

---

### Post by bodhi.zazen on 2007-06-22
Easiest is to install the desktop CD.

If not : ```
sudo apt-get install ubuntu-desktop
```From the command line.

---

### Post by Jimmyfj on 2007-06-22
You'll need to have the install disk in the drive - or use aptitude to install what ever programs you'd want

---

### Post by p_quarles on 2007-06-22
> **Jimmyfj said:**
> You'll need to have the install disk in the drive - or use aptitude to install what ever programs you'd want
I.e., just substitute "aptitude" for "apt-get" in the code lines that others listed above. 

If you think you can get used to the command line, though, you might consider sticking with the basic server package. I run a file/web-development server off a semi-old machine (Pentium IV with 384 MB RAM) and not only has this setup drastically increased the old machine's usability, it's saved space: I administer it from SSH, and therefore don't need a monitor or keyboard for it. 

Of course, if you want to use the server box as a desktop as well, you should install the Ubuntu desktop edition.

---

### Post by siegfried drews on 2007-06-22
Thanks  again to all for your help.... this is really a great way to learn.  I am still persisting with installing desktop but eventually like to copy p_quarles approach. I have a similar situation with an old P4 box and 512MB  ram. Dont't understand whar "administering from SSH" means though.

I have loaded the server installation disk but still received the same reply when looking for umbuntu-desktop. I also tried umbuntu desktop disk but got same result. It seems that it does not look in CD drive automatically so what do I have to add in command line for "it" to look in CD drive.  Please give me the entire command line to make umbuntu desktop install work.

So much to learn ... and so little time!!!

Thank you

---

### Post by bodhi.zazen on 2007-06-22
If you want to use the CD you need the alternate CD rather then the desktop or server CD.

---

