---
title: "Guide to installing a LAMPP Server with GUI"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by velkymx on 2007-05-19
As a Windows user I am often perplexed by how far Linux has come and yet how far it has to go to catch up to Windows. In some ways Linux outshines Windows, and in my opinion the best way is in the server segment. My biggest complaint with Linux is that you have to be a code junky to know just how to use the system. Often you would have to type esoteric phrases into a Dos like terminal just to get things working. I am a Windows user after all and I need my GUI (General User Interface)!

So with the latest release Ubuntu Linux I set about moving my PHP web sites from my Windows 2003 Server to a LAMPP (Linux Apache MySQL PHP Python) server. I tell you I have succeeded in both the improved performance of Linux while retaining my drug like addiction to easy to use GUIs. With a little research I was able to compile this guide with excellent results.

Full Guide: [http://www.synergymx.com/page.php?Title=Guide_to_installing_a_LAMPP_Server_with_GUI/](http://www.synergymx.com/page.php?Title=Guide_to_installing_a_LAMPP_Server_with_GUI/)

---

### Post by eentonig on 2007-05-19
Or,

you could have installed the server CD, which has a lamp server option doring installation.

And then after the initial setup and if you really want that GUI. Just type

> sudo apt-get install ubuntu-desktop

As a side note, I don't like you explaining how to enable root. As it really isn't necessary. You can do al administrative tasks via the sudo command.

---

### Post by hyper_ch on 2007-05-19
Well, a server running a GUI is wasting ressources...
You see, Linux has no registry like windows... in linux all configuration is stored in files... and what's the quickest way to alter configuration? Exactely, alter the config files... hence it's a lot of text based in the server area... there's really no need for a gui...

Anyway, if you want a desktop and webserver in one box, install teh desktop first and then follow this here:  [http://www.howtoforge.com/perfect_setup_ubuntu704_p3](http://www.howtoforge.com/perfect_setup_ubuntu704_p3)

---

### Post by velkymx on 2007-05-19
The whole point of the guide is to make it easy to administer - the Server version of Ubuntu is for Advanced users. I was making it for more Windows type users.

---

### Post by funkythumb on 2007-07-03
Well, though it may be true that a Linux server with a GUI isn't the most efficient way to go, I'd still take an imperfect Linux system over a Windows server any day! Especially with the huge bloated mess that Win2K3 has turned out to be.

Also, I wanted to and encourage anyone who makes an attempt to provide a bridge for Windows admins to use Linux servers. I've been a Windows tech for many years, and have had to limit my jumping into Linux to a part-time endeavor. Mostly because I'm married, have two kids, have a full time job (IT Project Coordinator), go to school full time in the evenings, and the rest of what goes on in a "normal" life. A year ago, I didn't have the time to break down my networks and spend the days/weeks needed to figure everything out from scratch at the  command line.

After a year of tinkering, getting old hardware that I've imaged over and over again, I've finally switched my own and my wife's home systems to Ubuntu. I've also finally become comfortable enough with the CLI to set up my 1.3TB video editing station (Feisty) and 400GB raid5 server (Dapper) replacing my Win2K server box.

The most recent distros make LAMP server installs super painless. I just wish a SAMBA version or wizard would be made up as well. Coming from a Windows world, file sharing is still a bit mystic to me.

---

### Post by hyper_ch on 2007-07-04
for samba you can use SWAT

---

