---
title: "Which USB wireless dongle will work with Feisy?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-05-20
Please tell me which will work.  Maybe a link to Amazon/whatever. 

It has to be guaranteed to work, NO BULLSHIT INCOMPATIBILTY WITH DRIVERS NONSENSE! :)

I want to be able to load up Ubuntu and be connected to the net with it. It will just work. 

Thanks.

---

### Post by aberadam on 2007-05-20
Oh, available in the UK.

---

### Post by Bachstelze on 2007-05-20
[http://www.amazon.co.uk/ASUS-WL-167G-WIRELESS-USB-802-11g/dp/B000H80EOM/ref=sr_1_5/202-0576696-9059039?ie=UTF8&s=electronics&qid=1179656840&sr=1-5](http://www.amazon.co.uk/ASUS-WL-167G-WIRELESS-USB-802-11g/dp/B000H80EOM/ref=sr_1_5/202-0576696-9059039?ie=UTF8&s=electronics&qid=1179656840&sr=1-5)

Writing you using one of those right now :)

---

### Post by aberadam on 2007-05-20
"Feisty" even.

---

### Post by AlexenderReez on 2007-05-20
belkin is the best......:KS:KS

---

### Post by aberadam on 2007-05-20
Thanks very much, when I plug that in it will 'just work'?  For definite.  I don't want to be installing anything or messing about.  I just want to see the Internet working. 

Please reassure this computer idiot.

---

### Post by aberadam on 2007-05-20
Which Belkin?  Link please.  There's only one of those Asus ones left...

---

### Post by Bachstelze on 2007-05-20
No, it ill not "just work". Linux drivers are available, and they're very easy to install. Isn't that enough ?

---

### Post by carusoswi on 2007-05-20
I am using the Belkin N1.  It took me a long time to figure out how to make it work, and it still cannot sit overnight without losing its association with ESSID - I have to manually re-associate it with the command:

sudo iwconfig wlan0 ESSID XXXXX where 'XXXXX' is the name of my ESSID.  I am not certain why it does not retain its association, but, once associated, it is very reliable and extremely quick.  I, too, am running Feisty.

Caruso.

---

### Post by aberadam on 2007-05-20
No it's not.  I've already spent about 5 hours trying to get my current USB thing to work which is why I'm willing to buy a new one as long as it 'just works'.

There must be one model that Ubuntu has the correct driver for already pre-installed...  Surely.

---

### Post by aberadam on 2007-05-20
Oh no Caruso... 

Pleases someone tell me I can just buy something that will plug in and work... 

Microsoft I love you!  I should never have deleted two of your XP partitions to make room for Ubuntu!  Please let us go back to the problem-free way things were!

---

### Post by AlexenderReez on 2007-05-20
:lolflag::lolflag:


i'm using belkin wireless g USB network 802.11g  ......i don't install any kind of driver .....even ndiswrapper in.....feisty and gutsy....it is autodetect...using wifi-radar....(i remove gnome - network-manager...)


and my wireless is really fast.....i'm using it right now in  university....sometimes most of  my friends don't get the network but my wireless adapter never failed.....

---

### Post by Bachstelze on 2007-05-20
> **aberadam said:**
> 
Microsoft I love you!  I should never have deleted two of your XP partitions to make room for Ubuntu!  Please let us go back to the problem-free way things were!

Oh yeah ? Are you telling us you never needed to install drivers in XP ?

---

### Post by aberadam on 2007-05-20
reez, that sounds great.  Apart from the bit about 'wifi radar' (maybe if I tried that now it would work... ).   Can you explain a bit more.  Is it simple this 'wifi radar'?

Hymn, the dongle I'm currently using on XP either just worked or came with a disk that just worked after I stuck it in and clicked a few things.  I can't remember.

---

### Post by AlexenderReez on 2007-05-20
hm...when i first run with my wireless...i also like damn hell try to figure out how to set my wireless so that it detect my network...try ndiswrapper...install driver...but it is seems it get even worse......then i make fresh install feisty.....and upgrade to gutsy ( without realized that i don't install wireless adapter  yet  )..so after that i think why should i install the driver if without it...it is even better.....

if you interest then here you are

> [http://www.amazon.co.uk/Belkin-802-11g-Wireless-Network-Adapter/dp/B0006374PK](http://www.amazon.co.uk/Belkin-802-11g-Wireless-Network-Adapter/dp/B0006374PK)

---

### Post by AlexenderReez on 2007-05-20
> **reez0105 said:**
> hm...when i first run with my wireless...i also like damn hell try to figure out how to set my wireless so that it detect my network...try ndiswrapper...install driver...but it is seems it get even worse......then i make fresh install feisty.....and upgrade to gutsy ( without realized that i don't install wireless adapter  yet  )..so after that i think why should i install the driver if without it...it is even better.....

if you interest then here you are

more over it is live time warranty !!!

---

### Post by aberadam on 2007-05-20
Thanks reez.

I though gutsy wasn't out for another 6 months though...

---

### Post by AlexenderReez on 2007-05-20
> **aberadam said:**
> Thanks reez.

I though gutsy wasn't out for another 6 months though...

i'm using pre pre pre pre pre alpha released.......:lolflag::lolflag::lolflag:

nothing special .....i just want to help the development.....help test.....check the error.....learn in deep about system .......try to correct error.....so far not having any kind of dangerous problem yet...(:lolflag: i never having serious problem either in ubuntu :lolflag:)

---

### Post by aberadam on 2007-05-20
:p:p

Right, so I need Gutsy to use that Belkin USB stick.

---

### Post by AlexenderReez on 2007-05-20
> **aberadam said:**
> :p:p

Right, so I need Gutsy to use that Belkin USB stick.

nope.....please dont either....it will bring a lot of breakage...unless you are patient or ableto handle the breakage....feisty is already enough...just search in synaptic for network manager....remove gnome-network-manager...search wifi-radar....install it.....

reconfigure network.......

> sudo /etc/init.d/networking restart
 

then open wifi-radar which in application--->internet......set youkind of wireless that you are using with...

open
> gksu gedit  /etc/network/interfaces

make sure your kind of wireless in there....

---

### Post by aberadam on 2007-05-20
Great, thanks.  I might try that with my current wireless dongle. 

You seem to know what you're doing, if you've got a couple of minute I'd really appreciate it if you could take a look at my original effort to get online, this thread: [http://ubuntuforums.org/showthread.php?t=448646]("http://ubuntuforums.org/showthread.php?t=448646")

---

### Post by AlexenderReez on 2007-05-20
> **aberadam said:**
> Great, thanks.  I might try that with my current wireless dongle. 

You seem to know what you're doing, if you've got a couple of minute I'd really appreciate it if you could take a look at my original effort to get online, this thread: [http://ubuntuforums.org/showthread.php?t=448646]("http://ubuntuforums.org/showthread.php?t=448646")

roaming mode is even easier.....it doesn't required you to set anything in wire-radar.....
> wlan0 IEEE 802.11g ESSID:""
[COLOR="Black"]**Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated**[/COLOR]
RTS thrff Fragment thr=2346 B
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
Reply With Quote

it is seems you doesn't set your mode to roaming :p:p
ok lets try....
just follow my instructions........

don't need to configure wifi-radar....after install wifi-radar and remove gnome-network-manager..and reconfigure your wireless...just restart (becuase you are using roaming mode)...

after restart.....
try to open firefox....if still failed then ....open wfi-radar----->applications---->internet....

you should see there is/are network /s over  there....click create ......just save....don't need to configure anythin...then just connect..

---

### Post by aberadam on 2007-05-20
Thankyou very much:).  I'll try all that when I get some time this afternoon.  I'm sure I was being told to install drivers though.  I can see the network, just can't get it to accept my password and connect.

---

### Post by MikeDK on 2007-05-24
lol aberadam, free-way thing, thats just Microsoft leading you straight to hell, with root-access all the way

Kind Regards mikeDK

---

### Post by MikeDK on 2007-05-24
thats why its called virus in windows :-P

---

