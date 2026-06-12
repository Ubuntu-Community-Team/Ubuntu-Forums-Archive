---
title: "[SOLVED] Setting Up Web Sever On Ubunt Gusty Gibbon 7.10"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-01-24
Ok, so I've been told that I can make like a small web server on my Linux machine. All I have is a Sony Vaio laptop got it for about $700 American dollars on sale at best buy. It's normally $1,300 American dollars so it's not bad but it's still just a stock laptop. How would i put like a web server program on my laptop? or is it even possible? I really don't know. if it is possible I'd like it to take up as little space as possible...I'm really kinda confused about what it all is but if anyone knows what 110mb.com is I'd like it to be like that kinda but on my computer where I can put whatever I want onto it and set my web address as what I want it. any help is great. I don't know if it's even possible and that was just like rumour that I heard or what? and if I can do it will that make my computer more likely to get hacked and messed up? because I don't want to put my computer in danger.

thanks
n00b(aka)RadiationHazard

:lolflag:

---

### Post by imon9 on 2008-01-24
haha...yes it is possible 100% certified :D

and it is as easy as installing LAMP from synaptic by a few click.. :)
configuring it will be rather harder (need some learning coz not much GUI/frontend for it), that mean u have to edit the config file in text editor....

tho that computer should be on 24/7 if u want the website to run 24/7 (which most ppl expect it to be)

so ur cost will be:
(1) an Internet connection preferably with static IP
(2) an domain name (u can find a lot of free ones, but u can buy your own domain for a few bucks/year)
(3) expect ur $700 laptop to be running 24/7, so have a good heat-dispersing measure will be appreciated :D

---

### Post by RadiationHazard on 2008-01-24
would [this]("http://www.howtoforge.com/ubuntu_lamp_for_newbies") be a good site for installing LAMP?

---

### Post by RadiationHazard on 2008-01-24
Ok, So i did what that site told me to and i think i've got it all set up now. (screen shots below.) but i don't know where the file is. how to actually get it so people can go to it or add pages and stuff to it. please helpp!! :(:confused::( haha

---

### Post by OffAxis on 2008-01-24
sure.
although if you're not using php you won't need that, and if you don't have any database programs you won't need the mysql.

All you really need for an html/css/javascript website is apache2.

```
sudo apt-get install apache2
```

your document folder will be 
**/var/www**

you can modify /etc/apache2/apache2.conf to your liking, and put the configuration file for your website in /etc/apache2/sites-available/
then use the command
```
a2ensite
```
 to 'Turn the site on' (which just creates a link between the sites-available folder and sites-enabled folder)


On the same machine you can access the site at [http://localhost](http://localhost)
on the LAN you can access it at [http://[your](http://[your) machine's local ip address]
If you want to access the site externally (from a computer not on your LAN) you'll need to forward the 80 port on your router.
Even if you don't have a domain name, you can access the site at [http://[your](http://[your) WAN ip address] as long as you've got that 80 port forwarded to the local ip.

When you're setting it up and getting your .conf files straightened out you'll need to restart apache2 to test your settings. You do that with 
```
sudo /etc/init.d/apache2 restart
```

or 
```
sudo /etc/init.d/apache2 reload
```

Good luck.
And don't forget to check the documentation on the apache website when you have questions;
[http://httpd.apache.org/docs/2.0/]("http://httpd.apache.org/docs/2.0/")

---

### Post by OffAxis on 2008-01-24
> how to actually get it so people can go to it
The folder
**/var/www**
is your web server's root folder. If you put an **index.html** file in there, then it will be displayed when anyone accesses your server.

---

### Post by RadiationHazard on 2008-01-24
well you see. i'd already went by the instructions of that other site? so what do i do? =\\

---

### Post by kevinatkins on 2008-01-24
Hi,

... and to create your web pages, I'd thoroughly recommend 'kompozer', which is a nice, simple, GUI-based program for web content creation....

By the way, slightly off-topic, what's the lovely black theme you've got on your machine? It looks really good!

Cheers.

---

### Post by RadiationHazard on 2008-01-24
> **kevinatkins said:**
> Hi,

... and to create your web pages, I'd thoroughly recommend 'kompozer', which is a nice, simple, GUI-based program for web content creation....

By the way, slightly off-topic, what's the lovely black theme you've got on your machine? It looks really good!

Cheers.

[This]("http://www.gnome-look.org/content/show.php/Blue-Junior0.9-9?content=72003") is the Theme

[This]("http://compiz-themes.org/content/show.php/radial?content=71352") is my Emerald Theme


and thanks! :)

i'm glad that you like it.

---

### Post by RadiationHazard on 2008-01-24
Ok.
thanks! 
I found the folder!!
now how do i give it a url so that people not on my computer can visit the site?
and how do i make it so that my friend can help me with editing it but have access to the rest of my computer. i don't trust him that much :lolflag:


**_Found another problem so i'm just posting it in the same post:_**

ok so i found the folder and i tried to make a new document. it wouldn't let me so then i tried making a document on my desktop and dragging it into there and it said i don't have permission?? what's up with that? haha =/

---

### Post by OffAxis on 2008-01-24
> i'd already went by the instructions of that other site? so what do i do?
don't worry about it. You've just got more options running than the bare minimum. PHP is nice for scripting work, and mysql doesn't take up a whole lot of memory (just a few megabytes).

There are a bunch of steps in there (like reassigning your mysql bind-address) that are unnecessary at this point in your setup.

Maybe I missed it in the how-to, but they never actually accessed the phpmyadmin control page.
If all went well, you'll have a folder on your root page that says 'phpmyadmin'. Click on that and it should open a webpage that'll ask for a name and password for database access. If the link isn't there you'll have to create it yourself (which is a little more involved).
You'll want to check the 'users' options, because mysql creates 2 or 3 accounts initially. In the how-to you reset the root password, but there's a 'Guest' account or two that have no passwords. Before opening your site up for general use you'll want to do away with those accounts or assign a password to them.

---

### Post by RadiationHazard on 2008-01-24
Ok, I'm sorry i'm a huge n00b!
umm, below is my var/www folder? and i don't think what you're telling me about is there...

---

### Post by OffAxis on 2008-01-24
> now how do i give it a url so that people not on my computer can visit the site?
They can if you forward port 80 on your router to your machine's local ip (probably a 192.168.x.x number)
```
ifconfig
```

will list it.

After you set up the forwarding, then anyone can put in your router's WAN ip and it'll go to your website.

You can check the ip on your router or go here
[http://www.whatismyip.com]("http://www.whatismyip.com")
and it'll tell you.

---

### Post by RadiationHazard on 2008-01-24
this is what came up....

```
[CODE]jordan@jordan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:A9:80:D7:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:31:A2:43  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe31:a243/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:729418 errors:10 dropped:66432 overruns:0 frame:0
          TX packets:840794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:476694229 (454.6 MB)  TX bytes:740786334 (706.4 MB)
          Interrupt:18 Base address:0xc000 Memory:da000000-da000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:202893 (198.1 KB)  TX bytes:202893 (198.1 KB)

jordan@jordan-laptop:~$ 
]
``` 

so what am i supposed to do?:confused:

---

### Post by RadiationHazard on 2008-01-24
i'm feeling really stupid right about now!! :(
haha...

---

### Post by lespaul_rentals on 2008-01-24
Run the following command:
```
sudo nautilus
```

This will open a superuser Nautilus, which will allow you to drag and drop to all folders (such as /var/www).

---

### Post by OffAxis on 2008-01-24
> inet addr:192.168.1.4
that's the one, right there.

So then your router address is 192.168.1.1

name:admin
password:


those might be your default values;and if you haven't changed your default name/password now would be the time.

---

### Post by lespaul_rentals on 2008-01-24
What kind of router do you have?  Can you access the router's IP address (judging by the output it seems it would be 192.168.1.1)?  Do you know how to forward port 80 to your private IP -- 192.168.1.4?

If you can't figure it out, but you can access your router and enable remote management, I would be more than happy to forward port 80 for you.

---

### Post by RadiationHazard on 2008-01-24
Ok, so step by step what are you asking me to do? i'm so confused right now it's not even funny! :( and thanks for allll the help!! i really do appreciate it!!

---

### Post by RadiationHazard on 2008-01-24
what's remote management?

---

### Post by lespaul_rentals on 2008-01-24
It allows an administrator to go into the router and make changes.

Go into your browser, and type 192.168.1.1

Tell us what you see.

---

### Post by OffAxis on 2008-01-24
Okay; let's slow it down.

1. You need to set up port forwarding at your router.
Open firefox, enter 192.168.1.1 at the top.
A challenge box should open.
Enter your name and password. If you haven't changed anything it might be
username: admin
password: (nothing)
Otherwise, enter your name and password.

Next, Look for 'Port Forwarding'. Click on that.


You'll need to forward port 80 to 192.168.1.4

and that's it. Save and exit.

2. Accessing your Web Page from the web
Did you go to [http://www.whatismyip.com?](http://www.whatismyip.com?)
Now enter that ip into firefox.
Your 'apache 2 default' folder should show up.

How are we doing?

---

### Post by RadiationHazard on 2008-01-24
when i go to that site and put in my user name i use to login to my computer nothing comes up and when i enter my user name and password i use to login to my computer still nothing happens  :(

and yes. i did go to that ip thing. i know my ip

---

### Post by OffAxis on 2008-01-24
> when i go to that site
The 192.168.1.1 site?
it won't be your computer's name/password but the router's name/password (it is separate and wholly distinct).
What kind of router is it?

There may be a sticker on it that says the default name/password.
If necessary, the router can be reset. There's an exceedingly small button somewhere on it that'll take it back to it's default values. If you're on a DSL line you'll want to make sure you know your account name and password for logging in at your ISP before you press the button.

---

### Post by RadiationHazard on 2008-01-24
I use netgear. and my laptop has a built wireless receiver.

[here]("http://shop2.outpost.com/product/4354385?site=sr:SEARCH:MAIN_RSLT_PG") is a link to the exact wireless router that i'm using.

fry's is were i got it too.

---

### Post by lespaul_rentals on 2008-01-24
Try the following to login:

admin
admin

admin
pass

admin
password

admin
default

admin
test

admin
[no password]

---

### Post by OffAxis on 2008-01-24
it should be 
name: admin
password: password

---

### Post by RadiationHazard on 2008-01-24
Ok!!
I'm in! :)
now what do i do?

PS. I have to go to the store real fast. i should be back in less than an hour. i hope that one of you guys is still on to help me finish

---

### Post by OffAxis on 2008-01-24
awesome.
Look for 'Port Forwarding' down the left hand side. Click on that.


You'll need to forward port 80 to 192.168.1.4

and that's it. Save and exit.

By the way, you probably want to change your router login name and password from the default.

---

### Post by RadiationHazard on 2008-01-24
well my password is already changed. the password is already changed. :)
haha
and here is a screen shot of the port forwarding section thing. what am i supposed to do?:confused:

---

### Post by RadiationHazard on 2008-01-24
Sorry. I'd forgot to put the screen shot. But it's there now! =D

---

### Post by RadiationHazard on 2008-01-24
Ok, I figured it out!
Thank you for all you help!!
I'm closing this thread and opening a new one cuz this ones getting a little to long.
and plus this ones for setting up a server. which i have now thanks to you.
now i'm starting a new thread on how to actually get an url and not just my ip address.:):):):):):):):)

---

### Post by OffAxis on 2008-01-24
choose HTTP from the dropdown list box
under 'Server IP Address' put
192.168.1.4
and click the 'Add' button.

---

