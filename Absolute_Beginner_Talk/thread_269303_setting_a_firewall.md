---
title: "setting a firewall"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-01
after spending nearly 24 hours to create the necessary partitions (on 3 hard drives)to install linux, making shortcuts of my partitions inside my home folder and just finishing setting my screen resolution at 1280x1024, i think the next step is to setup a nice firewall.. 

off course you already noticed that if i spent 24hours to pass 3 simple tasks, i must be a total noob!!! yeah, i am a noob and i need help to create a firewall, can you guys help me?

---

### Post by PPAAUULL on 2006-10-01
What program are you going to use?

---

### Post by PPAAUULL on 2006-10-01
If you want a suggestion Firestarter is nice, and it is easy to use.

---

### Post by uk_sphinx on 2006-10-01
sudo aptitude update
sudo aptitude install firestarter

---

### Post by cmaranhao on 2006-10-01
> **uk_sphinx said:**
> sudo aptitude update
sudo aptitude install firestarter

after that, will the firewall be installed or do i have to do some tweacking later?

---

### Post by uk_sphinx on 2006-10-01
the firewall will be installed but all ports are set at defaults i think.
pretty sure most incoming is blocked except smtp http etc for internet .
youl have to set the ports up as you need them opened.
or exceptions. i havnt had no probs yet its simple.
just have a look at the program and youl figure it out.
you can type code to read the manual.

sudo man firestarter

something like that.someone correct me if im wrong

---

### Post by cmaranhao on 2006-10-01
maranhao@maranhao:~$ sudo man firestarter
No manual entry for firestarter

where is the help?:???: 

i want to use amule in the future, how can i open the necessary ports to use amule? i don't think i'll need to open ports for anything else.. just tell how to open for amule and i'll be done with firewalls :-D

---

### Post by brianC on 2006-10-01
[http://www.grc.com/default.htm](http://www.grc.com/default.htm),scroll down to the ShieldsUp!, test all ports.
Test's your firewall for holes

---

### Post by uk_sphinx on 2006-10-01
i havnt had to do one myself yet let me go check 4 u m8

---

### Post by uk_sphinx on 2006-10-01
il check your security if you give me ur ip and a bit of time to get some proggys.
better than a website can.

mind you does linux have nmap accessable from the terminal.

---

### Post by uk_sphinx on 2006-10-01
you go to policy and choose a aplication youve installed and set the rules

---

### Post by cmaranhao on 2006-10-01
> **brianC said:**
> [http://www.grc.com/default.htm](http://www.grc.com/default.htm),scroll down to the ShieldsUp!, test all ports.
Test's your firewall for holes

wow, this firewall rocks:D 

i will test it more but until now it seems to be very secure :cool:

---

### Post by cmaranhao on 2006-10-01
one more thing.. i can't remember exactly but i think emule need both 4662 and 4672 ports opened.. how can i open them?

---

### Post by brianC on 2006-10-01
Try the firestarter tutorial [http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)  the policy page

---

### Post by cmaranhao on 2006-10-01
i am worried with these results (those were checked in shields up):

[https://www.grc.com/x/ne.dll?rh1dkyd2](https://www.grc.com/x/ne.dll?rh1dkyd2)

> Solicited TCP Packets: RECEIVED (FAILED) — As detailed in the port report below, one or more of your system's ports actively responded to our deliberate attempts to establish a connection. It is generally possible to increase your system's security by hiding it from the probes of potentially hostile hackers. Please see the details presented by the specific port links below, as well as the various resources on this site, and in our extremely helpful and active user community.



Unsolicited Packets: PASSED — No Internet packets of any sort were received from your system as a side-effect of our attempts to elicit some response from any of the ports listed above. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system remained wisely silent. (Except for the fact that not all of its ports are completely stealthed as shown below.)



Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.

---

### Post by brianC on 2006-10-01
In the  Firestarter Preferences under the icmp filtering tab, check the enable icmp filtering ,test again.

---

### Post by cmaranhao on 2006-10-01
the only thing i've done was this:

sudo aptitude update
sudo aptitude install firestarter

then i tested it in that site.. i already rebooted my pc and i "can't see" any firewall.where are those Firestarter Preferences?

---

### Post by cmaranhao on 2006-10-01
this may seem a bit odd but have i instaled the firewall? i don't have it in applications menu..:???: help

---

### Post by brianC on 2006-10-01
Open places,home file system,usr,applications, look for firestarter and click. If you use alacarte menu editor you can create an icon . Open alacarte, file new entry, then right click on the firestarter icon (in th application folder),properties,launcher and copy the info to alacarte....me a newbie too....should work.

---

### Post by tdrusk on 2006-10-01
I remember reading, I think on this site, that a firewall isn't needed. Is that true?

---

### Post by brianC on 2006-10-01
Not really needed. I was having issues trying to connect to the internet,real slow, slower than dialup. Installed firestarter and all was well. I read that too, but it helped me. Sort of like having the lights on , nobody home,doors locked, and the car in the garage. Could be home, could be away,go to the next house,maybe the doors open.....

---

### Post by tdrusk on 2006-10-01
well I installed it, but I don't see what good it could do. Nobody can mess with your stuff, or at least the important stuff.

If it's not necessary I will delete it. So someone please tell me.

---

### Post by brianC on 2006-10-01
If it is slowing your system down, causing issues with accessing the net, remove it.If not ,leave it, if only for peace of mind.

---

### Post by uk_sphinx on 2006-10-01
look its your choice but i would never recomend leaving a computer unprotected like that.
you do need it and dont uninstall it.
click on applications      go to internet      click on firestarter.
thats where it is.
after you installed it.
im supprised no-one else has told you.



it shouldnt slow your computer down that much its only monitoring for intrusion attempts.
if you have no firewall on its like leaving your front door open on your house.would you do that???

---

### Post by brianC on 2006-10-01
"If it is slowing your system down, causing issues with accessing the net, remove it.If not ,leave it, if only for peace of mind."

notice the word If.
 
Doing a search of the internet for firewalls in linux results in a lot of people saying that it in not really neccessary.

"Sort of like having the lights on , nobody home,doors locked, and the car in the garage. Could be home, could be away,go to the next house,maybe the doors open....."

Said the same but in a different order

---

### Post by tdrusk on 2006-10-01
How can I make firestarter start when I boot up?

---

### Post by uk_sphinx on 2006-10-01
ok bri your right.
hackers cant fingerprint your operating system by sending packets to ur computer.
they certainly cant send packets to specific ports on your computer to see what programs you got running.
then considering they cant do that they wont take that info and go to 1 of hundreds of sites and find an exploite for free to hack you based on the knoledge they gathered.
firewalls dont stop backdoor access from trojans either.
axctually maybe scrap the last one (think i heard someone say viruses and trojans are practicly obsolete in linux)

well do as you like its your choice to make.
its not hard to find your own answers on google.

---

### Post by brianC on 2006-10-01
This is from the firestarter FAQ on starting after reboot.

"Q: Do I have to start Firestarter after I have rebooted?

Usually, no. When Firestarter is installed from a package, the firewall is running as a service. You can query the status of the service by executing /etc/init.d/firestarter status. The excemption to this is Gentoo users, dial-up users in some cases and persons who have installed from source and not registered the Firestarter sytem service.

For an in-depth answer, see the section on persistence of the firewall"

---

### Post by uk_sphinx on 2006-10-01
i dont think its run as a service (default)
start the program
go to edit
go to preferences
go to firewall click on activate at program start up
dont know if it means startup by program though.

[edit] ow i see what you mean. yeah i think its run in the background but you have to turn a setting on to actually get the program to start up.the gui i mean.

---

### Post by uk_sphinx on 2006-10-01
u any good on aptitude brianc?
iv got a prob on a different thread if you are

---

### Post by brianC on 2006-10-01
Activate on start up was checked, but I think it was checked when installed. I installed through  add/remove..

---

### Post by tdrusk on 2006-10-01
I just ran the scan on [http://www.grc.com/default.htm](http://www.grc.com/default.htm) and I passed everything, without a firewall.

I feel safe.

I read on this board that you only need a firewall if you are running a server, or stuff of that nature.

---

### Post by uk_sphinx on 2006-10-01
give me your ip address and il test u with a variety of packets.

---

### Post by tdrusk on 2006-10-01
no

---

### Post by uk_sphinx on 2006-10-01
maybe your right???
but from my paranoid reading iv been led to believe its a bad thing not to have one.
maybe its different on linux.
id never have a windows xp box unprotected.
im going to have to do a bit of reading on it.
suppose it could be just a windows thing with all the trojans etc.
i used p2p quite a bit at one time and i was always finding hidden threats in archives and software.
i dont think u would be too happy without one if u knew someone was targeting u though.

***well its been emotional***
            cya

---

### Post by cmaranhao on 2006-10-02
guys, i need additional help.. 

all i've done was this:

sudo aptitude update
sudo aptitude install firestarter

after testing the firewall in the site you guys linked to me, i found out that i still have holes.. 

now i want to edit the preferences of the firewall but i don't know how:???: 

you guys mention you can "view icons and menus" of the firewall and set your choices over there but i don't have them anywhere.where is the firewall icon?

---

### Post by harisund on 2006-10-02
Strictly speaking, you don't (atleast not this desperately) need a firewall. 

What do you need a firewall for? Are you just trying to block ports? Are you trying out some NAT or something? 

By default Ubuntu comes with no open ports. The softwares that you install decide which ports to open. 

A simple "netstat -plant | grep LISTEN" will tell you what TCP ports are being listened upon. Do a reading of 'man netstat' to find out about UDP ports.

---

### Post by cmaranhao on 2006-10-02
common man, i don't know much about linux, don't ever heard about NAT before..you tell me to go and do something else, this will do even worse.lol

i want a firewall, i installed one, just like i said in my previous post but something is missing (the icon or something) and i want to set its preferences

so please, someone tell me how to get to those preferences:???:

---

### Post by xpod on 2006-10-02
It is`nt in the "apps" menu but you`ll find it under "system>adimistaition>firestarter"

---

### Post by cmaranhao on 2006-10-02
> **xpod said:**
> It is`nt in the "apps" menu but you`ll find it under "system>adimistaition>firestarter"

i already searched in applications and also in administration.. no firewall icon :(

---

### Post by uk_sphinx on 2006-10-02
hello im back

there is a different way to start it m8

type      sudo firestarter

type your password

gui will appear
hope this helps

---

### Post by cmaranhao on 2006-10-02
it says this:

sudo: firestarter: command not found

what should i do now?

---

### Post by uk_sphinx on 2006-10-02
well i might be wrong but it sounds to me like you havent installed it
are you sure there wasnt an error when you installed it.

why dont you start a fresh terminal.
type out the code your doing to install it.
then do the code i said above and copy the whole lot to your next post and let us look at it.

---

### Post by cmaranhao on 2006-10-02
can you please write all the code down so i can see how its done correctly??

i am a total zero in this and i'm sure i'm doing it wrong. i would be extremelly appreciated

---

### Post by uk_sphinx on 2006-10-02
presuming you have not installed it.

[COLOR="Red"]sudo aptitude update.[/COLOR]

[COLOR="Red"]sudo aptitude install firestarter
[/COLOR]
[COLOR="Red"]sudo firestarter[/COLOR]

*****dont just copy and past it all to the terminal in one go.you have to do 1 line at a time.*****

if it says you have allready installed it.....

try reinstalling it....

[COLOR="Red"]sudo aptitude uninstall firestarter[/COLOR]

****then go to top and install it again as i stated above****

---

### Post by cmaranhao on 2006-10-02
i've done it like you said.. i will copy and paste the final result

> maranhao@maranhao:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper-updates Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main Packages
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/restricted Packages
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main Sources
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/restricted Sources
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper-updates/main Packages
Get:5 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper-updates/main Sources
Get:6 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [51.3kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4496B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [12.8kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [960B]
Fetched 101kB in 1s (76.8kB/s)
Reading package lists... Done
maranhao@maranhao:~$ sudo aptitude install firestarter
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "firestarter"
The following packages have been kept back:
  gdb openssh-client ssh-askpass-gnome
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
maranhao@maranhao:~$ sudo firestarter
sudo: firestarter: command not found
maranhao@maranhao:~$

notice that when i make sudo firestarter it dosn't make anything :???:

---

### Post by uk_sphinx on 2006-10-02
you need to enable extra repositorys.
do you know what they are??
go to this site...    [http://www.psychocats.net]("http://www.psychocats.net")

read through the ubuntu tutorial, especialy the bit about installing software.
take note of setting up extra repositorys.multiverse and universe i think.
its too much for me to explain here.click this click that etc.
u might think to just not bother but if you skip this advice i garantee you will be making another thread soon when you want to install a different program.
dont worry you'l get it its simple.
i find that i understand things better when i consult a tutorial over someone just giving me code as a quick fix.
that way i understan the cause of my problems and not just an answer.
also i wont be asking for advice when something similer comes up.

!!!good luck!!!

---

### Post by cmaranhao on 2006-10-02
please, give me the answer](*,) 

i know what you mean though about studying our own problems and to understand how to fix them.

however i need to get this machine up and running soon because i need to work on my project (and time is always running, in fact, i should have this machine already set).. its like, i should be working on the project instead of setting linux (but windows sucks so much) that thought setting linux first and working later.. but this is already taking too much of my time..

can you please just give me the commands?? i am also trying to get vmware ready and i am having problems with that too! as time goes by i will read more about how to install stuff, its just that learning right now is kinda troublesome.. i don't have the time!

please, help me set the firewall.. ](*,)

---

### Post by scc4fun on 2006-10-02
CMaranhao,

Firestarter was not installed. In your output I see that Firestarter was not found by aptitude:

> maranhao@maranhao:~$ sudo aptitude install firestarter
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
**Couldn't find any package whose name or description matched "firestarter"**
The following packages have been kept back:
gdb openssh-client ssh-askpass-gnome
**0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.**
Need to get 0B of archives. After unpacking 0B will be used.

You need to enable the additional software repositories that Aptitude (or apt-get) will use to obtain software to install. You can find instructions on how to do that [here]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html").

Then try the same commands as before:
sudo aptitude update.

sudo aptitude install firestarter

sudo firestarter


(espero que isso te ajuda!)

---

### Post by cmaranhao on 2006-10-02
> **scc4fun said:**
> CMaranhao,

Firestarter was not installed. In your output I see that Firestarter was not found by aptitude:



You need to enable the additional software repositories that Aptitude (or apt-get) will use to obtain software to install. You can find instructions on how to do that [here]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html").

Then try the same commands as before:
sudo aptitude update.

sudo aptitude install firestarter

sudo firestarter


(espero que isso te ajuda!)


i will try..

(oxalá me ajude, já estou a tentar há mais de um dia)

---

### Post by cmaranhao on 2006-10-02
just installed it through synaptic.. as easy as windows:D 

thanks a lot guys for all your help;)

---

### Post by cmaranhao on 2006-10-02
i tested the firewall here:

[https://www.grc.com/x/ne.dll?rh1dkyd2](https://www.grc.com/x/ne.dll?rh1dkyd2)

it failed in the ping test

> Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.


what can i do now to pass the ping test?this is my summary:

> GRC Port Authority Report created on UTC: 2006-10-02 at 23:42:53

Results from scan of ports: 0, 21-23, 25, 79, 80, 110, 113, 
                            119, 135, 139, 143, 389, 443, 445, 
                            1002, 1024-1030, 1720, 5000

    0 Ports Open
    0 Ports Closed
   26 Ports Stealth
---------------------
   26 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: FAILED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

---

### Post by az on 2006-10-02
> **cmaranhao said:**
> 
it failed in the ping test



Big deal!  If you use your computer to browse web sites, you are making your presence known anyway.  The only way to make your box completely invisible on the net is to not go on the net.  As stated, by default, nothing listens to the network anyway.  Unless you install stuff which allows other into your computer, you are safe.  You don't need a firewall on a desktop.

---

### Post by cmaranhao on 2006-10-02
just made it a trustealth :)

> GRC Port Authority Report created on UTC: 2006-10-03 at 00:01:59

Results from scan of ports: 0, 21-23, 25, 79, 80, 110, 113, 
                            119, 135, 139, 143, 389, 443, 445, 
                            1002, 1024-1030, 1720, 5000

    0 Ports Open
    0 Ports Closed
   26 Ports Stealth
---------------------
   26 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: PASSED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

i am so happy, i spent HOURS trying to achieve this](*,) 

thanks for your help and most of all, patience!!!! stay cool guys

---

### Post by podunk on 2006-10-02
What did you do to block pings? can you still surf the web?

---

### Post by cmaranhao on 2006-10-02
sure, i am surfing it right now.. i went to the firestarter options and enabled ICMP filtering.. 8)

---

### Post by distroman on 2006-10-02
> **podunk said:**
> What did you do to block pings? can you still surf the web?
Firestarter > Edit > Preferences > ICMP Filtering :)

---

### Post by cmaranhao on 2006-10-02
just installed amule but now i don't know how to open the ports.. 

i want to open TCP (port 4662) and the udp (port 4672)

how do i open them?

---

### Post by brianC on 2006-10-02
If you go to the firestarter web page they have a totorial on opening ports. Lot of info ,lots of help.

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by Kulgan on 2006-10-03
is it actually necessary to install an external firewall on ubuntu? I thought that so long as you were behind a router with a firewall, that would be taken care of?

---

