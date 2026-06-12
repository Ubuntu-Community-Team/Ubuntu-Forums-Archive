---
title: "ubuntu and cable modem"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by lani on 2006-12-26
hi all please bare with me  as ime new to the board
and in particular a ubuntu board
im having problems with my cable ubuntu configurations
i had ubuntu and win xp on a dual boot 
i could get xp to work with my cable.
 but ubuntu was another Q
at the moment i need win xp
so to use xp and ubuntu i need the dual boot
the other alternative is use another hdd
and use them as a single unit
but the hassle of plugging and and un plugging cables 
isnt for me 
i know what the problem is 
i need to know th 
ip address
gateway address 
subwaymask 
and dns 
of ubuntu
to get it to work
i rang my isp and this is the conversation we had
me how do i configure the ubuntu cable addresses
the guy on the ph; we are instructed to configure
windows only 
does the not include ubuntu or any linux sys 
he. yes
 as member of several boards around
 the world i posted this message 
and at drews world 
some one gave me two sites to look at 
this was one of them
now my Q can i be helped or not
or do i just revert back to windows
by the way i uninstalled ubuntu 
but i can reinstall it when needed 
thanks if you can help
ps my version of ubuntu is 6.6 
lani

---

### Post by Tzumli_D on 2006-12-26
Which country are you in? In Australia there are issues with bigpond and I've just been through the process to fix this myself.

---

### Post by Malta paul on 2006-12-26
Hi, 
Ubuntu Firefox web Browser should detect your cable modem, on boot up.
Check System>preferred applications> then Internet - web browser, and check that it is set to Firefox, and tick 'open link with browser default'

You e-mail programme will have be setup using your IP setting. Get these from your Windows settings then follow the wizard to put them into your email programme.

Good luck :)

---

### Post by lani on 2006-12-26
hi thank you for your reply
im from new zealand
and ive found the broad band companys 
are reluctant to to try and help 
linux users
in this country 
its probably not commercially viable
however 
i thought about dial up
but i believe my modem isnt linux compatable
tho when i bought it 
i bought it with the proviso as linux compatable 
that was when i had mandrake 9.1
but the modem  company supplied a tech to configure 
the dial up for free
and i used for about two years
but i bought a bigger hdd
and forgot i had to reinstall mandrake 
and so lost the connection
my cable company is telstra/clear
telstra beeing a sudsidery of australia telstra
ive been into ubuntu 
and typed ifconfig 
and the message i got was 
the ip address 
sub mask
but no gateway nor
dns configuration 
i wanted to post as much info as i could to you
sorry bout the long post 
im trying to give you as much
info as i can gather 
but beeing new to ubuntu 
i find it a bit daunting
lani

---

### Post by lani on 2006-12-26
ok i did as you instructed 
set my web browser to firefox
but the sys tells me failure to load firefox
that was the message i got when i first installed ubuntu
and i have no way of telling im on line or not 
in the brodband configuration 
it says 
connection 
is active 
but unless i can get on line how do i know this
thanks 
lani

---

### Post by lani on 2006-12-27
hi thanks for you replys 
and ive decided not to continue with ubuntu
as i found it is a clone of mozilla
and i dont want mozilla
i want a linux  OS
i can down load susse or debian 
thanks all the same 
lani

---

### Post by kinematic on 2006-12-27
open the command prompt in windows and type "ipconfig"(without the quotes).
that will show your ip addres,gateway,dns servers and search domain.
if your isp assigns ip addresses with dhcp you'll need your hostname wich you can find in windows by right-clicking on my computer and than go to properties.
all you have to do if your isp uses dhcp is fill in your hostname in the network manager in ubuntu(that's all i have to do),system>administration>network.
if you have a static ip addres just fill in the ip addres you found in windows along with the dns server,search domain and your hostname.
i'm not sure if that will do it because i've always been with my current isp and as i mentioned i only have to fill in my hostname provided by them.

---

### Post by MrHorus on 2006-12-27
> **lani said:**
>  
and ive decided not to continue with ubuntu
as i found it is a clone of mozilla
and i dont want mozilla
i want a linux  OS


Excuse me?

Mozilla is a software initiative, Linux is an operating system.

Ubuntu is a distribution of Linux.

By all means download Debian or Suse if you think this will solve your problem but if you can't get your cable modem to work in Ubuntu then I am seriously skeptical that you will have much joy in any other distribution.

---

### Post by xpod on 2006-12-27
> hi thanks for you replys
and ive decided not to continue with ubuntu
as i found it is a clone of mozilla
and i dont want mozilla
i want a linux OS
i can down load susse or debian
thanks all the same
lani

:confused: 
Mabey just reverting back to windows after all would be your best bet....at least until you have a better understanding of the differences between a browser and an os;) 

Even i in my limited knowlage would be interested to know how you came to those conclusions:-k 
Good luck regardless

---

### Post by kinematic on 2006-12-27
I missed that post and all i can say is wtf?
But yes....it's probably best to stick with Windows if you think the Ubuntu GNU/Linux operating system(wich is based on Debian)is a clone of a Mozilla web-browser or e-mail program ;)

---

