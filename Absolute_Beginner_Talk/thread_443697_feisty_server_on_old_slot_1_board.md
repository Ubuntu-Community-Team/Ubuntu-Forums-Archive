---
title: "feisty server on old slot 1 board"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by tonytux on 2007-05-14
:popcorn: I'm fairly new to Ubuntu and haven't had much trouble with it, seems to be running well, so i decided to boot up an old slot 1 board with it and an old P2 that I was able to overclock with the bios to 333, has 3 pc-100 slots for ram and scrounged up 3 64 MB ram sticks for it,  I have a total of about 1 gig of memory between the two HD s I dug out of the closet (one's a 720 MB installed as the "\"  and the other is 420 MB installed as the "usr") I installed the feisty server edition as LAMP, to save on space, which I understood was a command-line-only release to basically touch up on my command line abilities, not too sure what I really want to do with this machine, and slightly confused about a few things on facing a command line.  I have "sudo vi"ed the repos to be able to get the universe repos and tried to install fluxbox for some GUI abilities, which I can't seem to get running at all.  I wanted to use this as a small web site for family to check out pics , but as I'm behind a router and my ISP said I can't use a static IP, without going to the next step in our internet plan (wich is an ungoddly amount to just load up an FTP like server for a few pics).  I guess my few questions would be:

1.how to get fluxbox up and running the hard way without actually reinstalling as xubuntu

2.how to unconfigure the DHCP client within the "server" so that I can forward my ports through my router using            a static IP (hopefully being able to "keep" my current IP as long as possiable by staying up and running as long as possible, IP seems to stay constant as long as I'm constantly on line)

3.how to set up a simple FTP or web server to beable to allow family to see pics.

I know there are possibly hundreds of FTP how to's but I was hoping for at least a link to an easy to understand guide that is geared towards ubuntu or just command line opperations, so I can get the practice in.  (Ubuntu server guide is all based on GUI and this seems to be a slight problem considering my HD constraints.)

i figured it would be a fun project

Thanx in advance of anyone willing to respond....

---

### Post by poohbear1616 on 2007-05-14
Here is one link.
[http://www.howtoforge.com/perfect_setup_ubuntu704]("http://www.howtoforge.com/perfect_setup_ubuntu704")
The first couple pages go through the install then gets to the nitty gritty...:) 
Might get you going.

---

### Post by tonytux on 2007-05-15
thanx much, sounds just like what I'm looking for, i appreciate the help...:guitar:

---

### Post by mlentink on 2007-05-15
You might also want to take a look at Webmin, which is what I use to adminster a DD server

---

### Post by lazyart on 2007-05-15
As far as your ip address, set up an account at dyndns.org, install a client on your server that will update when your ip address changes and in the end you'll be able to refer to your machine as a name instead of a number.  This is how I run a mail server on a $50/month cable line.

---

### Post by tonytux on 2007-05-15
now I'm probably gonna want to put this lil server in front of my router, correct? gonna need to reconf al the info if I do, router ip and real ip are different, since I am doing that nice little howto for feisty server you pointed out, 

And what client would I need to install to keep my ip up-to-date with the DNS? Is it some sort of DNS client itself and in doing so I'm gonna have to get a larger HD,  (to store this DNS's info?)  which I plan on doing anyways, just figured this would be a nice little starter test.

thank you all for your excellent points, I will be using them for my project 8-)

---

### Post by lazyart on 2007-05-16
Your server can sit behind the router.  The client will know what to do about all that.

Search the repositories for dyndns, or go to dyndns.org as there are clients there though you might have to make them if you do.  All this client does is check to see if your ip address has changed, and if so contacts dynds.org and tells them.  It's real tiny.

---

### Post by tonytux on 2007-05-16
I really hope it's tiny cause I'm down to 30MB on my usr "drive" trying to fallow the feisty perfect server setup linked to earlier.  if I do find the dyndns thing and have to compile from tarball is there a way to get it onto the lil server, don't think it'll let me surf the web :) I'm just learning this stuff and using ssh is a little tricky for me, not sure how to ssh something over the network and get alot of "...port 22 conection refused" when I try to do anything with it, I'm sure it's probably easier than I'm making it for myself.
anyone know how much of that guide I can actually skip to just get away with an ftp or simple webserver set up, I don't really want all that mail stuff right now, plus I keep getting stuck on the SMPT-AUTH and TLS part of it, just giving me a hard time or something, mght have something to do with the way I entered in some of the config stuff. 
anyways, thanx for the dyndns.org thing, as soon as I feel I can get this little beast to actually do what I want i'll be putting it on there and using it

edit:found that little dyndns packet in synaptic, and you're right it sounds simple and looks pretty small 303K, now I just have to find all the spots where I put a domain name in and change them to whatever it ends up being

---

### Post by az on 2007-05-16
You will have an easier time putting everything on the 720MB drive and using the other drive for swap space rather than trying to fit /usr on it.  

See here for running a basement web server:

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by blazercist on 2007-05-16
hate to be captain obvious here but why would he need such a heavy duty distro as feisty to run a webserver?  for that old hardware i would suggest using Damn Small Linux, it comes with a gui and all u gotta do is install apache....  plus it only takes 50MB of harddrive space and uses far less ram.

---

### Post by louieb on 2007-05-16
Just a thought but I recently went down to a local mom and pop computer store and picked up an old 8 gig IDE hard drive. They had plenty of small old drives they were selling for a dollar a gig or less.  And while your there look to see if they have any old slot 1  cpus around. I've see them at the swap meets for 5 bucks or less.  If you can fine one 350 mhz or higher then you can raise the buss speed from 66 to 100 mhz. That can make a big difference in the performance of those old machines.

---

### Post by tonytux on 2007-05-16
blazercist, you have a very valid point, I did look at using DSL at first, but have been using ubuntu on all my machines, I enjoy it, am familiar with it (more than any other distro), and kinda wanna challenge myself with the command interface, plus I'm not sure if DSL is a debian, where I can just apt-get whatever packets I need. And to make my project easier I'm getting a bigger HD, like 20G, just for that reason, granted I'll want to start over or rescue-CD and cp all of it over, but I need the practice and want to feel better about myself for atleast trying it the hard-way.  I hear so much about the CLI that I want to join in the fun. Hard-headed as it seems, but I'm kinda sick of all the extra pizzaz the GUIs give me and want to know what actually makes this thing tick, getting dirty with the config files and all that...


louieb, that's exactly what I'll be doing this friday, and it's the only ma&pa computer store in my area that still has any old ide's, not sure how the CPU will fair, I think I can only get up to 333 on my board, but I will give it a shot if i run across one

---

### Post by blazercist on 2007-05-16
tonytux [http://damnsmalllinux.org/](http://damnsmalllinux.org/) claims that the hard drive install Transforms DSL into a Debian OS, furthermore, are you aware that you can modify the init scripts and have the system start in any runlevel you desire thus making it headless and sparing you the GUI luxuries?  Not trying to sway you one way or the other- I use Feisty on my laptop as a webserver and file server as well as for normal desktop use but its a powerful sucker with 2.2ghz turion 64 2 gigs of DDR2 ram and 100Gigs of HD space.

---

### Post by tonytux on 2007-05-18
finally got it all taken care of, up and running and all that, thank you all very much for the help and pointers, I eventually had to use the debian netin .iso to get just the bare minimums, mounted my lil 420 MB as my /var, to hold all content, never did get to get the HD I said I would, then skipped through alot of that feisty server how to to help me get configured all up and running, did the dyndns, which is a very good spot.  the little box actually is a little faster then I was expecting, but that's with just me lookin at the web site and tinkering around trying to get this HTML thing down pact, and Java and all that fun stuff.  Took me a while to realize where my www data was all stored, but found it and am now going through [COLOR="Blue"][http://www.htmlgoodies.com](http://www.htmlgoodies.com)[/COLOR] to get the scripting down. so nothing spectacular is on there yet, but I'm getting there and would have never done it with out all of your help.....thanx alot,

I plan on retireing my current machine into a server, when I can upgrade, 433P2 192MB , and that will be much more fun..........:D

[COLOR="Blue"][http://patches.boldlygoingnowhere.org](http://patches.boldlygoingnowhere.org)[/COLOR] check it out if you want, like I said it's nothing to brag about yet...

---

