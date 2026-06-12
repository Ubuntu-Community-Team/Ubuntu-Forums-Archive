---
title: "Virus on sda1 PLEASE HELP ME"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by pgar23 on 2007-09-17
Hi.
I have a virus, spyware, adware etc. on my windows drive. Never thought it would happen to me. :(
When I try to install a anti-spyware software on the windows drive, the virus keep closing my installation, so I can't install anything.
Is it possible to install a file FOR windows FROM ubuntu?
This is essentially what I want to do;
I have a file (ad-aware 2007) on my ubuntu desktop, I want to install the file to my windows drive (sda1), but the file is .exe and I need to get the virus and everything else off my comp. PLEASE HELP.
Also does anyone know of a better anti-spyware/virus removal software or is this good enough? (if you know of one please provide URL, Thanks)

---

### Post by CaptainInsaneO on 2007-09-17
You can install avg antivirus from the repo's, install that and scan your windows drive with it. Virus should be gone.

Edit: I should be more clear: scan your Windows drive with that from Ubuntu.

---

### Post by diatribe on 2007-09-17
a good antivirus is nod32, you may also want to get spyware s&d

---

### Post by mendingo84 on 2007-09-17
another excellent antivirus/firewall/antispam is BitDefender Pro ( and i think it's also cheap enough )

---

### Post by regomodo on 2007-09-17
do you have another XP machine?

Put avast or nod32 ($) on it and attach the virus-infected drive and scan. 

I don't know how to do the way which are asking. Sorry

---

### Post by pgar23 on 2007-09-17
> **diatribe said:**
> a good antivirus is nod32, you may also want to get spyware s&d

Is nod32 and spyware s&d ubuntu compatible...as I cannot install anything on my windows drive bcuz the virus close it down everytime.

---

### Post by pgar23 on 2007-09-17
> **regomodo said:**
> do you have another XP machine?

Put avast or nod32 ($) on it and attach the virus-infected drive and scan. 

I don't know how to do the way which are asking. Sorry

Hey this is a great Idea...I am going to try this. Thanks

PS. if i do this will the non-infected PC get infected once I attach the infected drive?

---

### Post by Toet on 2007-09-17
> **pgar23 said:**
> PS. if i do this will the non-infected PC get infected once I attach the infected drive?

That of course is something that can happen, depending on the virus. (you could google for that). I would go to do it via Ubuntu, or burn a boot cd with software on another machine.

---

### Post by Gremlinzzz on 2007-09-17
[http://www.howtoforge.com/avg_antivirus_ubuntu_feisty](http://www.howtoforge.com/avg_antivirus_ubuntu_feisty)
:guitar:

---

### Post by CaptainInsaneO on 2007-09-17
> **CaptainInsaneO said:**
> You can install avg antivirus from the repo's, install that and scan your windows drive with it. Virus should be gone.

Edit: I should be more clear: scan your Windows drive with that from Ubuntu.

I agree with this guy. :lolflag:

---

### Post by Irony on 2007-09-17
Perhaps you can boot up in windows recovery mode F8 and install from there - it depends on the virus, you'd need to google it to find the solution.

---

### Post by pgar23 on 2007-09-17
> **CaptainInsaneO said:**
> I agree with this guy. :lolflag:

I can't find avg antivirus...
Am I doing this correctly...Accessories> Add/Remove > search "avg", "avg antivirus", "antivirus" ? I am not finding it...  :(

Disregard this post, Gremlinzz left a helpful URL...Thanks

---

### Post by Yes on 2007-09-17
[http://ubuntuforums.org/showthread.php?t=136064&highlight=AVG](http://ubuntuforums.org/showthread.php?t=136064&highlight=AVG)

---

### Post by CaptainInsaneO on 2007-09-17
> **Gremlinzzz said:**
> [http://www.howtoforge.com/avg_antivirus_ubuntu_feisty](http://www.howtoforge.com/avg_antivirus_ubuntu_feisty)
:guitar:

If you can't find it in the repo's, this is a good guide to installing it. :)

---

### Post by the.phantom on 2007-09-17
one of the best anti-mailware programs is free !

it was called "ewido"
but now it is part of Grisoft  (avg)

if you go to their site you can d/l it to the windows side and run it in safe mode
[http://free.grisoft.com/doc/downloads-products/us/frt/0?prd=asf](http://free.grisoft.com/doc/downloads-products/us/frt/0?prd=asf)

and do you know how to run a HJT  ( hijack this)

if so i still know of a few good anti-mailware forums that can help you !
and as someone said spybot S & D is good too 

and if you run a program like spywareblaster it will block a lot of the junk from getting on your system 

you should be able to run and use all those in "safe mode"
if you need a good windows anti-crapware site i can recommend a few great ones if you like?

i worked support on that stuff untill i gave up and went to Ubuntu

---

### Post by kelvin spratt on 2007-09-17
use hirens boot disc its a live cd has all the tools you can think of and antivirus

---

### Post by pgar23 on 2007-09-17
> **the.phantom said:**
> one of the best anti-mailware programs is free !

it was called "ewido"
but now it is part of Grisoft  (avg)

if you go to their site you can d/l it to the windows side and run it in safe mode
[http://free.grisoft.com/doc/downloads-products/us/frt/0?prd=asf](http://free.grisoft.com/doc/downloads-products/us/frt/0?prd=asf)

and do you know how to run a HJT  ( hijack this)

if so i still know of a few good anti-mailware forums that can help you !
and as someone said spybot S & D is good too 

and if you run a program like spywareblaster it will block a lot of the junk from getting on your system 

you should be able to run and use all those in "safe mode"
if you need a good windows anti-crapware site i can recommend a few great ones if you like?

i worked support on that stuff untill i gave up and went to Ubuntu

Would you be so kind as to provide the URL's please...also is there a software that will block the virus, spyware...etc from even downloading...?( What I mean by this is...I click d/l file, then the software will say "this is a virus, do not d/l this")

---

### Post by LowSky on 2007-09-17
use synaptic package manager under System>Admin

check for antivirus

---

### Post by lisati on 2007-09-17
> **pgar23 said:**
> I can't find avg antivirus...
Am I doing this correctly...Accessories> Add/Remove > search "avg", "avg antivirus", "antivirus" ? I am not finding it...  :(

Disregard this post, Gremlinzz left a helpful URL...Thanks

The last time I checked grisoft had a linux version of AVG available at [http://free.grisoft.com](http://free.grisoft.com)

EDIT: p.s. the only time I've been seriously affected by a virus it was on Windows (as a result of being careless with an attachment from someone I didn't know while using an antivirus system different to the one I normally use) and had to re-install Windows. You might have to pencil that in as a last resort.

---

### Post by CaptainInsaneO on 2007-09-17
> **pgar23 said:**
> Would you be so kind as to provide the URL's please...also is there a software that will block the virus, spyware...etc from even downloading...?( What I mean by this is...I click d/l file, then the software will say "this is a virus, do not d/l this")

Maybe Linux? :lolflag:

But seriously... AVG does this. I've actually lost a couple no-cd cracks for my games that way, avg freaks out when I turn on my external hdd and quarantines them as viruses. It's a very good anti-virus for the money (free).

---

### Post by pgar23 on 2007-09-17
can someone please send me the URL link to the AVG download ( i want the actual deb download file)...when I try to get it I get a window with a bunch of weird code and it slows down my comp...why is this happening to ME? hahaha :(

---

### Post by Fornax-101 on 2007-09-17
[http://free.grisoft.com/doc/5390/us/frt/0?prd=afl]("http://free.grisoft.com/doc/5390/us/frt/0?prd=afl")

---

### Post by pgar23 on 2007-09-17
> **Fornax-101 said:**
> [http://www.grisoft.com/doc/31/us/crp/0?prd=avl](http://www.grisoft.com/doc/31/us/crp/0?prd=avl)

Thanks, but I am looking for the actual download file, the one where I would select "save to disk"...I can't get to it for some reason, my comp slow down too many much.

looking for something like this screen:
see attachment...

---

### Post by the.phantom on 2007-09-17
pgar23
you can go here ( safe as mysite)

[http://rcip.com/mitch/PhantomPhixer.html](http://rcip.com/mitch/PhantomPhixer.html)

on that page scroll down and read "how did i get infected" by tonyK  ( a true expert )
and if you click the newbie/oldie list

all is free software
and for anti-crapware
scroll down to 
SPYWARE TOOLS - REQUIRED

i no longer recommend adaware
and ie-spyed is ok IF you just use IE

but there are links and "how to on most of it "

now there are also a few free safe online scanners and STINGER in the online scan area ( stinger is a self starting scanner for the top virus

spywareblaster will block a bunch of bad sites
and if you use firefox on the windows box online i did this

[http://rcip.com/mitch/ffhost.html](http://rcip.com/mitch/ffhost.html)

it is updated several times a day and will block several thousand sites that are involved with malware
and you can use adblock to use the list 

now if you want to run a HJT log and post it i would recommend here

[http://maddoktor2.com/index.php](http://maddoktor2.com/index.php)
just read the sticky in the HJT log areal 

it is part of ASAP
[http://asap.maddoktor2.com/](http://asap.maddoktor2.com/)
and the forums are totally safe !
any questions just let me know ;-D

so bottom line
spywareblaster
spybot S & D
avg anti spyware
and all are free and work !


spywareblaster will only work if you have a clean system to begin with ! so get your box clean first

---

### Post by Fornax-101 on 2007-09-17
I dont know why you dont get that screen but maybe you could try to get it with wget, open a console and type:
```
 cd ~/Desktop && wget http://free.grisoft.com/filedir/inst/avg75fld-r49-a1130.i386.deb
```

---

### Post by pgar23 on 2007-09-17
> **Fornax-101 said:**
> I dont know why you dont get that screen but maybe you could try to get it with wget, open a console and type:
```
 cd ~/Desktop && wget http://free.grisoft.com/filedir/inst/avg75fld-r49-a1130.i386.deb
```

Ok...I did this, but where should i go to run this program? I dont see it anywhere under accessories.

Edit: my mistake, I see it on desktop...hahaha

---

### Post by pgar23 on 2007-09-17
I am running the AVG antivirus software, but I dont see sda1 as an option to test...do I need to specify the path? (if so, what is the path to sda1?)

---

### Post by Fornax-101 on 2007-09-17
/dev/sda1

But is your windows partition mounted?

---

### Post by nexes on 2007-09-17
To answer your original question, yes, odds are you can install any of that software from Ubuntu.

sudo apt-get install wine

Nearly every installer I've tried in Ubuntu has worked. Just open the setup.exe and point it at your Windows drive (if you have write access to the partition).

Hell, you might even be able to run it if it's something simpler like Ad-Aware, but I honestly have no idea on that front.

Of course, whatever you're infected with may well just close the program when you attempt to open it, even after it's installed. So if you can scan it from Linux with a native tool, all the better. I just wanted to mention that yes, it should be possible in the way you originally mentioned. :)

---

### Post by pgar23 on 2007-09-17
> **Fornax-101 said:**
> /dev/sda1

But is your windows partition mounted?

Yes, my windows partition is mounted, but when I type the path "/dev/sda1" into the "path to test" section of AVG, it say "path can't be tested"...so I went to my desktop just to triple check that sda1 is mounted, when I right-click I get the option to unmount, so I would assume that it is mounted.
Any further help is greatly appreciated guys, thanks so much.

---

### Post by oilchangeguy on 2007-09-17
why not try this, burn avg to a cd. boot windows into safe mode, no other safe mode option, just safe mode. use the admin id to log in. turn off system restore. reboot into safe mode again, admin id, install avg from the cd and let it run. it will not have the current definitions, but it should be enough to get you started. when you get the computer back on the internet, update the definitions, and scan again.

---

### Post by pgar23 on 2007-09-17
Btw, is "/dev/sda1" the full path?

---

### Post by Fornax-101 on 2007-09-17
oops, it seems you can't use /dev/sda1, my mistake
maybe you could copy the link from nautilus when you open the windows partition (ctrl+l)

---

### Post by pgar23 on 2007-09-17
why when I use nautilus the sda1 file does not show up, but I can obviously see it on my desktop...
SEE ATTACHMENT

---

### Post by oilchangeguy on 2007-09-17
have you read post #31?

---

### Post by pgar23 on 2007-09-17
nevermind, I got it...it was under "media" then sda1...DUH! lol

---

### Post by pgar23 on 2007-09-17
> **oilchangeguy said:**
> have you read post #31?

where/what is post #31?
Edit: I read post #31, it sounds highly complicated, and I jus figured out how to scan sda1 from ubuntu...good suggestion/way too complicated.

---

### Post by oilchangeguy on 2007-09-17
> **pgar23 said:**
> where/what is post #31?
Edit: I read post #31, it sounds highly complicated, and I jus figured out how to scan sda1 from ubuntu...good suggestion/way too complicated.

if you say so.

---

### Post by pgar23 on 2007-09-17
Once I finish the test, how do I quarantine the virus', etc.?

---

### Post by pgar23 on 2007-09-17
I have 35 infected files on my comp...how can I quarantine these?

---

### Post by pgar23 on 2007-09-17
does anyone know of a URL that points to the full version of AVG, but is cost-free?  :)

---

### Post by oilchangeguy on 2007-09-17
> **pgar23 said:**
> does anyone know of a URL that points to the full version of AVG, but is cost-free?  :)

[http://free.grisoft.com](http://free.grisoft.com)

---

### Post by DM was on fire! on 2007-09-17
edit - I speak too soon. Never mind.

---

### Post by pgar23 on 2007-09-18
Found out that I had 425 infected files...ended up having to fresh install XP and Ubuntu...::snaps fingers + brings arm across chest::

---

### Post by jmpmjmpm on 2007-09-18
***didn't see above post, but will leave my comments here for future searchers***


if I were you I would take a different aproach. I would get all my important data off that windows drive using ubuntu and scan it all with avg when it comes over to make sure it's virus free (avoid copying over any type of executable files), burn it all to cd/dvd so you can put it all back in your fresh/clean system later. (plus, you then have a backup of your stuff)

I would then do a full format and re-install of windows from a known good source (if your running pirated windows then there is no way to know the install will not be infected from the outset as some nasty people build malware in when they create the install image). If you do not have a known good source, that is, you don't have an original and genuine windows disk, or recovery cd's, then, I would stop right there and consider either purchasing windows or making the switch to gnu linux completely.

Once any system is infected, there is no certain way to know it's clean again apart to format and re-install from known good source. Almost all of the pirated software you get from bittorrent etc these days is infected with malware, including windows! If you can't afford to buy software for windows there are good free/open alternatives even for windows for most applications, but then why not switch completely? If you need windows for games, buy an oem xp home edition and use it for playing your games or see if there is a way to make them work in linux. Use windows for games and linux for everything else, at least you will know your important data and activities will be safe from evil people.

---

### Post by darren1270 on 2007-09-18
> **jmpmjmpm said:**
> ***didn't see above post, but will leave my comments here for future searchers***


if I were you I would take a different aproach. I would get all my important data off that windows drive using ubuntu and scan it all with avg when it comes over to make sure it's virus free (avoid copying over any type of executable files), burn it all to cd/dvd so you can put it all back in your fresh/clean system later. (plus, you then have a backup of your stuff)

I would then do a full format and re-install of windows from a known good source 

Once any system is infected, there is no certain way to know it's clean again apart to format and re-install from known good source.

Just like to say this would be my approach as well.  I have a lot of customers that think  just because they got some software from their brother or cousin or whomever.... they think it is clean and legal.  When they end up having to call me, they get upset when I give them a bill for 45 or 50 dollars to fix their system when the problem could have been avoided in the first place.

Darren

---

