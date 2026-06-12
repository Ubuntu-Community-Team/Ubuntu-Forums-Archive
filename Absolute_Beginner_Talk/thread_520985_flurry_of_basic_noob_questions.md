---
title: "flurry of basic noob questions"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by mamadu bwana on 2007-08-08
Hi,

I am new to Ubuntu and I have just installed a wifi network in my home.  I have a number of pathetically basic questions which I would need some help with:

1) I am using the firestarter firewall.  I need to be root to launch it, but I would like to have it started each time I boot up my computer.  Alas, since I use Ubuntu as a user, when I reboot my session does not have to priviledges to restart firestarter.  how do I make my system automatically start firestarter every time I start my computer?

2) I have created a /usr partition on a hard disk which I wanted to use to store downloaded files on.  However, only root can write on this subdirectory.  Would it be safe to "open" /usr to all by a chmod 777 command or how do I give full read/write access to /usr to myself as a user?

3) I am using the cable modem given to me by brighthouse and a Linksys WRT54G wireless broadband router.  I noticed that since I switched from dial-up to broadband I never get any suspicious/hostile hits reported by my firestarter firewall.  Is there a built-in firewall inside my cable-modem, wireless router or does brighthouse filter packets on its networks?  How good is the protection given by this?  Should I even bother having a firewall on my individual computer?

Lastly, I have not succeeded in making any USB wireless cards work with Ubuntu (Feisty Fawn).  Is there one out there which works "out of the box" without any manipulations?

May thanks for any help.

Mamadu

---

### Post by Dr Small on 2007-08-08
Your firewall is always on. Firestarter is just the GUI for it. So you don't need to worry about it automatically coming up on bootup. Your firewall is there :D

And about the /usr partition, I think you should chown it to your account. (Somebody else will have to answer this, because I don't know if that is the best move).

Regards,
Dr Small

---

### Post by meierfra on 2007-08-08
3) Your wireless router has a build in firewall.

---

### Post by Het Irv on 2007-08-08
> **mamadu bwana said:**
> Hi,

Lastly, I have not succeeded in making any USB wireless cards work with Ubuntu (Feisty Fawn).  Is there one out there which works "out of the box" without any manipulations?



Feisty Fawn does not support USB out of the box.  To get USB support you have to run the updates and that should do it.

---

### Post by mamadu bwana on 2007-08-08
@Dr.small - alas, my firewall is not always on. when I do "sudo iptables -L" I see that firestarter did *not* start up again...
@meierfra - I realize that, my question was how good is that firewall really?
@Het Irv -  I ran all the updates (sudo apt-get update && sudo apt-get dist-upgrade) but the cards which I tried still do not work.  Does anybody know of what which is truly plug-and-it-works?

---

### Post by Steveway on 2007-08-08
Firestarter is no Firewall!
It is a gui wich helps to configure Iptables, wich is your Firewall.
Iptables is installed by default and starts always on boot up.

---

### Post by Nythain on 2007-08-08
another note... you should not be using your /usr directory to store downloaded files in
you would be much better off setting up /home with its own partition, and creating a directory in your home (/home/username/stuff) and storing downloaded files there. you could go even farther by creating a seperate partition and mounting it at like /mnt/stuff or /media/stuff or whatever, that way if you ever reformat you can nix your home directory (if you want, some do some dont) and still have access to the stuff you have downloaded before.

I have three hard drives for my computer
A - /boot, SWAP, and / partitions (contains my actuall linux system install)
B - /data (contains files i have downloaded, eg music, pictures, programs)
C /data/video (contains all the videos i have downloaded)
With this setup unless i accidently click on something i really shouldnt during the ubuntu install process i have no worry about losing any of my backed up/saved/downloaded material i have been collecting over the years

/usr is used for a completely different purpose (generally its where user specific programs get installed, and thier config files if not found in that users /home directory) wich is why you dont have permission by default to edit it

Your wireless router will do an ok job of providing minimal firewall protection, though if you are truley paranoid i wouldnt rely on it solely.

Firestarter is just a GUI for iptables wich is by default installed and running in ubuntu. If you need Firestarter to run at startup, you will have to search on how to have things autostart on login with gnome, and just have it gksudo firestarter... it will ask you for a password everytime, but it will load just fine after that... i had firestarter autoload with when i ran kde, but eventually got annoyed at my computer asking me for my passowrd to load it everytime i booted up.
An alternative, you could add firestarter to your sudoers list so you dont have to put in a password when you run it... you can google sudoers or search here for how to edit that file, but be carefull, things are meant to require passwords for a reason

As far as the usb adapter, i believe thats already been coverd, and i cant help much because im all pci like

---

### Post by foxholeunder on 2007-08-09
> **mamadu bwana said:**
> Hi,

I am new to Ubuntu and I have just installed a wifi network in my home.  I have a number of pathetically basic questions which I would need some help with:

1) I am using the firestarter firewall.  I need to be root to launch it, but I would like to have it started each time I boot up my computer.  Alas, since I use Ubuntu as a user, when I reboot my session does not have to priviledges to restart firestarter.  how do I make my system automatically start firestarter every time I start my computer?

2) I have created a /usr partition on a hard disk which I wanted to use to store downloaded files on.  However, only root can write on this subdirectory.  Would it be safe to "open" /usr to all by a chmod 777 command or how do I give full read/write access to /usr to myself as a user?

3) I am using the cable modem given to me by brighthouse and a Linksys WRT54G wireless broadband router.  I noticed that since I switched from dial-up to broadband I never get any suspicious/hostile hits reported by my firestarter firewall.  Is there a built-in firewall inside my cable-modem, wireless router or does brighthouse filter packets on its networks?  How good is the protection given by this?  Should I even bother having a firewall on my individual computer?

Lastly, I have not succeeded in making any USB wireless cards work with Ubuntu (Feisty Fawn).  Is there one out there which works "out of the box" without any manipulations?

May thanks for any help.

Mamadu


I literally have over 2000 feet of ethernet cable strung from plant hooks on my ceiling so I can not help you with the wireless troubles, but as for question 3:

Any type of router is a firewall the only difference is how much each make/model allow you to configure it. A router actually blocks incoming traffic unless you have requested information from the outside then it will allow the requested traffic inside. If you change your routers configuration and open ports permanently then unwanted outside traffic can get in, otherwise a router blocks everything.

Firewalls no matter what operating system you are running do not block anything from coming into your computer, all firewalls do is notify you that something has entered your computer. The same thing goes for anti-virus.

I caution you about wanting firestarter to load every time you start your computer as all firestarter is as mentioned by steveway i think it was, this is a gui for configuring your iptables, and should only be executed as root, to have it running as a full-time service is a major security risk.



I must assume you defined your own partitions manually during installation; as /usr is created by default when you let the partition manager auto-partition for you. in a standard auto-partition setup /usr is filled with all sorts of application data that should be owned by root and root only, as many application configuration files are installed here. 

If you desire adding ownership for yourself for /usr or any file/folder you desire all you have to do is fire up a terminal and type:
```

sudo chown your-user-name /usr

```

That will give you read/write access to the /usr directory although I strongly caution you to avoid this if many applications have data installed in this directory as this too is a major security risk.

---

