---
title: "Need help instaling azureus bittorent client"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-07-04
I found a guide at Nerdica that shows how to install azureus via command line and then ultimately how to set up a headless bittorrent server using ubuntu.  Well, I don't want to do the headless part but I would like to be able to remotely administer a bittorrent personal server. I followed the following list of commands:
```


mkdir ~/software
cd ~/software
mkdir azureus
cd azureus
wget \
http://prdownloads.sourceforge.net/azureus/Azureus2.5.0.4.jar?download \
-O Azureus2.jar
wget http://azureus.sourceforge.net/cvs/log4j.jar
wget http://azureus.sourceforge.net/cvs/commons-cli.jar
wget http://nerdica.com/wp-content/uploads/2007/06/azureus
wget http://nerdica.com/wp-content/uploads/2007/06/azureus-gui
mkdir ~/bin
mv azureus-gui ~/bin/
chmod +x ~bin/azureus-gui

```

and get the following results:

chmod: cannot access `/bin/azureus-gui': No such file or directory
don1@don1-ubuntu:~/software/azureus$ 


I'm not sure what's going on.  I was hoping that some one here could point me in the right direction.

This is the URL for the entire guide:
[http://nerdica.com/?p=30](http://nerdica.com/?p=30)

Thanks in advance,

VC

---

### Post by Majorix on 2007-07-04
I believe there is a typo in the code you have used.

It should read
```
chmod +x ~/bin/azureus-gui
```

because ~bin without the / in between refers to /bin, which is not what you need. Try using what I typed.

---

