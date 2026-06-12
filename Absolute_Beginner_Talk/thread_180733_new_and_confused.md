---
title: "new and confused"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by yourearthlymaster on 2006-05-22
hello world, just got linux today and been racking my brains trying to get stuff working.  I hear no sound, can't get online, an who knows what I haven't found yet!](*,) 
I need to get the internet thing first.  I have bellsouth DSL.  attempted the whole, sudo pppoeconf thing and the system-admin-networking-dhcp thing.  
My modem even says there is an established connection, but when I try to open a page, a pop-up says "The connection was refused when attempting to contact www.google.com"

Please help, going.....mad......

---

### Post by ProjectGod on 2006-05-22
were you previously using this bellsouth device with a windows machine? how did you set it up on your windows machine? did you have to type your username / password to access broadband? every time you wished to connect to the internet? or was it AUTOMATIC / always on broadband?

early days yet! but we get alot of similar problems here on this forum... and its leaning towards a DNS error. hopefully! check your network settings and make sure you have DNS server as your ISP's DNS server IP address. ring em up to confirm.

---

### Post by yourearthlymaster on 2006-05-22
My DSL worked flawlessly with my windows machine.  I didn't have to login every time to get online.  It was automatic.  

But you lost me @ DNS server IP address.

---

### Post by ProjectGod on 2006-05-22
cool.

DRAT! i'm on a windows machine right now! so i can't remember from the top of my head where you set the network options! you can easily navigate to it using the GUI. 

just make sure your ethernet card (network settings) on your ubuntu machine is correct first. that is to say...

DHCP enabled (automatic IP addressing ... )

now on your windows machine... log into the ROUTER (bluesouth) device. check what DNS server its using.

now on your ubuntu machine... there should be an option in the (network settings) about DNS configuration. a tab or button or something like that... after you find it... use the same DNS server that's configured on the router on your ubuntu machine.

hope this works!

---

### Post by yourearthlymaster on 2006-05-22
ok I did that, now to try it out be back shortly.

---

### Post by ProjectGod on 2006-05-22
cool

---

### Post by RRS on 2006-05-22
You log into the router thru your web browser (IE, Firefox, etc.). You should be able to do this with Firefox from the Ubuntu machine also since your not actually going onto the internet.

Simply type your routers IP in the address bar and click "Go"

If you don't have your routers IP you might find it listed [here.]("http://www.pcmech.com/forum/showpost.php?p=1069209&postcount=3")
You might also check "favorites" in Windows as it may have been added when you did the DSL setup.

For more detailed assisistance it would be handy to know the make/model of your router. Also, does it function as a modem too or do you have a seperate DSL modem with a router connected between it and the computers?

---

### Post by yourearthlymaster on 2006-05-22
ok im back, that didn't work.  do you think that maybe bellsouth isnt linux campatable.  and if so, is there any way to make it work?

---

### Post by ProjectGod on 2006-05-22
could you please be more elaborate? so you have configured the exact DNS server on your ubuntu machine as found in the dns server settings of the router?

can you ping. the router or windows machine? at the terminal try

**ping (addr)**

addr is the ip address of your router / windows machine. e.g. ping 192.168.200.1

if you aint too sure about the window's ip address... go to windows. click start. run. type "cmd" enter. at the command prompt. type "ipconfig /all"

check he ip address... and try to ping it from the ubuntu terminal.

please try this also... at the terminal on the ubuntu machine... type

**ifconfig**

could you give us the result of this command. please :D

---

### Post by RRS on 2006-05-22
The ISP doesn't really care what OS you have, though most so called "help lines" will say use windows because that's all they know.

Before you can configure the computer we'll need more info about your connection.

First, what make/model of modem are you using? This may have been provided by Bellsouth when you first applied for service. Also does it use ethernet or USB cabling?

Next, do you have a seperate router or are you connecting the computer directly to the modem?

And finally what are the settings your using in Windows? These should be found in "network settings" if I recall.

If you can help us with this info I'm sure someone here can  help you solve the problem.

Edit; Forgot about ip and if conf's, thanks ProjectGod

---

### Post by yourearthlymaster on 2006-05-22
in the windows machine I get this when i ping:  

pinging 192.168.1.254: bytes=32 time=2ms ttl=64
etc.   
but in linux i get this:  

connect: Network is unreachable


with the ifconfig i get:  

Io     Link encap: Local Loopback
        inet addr: 127.0.0.1 Mask: 255.0.0.0
        inet6 addr: :: 1/128 Scope: Host 
        UP LOOPBACK RUNNING MIU: 16436 Metric: 1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 frame:0
        collisions:0 txqueuelen:0
        RX bytes:0 (0.0b)  TX bytes:0 (0.0b)
but I have followed the directions given word for word.

---

### Post by yourearthlymaster on 2006-05-22
I am connected to my modem by ethernet, and I am connected directly to it.  Modem Name WireSpeed Dual Connect ;Model C90-610030-06. 
network is set to obtain ip automatically

---

### Post by ProjectGod on 2006-05-22
as **RRS **mentioned. please describe the hardware setup more. the cabling, any other devices modem / router make model. etc etc. 

if its not too much of a hassle... on your windows machine. can you please give us the output of your Network configuration???

when you have internet connection on windows... go to START. click RUN. and type: cmd

at the command prompt. type:

ipconfig /all

we'd like the output... cheers.

check back to this tread regularly... cause i'm through for the day... more tomorrow. i'm at work! :mrgreen:

---

### Post by yourearthlymaster on 2006-05-22
oh yeah, DNS is disabled in DNS Configuration.

---

### Post by yourearthlymaster on 2006-05-22
DHCP Enabled. . . . . . . . : Yes
        IP Address. . . . . . . . . : 0.0.0.0
        Subnet Mask . . . . . . . . : 0.0.0.0
        Default Gateway . . . . . . :
        DHCP Server . . . . . . . . : 255.255.255.255
        Primary WINS Server . . . . :
        Secondary WINS Server . . . :
        Lease Obtained. . . . . . . :
        Lease Expires . . . . . . . :

1 Ethernet adapter :

        Description . . . . . . . . : Westell WireSpeed Dual Connect Modem
        Physical Address. . . . . . : 00-0F-DB-B5-83-2F
        DHCP Enabled. . . . . . . . : Yes
        IP Address. . . . . . . . . : 192.168.1.97
        Subnet Mask . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . : 192.168.1.254
        DHCP Server . . . . . . . . : 192.168.1.254
        Primary WINS Server . . . . :
        Secondary WINS Server . . . :
        Lease Obtained. . . . . . . : 05 22 06 21:59:31
        Lease Expires . . . . . . . : 05 23 06 21:59:31

---

### Post by ProjectGod on 2006-05-22
ahhh what the heck! i'll stay on a little longer. 

ok.

how do you connect your windows machine to the modem / router.? usb? or ethernet?

when you said earlier... that the "DNS is disabled" on which machine were you talking about? 

i'm getting quite confused! :)

so basically you have 1 modem / router that has 2 ethernet (cat 5) cables attached to it from an ubuntu machine and a windows machine right? and this modem / router also has a port to which the phone line connects right?

---

### Post by yourearthlymaster on 2006-05-22
the windows machine is connected to the modem via usb, linux via ethernet.  
the readout from the command prompt is from the windows machine.
"DSN disabled was from the windows machine under control panel->network.  

and i really appreciate all the help your trying to give.  thanx

---

### Post by ProjectGod on 2006-05-22
excellent.

as i've said earlier i'm not on a ubuntu machine right now. so its hard for me to tell where exactly "network configurations" is. 

what you'll have to do basically is this... 

on ur linux you'll have to enable dhcp... and enable the interface itself! from the looks of your ifconfig output you havent configured network settings at all yet... (or perhaps your linux didnt detect your ethernet adapter at installation?)!. after you've enabled dhcp you'll have to insert the DNS server details... and whammy! you'll have internet access!

more when i get home. have a nice night / day. :)

---

### Post by yourearthlymaster on 2006-05-22
thanx again PG.  goodnight

---

### Post by RRS on 2006-05-22
Let's try this now; 
In Ubuntu, System>Administration>Network Settings
Open the DNS tab and select "add" next to the DNS Servers listing box.

Type in 192.168.1.254 and "enter". 

Now select the connections tab and click on eth0, then "properties". 

Select DHCP from the dropdown menu and checkmark "enable this connection" and "OK", then "OK" again to close network connections.

This should set things setup for you but I'm still curious about your DSL modem. The Westell device shown in your  Windows ipconf appears to be the computers ethernet card(IP 192.168.1.97) while I believe the 192.168.1.254 address belongs to whatever seperate device you have connected between the computer and the wall.

If I'm correct in this then the above instructions should work, if not then please let us know what, if any, external components you have connected and what procedure you used to originally enable your DSL service with the Windows computer.

Good luck, and remember to post back if succesfull please.

---

### Post by RRS on 2006-05-22
> the windows machine is..........your trying to give. thanx

> excellent.................have a nice night / day. 

Sorry, missed these while checking my own settings to make sure of the directions I was giving. Also a very slow typist.

---

### Post by ProjectGod on 2006-05-23
do what **RRS **mentioned. and it should be perfect. you may very well need to set your ISP's DNS servers though under SYSTEM ... ADMINISTRATION ... "NETWORKING" ... "DNS" tab ... add the IP address of your ISP's DNS server. 

remember how i said you can check this by logging into the router from the windows machine and checking it there??

[SIZE="2"]if you think your post has disappeared then just log in using your credentials into ubuntu forums and search your thread / posts via the search menu under "forum navigation". [/SIZE]

:)

---

