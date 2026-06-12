---
title: "Setting up homserver - Any OS specific?"
date: 2012-04-23
forum: Any Other OS
---

### Post by Jezzze on 2012-04-23
As the title indicates, I am planning to set up a homeserver, which I would like to use to store files on and be able to open these from other PC's/laptops using Windows (for example: when at work, college, and so on).

I did some searching on the internet, mostly I found guides to set up your own server, like using Ubuntu Server, and configure it so you can make it accessible for other computers. 

However, I was wondering if there is any Linux-based OS that contains all these packages, so I could use an OS especially meant for homeservers, instead of setting up a server.

Not that I am too lazy to try, but it would be a lot easier though.

---

### Post by snowpine on 2012-04-23
Ubuntu Sever would be a great choice! If you are looking for something much simpler, FreeNAS is very popular: [http://www.freenas.org/](http://www.freenas.org/)

---

### Post by gordintoronto on 2012-04-23
If you want to make files available over the Internet, that goes beyond what I think of as "homeserver."

Installing the packages is about 5% of the work you need to do. Ubuntu Desktop -- with a handful of added packages -- will do what you want, and working in the GUI is generally easier than being restricted to the command line. At least you can fire up a browser and Google any error messages you get.

There are bigger questions: does your ISP allow you to run a server? Do you have a static IP address from your ISP, or will you be using a service such as dyndns or no-ip? Do you understand "port forwarding"?

---

### Post by snowpine on 2012-04-23
Have you considered simply using a "cloud storage" service such as Ubuntu One or Dropbox?

---

### Post by drdos2006 on 2012-04-23
It is not the OS you should be concerned about if you want to access your server via Internet. It should be the knowledge of how to lock the server down from unwanted access apart from yourself.

Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb

Install with :
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by lykwydchykyn on 2012-04-23
Zentyal and ClearOS are two options for very friendly server operating systems, suitable for home or business use.

Of course, it depends on your knowledge level and what you want things to look like from the client.  You can get what you're asking for just by installing openssh on just about any Linux distro you want.  

From there everything else is external: 

 - port forwarding on the router
 - registering with a dyndns service
 - Installing client software like WinSCP on the windows computers

---

### Post by Jezzze on 2012-04-24
Thanks for all the replies you posted, they are all very helpful :wink:.

I use Dropbox, but in order to use it, I would need administrator rights on the PC's I work on to use them most efficiently. I could open files by using the browser though. And on the other hand Dropbox and Ubuntu One offer 2 GB of free space, which is sometimes just not enough, and I am not willing to pay for online storage as long as there are free alternatives.

I got a static IP adress, and the server should not generate that much traffic, since it will only be used by myself. Internet connection should be able to handle it, and the ISP was never a problem.

And yes, I understand port-forwarding. Often had to do that to make game-servers work, running from homehost. 

But I think I will see if I can set up a server using Ubuntu, (and hopefully learn a bit more about servers) and see what I can get from there. The guide drdos2006 posted looks very helpful for that. Thanks again for all the replies!

EDIT:

Realised that setting up a NAS would be far easier, since you should not be able to access that from outside your home network. First I 'll try for the NAS, then see if I could really use it outside my home network.

---

### Post by Jezzze on 2012-05-03
Installed FreeNas 8.2 on my homeserver, and works like a charm! All settings and changes can be made via your browser, doesn't matter what OS you run. Server is approachable on both XP and W7 systems :). 

Thanks again everyone for the help! Maybe next time I can experiment with an Ubuntu server or something like that to take it to the next level ;).

---

