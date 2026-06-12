---
title: "Just Installed Ubuntu 6.06 : Some questions...!"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by bimaljr on 2007-01-20
Hi,
I have just installed Ubuntu 6.06 on my PC
I am a newbie.
The instation was fine and no problem, I have give **bimal** as username. 

**My questions :**
1. I cannot create folders at anywhere, I can create folder on desktop only... how to create... it says you have no permission to do this...???

2. How to connect internet??? I have cable internet connection, and with login ID and PASSWORD.

3. How to login ROOT??? what is the password?? When I type command SU in terminal, it asks me for password... what is my password, I have give my user password which I given at installation, but nothing works...


Please help me on this... Thanks in advance...

---

### Post by EdThaSlayer on 2007-01-20
> 1. I cannot create folders at anywhere, I can create folder on desktop only... how to create... it says you have no permission to do this...???

You can create files in your desktop and your home directory(home directory can be found in Places->Home).

> 2. How to connect internet??? I have cable internet connection, and with login ID and PASSWORD.
I have never touched a cable modem before, so I can't really help you with this one :( 

> 3. How to login ROOT??? what is the password?? When I type command SU in terminal, it asks me for password... what is my password, I have give my user password which I given at installation, but nothing works...

Ubuntu by default doesn't have root. It instead uses "sudo" where you have to use the password of your user(in your case bimal).So everytime you want to install something using root priveleges all you have to do is type "sudo applicationname/processname" and it will run it. The good thing about sudo is that it also goes off automatically after 15 minutes(making it quite secure). There are some ways to get the root user back in Ubuntu although it is not usually recommended.

---

### Post by geokok1981 on 2007-01-20
> **bimaljr said:**
> Hi,
I have just installed Ubuntu 6.06 on my PC
I am a newbie.
The instation was fine and no problem, I have give **bimal** as username. 

**My questions :**
1. I cannot create folders at anywhere, I can create folder on desktop only... how to create... it says you have no permission to do this...???

2. How to connect internet??? I have cable internet connection, and with login ID and PASSWORD.

3. How to login ROOT??? what is the password?? When I type command SU in terminal, it asks me for password... what is my password, I have give my user password which I given at installation, but nothing works...


Please help me on this... Thanks in advance...

1. You should be able to create folders in the desktop and your hoem folder. The rest places (filesystem in general) require super user rights in order to modify them, but you should not mess with them unless you know what you are doing.

3. In Ubuntu there is no su. You should be using the "sudo" command when you need su rights. This was decided for security reasons. In example if u want to edit a file for which u need su rights u give to  a terminal the command:

sudo gedit myfile

Then the terminal will ask for your user password which is the one u specified during Ubuntu installation.

---

### Post by deadgobby on 2007-01-20
On #2 Did you check System>Admin>Networking?
On #1 and #3 I think you may did some thing wrong at the install.
 How to set/change/enable root user password open up the terminal and copy and paste the following.
sudo passwd root

Most of the time the password you signed on to is the same password as root. 
Here is a Wiki page to help you out.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
[http://www.unix-tutorials.com/tutorials.php?os=Ubuntu](http://www.unix-tutorials.com/tutorials.php?os=Ubuntu)
[http://www.linuxreality.com/](http://www.linuxreality.com/)
[http://doc.ubuntu.com/screencasts/](http://doc.ubuntu.com/screencasts/)

Gobby

---

### Post by Simanek on 2007-01-20
[COLOR="Red"]*I see it took me too long to write my response, but I'll leave it all the same.*[/COLOR]
Well, if that is in fact your experience, you may want to reinstall. Sounds odd. However, maybe you are misunderstanding something.

1 If you go to the menu/Places/Home Folder   can you create a folder in there?
2 I am assuming you have your computer physically connected to your cable modem via ethernet. Go to menu/System/Administration/Networking  and see if your ethernet card is available as a device. If it is, highlight it and click 'Properties' and you will most likely see some familiar setting options there. If this isn't the case, perhaps you could explain your situation with a few more details.
3 Ubuntu works on the premise of having no root account (at least, it isn't 'active' by default. What the difference is, I'm not sure.) and only using the 'sudo' command to use root previledges for specific actions. When you type 'su' you are actually attempting to login as 'super user' for that terminal session. That might be your problem. Give 'sudo' or 'super user do' a try and enter your regular user account password.

---

### Post by bootslap on 2007-01-20
It would be a good idea to go thru the release notes first. It would give you more insights and would be helpful as a newbie..

---

### Post by bimaljr on 2007-01-20
:KS so many replies.... Thanks for all of you....
My 1st and 3rd problems are solved by your all help...
But my intenect connection problem is still as it is... :( 

**[FONT="Courier New"]This is the info of my network :[/FONT]**
When I go to system > Networking There are two connections.
**1. Ethernet Connection :** I think this is just a LAN connection and with text "The Interface eth0 is active". I have set all three IP address for my LAN connection as provided by my Service Provider.
**2. Modem Connection :** This is Desabled. When I go to enable this connection, it says for phone number and more info.. I thik it's for the dialup connection. it cannot save because i don't have any phone number to connect to net...

I can connect Internet on Fedora core 6 without any problem through system > Networking... but the Network box is different in Ubuntu...

---

### Post by bradford72 on 2007-01-20
Okay, I had internet connection problems too, and I'm not sure if this is the right fix for you, but what I had to do was configure firefox a bit...

Here's what I did, step by step (if you wanna try it yourself)

1. in the URL (address) bar of firefox type 'about:config' (omitting the quotes)

2. go down to the entry that says 'network.dns.disableIPv6' (again omit the quotes)...you can type network.dns.disableIPv6 in the filter box and it will take you straight there...

3. the default value for this is 'false' change it to 'true' by right clicking the value and choosing toggle.

4. close your browser (firefox) and restart it.

After I did that I was able to connect to any site I wanted to

I went back and forth between windows and ubuntu several times over this, I tried several different distros of ubuntu, and just about the time I was about to give up on linux for good, I came across a book that told me about 'about:config'.  There's a lot of stuff in there that should probably not be messed with until you know exactly what you are trying to do, and I just found that key by looking around in there and making a guess at what SEEMED right.  I think that I should maybe say that, as a noob, I'm only changing ONE AT A TIME, If what i tried doesn't seem to work, or I can't tell what the effect is I change the setting back, that way I haven't changed a bunch of stuff and forgotten what all I did if things go wrong!  Oh yeah, I keep a log of tried stuff and results too, that's maybe kinda anal...but I've got a record of what I did and how it worked so I don't have to try to remember what is what

---

### Post by Contrid on 2007-01-20
> **bimaljr said:**
> Hi,
I have just installed Ubuntu 6.06 on my PC
I am a newbie.
The instation was fine and no problem, I have give **bimal** as username. 

**My questions :**
1. I cannot create folders at anywhere, I can create folder on desktop only... how to create... it says you have no permission to do this...???

2. How to connect internet??? I have cable internet connection, and with login ID and PASSWORD.

3. How to login ROOT??? what is the password?? When I type command SU in terminal, it asks me for password... what is my password, I have give my user password which I given at installation, but nothing works...


Please help me on this... Thanks in advance...

1. You can only create folders in the home directory of the user with which you are currently logged in. The "Desktop" is part of that home directory. In order to create folders in other locations, you can use the terminal with a command "mkdir" or launch Nautilus as root.

2. Use the following command :

> 
sudo pppoeconf


Just follow the prompts...it's very easy.

3. With a new installation, you have the ability to change the root password from the currently logged in account. Use the following command :

> 
sudo passwd root


...and then type the new root password twice. To login as root using the terminal, use the following command below, and type the password you just created when it prompts for a password :

> 
su


Hope that helps...
Good luck ;)

---

### Post by Contrid on 2007-01-20
An addition to my post above...
Once you have used the command to launch the PPPOE configuration, such as :

> 
sudo pppoeconf


...you can check the connection status using the following :

> 
plog


All of this is done in the terminal.
You'll soon realize how incredibly powerful the terminal is.

---

### Post by bimaljr on 2007-01-20
> **Contrid said:**
> 1. You can only create folders in the home directory of the user with which you are currently logged in. The "Desktop" is part of that home directory. In order to create folders in other locations, you can use the terminal with a command "mkdir" or launch Nautilus as root.

2. Use the following command :



Just follow the prompts...it's very easy.

3. With a new installation, you have the ability to change the root password from the currently logged in account. Use the following command :



...and then type the new root password twice. To login as root using the terminal, use the following command below, and type the password you just created when it prompts for a password :



Hope that helps...
Good luck ;)

:) :D :guitar: 
Hey.... Good NEWS... Now I am connected to Internet on Ubuntu... Great man... It works =D> 

Thanks a lot...

---

### Post by Contrid on 2007-01-21
> **bimaljr said:**
> :) :D :guitar: 
Hey.... Good NEWS... Now I am connected to Internet on Ubuntu... Great man... It works =D> 

Thanks a lot...

Great to hear that it worked out for you.
I don't use cable, but I know that the username and password interface is PPPOE

Now...should your connection not start up when you login, you don't have to go through all that trouble again, since the configuration is already done. Simply use the following command to start your connection :

> 
pon dsl-provider


...and to disconnect

> 
poff


Enjoy Ubuntu!!!
Don't forget to post your questions on the forums. People here are extremely helpful and no question will ever seem stupid...believe me. ;)

---

### Post by bimaljr on 2007-01-21
:p  Thanks.. it works as you say...!

---

