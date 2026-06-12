---
title: "Get Server Edition to Install Desktop GUI"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by whiplash.2006 on 2007-10-02
Hey guys, been playing round with Ubuntu and other various distro's of Linux for a while now but I cant seem to get my head around using Ubuntu Server.  Now please DO treat me like a beginner becasue I am!  I have installed Ubuntu Server on a nice new shiny Dual Core Machine with 2Gb of RAM in, all went fine until I realised that there is no GUI.  So I go on the forums and find out I need to run the [COLOR="Red"]APT-GET INSTALL UBUNTU-DESKTOP [/COLOR]command.  Probelm is, when I run this it does not work!  Now one of the main problems I think I am having is I am behind a proxy!  Again being an absolute beginner I am not 100% sure how to configure the proxy settings in Ubuntu from a command line.  If anyone out there can help it would be greatly appreciated.  HELP ME!!!!!!!!!!!!

---

### Post by skymera on 2007-10-02
why dosent it work?
whats the error?

---

### Post by renzokuken on 2007-10-02
did you put "sudo" in front of the command?

```
sudo apt-get install ubuntu-desktop
```

then you can either start the gui by running 
```
startx
```

or by rebooting

---

### Post by whiplash.2006 on 2007-10-02
Error message is [COLOR="Blue"]E: Couldn't find package UBUNTU-DESKTOP[/COLOR] and yes I did put SUDO in front of the command

---

### Post by overdrank on 2007-10-02
> **whiplash.2006 said:**
> Error message is [COLOR="Blue"]E: Couldn't find package UBUNTU-DESKTOP[/COLOR] and yes I did put SUDO in front of the command

Hi and welcome, do you have a net connection with the machine? What is the out put of the commands ```
sudo apt-get update
```

---

### Post by whiplash.2006 on 2007-10-02
Thats what I was trying to say before lol.  I am behind a proxy and I think the reason I can't get any of the packages is because I cannot authenticate.  I don't know how to configue the proxy settings on Ubuntu server from command line.  I am connected to the local network as I have an IP address and can both see the network from the server and see the server from my Windows XP network machine.  It is just when I try to run updates I get the error I posted Just before [COLOR="Blue"]E: COULD NOT FIND PACKAGE UBUNTU-DESKTOP[/COLOR] :confused:

---

### Post by hyper_ch on 2007-10-02
"UBUNTU-DESKTOP" is not the same as "ubuntu-desktop"

---

### Post by whiplash.2006 on 2007-10-02
I did not type it in capitols on the server, I am just using them on here to get the command accross as clearly as possible so there are no misunderstandings but clearly that doesn't work either lol :)

---

### Post by hyper_ch on 2007-10-02
You can use this:
```

sudo apt-get install ubuntu-desktop

```

Meaning you enclose your commands with [ code] [ /code] tags (just without the space between the "[" and the "code" or "/code".

---

### Post by whiplash.2006 on 2007-10-02
I have already said twice, the package is not on the CD, it is downloaded from the net.  I have a proxy in front of me which I am unsure about how to authenticate to it from Ubuntu and I dont know how to configure my proxy settings on the server from a command line, Please help

---

### Post by renzokuken on 2007-10-02
if you have a desktop edition cd you could install it from that

no idea about proxies though

---

### Post by dark_harmonics on 2007-10-02
Does this help you at all? [http://docking.ncl.ac.uk/proxy/linux/](http://docking.ncl.ac.uk/proxy/linux/)
I want to lend you a hand and it does sound like a connection error, but the only proxy settings i use are for my firefox apps. I know how to do it from the gui but that website mentions several files that you might be able to edit like /etc/socks.conf . The file you need to edit is probably under /etc.

---

### Post by whiplash.2006 on 2007-10-02
OK so I know why the packages are not there, I cant access the internet.  Can anyone tell me how to configure my proxy settings using command line?

---

