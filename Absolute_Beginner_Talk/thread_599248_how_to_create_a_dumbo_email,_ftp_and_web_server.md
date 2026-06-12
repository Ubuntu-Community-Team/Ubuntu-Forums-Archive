---
title: "how to create a dumbo email, ftp and web server"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-11-01
how to create a dumbo email, ftp and web server which can be easily done by a noob? any idea?

---

### Post by bubbalouie on 2007-11-01
Depends what you mean by dumbo... but, I recommend a VM of some kind to do the job if you want an 'easy time' VMWare have 'virtual appliances' which include lamp servers, these servers are free, you download the appliance, open it like any other VM and hey presto you have working LAMP & email. I have used these quite a bit for sandboxes before deploying onto real servers, usually with good results.

Of course this requires VMWare player, you can download it from VMWare.com then you will just need to unzip and run as root for the install. (There should be at least one or two tutorials about).

[www.ubuntuguide.org](www.ubuntuguide.org) has some good guides on setting up LAMP etc if you want to use a real computer to do the work, but for quick and dirty sand boxes, virtual appliances are great.

Good Luck :)

---

### Post by afeasfaerw23231233 on 2007-11-02
i want a web based (or something like this) interface for a user who don't have much command line knowledge

---

### Post by bubbalouie on 2007-11-02
This is the tool I use:

[http://virtualappliances.net/products/lamp.php](http://virtualappliances.net/products/lamp.php)

It has a limited set of web interface tools, but you can access the wwwroot using a windows network share.

I couple this of course with a working install of VMWare. Of course, you must first have VMWare, to avoid the console all together, something like:

[http://www.totalchoicehosting.com](http://www.totalchoicehosting.com)

Might be a good idea, the cost is very low, and suits most personal requirements (subject to your own needs of course).

---

### Post by afeasfaerw23231233 on 2007-11-03
can't that LAMP Virtual Appliance run on virtualbox?

---

### Post by afeasfaerw23231233 on 2007-11-03
when i try to install vmware player by add/remove it says i can't

---

### Post by gn2 on 2007-11-03
This gadget may interest you:

[http://en.wikipedia.org/wiki/NSLU2](http://en.wikipedia.org/wiki/NSLU2)
[http://www.nslu2-linux.org/](http://www.nslu2-linux.org/)

---

### Post by afeasfaerw23231233 on 2007-11-03
currently i am using a dlink(model di 524) wireless router - connected via wire - you advice me to buy that linksys router? i just want something 'free' (just like ubuntu) but can meet my need. are there anything like LAMP Virtual Appliance which can be installed on virtualbox?

---

### Post by gn2 on 2007-11-03
It wasn't advice to purchase and it's not a router.
But it is interesting.

It's an all-in-one mini Linux network file server that can do all the things you want and more.

It has a very low power consumption and costs significantly less to run 24/7 than a PC.

---

### Post by afeasfaerw23231233 on 2007-11-03
well, that is a network file server............... but i won't buy it

---

### Post by gn2 on 2007-11-03
> **afeasfaerw23231233 said:**
> well, that is a network file server

It's a lot more than that.

---

### Post by bubbalouie on 2007-11-04
> **afeasfaerw23231233 said:**
> when i try to install vmware player by add/remove it says i can't
Sorry about the delay, I have been away from the computer for a bit.....

Try downloading from the VMWare web site, that is how I did it, then run the installer as root from a console, it will ask a bunch of questions, but you should more or less be able to stick with all of the defaults and have it work.

As an aside, ahead of installing it run the following:

*sudo apt-get install build-essential*

---

### Post by afeasfaerw23231233 on 2007-11-05
thanks, i am downloading it.

---

### Post by hyper_ch on 2007-11-05
and once you have vmware running have a look at the perfect howtos (not the desktop ones) over at [http://www.howtoforge.com](http://www.howtoforge.com)

There's also one for Ubuntu Feisty (although I prefer Debian Etch as server) that will contain step-by-step instructions on how to setup a server in a ISP-like setup. This means in the end you'll have a complete server where you can easily add domains, manage email and so on.

---

### Post by afeasfaerw23231233 on 2007-11-05
how to install it?

---

### Post by hyper_ch on 2007-11-05
don't use the player, use the server edition.

---

### Post by afeasfaerw23231233 on 2007-11-05
but server edition need to pay?

---

### Post by hyper_ch on 2007-11-05
No, server edition is also free...

[http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/)

And for the serial, go here and register:
[http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)

--> it's free of charge

If you have problems, maybe this helps:  [http://ubuntuforums.org/showthread.php?p=3639728](http://ubuntuforums.org/showthread.php?p=3639728)

---

### Post by afeasfaerw23231233 on 2007-11-05
but how to install it? -- noob

---

### Post by bubbalouie on 2007-11-05
Open a command console (terminal), then:

```

cd /home/wongs/Desktop/vmware-server-distrib *You will need to complete the end bit, hitting tab may help*
sudo ./vmware-install.pl

```

Then follow the prompts, hopefully everything should work there after, though I have never needed to use the server version of VMWare with multiple desktops etc so here after hopefully hyper_ch can help you out :)....

---

### Post by afeasfaerw23231233 on 2007-11-06
it has bee installed but where to start? i am new to linux and don't know what to do with this black screen! i want a webmail, ftp server, web server, smb, nfs and that's all. can i get an easier admin page like webmin? the server usage would be very very little (max 3 users at the same time) i cannot find a user guide on [http://virtualappliances.net/products/lamp.php](http://virtualappliances.net/products/lamp.php)

---

### Post by hyper_ch on 2007-11-06
to be honest, I have no clue what you did...

---

### Post by dfreer on 2007-11-06
It looks like you got vmware server installed correctly, and have installed a "virtual appliance" of Ubuntu Server 7.04 with LAMP, webalizer, CIFS/Samba, and phpMyAdmin installed. (virtual appliance being a preinstalled virtual machine). This should be more than enough to get started, but if you don't know how to use it what's the point?

There probably is no user guide, because you are expected to know what you are doing with this. And to be honest if you don't know what you are doing, you should sit down, learn how to install an Server OS with it's various services, or pay the $10 a month for a hosting service. Do you even have a static IP address or a method of hosting your own web server at home?

---

### Post by bubbalouie on 2007-11-06
This is a LAMP server, a few tips, log in here are the users:

user: **root**
pwd: **root**

Change at least the password, you have a normal linux console if you need it in there.

You should be able to connect to a samba share called **wwwroot**, login for samba share is below:

user: **admin**
password: **admin** *(I think) *

Actually, to save time here:

[http://virtualappliances.net/documentation/readme/README.lamp.html](http://virtualappliances.net/documentation/readme/README.lamp.html)

It is the documentation for your server, now, this is more or less the simplest way to run a LAMP server (Shy of using a second computer and a LAMP live Disk) without having to spend much time on the console. This may seem a little daunting, but the basic tasks (setting up a web page etc) are all just a case of dumping files onto the samba share it gives you. For more complicated tasks, you can ask the people on the forums for help, or refer to the [http://ubuntuguide.org](http://ubuntuguide.org) site, given this is based on Ubuntu Server 7.04 you will find many knowledgeable people here to help (hopefully).....

Finally, you mentioned you want NFS, perhaps Samba may be a better option if you are sharing many files and want your windows buddies to come and play too, I have found the following tute to be quite good:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Just perform the tute on the machine you want to share files from.

---

### Post by hyper_ch on 2007-11-06
well, I pointed out the perfect how to where you'll end up with a complete webhosting solution and gui to control (almost) anything needed...

---

### Post by bubbalouie on 2007-11-06
> **hyper_ch said:**
> well, I pointed out the perfect how to where you'll end up with a complete webhosting solution and gui to control (almost) anything needed...
Agreed, [http://www.howtoforge.com](http://www.howtoforge.com) is VERY handy, to be honest I think the internet has become a prosthetic memory :confused:, sites like this are invaluable....

The guides can be applied to the VM without contaminating the main PC (as you would definitely know), so they should be quite useful.....

At the end of the day, I was trying to provide afeasfaerw23231233 with a way to get what he/she wants without possibly 'breaking' their presumably happily configured PC (and maybe save some time), and provide a safe way to learn about apache, PHP etc. To that end, virtual appliances make great sand boxes, for something a touch more powerful, you would need a more dedicated box and a 'real' install of apache etc....

With a dedicated box handy I think going the route of using your suggestion would yield a superior system and provide a better learning experience as you would need to build everything, if I had to teach someone how to do this, your approach would be best.... Mine was more of a quick and dirty shortcut to get a basic personal server up as quick as possible....

---

### Post by afeasfaerw23231233 on 2007-11-06
i find this guide useful 
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html) 
i am downloading 6.06 server version and trying to install it on vmware. it hangs up in virtualbox

---

### Post by hyper_ch on 2007-11-06
bubble:

Well, I was thinking that he setup such a server in vmware according to the perfect howtos... after installation first thing he needs to do is install openssh-server and then using his normal terminal to log into the vm server...

Then he can mainly just coyp'n'paste and he should be up and running soon with ISPConfig...

---

### Post by bubbalouie on 2007-11-07
> **hyper_ch said:**
> bubble:

Well, I was thinking that he setup such a server in vmware according to the perfect howtos... after installation first thing he needs to do is install openssh-server and then using his normal terminal to log into the vm server...

Then he can mainly just coyp'n'paste and he should be up and running soon with ISPConfig...
Sounds fair, it seems to me, that this would be more or less solved :) (hopefully, I am sure afeasfaerw23231233 will say so if not)

---

