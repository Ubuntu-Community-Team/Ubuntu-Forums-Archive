---
title: "Interet Connection Using kppp"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by tin2 on 2006-11-25
I want to connect to internet using kppp; what should i do?
I usually have to type all this:

sudo pppd /dev/ttyS0 115200 debug usepeerdns defaultroute noauth connect '/usr/sbin/chat -v "" at+crm=1 OK "atdt#777" CONNECT' mtu 264

---

### Post by groggyboy on 2006-11-25
i haven't used ppp in a while (and never in linux) so i can't help you with specifics.  however, launching kppp is as simple as typing "kppp" in a terminal in your KDE session.  :D

---

### Post by Cariboo1938 on 2006-11-25
> **groggyboy said:**
> i haven't used ppp in a while (and never in linux) so i can't help you with specifics.  however, launching kppp is as simple as typing "kppp" in a terminal in your KDE session.  :DHi groggyboy,
I see you are using Kubuntu. I want to use KDE in Ubuntu and I tried to configure kppp. 

This is what I did until now:
I installed KDE in Ubuntu 6.10-64 bit and when I chose "Session KDE" I want to use Kppp to connect to the Internet. 
In Gnome I use GNOME ppp which works very well. It means that the modem is recognized and working.
Here is how I tried to configure kppp (without success).

> 
--> Kstart
---> Internet
----> KPPP Internet Dial-Up Tool
[KPPP window opens]. 	Click Tab: [COLOR="Magenta"]Configure[/COLOR]
                   	click Tab: 'Accounts' and select: [COLOR="Magenta"]New[/COLOR]
['Create new Account' window opens].	Select: [COLOR="Magenta"]'Manual Setup'[/COLOR]
                                 	Enter Connection Name: [COLOR="Magenta"]Provider[/COLOR]. In my case [COLOR="Magenta"]"Telus"[/COLOR]
                                 	Under Phone Number click: [COLOR="Magenta"]Add [/COLOR]and enter the phone # to connect to Provider.  								   In my case "[COLOR="Magenta"]359 6530[/COLOR]". 
                     
To finish configure click: [COLOR="Magenta"]ok[/COLOR]
                                 	Select tab: Modems and click: [COLOR="Magenta"]New[/COLOR]
                                 	Under Device enter Modem Name. 
In my case "[COLOR="Magenta"]TOPIC SEMICONDUCTOR Corp TP560[/COLOR]"
                           			"      "   Modem Device. 
In my case "[COLOR="Magenta"]/dev/ttyS2[/COLOR]"
						"      "   Connection Speed. In my case "[COLOR="Magenta"]575600[/COLOR]"
                                                   
To finish configure click: [COLOR="Magenta"]ok[/COLOR]
Back to KPPP window. Enter Login ID. In my case "[COLOR="Magenta"]lunaazul[/COLOR]"
                     Enter Password. In my case "[COLOR="Magenta"]********[/COLOR]"
		     Check mark "[COLOR="Magenta"]Show log window[/COLOR]"
		     click: [COLOR="Magenta"]Connect[/COLOR]
Window 'Connecting to: Telus' opens and says: '[COLOR="SeaGreen"]Modem Ready[/COLOR]' and '[COLOR="SeaGreen"]Initializing Modem[/COLOR]', and 
'Login Script Debug Window' opens but stays empty.


After a few seconds both windows close and nothing happens. What do I do wrong?
Thanks for any comment, reply or help!

---

### Post by groggyboy on 2006-11-25
well Caribou:

I'm not familiar with using modems under linux.

btw, i can see you've posted about this elsewhere as well.  i wish i could help you, but all i can really do is point you at other posts.  it seems like a lot of them are older - for breezy or dapper.  however, [this one over at kubuntuforums]("http://kubuntuforums.net/forums/index.php?topic=10830.0") is for edgy.  it suggests adding a couple lines to your /etc/ppp/options file.

also: from the [ubuntu wiki article on kppp]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f80f2865d7f29664a8506ef25b0e40eaf4420c10"): in the /etc/ppp/peers/kppp-options file uncomment the line reading "noauth".

finally, a lot of the posts suggested editing your /etc/ppp/options file, changing "auth" to "noauth".  this last bit of advice may no longer apply to edgy - i have no idea.

you could also run kppp from a terminal - it may spit out error code that could help you.

i wish i could do more for you, Caribou.  But as I said, I don't know this stuff... :-|

---

### Post by Cariboo1938 on 2006-11-25
> **groggyboy said:**
>  .....
you could also run kppp from a terminal - it may spit out error code that could help you.
wish i could do more for you, Caribou. But as I said, I don't know this stuff... You did a lot for me!
Thank you so much.
I used this as "sudo kppp" and could get it working.
You really helped me a lot with the other hints too.
I appreciate your quick reply also. 
Thanks again!:)

---

