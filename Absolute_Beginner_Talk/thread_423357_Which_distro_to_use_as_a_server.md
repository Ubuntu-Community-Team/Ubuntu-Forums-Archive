---
title: "Which distro to use as a server"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Jordanwb on 2007-04-25
Now note this computer is 7 years old:

Celeron 533 Mhz
256 MB RAM
10/100 MB PCI NIC
48X CD
100 Mhz FSB

What I'm doing is I want to set it up as an intranet server to do make web applications. See I'm a website designer so I'll need MySQL, and PHP 5. I installed Ubuntu 7.04 Alternate but I don't like the having to login each time. I tried the server version but I got a DOS like enviroment which I wasn't expecting.

Does anyone have a suggestion for a distrobution of Linux that would fit these requirements? Any help would would be appreciated.

---

### Post by 007Bond on 2007-04-25
Easily the best choice for you with low specs such as these is to go with Xubuntu because it is very lightweight and still packs a punch. Gnome (ubuntu) might be a little too demanding for your cpu to handle.

---

### Post by Jordanwb on 2007-04-25
I'll take a look at Xubuntu as well as others. I can download it at school about 8X faster than here (Home 50 KB/s school 400 KB/s)

I'll see what others suggest. Thanks 007

---

### Post by speeddemon8803 on 2007-04-25
Any more help just let us know

---

### Post by igknighted on 2007-04-25
Why not just install Ubuntu server edition?  It sets up apache/mysql/php during the install.  If you need a gui after that install something really light like Xfce (preferably not the whole of xubuntu-desktop) or even better Fluxbox or IceWM.

EDIT: For a web server, you want something dos-like.  Having a GUI (especially on a machine that old) will dramatically reduce its performance.  You are better off using it alone with no gui (or even monitor) and using ssh (or putty if you are using windows)  to update it when needed (or webmin).  That said, if you still want a GUI, just install the bare minimum, because even Xubuntu has tons of GUI specific services that will drag a machine of that age down that as a server you will never need.

---

### Post by Jordanwb on 2007-04-25
I tried the server version but as I said I wasn't expecting a DOS like enviroment, plus I'm not familiar with MySQL commands other than SELECT, UPDATE, DELETE etc. The basic table queries

---

### Post by 007Bond on 2007-04-25
igknighted (regards) Has a very strong point. As i did not see that it was for server I would suggest a server install followed by an Xfce desktop replacement. Or maybe an Alt server iso.

---

### Post by Jordanwb on 2007-04-25
I also want to be able to perform remote mysql commands using something like phpMyAdmin.

---

### Post by igknighted on 2007-04-25
> **Jordanwb said:**
> I tried the server version but as I said I wasn't expecting a DOS like enviroment, plus I'm not familiar with MySQL commands other than SELECT, UPDATE, DELETE etc. The basic table queries

All you need to do is type "sudo apt-get install xserver-xorg xfce" or "sudo apt-get install xserver-xorg icewm" to get a gui that you can start on command (startx).  The gui is easier to install than the server, so start with the server then add the gui.

---

### Post by Jordanwb on 2007-04-25
so I'd type in "sudo apt-get install xserver-xorg xfce" at the command prompt and I'd get a GUI?

Plus I want to be able to shut down the computer by pressing the power button

---

### Post by Jordanwb on 2007-04-26
I typed in "sudo apt-get install xserver-xorg xfce" (no quotes) at the prompt but it didn't install anyhhing. It said it couldn't find the package or something. I was able to install MySQL but I had no idea on how to start it up or to install Apache .

---

### Post by igknighted on 2007-04-26
> **Jordanwb said:**
> I typed in "sudo apt-get install xserver-xorg xfce" (no quotes) at the prompt but it didn't install anyhhing. It said it couldn't find the package or something. I was able to install MySQL but I had no idea on how to start it up or to install Apache .

Sorry, it's xfce4 not xfce :hides in shame:

---

### Post by Seisen on 2007-04-26
Actually its 

```
sudo apt-get install x-window-system core xfce4 
``` that will give you X and XFCE.

and here is some help on installing apache and getting it to work.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server")

---

### Post by Ateo on 2007-04-26
for one, servers should never have a GUI. All that memory used up by the GUI can be better utilized elsewhere...

Anyways, try Gentoo OR Feisty Fawn Server Edition. The first is great is you have lots of time. The latter is great because it just works.

If you find that you REALLY REALLY can't deal without a GUI, install webmin. But to have Gnome, KDE or XFCE is just dumb as it uses up precious resources.

---

### Post by rillip on 2007-04-26
Running that command would install the gui. To run the gui, you'd just type "startx" (or it might be sudo startx, if you get an error about insufficient permissoin or something of the like, try that).

You can always shut down with the power button.  That's kind of the point.  Whether it's a good idea or not...  I'd recommend just running the command "sudo shutdown" whenver you want to shut down.

Additionally, you do not need a gui to have PHPMyAdmin.  I work for a web hosting company, and our customers use it every day; there is no gui setup on the servers (we have one for them to install it, but it just runs a script on the backend).

---

### Post by az on 2007-04-26
> **Jordanwb said:**
> I also want to be able to perform remote mysql commands using something like phpMyAdmin.

Enable the universe repository (it is already enabled in feisty)
and run

sudo apt-get install phpmyadmin


I would suggest that the best setup is to run a headless server (with no GUI) and control it remotely, even using windows.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Install the LAMP stack, and ssh and you can use Putty to connec to the box and administrate it.  You can install phpmyadmin and whatever web application you use.

---

### Post by Jordanwb on 2007-04-26
I'll try all that when I get a chance. Performance isn't an issue I want to make sure that my web apps will work on a linux enviroment before I put it on my website which is on a Linux server.

---

### Post by Jordanwb on 2007-04-26
How do I install gksu whatever that is? I typed in "sudo apt-get install gksu" (no quotes) but it couldn't find the package any suggestions?

---

### Post by stmiller on 2007-04-27
Yeah why would you need xorg on a server?

Just use the ubuntu server install disc.

---

### Post by Jordanwb on 2007-04-27
^ I have no idea. I'm a newb to Linux. Right now I'm trying to install a FTP server.

---

### Post by arbulus on 2007-04-27
I have a file and print server, and have very little need most of the time to actually sit at it and use it directly.  But when I do, I like having the option of the GUI, so what I did was install the Boot Up Manager (BUM) You should be able to find that in the Synaptic Package Manager.  It gives you control over what applications will start on boot.  I just turned off the GUI, so when I boot, I just get a terminal prompt.  I don't even log the thing in.  I just boot it, leave it at the terminal log in prompt and turn the monitor off.  And if I need to use the GUI, then I can start it up as necessary.  

As others have mentioned, XFCE, Fluxbox, or IceWM would be best for your system specs for a GUI.

---

### Post by bigfatdummy on 2007-04-27
I like GUI on my server because its my only Linux machine at the office. It gets old doing everything remotely on a windows box.

Also why does it matter if server resources are not a concern?

---

### Post by az on 2007-04-27
> **bigfatdummy said:**
> I like GUI on my server because its my only Linux machine at the office. It gets old doing everything remotely on a windows box.

I find using the command line remote makes me able to get things done a lot faster.

> **bigfatdummy said:**
> 
Also why does it matter if server resources are not a concern?

It's also a security concern.  It's best practice to not install anything on a production server that you don't need.

---

### Post by Jordanwb on 2007-04-27
I tried to install Proftpd to get ftp access but it can't find the package. There was a documentation on configuring proftpd but it doesn't say anything about installation.

---

### Post by az on 2007-04-28
proftp is in the universe repository,  You need to enable the universe repo.

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)
[https://help.ubuntu.com/community/Repositories/CommandLine?action=show&redirect=CommandLinePackageManagement](https://help.ubuntu.com/community/Repositories/CommandLine?action=show&redirect=CommandLinePackageManagement)

---

### Post by bigfatdummy on 2007-04-30
I guess its a matter of comfort level. If you are comfortable with Linux and have the ability to figure out the commands then you would rather not having the GUI. I can see your point about not installing anything you dont need. 

I have a LAMP server up and running. I will just force myself to learn it.

---

### Post by TheGameAh on 2007-05-09
Could you simply install everything you needed with a GUI in place, then when you were done, disable or tell the GUI not to start?

I too find myself lost at times in a Linux environment without a GUI.

---

