---
title: "basic web server/home networking questions"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-06-24
hope this is the right forum, seems kinda general, so....

my setup is as follows:

bresnan cable, 2 computers, both connected through ethernet to a linksys wireless router (wireless is turned off). one computer has a dual boot xp/edgy setup with a shared fat32 partition for files, the other is just edgy all on one partition. i plan to install ubuntu 6.06 server on it instead after i back things up to the maxtor external hd. these 2 computers can both get on the internet, but can't share files or printers. my roommate sometimes uses the old computer to do research or type papers for school.

i want to install a web server (lamp) on the old computer for testing different software & learning more about how things work. another thing i want to try is a file server for music/files that i can access from the new computer or over the internet (ssh?).

questions:

what's the best way to back up / sync certain folders from both computers to the external hd?

if i install ubuntu-desktop will i get firefox & open office?

bresnan doesn't give out static ips to home users. am i right that i have to get a domain & custom dns service from dyndns.org to make [www.example.com](www.example.com) work right on my home server? if there's a better/cheaper way to go about it i'm interested to know.

is it a real bad idea to let roommate use the server as a desktop on occasion?

what's the best partition plan for a server?

is there any security measures i can take for both comps & the router to make sure i don't get hacked? hehe...

ty for any help, so far i'm really enjoying ubuntu :P only major issue i had so far was wireless but in my experience it sucks in windows too so i don't hold it against ya :P

---

### Post by punx45 on 2007-06-24
thats alot of questions, probably most of which can be answered just by reading other threads.. but ill address a few anyway.

> **lunaz said:**
> 
if i install ubuntu-desktop will i get firefox & open office?
no.  nor will you get a GUI. server install is very basic, and will leave you with just a command line.   but those things can be installed easily if you know how to enable repositories in sources.list and are familiar with using apt-get on the command line.
alternatively, if you are afraid of the command line, you can always start with a desktop install, and then just install the services you need like apache, openssh server, etc...
> **lunaz said:**
> bresnan doesn't give out static ips to home users. am i right that i have to get a domain & custom dns service from dyndns.org to make [www.example.com](www.example.com) work right on my home server? if there's a better/cheaper way to go about it i'm interested to know.
yes you will need a dynamic DNS service to keep track of your changing ISP IP 
dyndns.org has free solutions, you use a subdomain of one of many domains they own, something like yourchoice.homelinux.com.   there are other dynamic dns services, and some might let you bring your own domain if you choose to buy one.   do a google/forum search for "dynamic dns" 

> **lunaz said:**
> is it a real bad idea to let roommate use the server as a desktop on occasion?
if you are lazy like i was it can be :-D   use unique user names and strong passwords and you should be fine
[http://ubuntuforums.org/showpost.php?p=2401943&postcount=6](http://ubuntuforums.org/showpost.php?p=2401943&postcount=6)

> **lunaz said:**
> what's the best partition plan for a server?
just for messing around the default install will be fine.   if you are concerned about you or your roomate loosing stuff if your brick the system, a separate /home partition cant hurt.

> **lunaz said:**
> is there any security measures i can take for both comps & the router to make sure i don't get hacked? hehe...
do common sense things like disabling remote administration of the router, use unique user names (e.g. not stuff like john, or mike) and strong passwords - letters numbers and !@# type characters

for service specific things check the servers and security section, especially the stickies

---

### Post by arvevans on 2007-06-24
Lets see if I can answer some of your questions:

[LIST]
[*]If your Linksys router has firewall functions, this can be used as a front end to protect all your local computers.  If you want outside entities to access your local systems then you will have to allow specific port requests to punch through the firewall.
[*]Each computer can still have it's own firewall as added protection in case your primary defense gets compromised.
[*]When you install ubuntu gnome desktop you should automatically get Firefox, Open Open office, and the other default applications.  Then use Synaptic or apt-get to add other applications that you want to download and install.
[*]If you use dyndns for remote access re-direction, you need to download and install "ddclient" but then go to dyndns.com and find their recommendations for configuring ddclient on Linux.  They will have you set ddclient configuration so that it asks their system what the real IP address might be, thus you avoid having it set dyndns to match your LAN IP (incorrect) instead of the cable company provided IP address.
[/LIST]
_._

---

### Post by lunaz on 2007-06-24
thanks for the help :P

should i make a user account for the roommate on both my computers so there's no chance of something going wrong? right now each computer just has one user, me.

if i make her accounts, do i have to do a /home partition for each USER or just one total?

sorry for the noob questions lol, can't seem to find exact answers to this stuff....

---

### Post by punx45 on 2007-06-24
> **lunaz said:**
> thanks for the help :P

should i make a user account for the roommate on both my computers so there's no chance of something going wrong? right now each computer just has one user, me.

if i make her accounts, do i have to do a /home partition for each USER or just one total?

sorry for the noob questions lol, can't seem to find exact answers to this stuff....

you probably should on the ubuntu systems because access controls are useful.   obviously windows is possible but pretty useless :)
no you dont have to do anything with the /home partition.   when you add a user it automatically gives the user their own home directory within /home   just like you have /home/yourusername it will create /home/herusername

---

### Post by lunaz on 2007-06-24
thanks :)

so if i got a custom dns top lvl domain from dyndns.org, i wouldn't need to install bind on my server right?

in order to secure both computers, should i have firestarter on each one? or is my router+firewall combo enough?

---

### Post by punx45 on 2007-06-25
those questions might be better answered in the [servers and security]("http://ubuntuforums.org/forumdisplay.php?f=7") section

---

