---
title: "Ssh????"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-05-09
Can anyone guide me in the right direction on how to install and configure SSH?:confused:

---

### Post by ryanakca on 2006-05-09
SSH is installed by default I believe... To ssh to another computer, you would run this in Konsole or Terminal or whatever terminal/console there is on your system:
ssh username@address
example: ssh [email]ryan@kubunturocks.org[/email]

If it isn't installed, run this:
sudo apt-get install ssh

Hope this helps... And I presume you want the client and not the server :)
Cheers,
ryanakca

---

### Post by ubuntu_demon on 2006-05-09
AFAIK an ssh client is installed by default but to install a ssh server you will have to do the following :

$sudo apt-get install ssh

The standard configuration works but it will only ask for a username and a password so you have to make sure not to have easy username / password combinations otherwise it's insecure.

to log into your machine from remote just do the following :
$ ssh username@ipadress

if you want more security (for instance because you don't trust the users of your system to have safe passwords or because your just a bit paranoid) look here :
[http://www.ubuntuforums.org/showthread.php?t=137746](http://www.ubuntuforums.org/showthread.php?t=137746)
[http://www.ubuntuforums.org/showthread.php?t=30709](http://www.ubuntuforums.org/showthread.php?t=30709)

---

### Post by skippy81 on 2006-05-09
You should just be able to download SSH as a package with apt-get or synaptic.   Once its installed the service should start automatically.  There is a config file in /etc/ssh/ssh_config but I doubt you will have to edit it.  

Once youve installed it, use another machine and use a utility such as Putty to telnet onto port 22.  If its working you should be greeted by a shell prompt and asked to enter your user name and password so you can get in.  

If your not getting a response on port 22, then make sure there isnt a router/firewall between your host and the linux box.  If there is, you will need to set up port forwarding on port 22 to the linux host - most decent hardware routers make this very easy.

---

### Post by NeoGreen on 2006-05-09
Okay, I'll try it thanks.:)

---

### Post by NeoGreen on 2006-05-10
What is the difference between VNC and SSH?:confused:

---

### Post by ubuntu_demon on 2006-05-10
[QUOTE=NeoGreen]What is the difference between VNC and SSH?:confused:[/QUOTE]
with you can log in from remote in text mode. ssh uses encryption.

with vnc you can log in graphically from remote. vnc doesn't use encryption. vnc uses more bandwith than ssh. You can tunnel vnc over ssh so that it uses encryption. 

you can also use freenx which is similar to vnc and uses less bandwith and uses encryption but it is more of a hassle to set up.

If text mode is enough use ssh. Otherwise try vnc. If you find vnc is too slow for you try freenx.

---

### Post by Jason_25 on 2006-05-10
[QUOTE=ubuntu_demon]AFAIK an ssh client is installed by default but to install a ssh server you will have to do the following :

$sudo apt-get install ssh
[/QUOTE]
Actually, the command is 
```

sudo apt-get install openssh-server

```

---

### Post by ubuntu_demon on 2006-05-10
[QUOTE=Jason_25]Actually, the command is 
```

sudo apt-get install openssh-server

```[/QUOTE]
That's totally the same but takes more typing :)

ssh installs openssh-client and openssh-server. But openssh-client is also installed by ubuntu-standard so in effect only openssh-server will be installed.

---

### Post by gr0kzer0 on 2006-05-10
My username on my ubuntu box is, eg, xxx. I have a shell account at tty.freeshell.org, where ny username is also xxx. I give command in console
```
ssh tty.freeshell.org
```

The computer asks for pw for [email]xxx@tty.freeshell.org[/email]. Type it in and I'm connected.

ssh is encrypted so no nosy-assed crackers can eavesdrop.

ssh can also be configured to use encrypted keys instead of pw, but I haven't figured it all out yet.

This is for ssh out of my box, not in. You need the ssh daemon for that.

PS try "man ssh"

---

### Post by n3tfury on 2006-05-10
[QUOTE=ubuntu_demon]with you can log in from remote in text mode. ssh uses encryption.

with vnc you can log in graphically from remote. vnc doesn't use encryption. vnc uses more bandwith than ssh. You can tunnel vnc over ssh so that it uses encryption. 

you can also use freenx which is similar to vnc and uses less bandwith and uses encryption but it is more of a hassle to set up.

If text mode is enough use ssh. Otherwise try vnc. If you find vnc is too slow for you try freenx.[/QUOTE]


ultravnc i believe has encryption plugins.

---

