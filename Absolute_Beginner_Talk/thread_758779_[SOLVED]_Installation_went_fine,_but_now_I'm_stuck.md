---
title: "[SOLVED] Installation went fine, but now I'm stuck at the command prompt"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by cindylivengood on 2008-04-18
I completely understand what the author was saying.  I am on day 2.  So, I am not sure you can get much greener than that.  Yesterday I downloaded Ubuntu, prepared an old Dell computer for it, and today, I installed Ubunutu Server on that machine.

As for the installation process, it was great, smooth and easy.  Not as mindless as Windows, but that's a good thing.

Then about an hour ago, I finished the installation and restarted the machine.  Up came the command prompt, and guess what?  I have no idea what to type at the command prompt.  I haven't the slightest idea how to get to the desktop.  

Now What?

---

### Post by aysiu on 2008-04-18
Ubuntu Server doesn't come with a graphical interface.

Did you mean to install a server? If so, keep it at the command prompt and learn how to use it.

If you really meant to install a home desktop, then follow this guide:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by Sukarn on 2008-04-18
> **cindylivengood said:**
> I completely understand what the author was saying.  I am on day 2.  So, I am not sure you can get much greener than that.  Yesterday I downloaded Ubuntu, prepared an old Dell computer for it, and today, I installed Ubunutu Server on that machine.

As for the installation process, it was great, smooth and easy.  Not as mindless as Windows, but that's a good thing.

Then about an hour ago, I finished the installation and restarted the machine.  Up came the command prompt, and guess what?  I have no idea what to type at the command prompt.  I haven't the slightest idea how to get to the desktop.  

Now What?

You installed Ubuntu Server and expect Ubuntu desktop to be available?

Get the ubuntu desktop cd from [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu) or type this in the command prompt in ubuntu server (this will only work if your internet connection is working) -
```

sudo aptitude update
sudo aptitude install ubuntu-desktop

```

---

### Post by cward002 on 2008-04-18
Ubuntu Server does not come with a GUI  preinstalled. if you want a graphical desktop, either re-install using a desktop CD, or simply type
sudo aptitude install ubuntu-desktop(for GNOME) or sudo  aptitude install kubuntu-desktop (for KDE). ubuntu will ask for your password which is the one that you gave to your user during the installation process. Ubuntu will then download and and install all the necessary files for a graphiical desktop. Then simply restart X and Voila!!!

---

### Post by cindylivengood on 2008-04-18
I intended to install the server, but I wanted to install the desktop as well.  I didn't find a version where I could choose to do both.  I'm not sure why one can't offer the Edubuntu with a server edition and a wiki.  I asked about such a thing in the Edubuntu list, but not one response was given to my introductory post.

I went ahead because it never occurred to me that a version would be put out there, encouraging people to switch, without any form of desktop at all.  Now I need to figure out how to install a desktop, web browser, and the wiki program.

It would be nice if no one made fun of me for wanting to learn something new and wanting to expose my co-workers to something I know to be superior to what we have.  Switching from windows systems to LAMP means people have to start from nothing.  

I know it will never happen unless someone is the canary.  Tag, I'm it.  The learning curve is high, but I'm smart enough to learn.  My mission is to start with building a faculty wiki and later a student wiki.  I need to have the first built by August 1.  I have no one to ask.  No one to support me.  I have to learn it all on my own, getting advice from anyone kind enough to give it to me.  I'll buy books and read web pages.

Thank you for taking time to read, and hopefully help.

---

### Post by aysiu on 2008-04-18
No one has made fun of you.

Servers in Linux are generally run from the command-line.

As others have said (and as I've explained in the link I posted earlier), you just need to add the Desktop version on top of the Server, and you'll then have both.

---

### Post by qamelian on 2008-04-18
And for assistance with the stuff you want to do, here is a good stating point:
[https://help.ubuntu.com/7.10/server/C/](https://help.ubuntu.com/7.10/server/C/)

---

### Post by cindylivengood on 2008-04-18
Thank you.  I am installing it now.  Is there a command list I can download and print?  Just reading those will go a long way towards educating me.

> **Sukarn said:**
> 

Get the ubuntu desktop cd from [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu) or type this in the command prompt in ubuntu server (this will only work if your internet connection is working) -
```

sudo aptitude update
sudo aptitude install ubuntu-desktop

```

---

### Post by aysiu on 2008-04-18
> **cindylivengood said:**
> Thank you.  I am installing it now.  Is there a command list I can download and print?  Just reading those will go a long way towards educating me.
This isn't a bad place to start:
[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by cindylivengood on 2008-04-18
Is it supposed to take 2 hours to download and install this?  My computer is still doing the deed and it says it will be another 1.5 hours.  Am I going awry on my first day?

---

### Post by aysiu on 2008-04-18
> **cindylivengood said:**
> Is it supposed to take 2 hours to download and install this?  My computer is still doing the deed and it says it will be another 1.5 hours.  Am I going awry on my first day?
How fast is your internet connection?

---

### Post by cindylivengood on 2008-04-18
Its through my school district, and sometimes the bandwidth gets pretty tight since the staff and students are logged on and using the internet.

It went through a series of connections refused by ubuntu and then started installing the program.

This is exciting to me.  I feel like a kid with a really expensive new toy.  I've been reading the sites you guys sent me.  Thanks!

---

### Post by MONODA on 2008-04-18
yes it will take a while since the files downloading are large. Anyway, wlecome to ubuntu! I suggest you check this out: [http://hey4.com/ubuntu_cheat_sheet](http://hey4.com/ubuntu_cheat_sheet) it has helped many new users. Also, read the site that aysiu provided, linuxcommand.org, it is a great place to start.

---

### Post by cindylivengood on 2008-04-18
It seems as if I am going to be stopped, if only temporarily.  The download time is a whopping 8 days 4 hours and some minutes.  The first attempt to install the desktop failed.  When I gave the command, it prompted for the installation cd.  What is on the cd that might be required if I installed it fully on the hard drive?  Is there a way around this?

What causes the connections to be refused by ubuntu?

As a side note, I already like using the command line better.  Feels like the old days when things happened faster at the tip of your fingers and you knew what was going on.  I'll get there, with a little help from my new best friends!

---

### Post by cindylivengood on 2008-04-18
I might have to wait until everyone goes home to get enough bandwidth to download this stuff.  grrr.

While waiting for that, a bean is a post, correct?  But, how does one thank someone to show up in their counter?

Thanks for all your help.  People are already coming to see what I am doing.  Some are getting excited about it.

---

### Post by aysiu on 2008-04-18
It's prompting for the installation CD probably because you have it in the list of available software repository sources.

Edit the list ```
sudo nano -B /etc/apt/sources.list
``` and comment out (put a *#* sign in front of) the line that has the word *CD-ROM* in it. Then save (Control-X, Y, Enter) and ```
sudo apt-get update
```

---

### Post by sanus|art on 2008-04-18
You might want to look into window manager - it is 90% lighter than all * - desktops. Here's one:
[http://fluxbox.org/](http://fluxbox.org/)

To install use:

```
sudo apt-get install fluxbox
```

---

### Post by tnl2k7 on 2008-04-18
Just so you know dude,

When you use Ubuntu, you're never on your own learning, the forum community is very friendly (unless we're hungry :lolflag:) and will always be around to help you.

Come by and ask questions like everyone does at some point, and one day you might just end up as the expert helping others.

Good luck!

---

### Post by cindylivengood on 2008-04-18
Thank you!
The update and desktop is 85% downloaded.  I can't wait.  I saw samba was included in that download.  I was planning on tackling that next... after I get this other project up and running well.

Now, does that mean if I type:

sudo apt-get install **compatible program name**

This will get and download the program without me searching, clicking and doing all the stuff required to use windows?

oops... I want to get wiki.

---

### Post by aysiu on 2008-04-18
> **cindylivengood said:**
> 
Now, does that mean if I type:

sudo apt-get install **compatible program name**

This will get and download the program without me searching, clicking and doing all the stuff required to use windows? Yes. That's one of the great things about Ubuntu (and Debian-based distros).

Read more here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Michael R on 2008-04-18
> **Sukarn said:**
> You installed Ubuntu Server and expect Ubuntu desktop to be available?

Get the ubuntu desktop cd from [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu) or type this in the command prompt in ubuntu server (this will only work if your internet connection is working) -
```

sudo aptitude update
sudo aptitude install ubuntu-desktop

```

when I tried this it said no packages matched. I have ubuntu Server 6 installed and would like a graphic interface to make things easier for myself as well as the other new admins none of us know linux. but I want to setup a linux server to replace the microsoft server 2003

thanks

---

### Post by cindylivengood on 2008-04-18
ok.  I have installed the desktop and it seems to be working great.  The screen resolution needed changed and I did that ok.  But, now I can't figure out how to get the command line again with the desktop open.  I can get the command line with the desktop open, right?

---

### Post by cindylivengood on 2008-04-18
Hi Michael R.,

You are not alone!  I just started my first server today and have to learn everything from the bottom up.

I installed Ubuntu Server 7.10.  Perhaps you would consider going back and installing that instead?  That is the only posted difference between us, and it worked great for me.

This will be fun learning together.

---

### Post by aysiu on 2008-04-18
> **cindylivengood said:**
> ok.  I have installed the desktop and it seems to be working great.  The screen resolution needed changed and I did that ok.  But, now I can't figure out how to get the command line again with the desktop open.  I can get the command line with the desktop open, right?
[This](http://www.psychocats.net/ubuntu/terminal) will help.

---

### Post by cindylivengood on 2008-04-18
Thank you so much.  I looked at that thing for quite some time.  I managed to miss that one line in the navigation bar.  I'm so excited!!  When I restarted my computer after installing the desktop it said there were 29 updates ready to install.  That was nice.

This went so well, thanks to you guys, that I am going to go home and get out one of my old computers and set it up as well so I can practice at home and work until it becomes as much second nature as DOS 5.1 was.

Now to get that wiki program...

---

### Post by aysiu on 2008-04-18
Glad it all worked out.

If you have further questions, start a new thread, and we'll try our best to help you.

---

### Post by Sukarn on 2008-04-19
> **aysiu said:**
> [This](http://www.psychocats.net/ubuntu/terminal) will help.

Do you think (the case here being an intended server) that the guy should be told about virtual terminals tty1-6?

NOTE TO OP: Ignore this post if it does not get a reply. The terminal available from the menu should be sufficient for most purposes.

---

### Post by Sukarn on 2008-04-19
> **Michael R said:**
> when I tried this it said no packages matched. I have ubuntu Server 6 installed and would like a graphic interface to make things easier for myself as well as the other new admins none of us know linux. but I want to setup a linux server to replace the microsoft server 2003

thanks

Are you sure that your internet is working with ubuntu?

Did you run the command *sudo aptitude update* before running the command *sudo aptitude install ubuntu-desktop* ?

When you run the command [i[sudo aptitude update[/i] could you post a few lines of what the output is?

I mean, is it something like
```

Get:2 http://ppa.launchpad.net hardy Release [27.6kB]
Get:3 http://ppa.launchpad.net hardy Release [27.6kB]

```
This is just a little example of what it should look like, not exactly what it will be for you. Your output will most probably be different.

Finally, if your output looks similar to what I posted above (but still somewhat different (like something else in place of "ppa.launchpad.net" and something else in place of "hardy")) and you still cannot install ubuntu-desktop, then could you post the contents of the file */etc/apt/sources.list* ? (type this in the terminal to get the contents of the file) -
```

cat /etc/apt/sources.list

```

---

### Post by cindylivengood on 2008-04-19
I got it all working fine.  The internet problem is because our district does not have enough bandwidth.  They need to set up more servers as well.

Now I am working on the wiki, but I am not at school now, so I have to wait.

Thank you for all this help. You guys are the greatest.

---

### Post by cindylivengood on 2008-04-19
Oh, I should note, but not sure who to tell, but in IE 7, it doesn't appear the little thanks icon appears.  I noticed it in firefox when I used it from the Ubuntu server we all just set up.

---

### Post by cindylivengood on 2008-04-19
Ok, correct me.  I meant in the IE on the vista machine.  It shows up on my IE 7 on my XP computers.

---

### Post by Sukarn on 2008-04-19
> **cindylivengood said:**
> Ok, correct me.  I meant in the IE on the vista machine.  It shows up on my IE 7 on my XP computers.

I don't think too many people here would care about that, as we're mainly here to help people, not to gather thanks.

---

### Post by Michael R on 2008-04-19
i was getting the feeling my internet wasn't working last night after i posted. I thought it should be because the install was supposed to be over the net. 

sources.list 
"deb cdrom:[ubuntu-server 6.06.2 _Dapper Drake_ - Release amd64 (20080110.1)]/ dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restriced
deb-src [http://usarchive/ubuntu.com/ubuntu/](http://usarchive/ubuntu.com/ubuntu/) dapper main restricted"

then a couple lines about updates from the same address but 'dapper-updates' instead of dapper

as for the network I have a static IP address set on this computer (that I have used under the puppy version of linux that was just booted off a CD) 
/etc/network   interfaces    reads:
#the loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.77.145
    netmask 255.255.255.0
    gateway 192.168.77.50
    dns-nameservers 192.168.77.50

I feel so lost in linux console right now
thanks for the help

edit : I can talk to my network now and am loading ubuntu-desktop packages all is well for now.

---

