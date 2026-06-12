---
title: "how get graphical interface on 7.04 server?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by jms1024 on 2007-06-28
I had some trouble installing 7.04 server on a Dell PowerEdge 1850.  It kept getting stuck (or taking a VERY long time) after the point in the software install where it said "Installed update-manager-core".

I read this post:
[http://ubuntuforums.org/showthread.php?t=472446&highlight=%26quot%3Bupdate-manager-core](http://ubuntuforums.org/showthread.php?t=472446&highlight=%26quot%3Bupdate-manager-core)

and after trying a new CD and seeing the same "hang" I tried the Ctrl-Alt-F4, which took me to an install log.  After seeing several (about 10-11) messages of:
in-target  err [http://us.archive.com](http://us.archive.com) fiesty/main Packages (and "restricted Packages, and Sources) and ...archive.com fiesty_updates/main Packages etc
it finally started scrolling up the log and defaulted thru the GRUB loader and ejected the CD.

So with Ctrl-Alt-F2 (for tty2 I think) at the prompt I typed "exit" and the system rebooted.

Now I can get into 7.04, but I don't have any GUI.  And all attempts to "initx" or "startx" etc just tell me to do things like "sudo apt-get install xinit"  which tells me that xinit doesn't exist and try x11-common.  I try that and the system says:
Media Change: please insert the disc labeled '/cdrom/' and press enter.

I do that and it when I press enter it just scrolls up asking me to do that again.

So, (phew) here's what I want to do:
1) Get to a graphical UI
2) Install an FTP server (for clients to have their own logins going to only their own drop off folders)
3) Install Webmin and create a non-admin group so others can add FTP accounts with the correct permissions for new clients.

Any and ALL help will be HIGHLY APPRECIATED.

Thanks in Advance!

---

### Post by tarek on 2007-06-28
Hi, the server version of Ubuntu doesn't come with a GUI. 
To install Ubuntu (Gnome) enter this command: sudo aptitude install ubuntu-desktop
To install Kubuntu (KDE) enter this command: sudo aptitude install kubuntu-desktop
To install Xubuntu (Xfce) enter this command: sudo aptitude install xubuntu-desktop

If you want a very light weight desktop environment try fluxbox: sudo aptitude install fluxbox

TK

---

### Post by tarek on 2007-06-28
I forgot about the FTP thing, there are several ftp servers you can choose from, this is one of them:
[http://doc.ubuntu.com/ubuntu/serverguide/C/file-servers.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/file-servers.html")

Another one I know is proftpd.

Regarding webmin, for some reason I the webmin installation from the repository didn't work so I downloaded the debian package from webmin website:
[http://www.webmin.com/download.html]("http://www.webmin.com/download.html")
Choose the debian package and the debian installer will take care of everything else.

TK

---

### Post by tarek on 2007-06-28
Sorry jms1024, too many tabs I forgot about the cdrom problem. You will need to edit the source list.

1) backup your source list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

2) edit the file with vi or any editor you like:
```
sudo vi /etc/apt/sources.list
```

3) search for cdrom and when you find it add # to the beginning of the line to make a comment.

4) save and close

5) update the repository:
```
sudo aptitude update
```

Now it shouldn't ask for the cdrom.

TK

---

### Post by jms1024 on 2007-06-28
WOW!  :D  Thanks Tarek!  Appreciate the thorough and clear answers.

I haven't used Linux for about 6-7 years (back in RH5/6 days) and I've never used Ubuntu before, but am looking forward to digging in.

I'll give this a whirl tomorrow morning!

Thanks again!  =D>

---

### Post by jms1024 on 2007-06-29
Aargh!  I can't even get "sudo aptitude install (none, x, or k)ubuntu-desktop" to work.  It says it's checking some list then it says "couldn't find any packages whose name or description matched "ubuntu-dekstop" " etc.

I get the same if I "sudo aptitude install" "proftpd" "webmin" "fluxbox".

Is my OS install working?!!!

---

### Post by steve.horsley on 2007-06-29
Is networking working? I don't think ubuntu-desktop is on the CD, so it has to call home and download those packages.

---

### Post by Chayak on 2007-06-29
I'm using a PowerEdge 2600 as one of my servers and I basically went with installing the desktop CD which I've had better luck with hardware detection and then adding whatever packages I needed from there

---

### Post by tarek on 2007-06-29
Hi, type the following and press enter:
```
w3m http://google.com
```

Does it take you to google.com? If not then your pc isn't connected to the internet.

tk

---

### Post by jms1024 on 2007-06-29
Hi all.

I finally got it working.

First - Tarek - thanks for the earlier posts.  I still had to edit my sources.list to stop it from asking for the CD, and that's worked.  Thanks!

Turns out the issue I had with the install was also keeping me from installing any packages (like the ubuntu-desktop, etc)

The problem was this server is on a vlan that is kept off the internet.  (uggh). :roll:  I figured this out when I was able to do a "wget http://..." for a document on our local lan, but not to one on the internet. ](*,)

Since I didn't know how to open a port in our firewall I temporarily just jumpered a cable from our DMZ into that server, and reinstalled the OS.

Ahhhh!  So much better. :D The install was a BREEZE after that.

Then I was able to install ubuntu-desktop, and from there I installed the Java JRE using the desktop synaptic add/remove program.  Then I went to the web and installed webmin.  I then used wemin to install proftpd (for FTP) and Samba.

And I found my notes on how to get thru the firewall temporarily while on the network, so now it's secure again and if I need to get out I can (without exposing the whole system to the world).

So now I have to learn up on how to setup this FTP and SAMBA stuff etc, but I'm on the way.  Thanks to you all for the help and suggestions!  :popcorn:

---

### Post by tarek on 2007-06-29
You're welcome, glad things are working for you.

---

### Post by malware7 on 2007-07-15
> **tarek said:**
> Hi, type the following and press enter:
```
w3m http://google.com
```

Does it take you to google.com? If not then your pc isn't connected to the internet.

tk

it's my problem now! i cannot download package
when i try download webmin:

> Resolving prdownloads.sourceforge.net….. failed: Name or service not known

when i try with command w3m,its can't load the url

what  must i do now?please help me

---

### Post by tarek on 2007-07-15
Do you have a GUI installed like Gnome or KDE? If so can you browse to any website online?

---

### Post by Nythain on 2007-07-15
even if you dont have a gui installed you can still install links2 and try browsing the web via cli... no sense in having a gui just to surf the web :)

edit: links2 and elinks are both console web browswers... elinks sports graphic support i believe, but im still a bigger fan of links2 for some reason. to install sudo apt-get install links2 or sudo apt-get install elinks should do the trick

---

### Post by malware7 on 2007-07-15
no gui...ubuntu 7.04  server edition..(LAMP server)
i want to use as webserver

---

### Post by malware7 on 2007-07-15
> **Nythain said:**
> even if you dont have a gui installed you can still install links2 and try browsing the web via cli... no sense in having a gui just to surf the web :)

how to do it? i'm still noob :(
but i think maybe the problem is connection

---

### Post by tarek on 2007-07-15
> **Nythain said:**
> even if you dont have a gui installed you can still install links2 and try browsing the web via cli... no sense in having a gui just to surf the web :)

True. I was just wondering what installation he has.

---

### Post by Nythain on 2007-07-15
> **malware7 said:**
> how to do it? i'm still noob :(
but i think maybe the problem is connection
first
```

sudo apt-get install links2      (or elinks for graphical support)

```then from teh command line
```

links2

```should be the command to load up the browser... from there its no different than any other browser really... you have a menu bar, and a display area... i think alt+g will popup the url box to go to a specific site... so you would hit alt+g and type in [www.google.com]("http://www.google.com") and see if it loads

edit, ok, its just g... not alt+g... just installed to make sure i was giving you the right help

---

### Post by tarek on 2007-07-15
Try this:
```
sudo aptitude install links2
```

Once installed enter:
```
links2 http://google.com
```

If you cannot download files from the online repository, then you're not connect to the internet. Otherwise, it's just w3m.

TK

EDIT:

Nythain was faster to post :)

---

### Post by malware7 on 2007-07-15
[QUOTE=Nythain;3024005]first
```

sudo apt-get install links2      (or elinks for graphical support)

```

its return error:
"E: Couldn't find package links2"

where are package links2?ubuntu cd already in cdrom :confused:

---

### Post by Nythain on 2007-07-15
its in the online repos... not sure if its in the cd repos or not, though i dont know why it wouldnt be, its small and cli and you would think it would be right up a server installs alley...

did you ever get your /etc/apt/sources.list set up to use the online repos instead of the cdrom

what does your /etc/apt/sources.list look like, could you paste it here... if it cant find it in the online repos you might be having an internet connection problem more than just a misconfiguration of something... so we'll see whats goin on

---

### Post by malware7 on 2007-07-15
i think this bcoz misconfiguration..maybe you can guide me how to check connection setting
let me try this 1st

---

### Post by Nythain on 2007-07-15
type ifconfig and give us the results
also, try pinging something
ping -c 1 google.com
and see if a ping can go through
and once again, still waiting on the output of your /etc/apt/sources.list file

---

### Post by malware7 on 2007-07-15
eth0     ip:192.168.1.10     bcast:192.168.1.255    mask:255.255.255.0
(manual config)

lo 
    inet addr:127.0.0.1  mask: 255.0.0.0

when i ping:
unknown host google.com

-----------------------


/etc/apt/sources.list file

#deb cdrom:[Ubuntu........

#see...
#newer....

deb [http://my.archive.ubuntu](http://my.archive.ubuntu)....
deb-src [http://my.archive](http://my.archive).....

#...
...
...
...
#....
deb [http://my](http://my)....
deb-src...

#...
..
..
..
..
#
deb [http://my](http://my)...
deb-src...


#
#
#
...
..


deb [http://security](http://security)...
deb-src [http://security](http://security)...
deb
deb
deb
deb


------------------------------------finish---

sorry i dont know how to complete paste just type

---

### Post by Nythain on 2007-07-15
ok, definately a connection to the net problem
i do notice that your ip is
192.168.1.10
that .10 seems a bit weird, usually its asigned 3 digits there, like mine is
138
so my next attempt at helping here would be this:
first back up /etc/network/interfaces
```

sudo cp /etc/network/interfaces /etc/network/interfaces.bak

```
then open up the interfaces file, not sure if you use nano or vi or what text editor you use but ill use nano as my example
```

sudo nano /etc/network/interfaces

```
find a line that should read like this
```

address 192.168.1.10

```
and change it to read
```

address 192.168.1.110

```
save the file and type
```

sudo /etc/init.d/networking restart

```
and see if you can ping google yet... if this breaks anything than all you really have to do is type
```

sudo cp /etc/network/interfaces.bak /etc/network/interfaces
sudo /etc/init.d/networking restart

```

---

### Post by malware7 on 2007-07-15
same...still cannot ping google or else
maybe i can try dchp enable?
let router to do it..but how to do it

---

### Post by Nythain on 2007-07-15
edit: give me a minute and ill try to find out how to set up interfaces file to rely on automatic ip via dhcp

---

### Post by Nythain on 2007-07-15
ok, lets try this this way

open up /etc/network/interfaces again
and change teh line
```

iface eth0 inet static

```to look like this
```

iface eth0 inet dhcp

```then
/etc/init.d/networking restart
and see if that gets you  an automatically assigned ip from yoru router

edit, not sure if you have to delete all the manually set settings that follow that line or if it ignores those since its set to dhcp

---

### Post by malware7 on 2007-07-15
finally...its work with dhcp...
tq so much Nythain for your great quick support :)

my ip with dhcp is 192.168.1.10
others is same

---

### Post by Nythain on 2007-07-15
ok, just glad we got you through that... so you can ping google now??? apt-get should work fine now for your then after you type sudo apt-get update so it can get a full list of apps

---

### Post by malware7 on 2007-07-15
yupps..i can ping & download now...
let me explore & play around 1st :)
tq again for ur superb support...

---

