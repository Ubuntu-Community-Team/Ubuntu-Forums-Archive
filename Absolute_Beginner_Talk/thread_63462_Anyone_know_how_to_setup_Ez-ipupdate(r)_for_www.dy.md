---
title: "Anyone know how to setup Ez-ipupdate(r) for www.dyndns.com"
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by thundertoad on 2005-09-08
Hi there,

Was wondering if anyone knew how to setup that **ip updating software** that **[www.dyndns.com](www.dyndns.com) **recommends. I downloaded both recommended applications but dont seem to have much success setting them up... [B]I even found a third one called ddclient.
[/B]
Anyway... **I did a quick search for ez-ipupdater in the forum** and couldnt find any wiki's or how to's for that application... **can anyway help with setting that up?**

any input is much appreciated.
Thanks,

ThunderToad

---

### Post by hashimoto on 2005-09-08
Synaptic provides some of those updating programs. Try searching with name & description. I  can't remember which one I have in use, but it was a breeze to set up as the installation process run an easy script to do that. Just filled in my details and that's it. Never bothered after that (heck, I can't even remember the program's name anymore...)

---

### Post by thundertoad on 2005-09-08
[QUOTE=hashimoto]Synaptic provides some of those updating programs. Try searching with name & description. I  can't remember which one I have in use, but it was a breeze to set up as the installation process run an easy script to do that. Just filled in my details and that's it. Never bothered after that (heck, I can't even remember the program's name anymore...)[/QUOTE]
 Yeah ... man I am so pissed... but I can only blame myself... After we finally got the stupid remote desktop to work yesterday I installed this application that should work instead of ez-ipupdate... and as my previous post says... its DDCLIENT the problem is that it too my internal network ip not my internet ip off my router... and that means that I have to go and look into the config file... which I have very little idea how to mess with... but DDCLIENT pretty much ruined my logging in from work experiment because it made my ip my home intranet ip... grrrr

anyone know any other programs... or how to fix this DDCLIENT thing..
the thing that pisses me off is that dyndns.com doesnt have some kinda history of what the previous ip was... grrr I guess that would be considered alot of useless info.

ok.. just have to wait to get home and either properly configure it or uninstall it... 
hashimoto... do you run off a router or a dsl modem?

ThunderToad

---

### Post by az on 2005-09-08
[QUOTE=thundertoad]Yeah ... man I am so pissed... but I can only blame myself... After we finally got the stupid remote desktop to work yesterday I installed this application that should work instead of ez-ipupdate... and as my previous post says... its DDCLIENT the problem is that it too my internal network ip not my internet ip off my router... and that means that I have to go and look into the config file... which I have very little idea how to mess with... but DDCLIENT pretty much ruined my logging in from work experiment because it made my ip my home intranet ip... grrrr

anyone know any other programs... or how to fix this DDCLIENT thing..
the thing that pisses me off is that dyndns.com doesnt have some kinda history of what the previous ip was... grrr I guess that would be considered alot of useless info.

ok.. just have to wait to get home and either properly configure it or uninstall it... 
hashimoto... do you run off a router or a dsl modem?

ThunderToad[/QUOTE]


Many routers have the DynDns client built-in.  For linksys ones, there is a way to get ddclient to get the ipaddress form the router.  As I recall, you can do 

ddclient --help

And it tells you how to set that up.

---

### Post by hashimoto on 2005-09-08
[QUOTE=thundertoad]
hashimoto... do you run off a router or a dsl modem?

ThunderToad[/QUOTE]

I'm using a DSL modem. 

azz is right: many routers have the client built in. Try looking your routers manual to see how to set it up. Should be relatively easy.

---

### Post by thundertoad on 2005-09-08
[QUOTE=hashimoto]I'm using a DSL modem. 

azz is right: many routers have the client built in. Try looking your routers manual to see how to set it up. Should be relatively easy.[/QUOTE]
 Thanks azz... I did that yesterday just couldnt quite figure out getting the router settings... I'm one of those folk who actually use the how to's.

I have this freaky generic router called Pro-Nets ... ART514x or something... anyhoo I figured out how to map ports (port fowarding) with it although they call the service... virtual servers.. humph... go figure... anyway I couldnt find any dyndns reference there... man I cant even find an update for its firmware... but hey it was a four port router/adsl modem and was cheap... so otherwise it works fine.

anyone actually use ddclient or ez-ipupdater? or am I the only one who's tried using them?

hello?... ello... llo... lo...o

ThunderToad

---

### Post by az on 2005-09-08
Another intesting option is to find an old computer and make it a router.  You plug it into the internet and then run ddclient from there.  You ca then connect your current router to that computer and continue with your regular setup.  You have to forward ports twice, though, but it wll work.  It would need to have to NICs.

I used to run a website from my basement like that.  I didn't care if the box got attacked because it didn't contain anything important.  Never did get attacked...

---

### Post by thundertoad on 2005-09-08
Ok so I had one of my friends come over and take a look at ddclient... we found the problem... it was in the configuration file... there is a setting to get the ip off the web.. we tried a few settings before that and that one was the one that got the right ip back. So wooohooooo... turns out the config file wouldnt be read with gedit but had no problems with nano... (shrug).

Azz... I know what you mean.. I have a friend of mine in australia who is a system admin. And that guy is a network expert... has like 5 machines running at home with different systems ... so he can conduct experiments on them.. He has a routing computer, a fire wall computer, another fire wall layer computer, a mail server and his main computer... he uses an old laptop for the routing I think. Not an option for me though.. because basically I sorta like my router...its ghetto but hey it works nicely and has my port forwarding setup and hell if it aint broke why fix it. I cant find frikkin firmware updates for it and the damn company wont answer my emails... but hey.. I was the sucker who bought it and they're all the way in taiwan... 

So ... onto my next endevour.. I found a solution but ez-ipupdater wasnt it... now to start vncing from work.. that would be cool.. then maybe figure who this whole ssh thing.

ok enough ranting.. I'm gonna go find something to eat.
 ;-) 

Thanks you guys for all the input.
ThunderToad

---

