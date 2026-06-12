---
title: "Building my own Linux Server :D"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by bumcheekcity on 2005-08-03
Just to put everything in perspective, I have this levels of knowledge about computers: 

- I've built about 5 x86 and AMD64 machines
- I've virtually never used the command prompt ever in my life, except the 'ipconfig' command.
- I have a friend with Windows Server 2003 installed on a PC, which acts as a rudimentary, but funtional server, and a router for his house.
- I have virtually no knowledge of Linux AT ALL, having only used the LiveCD that comes with the Linux Distribution, for about 10 minuites. I hope to get it installed on another computer soon, to get used to it. I have this idea that it's fundamentally like Windows (in that there is a GUI, Folders, Files, and programs to use) but more secure.

But anyway, I want to get myself a server, and I dont want to pay a lot of money for it (:D) - so I figured I would build it. I dont really fancy building the machine and then finding out that there are going to be hardware/driver/copmpatibility problems later though, so I thought I'd ask on what to build. 

I had figured this basic setup to be OK:
2800+ AMD64 (754pin)
Asus K8v-X Mobo
2x Viking 512MB RAM
Radeon 7000 64MB (<-- Indeed, ph33r the graphics power)

Also, of course with a CD-RW and floppy drives. Are there known driver issues with my Graphics card, and is the AMD64 series going to cause problems later, for having it run as a server, or programs not running. I also want it to act as a router, rourting the internet through the computers in my house. Im planning on putting another Network Card on it, and linking that up to a normal switch (that works on Windows Server 2003, and I'm assuming that Linux can do something similar).

Oh, and BTW, Linux DOES have a GUI, doesnt it? I mean, you dont have ot do everything via a command prompt? It's just that all the instructions I've seen people give are command-prompt style instructions, but the LiveCD gives me a standard, and fairly nice GUI to use.

---

### Post by nocturn on 2005-08-03
The question is "What do you want the server to do?"

I have an Ubuntu server at home doing fileserving, mailserver, webserver and a couple of others.  It works very well.

---

### Post by az on 2005-08-03
There is a GUI.  It is called X.  You did run the live cd, right?

Just about anybody who runs server applications (apache, postfix, ProFTP, etc) does not run X on the same box for two reasons:
1-  It is not secure.
2-  You do not need it for your server to run and it will cut down on performance.

So, you are not going to be able to set up a "server" and configure it without having to use the command line.  When you install a package, the documentation is in /usr/shrare/doc/*package*

---

### Post by nocturn on 2005-08-03
About the GUI thing, specially for server use: give the command line a shot, it has many benefits, even besides doing admin stuff remotely.

There are limits to every GUI in what you can do, the command line however is much more flexible.

Take the example of a simple task like manipulating files.
This command taks all jpeg files in a directory, resizes them and converts them to png, several steps per file in most GUI's.

```
for i in *.jpg; do convert $i  -resize 50% `basename $i .jpg`.png; done
```

or:
set the ownership of all files owned by the user with UID 1000 to his new UID:

```
find / -uid 1000 -exec chown 1002 "{}" ";"
```

What I want to demonstrate is that with the command prompt, you can dump the output of any command to the input of a new one, which makes for endless possibilities in what you can do.  The GUI limits you to the features the designer thought of.

---

### Post by Spleenie on 2005-08-03
[QUOTE=bumcheekcity]

I had figured this basic setup to be OK:
2800+ AMD64 (754pin)
Asus K8v-X Mobo
2x Viking 512MB RAM
Radeon 7000 64MB (<-- Indeed, ph33r the graphics power)

[/QUOTE]
 And you are just using this as a server? *cough*overkill*cough*

I have found that older hardware is more typically supported (as long as it isn't TOO old)

Don't ph33r the command line, it is your friend.

At any rate, [Ubuntu Guide](http://ubuntuguide.org) is absolutely tops for someone setting up for the first time. 

- Spleenie

---

### Post by nocturn on 2005-08-03
[QUOTE=Spleenie]And you are just using this as a server? *cough*overkill*cough*

I have found that older hardware is more typically supported (as long as it isn't TOO old)

Don't ph33r the command line, it is your friend.

At any rate, [Ubuntu Guide](http://ubuntuguide.org) is absolutely tops for someone setting up for the first time. 

- Spleenie[/QUOTE]

I don't know if it's overkill, it depends on what he will be using it for.  
My previous server used to be a compile server for slower clients (Gentoo), so it required beefed up hardware.

---

### Post by Knome_fan on 2005-08-03
While I agree with all the posters here praising the command line and I really think that learning it is worthwhile, I fear that some of the responses so far might seem a little scary.

So to answer your questions:
Yes, of course there's a gui for linux (in fact, there are even several)

However, I get the impression you really are looking more for not merely a gui, but gui tools to configure your server.
This is somewhat more complicated, as there are a lot of tools out there, but not many standard tools.
For example, you can use something like webmin ([http://www.webmin.com/](http://www.webmin.com/)) to admin your server.
Or you could use a distribution that unlike Ubuntu comes with a lot of graphical frontends to do server task. If that's what you are looking for personally I'd recommend giving Suse a try there.

[http://www.howtoforge.com/perfect_setup_suse_9.3](http://www.howtoforge.com/perfect_setup_suse_9.3)
This is a very easy to follow howto on how to setup up suse which also offers a lot of screenshots so that you might get a good impression of what to expect.

Have fun!  :grin:

---

### Post by aran384 on 2005-08-03
this is something that am kinda instreaded in aswell..... :D 

mainly because atm i got a router that isnt really that good at routing and one of my m8s had a linux box routing everything in his house and it seemed good from what he   told me but the problem for me is that

the router has wireless with superG @ 108mbps which we use for the laptops.....  

i can see why he is wanting a gui as well .. cos like me i dont know everything about the command line so it harder i gess for me.....and bum but yeah if u do know how to use the command line i know that it is better .....

---

### Post by bumcheekcity on 2005-08-03
[QUOTE=nocturn]The question is "What do you want the server to do?"

I have an Ubuntu server at home doing fileserving, mailserver, webserver and a couple of others.  It works very well.[/QUOTE]

To cut a long story short:
- Act as a router for my home network (probably comprising of about 5 PC's, maybe increasing to 8)
- Host maybe about 6 or 7 small websites, runnning PHP and mySQL.
- E-mail for each of the websites. 
- FTP for each of the websites.

[QUOTE=azz]There is a GUI. It is called X. You did run the live cd, right?

Just about anybody who runs server applications (apache, postfix, ProFTP, etc) does not run X on the same box for two reasons:
1- It is not secure.
2- You do not need it for your server to run and it will cut down on performance.[/quote]

I ran the LiveCD, and I just pressed ENTER at the prompt, at which point it whizzed around doing its thing and presented me with a nice Linux Screen abotu 40 seconds later. Im not joking when i say the only thing i can do is 'ipconfig' :D

[QUOTE=Spleenie]And you are just using this as a server? *cough*overkill*cough*[/QUOTE]

Overkill rules. I know someone who plays HL2 on an Fx-55 with the new 7800GTX. Overkill rules indeed.... *Drools*

[QUOTE=Knome_fan]While I agree with all the posters here praising the command line and I really think that learning it is worthwhile, I fear that some of the responses so far might seem a little scary.

So to answer your questions:
Yes, of course there's a gui for linux (in fact, there are even several)

However, I get the impression you really are looking more for not merely a gui, but gui tools to configure your server.[/quote]

Yeah. I read the instructions on installing PHP/mySQL on linux, and they seem impossibly hard to manage. On Windows Server 2003, it was just select and click. Nice for simple people such as myself. 

Thanks for all the links, I'm visiting them all.

---

### Post by aran384 on 2005-08-03
on this computer that i am on now is Ubuntu with php apache and mysql 

it was every easy to setup..... and didnt need configuring any thing.....


but i want to change few stuff u see...... which is the hard part =/

---

### Post by aran384 on 2005-08-03
what other disto can do all that suse can???? 

like Advanced disto ??? 

Red hat?
Mandrake? 

needs to be free btw....

---

### Post by nocturn on 2005-08-04
[QUOTE=bumcheekcity]To cut a long story short:
- Act as a router for my home network (probably comprising of about 5 PC's, maybe increasing to 8)
- Host maybe about 6 or 7 small websites, runnning PHP and mySQL.
- E-mail for each of the websites. 
- FTP for each of the websites.
[/quote]

Then Ubuntu can help you out :-) (and something like IpCop won't do).
I suggest using synaptic (if you use a GUI) to install apache2, the PHP modules and MySQL.  It worked out of the box for me.
For MySQL, don't forget to change the password to something secure.  I also recommend phpmyadmin to manage MySQL.


> 
Yeah. I read the instructions on installing PHP/mySQL on linux, and they seem impossibly hard to manage. On Windows Server 2003, it was just select and click. Nice for simple people such as myself. 


I don't know what you read (maybe the guides that compile from source?), but I had PHP/MySQL set up in minutes.  One note though, you will always need to do some configuring to make sure your setup is secure, that is where so many Windows programs go wrong.  They install with setup.exe -> Next -> next -> finish but do silly things like use default passwords.

Good luck, if you have any specific questions, please ask!

---

### Post by nocturn on 2005-08-04
[QUOTE=aran384]what other disto can do all that suse can???? 

like Advanced disto ??? 

Red hat?
Mandrake? 

needs to be free btw....[/QUOTE]

Most of them.
Fedora Core is not too bad, but Debian and even Ubuntu do not lack any of SuSE's features either.

---

### Post by bumcheekcity on 2005-08-04
[QUOTE=nocturn]Then Ubuntu can help you out :-) (and something like IpCop won't do).
I suggest using synaptic (if you use a GUI) to install apache2, the PHP modules and MySQL.  It worked out of the box for me.
For MySQL, don't forget to change the password to something secure.  I also recommend phpmyadmin to manage MySQL.[/QUOTE]

YOu mean there's a way for me to avoid having to do command-prompting (<--verb?) at all? And importantly, I did a brief search for synaptic, and found some ISO's, as well as some other installation instructions. Is it a program that runs INSTEAD OF the Ubuntu GUI, or runs with it, like Mozilla runs with/inside the WindowsXP GUI?

I have had many people recommend the programs that install Apache/PHP/mySQL in one easy program. Are they generally all good?

---

### Post by Knome_fan on 2005-08-04
Synaptic is simply the standard way of installing software on Ubuntu. Software installation on linux works differently from what you are probably used to with windows, that is, you don't download some installer and then execute it, but you have a repository or several repositories with the programs you can install and a tool called a package manager to install them. Synaptic is the graphical package manager for Ubuntu.

If you have Ubuntu currently installed, just click on System -> System Administration -> Synaptic Package Management (or something like this, I'm not on an english system right now, sorry).

Then you can simply choose the software you want to install, click apply and that's about it.

Ubuntu will then install and setup apache, etc. for you. The problem is that at least to my knowledge there is no nice and easy graphical program for Ubuntu to configure apache to your wishes (though it should basically run after you installed it).

That's why I recomended Suse, as Suse does have such a tool, as far as I know.

---

### Post by nocturn on 2005-08-04
[QUOTE=bumcheekcity]YOu mean there's a way for me to avoid having to do command-prompting (<--verb?) at all? And importantly, I did a brief search for synaptic, and found some ISO's, as well as some other installation instructions. Is it a program that runs INSTEAD OF the Ubuntu GUI, or runs with it, like Mozilla runs with/inside the WindowsXP GUI?

I have had many people recommend the programs that install Apache/PHP/mySQL in one easy program. Are they generally all good?[/QUOTE]

Synaptic is a frontend to apt-get.  Basicly it is a graphical program (running in the Desktop, not instead of it) that allows you to install and uninstall programs on Debian like systems (Ubuntu).  
More about synaptic is here [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)
No command-promt required for this.

A lot of the configuration of your Ubuntu system can be done in GUI's.  For the server part there are options like webmin that provide a web-based GUI to configure and manage stuff.

But be carefull setting up servers with limited computer knowledge,  you can accidentally open your system to anyone who can connect to it (the same goes for doing that on Windows).

---

### Post by Maxplayer14 on 2005-08-04
Let me tell you what I did at first and still do.  I run a personal game server, web pages, ftp, and a few other things on my box.

My box is at my office on a fast line.  There I use Gnome (the pre-installed GUI) to do several things.  You can install php, apache, perl all the straight from Synaptic if you want to.  Point and click away.  I don't use that as much anymore.  I use "apt-get install" to download and install what I need.

When I go home I usually shut the GUI down, although I have found my gnome and xorg (GUI process's) sitting at login only use about 1.8 percent CPU and 9 percent CPU.

Somebody mentioned Webmin on this thread.  I love it, but I can't get any release to work right on Ubuntu.  It works until I reboot then it won't work again.   If someone could enlighten me I am all ears.   Webmin is good.  You can do everything from there.   Its a web page that you can access from anywhere if configured properly.  You can install apps, upgrade, stop start services, just about anything you want.

Anyway from one Ubuntu noob to another I hope this helps.

---

