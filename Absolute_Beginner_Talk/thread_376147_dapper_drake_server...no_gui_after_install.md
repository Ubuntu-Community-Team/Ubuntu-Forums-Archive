---
title: "dapper drake server...no gui after install"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by no-name on 2007-03-04
im pretty new to linux, but im just trying to turn a old amd duron 1.8ghz machine into a home web server. isnt here supposed to be a gui? or is this all command line stuff? i have been sarching pages to no end and i think i read that there is supposed to be one so i wonder what im doing wrong here help!! ive been trying to do this for a week now!tahnks in advace and sorry if this is posted in the wrong area

---

### Post by annda on 2007-03-04
it's the right place to post.

server is just that - a server. if you need gui, install with those commands

sudo apt-get update
sudo apt-get install ubuntu-desktop

---

### Post by no-name on 2007-03-04
ok, and once i do that will it load its self? and will the gui let me do everything basic till i lern more commands??

---

### Post by hellraiser_rob on 2007-03-04
yes it will give a nice gnome user interface, from which you can access the internet etc to learn more.

---

### Post by maddog39 on 2007-03-04
You should have originally downloaded the desktop version. The server version is an extremely stripped down version of desktop ubuntu that was ment for servers, and servers dont have GUIs. However, ubuntu desktop is designed to be easy to use and for the new linux user.

---

### Post by no-name on 2007-03-04
i didnt think you could just use the desktop one for a server so i got the iso for server.  i do have both install discs though and the kubuntu one too. can these all be set up to be server systems?
i typed in those commands so right now its running a bunch of stuff and says 38% so i geuss i did this right. how do i launch the gui after its intalled?thanks

---

### Post by annda on 2007-03-04
you should see a graphical login screen after reboot. if not, type gdm or startx after you log in in the console.if it complains that gdm is not installed, install that too and gdm again.

---

### Post by no-name on 2007-03-04
is it hard to host pages with this os? my goal is to serve up my own web page and host a few others from at home. is this realistic with ubuntu.next i will have to learn how to make my own web page and how to host it on the pc for others to find. im a tattoo artist and need a way to have my own site. im D.I.Y. to the core :) i fix my own cars, my own pc, bla bla so i dont want to pay some jerk to host a page for me, so i want to learn how to

---

### Post by no-name on 2007-03-04
> **no-name said:**
> i didnt think you could just use the desktop one for a server so i got the iso for server.  i do have both install discs though and the kubuntu one too. can these all be set up to be server systems?
i typed in those commands so right now its running a bunch of stuff and says 38% so i geuss i did this right. how do i launch the gui after its intalled?thanks

well its moving slow to install at 48% now, so i could have used the desktop iso to run a server?

---

### Post by annda on 2007-03-04
there are a lot of packages to be downloaded...

if you prefer, you can install again from the desktop cd and the install ubuntu-server package (i am ALMOST sure it's called that). or search the forums for LAMP and see what you need to install except apache2 (the server).

---

### Post by no-name on 2007-03-04
it asked to install a LAMP originally, thats what i selected on the install. i tried the startx but no gui came up so i figured i did something wrong.
oh boy 62%
so ubuntu is debian based right?

---

### Post by no-name on 2007-03-04
ok it didnt work it gave me : failed to fetch something about the connection timed out

---

### Post by Darklighter137 on 2007-03-04
Servers don't have GUI's because they use up too many resources that are needed for server to do what it's meant for.  The desktop is for people who just want to use the computer.  You need to be very comfortable with the command line to keep a server up and running, so you may want to spend some time getting to know Linux in a GUI first (do a fresh desktop install).

Yes, it is Debian based.

---

### Post by no-name on 2007-03-04
so can i run a server with a gui anyways?

---

### Post by Darklighter137 on 2007-03-04
I am 99% sure the answer to that question is no, especially not without a very powerful machine.

---

### Post by annda on 2007-03-04
you can do anything you want with ubuntu.

for your personal server and setting up things and learning along i also recommend a desktop install. then you will be able to add/install all the server packages you need.

but if you really want to keep your current server install, you'll need to get those desktop/GUI packages again.

i think it may be easier to do a fresh install - you already have the cd's...

---

### Post by no-name on 2007-03-04
> **annda said:**
> you can do anything you want with ubuntu.

for your personal server and setting up things and learning along i also recommend a desktop install. then you will be able to add/install all the server packages you need.

but if you really want to keep your current server install, you'll need to get those desktop/GUI packages again.

i think it may be easier to do a fresh install - you already have the cd's...

can i use kubuntu instead? i cant find the ubuntu cd and i prefer kde anyways. its all about learning, i love it

---

### Post by no-name on 2007-03-04
i have it installed on the drive now so i am wondering what to do next if i can use it

---

### Post by annda on 2007-03-04
sure you can!

just remember that most people here use gnome and talk about synaptic as their packet manager etc. in K it's adept or something. when you ask for help, just mention that you run kubuntu. and you will be fine - any commands that you need to type into the terminal are the same.

have fun!

---

### Post by no-name on 2007-03-04
in the adept manager in the gui theres a few listings for apache 2 and alot of smaller ones, i just found out how to install them, so what else do i need installed to be on my way to trying this. im going to find the ubuntu disc and put it on my other hard drive, but for now play with kubuntu till i find it. im just too lazy to hook up my windoz pc to get the iso image and this laptop im using right now has no cd burner

---

### Post by annda on 2007-03-04
it depends on what you want to do on your server. if you want just html files, i think apache2 is enough. do you need a database? php? cgi?

google around and see what you need. then search adept for that.

and post a thread here if you need more help with the server setup.

---

### Post by no-name on 2007-03-04
ok so how do i run apache once its installed its not on  the menu

---

### Post by no-name on 2007-03-04
i installed ubuntu 6.10 and im in the add/remove but dont see apache listed. what command can i type to get it the real way and what do i open the terminal?thanks google just confused me with alota stuff. figured out how to add amarok though:)

---

### Post by larrybrazos on 2007-03-06
have you been to [www.ubuntuguide.org?](www.ubuntuguide.org?)  go there, play around with setting up some different programs and familiarize yourself with ubuntu.  you got to crawl before you walk.

i would put down the configuring apache project for now and get familiar with the basics first. 

here are a few projects to get you started . . .

1. add repositories to sources.list

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

2. how to install Java & Non Meida Browser Plug-Ins:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Java_.26_Non-Media_Browser_Plug-ins(1.4.3.1.1](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Java_.26_Non-Media_Browser_Plug-ins(1.4.3.1.1))

3. how to install multimedia codecs:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

4. how to install dvd playback capability:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability)

once you do a couple of these basic types of tasks, apache configuration will start to make a lot more sense.

---

### Post by etcpool on 2007-04-09
it's surely possible to host the web on ubuntu and i think it works its job best.

but it's not that easy as click&/or drag to configure the server in ubuntu 

if you really need gui with server configuration tools i recommend redhat or fedora serie (rhel would be best)....


etc,

---

