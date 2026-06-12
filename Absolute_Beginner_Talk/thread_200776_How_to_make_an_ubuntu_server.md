---
title: "How to make an ubuntu server?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by DiamondX on 2006-06-20
Hi, I am going to make a server for my home. I am planing on using Ubuntu, because it is the linux distro that I am most familiar with. Here is a list of the features I want to have:
:D = I know how to do this
:confused: = I dont know how to do this
[LIST]
[*]:D MythTV Backend
[*]:D Wireless router (I made a thread about this, I know how I will do it)
[*]:confused: Firewall
[*]:confused: Remote desktop - so I dont need a moniter to do stuff
[*]:confused: Some way to access it with a terminal
[*]:confused: A backup program's backend - to backup my laptop & desktop
[/LIST]

Most of the ??? ones I can probably figure out by finding a program (on sourceforge) and reading the docs. The one I would need help with is the remote terminal access. Does anyone know of a tutorial on the net that I can follow? I am a fast learner, and can probably do it with a little help. Thanks.

---

### Post by calx on 2006-06-20
Would ssh help? 

Try this..
*apt-get install ssh*

then...
*ssh you@127.0.0.1*

[QUOTE=DiamondX][*]:confused: Some way to access it with a terminal
 The one I would need help with is the remote terminal access. Does anyone know of a tutorial on the net that I can follow? I am a fast learner, and can probably do it with a little help. Thanks.[/QUOTE]

---

### Post by cskeide on 2006-06-20
I don't know the answer to all of this, so hopefully others will fill in the blanks.

Firewall:
[iptables]("https://help.ubuntu.com/community/IptablesHowTo?highlight=%28firestarter%29"). There are GUI frontends, such as firestarter. The approach to setting up a firewall will probably depend on how you plan to setup ubuntu as a wireless router, but you could probably achieve both with firestarter.

Remote Desktop:
Install a vncserver. There are several alternatives. More info at [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Some way to access it with a terminal:
Install ssh-server. More info at [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Hope this helps. Let me know if you need more specific instructions. =)

---

### Post by taurus on 2006-06-20
Firewall = firestarter or you don't really need it!

Remote desktop = FreeNX is one option.

Some way to access it with a terminal = install sshd and use ssh to log into your box.

A backup program's backend = simple-backup-config/simple-restore-gnome.

---

### Post by DiamondX on 2006-06-20
Thanks for all the quick replys! Isnt it ironic that you generally get faster and better support for free software? Anyway, the PC that will be the server has no motherboard (DOA from newegg, no more, got full refund), and I will order one hopefully today, maybe tomarrow.

I have a question: the router that I currently have is a D-Link DI-604. It is wired with a firewall. Should I disable the firewall on the router and put the server before the router (with 2 ethernet cards, idk if possible), or should it be after, just for my wireless notebook? Also, should my server also be connected to windows PCs? Would it be bad, security wise?

---

### Post by jason.b.c on 2006-06-20
> I have a question: the router that I currently have is a D-Link DI-604. It is wired with a firewall.

Well you could also make your server double as a router/firewall.. "maybe"

[www.routerboard.com/rb44.html](www.routerboard.com/rb44.html)

and (*"maybe"*) use

[www.ipcop.org/index.php](www.ipcop.org/index.php)

oh and here's somemore server stuff , in case you wanted to know more.[http://httpd.apache.org/](http://httpd.apache.org/)

You can test your firewall here.    [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

:D   I hope this helps at least a little bit..O:)

---

### Post by DiamondX on 2006-06-20
Wow, jason, thanks for all the links. I have 2 ethernet cards + the onboard from the motherboard. Im sure I could do something like the RouterBOARD. Wouldnt look as nice, but also wouldnt look that bad. I cant wait untill I get my stuff.

---

### Post by dmizer on 2006-06-20
here's my suggestions: 

first of all, if your archetecture is going to be as follows:
dsl/cable modem --> dlink router --> networked computers (including server)
then my suggestion is to not worry about a firewall on the server and just configure it from your router.

you might want to consider the following archetecture depending on what you want to do:
dsl/cable modem --> server computer (two nics) --> dlink router --> networked computers.
this would allow you more fine controll of your traffic, and isolate your windows networked machines for better security in file sharing.  but it would also be more difficult to setup.

for vnc, you'll want to take a look at this excelent thread (it's what i use):
[http://www.ubuntuforums.org/showthread.php?t=122402](http://www.ubuntuforums.org/showthread.php?t=122402)
in addition to that, you'll need tightvnc viewer (for security reasons, i suggest you stick with the viewer only install of tightvnc in windows):
[http://www.tightvnc.com/](http://www.tightvnc.com/)

for terminal access, into your server from a windows machine, you'll need putty: [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)
and you'll need to install an ssh server on your ubuntu server:
[http://easylinux.info/wiki/Ubuntu#SSH_Server](http://easylinux.info/wiki/Ubuntu#SSH_Server)

don't know about backups, i just have a samba folder on my server for that.
here's the most complete guide i've found for just about anything you want to do network wise: [http://easylinux.info/wiki/Ubuntu#Networking](http://easylinux.info/wiki/Ubuntu#Networking)

let us know how it turns out, keep track of snags you run into and post what you did to fix 'em.

---

### Post by jason.b.c on 2006-06-20
[QUOTE=DiamondX]Wow, jason, thanks for all the links.[/QUOTE]


Your welcome...:D 

Wait , Did you say your on **Cable Modem** internet..??  [http://www.shoplet.com/hardware/db/1030193.html](http://www.shoplet.com/hardware/db/1030193.html)

O:)

> System Requirements - Microsoft DOS, Microsoft Windows 3.x/95/98, Apple MacOS, Linux, Microsoft Windows 2000 / NT4.0, Microsoft Windows Millennium Edition

---

### Post by dmizer on 2006-06-20
sorry ... i just realized i linked you for breezy instead of dapper (habit).

the link for vnc (remote desktop) also has dapper directions so that's still good.

the rest of the information for configuring your server in dapper can be found here: [http://easylinux.info/wiki/Ubuntu_dapper#Networking](http://easylinux.info/wiki/Ubuntu_dapper#Networking) <- this is a very comprehensive guide.  i've linked you directly to the networking section, but if you go to the top of the page, there's lots more how to.

---

### Post by underdog on 2006-06-20
I just set up a machine similar to what you want, for windows clients putty (ssh) and ultravnc (remote desktop) work very well.

---

### Post by DiamondX on 2006-06-21
dmizer: Thanks for the links. FYI, the wiki you gave me is also at ubuntuguide.org. ;) I didnt see the Networking section, I just normally use it to get random programs running, like dvd reader, etc.

jason: I have a seperate cable modem. I dont think it would be any better at this point to have it in my server, but thats pretty interesting. Unfortunatly im on a **very** tight budget. :(

everyone: I think I have everything figured out except for the fine details. I am wondering if it would put my linux boxes (and server) at risk to have them linked to windoze machines? I know linux is very secure, but what are the chances someone would hack a windows machine and know how to get into the linux machines? Now that I think about it, I dont have any personal info. My parents use a windoze (and have CC numbers, social security numbers, and financial software on it... not good, Im trying to switch them over, but thats another story).

I still need to get money together and order parts. When I get them, I will most likely have new questions, but untill then, thanks a lot everyone!

---

