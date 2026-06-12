---
title: "Need help setting up basic LAMP on Ubuntu Desktop (Not Server Edition)"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Jhorra on 2007-06-07
I would like to do some development on my box, and not have to upload it to test.  All I want to do is set up a basic LAMP on my desktop install so I can put my files in and test them.  This will not be available to the internet.  I've tried to find instructions, but Ubuntu had to be all efficient and enable by default in their server edition, so I can't find any instructions on how to do this.  I know they are some basic commands, and I had it set up before, but I had to reinstall, and can't find the instructions again.

---

### Post by dave-5B on 2007-06-07
just go to [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Database_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Database_Server)

and follow the instructions to install apache, mysql and php

its that simple

---

### Post by aldreis on 2007-06-07
For the needs you describe, I believe XAMPP would be your best bet. ;-)

See [HOWTO: Setup easy web development environment (XAMPP)](http://ubuntuforums.org/showthread.php?t=223410)

---

### Post by dynoweb on 2007-06-14
i have done everything these tutorials say and they do not work for nothing.... does anyone know how to get a LAMP (linux) version of EasyPHP (windows) 

I guess that is what it is called I have no idea.

I am looking for the Linux version.

---

### Post by lazyart on 2007-06-14
What you do here is download 6.06 server and do the LAMP install.  Once done, log into the terminal and type```
sudo apt-get install ubuntu-desktop
```and you've got both.

---

### Post by easytec on 2007-09-29
Why don't you use Server Edition, just write your current files to a CD or DVD and install Ubuntu Server Edition version 7.10 Gutsy Gibbon (Beta currently) and once burnt to a disc the disc can run.
During the setup you will prompted to install the servers, use the space bar to select the correct servers of which you want, then press the tab button and enter to continue.

Then re-install your previous files!

It is alot more difficult to install it on it's own and PHP5 and MySQL don't go together easily, they need to register their globals to communicate.

---

