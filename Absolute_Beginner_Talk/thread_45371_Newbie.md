---
title: "Newbie"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by mh10190 on 2005-06-29
Hi
Im new to ubuntu
And to linux
Im wondering wat software comes with the ISO
Im currently using Fedora Core 4
Wich is 4 CDs and comes with alot of software
Im wondering since ubuntu is only 1 CD how much software does it come with
and does it come with OpenOffice 2.0 Beta

---

### Post by rachii on 2005-06-29
everything that i ever used in fedora, is on the ubuntu cd.   ubuntu just doesnt come with all that EXTRA STUFF.  and if there isnt a program on the disc, its very easy to install via apt and the ubuntu repositories.  the current ubuntu stable release doesnt come OpenOffice 2.0 beta, but does come with open office (you can install 2.0, i think the next ubuntu release in october will use 2.0?)
honestly, being experienced with ubuntu and fedora, i think ubuntu is much smoother, and more fun for new to linux users.

---

### Post by aysiu on 2005-06-29
Are you using dial-up? What's wrong with downloading the packages you want?

These are the ones that come with the CD:
[http://packages.ubuntu.com/hoary/](http://packages.ubuntu.com/hoary/)

---

### Post by mh10190 on 2005-06-30
The thing is i just installed Ubuntu
And i got everything working except the wireless on my laptop
it recognizes it i just cant configure it corectly
After i get that working im gonna use that great package link
I agree that Ubuntu is way better than fedora
But what do you think is the best linux out there for all the differnt uses
i know there isnt a best
but if u can mention some good ones and wat they are the best for
i checked out distrowach, its pretty good

and 
im wondering if you can help me with the wireless connection
i use a linksys wireless router
and the laptop has intel WIFI in it
i cant configure the IP or w/e correctly
is it possible to get walked thru this
thanx

---

### Post by poofyhairguy on 2005-06-30
Is this what you need?:

[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=intel+wireless](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=intel+wireless)

---

### Post by mh10190 on 2005-06-30
its a little advanced
but ill find my way
is their a simpler way
im quiete confused

thanks for the help

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=mh10190]its a little advanced
but ill find my way
is their a simpler way
im quiete confused

thanks for the help[/QUOTE]


Sorry its a little nerdy. The best thing about the command line is that you don't have to know whatthe stuff actually means though. Don't be intimidated by the command line. I know it seems weird and primative at first, but its great when you are following guides. Just copy and paste. I do amazing stuff in Ubuntu by copying and pasting commands that are foreign to me.

Be brave. Once you set things up you don't have to do it again. That is the only way to do it....but once you do it will work. Thats the good part.

Lets start you off slow with some lessor command line things to build your confidence.

Let me ask you a question- is there any way you can plug it in ethernet style and get some sort of internet on that machine?

If you can, follow the directions in this link. Its a little light copy and paste, it will be good practice and its needed to follow the instructions. I promise after we go throught all the command line stuff to get things set up, I'll tell you about some nice graphical applications you can use to keep the ship sailing.

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

This small step will allow you to install the software you need to follow that howto.

Can you do that much now?

Power to you!

---

### Post by mh10190 on 2005-06-30
Thanx For the link
Im wondering 
What if i got to a hotspot or something
How will i manage that

And how do i install programs
untarrring ????

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=mh10190]Thanx For the link
Im wondering 
What if i got to a hotspot or something
How will i manage that[/QUOTE]

Well...my favorite way is to put the ssid "any" (all lowercase) in the network tool. To get it go to "system" "administration" "networking." When you activate it will connect to a nearby connection.

Or you can install the program called netapplet. I think it lets you pick a network Window's style. You add it to you dock after you install it.

> And how do i install programs
untarrring ????

No. Once you get you internet working you can use synaptic. Do what that other link says, then go to synaptic. "system" "administration" "synaptic package manager." Hit reload. Then search (I search description and name). For that howto to work, you need to install the following programs in synaptic:

build-essential

linux-686

linux-headers-2.6.10-5

---

### Post by poofyhairguy on 2005-06-30
Here is easier to read directions:

[http://tvilda.tigbis.lt/dokuwiki/doku.php?id=ubuntu__intel_pro_wireless_2200bg__wpa_mini-howto_en](http://tvilda.tigbis.lt/dokuwiki/doku.php?id=ubuntu__intel_pro_wireless_2200bg__wpa_mini-howto_en)

---

### Post by mh10190 on 2005-06-30
these are excellent links
but
my ethernet connection doesnt work either
i can copy and paste
but how if i can access the web page

another thing i was tryin to mount my windows hard disk for reading with ubuntu
and i typed exactly wat it said for practice

and it didnt work

it said the file already esixts or something

another thing
wats "dir"

and synaptics will do wat exactly and how

thanks for all the help

---

### Post by mh10190 on 2005-06-30
y dont i just install net applet
i hav the card working
its activated
but it isnt connecting to my router

could the following be an issue

i use AOL as my ASP (i persoley hate it, but my famly needs it)
and with my windows machine i had to always sign into aol before using firefox
could this be an issue aswell

---

### Post by poofyhairguy on 2005-06-30
> another thing i was tryin to mount my windows hard disk for reading with ubuntu
and i typed exactly wat it said for practice

and it didnt work

it said the file already esixts or something

A reboot might fix that.

> another thing
wats "dir"

directory

> and synaptics will do wat exactly and how

thanks for all the help

downloads programs and install them. elegantly so things don't slow down. Best thing about Linux is all the free software. Most can be gotten easily in synaptic.


 I'm glad you got your wireless to work. I would go to a coffee shop or something tomorrow (use my any trick) and download some of the stuff you need.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=mh10190]
i use AOL as my ASP (i persoley hate it, but my famly needs it)
and with my windows machine i had to always sign into aol before using firefox
could this be an issue aswell[/QUOTE]

AOL can work. There are two ways. This way:

[http://www.ubuntuforums.org/showthread.php?p=209234#post209234](http://www.ubuntuforums.org/showthread.php?p=209234#post209234)

Or this one:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html)

---

### Post by mh10190 on 2005-06-30
so u think the fault is with my router
because my card is up and runing
but no connection

and

i started to check out synaptics

im not exactly usderstadning how to use it to download stuff

letsay i want to download Open office 2.0 beta

how will i go about doin that

btw

thanx for all the great help
im loving linux even more know

---

### Post by mh10190 on 2005-06-30
i seriously am not following the instalation process
building??
extracting??
making new dir????

---

### Post by mh10190 on 2005-06-30
also tell me
if i cant connect to my home's wireless network
how am i going to connect to a coffe shop's

the status of my connection is disconnected
how do i connect it
the ip, subnet, and dns is rite but the phsical address is wrong
but wat shoud i config it in
static ip
or
dchp

i dont get it y it just cant detect the networks in the area
and i just chooes the one i want

wat exactly should i do
thanks

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=mh10190]so u think the fault is with my router
because my card is up and runing
but no connection[/QUOTE]

No. Did you use DHCP on the router? Do you have the exact address and ssid? Did you try without WEP or WPA to see if it works?

> i started to check out synaptics

im not exactly usderstadning how to use it to download stuff

letsay i want to download Open office 2.0 beta

Connect to internet. Open synaptic. Search for openoffice. Click on the box next to "openoffice.org2"

Chose install. Click apply. It will download and install.

Its easy to use.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=mh10190]also tell me
if i cant connect to my home's wireless network
how am i going to connect to a coffe shop's[/QUOTE]

Well..the wireless card might be looking for a dns server....a place with wirless broadband would give you access to one of those instantly.

> the status of my connection is disconnected
how do i connect it
the ip, subnet, and dns is rite but the phsical address is wrong
but wat shoud i config it in
static ip
or
dchp

Which one does you router use?

> i dont get it y it just cant detect the networks in the area
and i just chooes the one i want

Thats what the netapplet program does. If you do my directions earlier and also get on the internet, you can easily download it in synaptic:

[http://support.novell.com/techcenter/articles/tp10007.html](http://support.novell.com/techcenter/articles/tp10007.html)

---

### Post by mh10190 on 2005-06-30
[QUOTE=poofyhairguy]No. Did you use DHCP on the router? Do you have the exact address and ssid? Did you try without WEP or WPA to see if it works?
[/QUOTE]

when i check network connections with my desktop that is connected it say
dhcp server #
and the static info

i dont know wat wep and wpa are

i have the ssid also 

wat can be wrong?

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=mh10190]when i check network connections with my desktop that is connected it say
dhcp server #
and the static info
[/QUOTE]

Then use dhcp and try again.

---

### Post by mh10190 on 2005-06-30
i used every possiblty

im stumped

---

### Post by mh10190 on 2005-06-30
btw
wen i installed the distro
it said something like the wireless is in "killing mode"
or something like that 
im not quite sure
and they couldnt connect

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=mh10190]i used every possiblty

im stumped[/QUOTE]


Ok..lets go to a different angle. Since you are on dial up, the only reason to connect to your network is to share files correct? Then what you should do it go somewhere  where you can connect wirelessly to some broadband and then install netapplet, the aol dialer, and samba (the program needed to network and share files with windows).

---

### Post by mh10190 on 2005-06-30
im not on dialup
im on cable
with a wireless network

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=mh10190]im not on dialup
im on cable
with a wireless network[/QUOTE]


sorry. I got confused. Ok. Lets try again.

Are you sure the card is working? what evidence do you have?

---

### Post by mh10190 on 2005-06-30
in "network settings"
it has it at eth0
and it is active
i configured it with dhcp
i unterned the essid (thats the name of the routher, rite?)
i entered the 3 DNS servers
i dont know wat to put in for hostname

the network icon in the tray has the wrong physical adress
and it says im disconnected

---

### Post by mh10190 on 2005-07-06
alright
i was playing around with this for a while now
it isnt working
i think the card is dedected
but im not sure
i dont want to type in the essid, and ip
arent there applications that detect networks like windows
everything automated
if there are cant i just download them on another computer
and burn it on a cd-r and install it on ubuntu

someone mentioned, netapplet

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=mh10190]
i dont want to type in the essid, and ip
[/QUOTE]


If it works...put the work "any" in the ssid blank and hit activate and it will connect to nearby networks.

---

### Post by varunus on 2005-07-06
mh10190:

can you open up a terminal and type "iwconfig" and post the output of that here?  Its sometimes easier to manually configure wireless from the console in linux, and that command will give some info that might be useful.

Good luck.

---

