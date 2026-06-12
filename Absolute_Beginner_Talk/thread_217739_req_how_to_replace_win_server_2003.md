---
title: "req: how to replace win server 2003"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by gotname? on 2006-07-17
if u wanted to replace server 2003 with ubuntu server, how would you do it?

i mean feature for feature.

i ask bcz im a nixiot and have zero clue what stuff is called in linux. previous help that i have requested in other forums inevitably leads to.. why do you want a gui on your sever? 

well, lets nip that in the bud. bcz command line admining a web server is not an option. u got a better shot of seeing ice cubes in a british pub than u got of me admining anything via command line [ok,. thats an exaggeration, but given a choice, gui all the time]

really, i only need ad/dns, domain.local w/ user management, file and print serving to win xp clients, and web server functions.

obviously, starting with the lamp install would be the first step, but what to install after that, and how to get a desktop on it so i can make sense of it all? 

tia.

---

### Post by scxtt on 2006-07-17
you don't have to install the server version just cause that's how it's branded ... you should install a desktop version (probably via the alternate cd) and just add the webserver packages you need ...

---

### Post by jrjr on 2006-07-17
I'm after the same thing eventually. For now I am dual booting the desktop version to learn some stuff. When I get comfortable my plan is to install the server version. Once thats in type this in:

```
sudo apt-get install ubuntu-desktop
```

That will install all the nice desktop gui stuff 
The good thing about the server install is that it will automatically install and configure LAMP - or so im told

Thats my plan and im stickin to it  :mrgreen:

---

### Post by scxtt on 2006-07-17
yeah, i'm sure the server version is "fine tuned" (and smaller), but you can get all the same software working from the desktop version ... and i've read a few posts where putting the GUI on-top-of the server isn't quite as smooth as most people like, but everyone's mileage varies ...

---

### Post by gotname? on 2006-07-17
wow, quick replies. thanks!!

well, first, why dont i install the desktop and then the server features?

- many docs i have read seem to agree that server builds are optimized with an eye on security. being as i am a noob to this, it would be helpful to start with an o/s that is screwed down tighter than a desktop build.

in addition, i dont know what the packages that i need are called, nor do i have a clue when there are choices, which ones are the best for my needs. for example, i need some sort of cross platform authentication. openldap does not offer this. it took me several days to find a web site that said " openldap does not support windows clients" . this may seem silly to an experienced linux admin, but that was several wasted days to find one sentence that had relevance. i still dont know how to authenticate windows clients in an active driectory type setup without trying novells NDS [e-directory].  being as there is a cost associated with nds,  im thinking, [ad] came free with my server 2003. why would i pay for a substitute that i have to invest time learning? there is so much information and only so much time i can devote to reading stuff during the day. plus, many linux docs are extremely tough to determine if they are applicable to my needs without reading a good portion of them. 

so my original question stands. what would you replace the traditional windows server feature set with?

thanks for the info jrjr. if i wanted xfce instead of kde would the command be:
```
sudo apt-get install ubuntu-xfce
```
or would it be :
```
sudo apt-get install xfce-desktop
```

---

### Post by scxtt on 2006-07-17
looks like it's just **sudo apt-get install xfce4**

---

### Post by T700 on 2006-07-17
> **gotname? said:**
>  plus, many linux docs are extremely tough to determine if they are applicable to my needs without reading a good portion of them. 

so my original question stands. what would you replace the traditional windows server feature set with?


I know you don't want to hear this and you're certainly welcome to flame away, but I don't think it is in your best interest to try this.  Unless you are willing and able to invest a great deal of time and effort to learning the ins and outs of Linux and server administration, you're going to end up with gaping security holes.  

A server, GUI or not, is not a simple thing to administer.  

Paul

---

### Post by rccharles on 2006-07-17
> **gotname? said:**
> 

so my original question stands. what would you replace the traditional windows server feature set with?

Do you have a specific set of features in mind?  Please list them one per line.

See Webmin for a browser based administration tool.
[http://www.webmin.com/](http://www.webmin.com/) 

A Ubuntu server forum:
[http://www.ubuntuforums.org/forumdisplay.php?f=45](http://www.ubuntuforums.org/forumdisplay.php?f=45)

Robert

---

### Post by Liam on 2006-07-17
> **gotname? said:**
> 
well, lets nip that in the bud. bcz command line admining a web server is not an option. u got a better shot of seeing ice cubes in a british pub than u got of me admining anything via command line [ok,. thats an exaggeration, but given a choice, gui all the time]


really, i only need ad/dns, domain.local w/ user management, file and print serving to win xp clients, and web server functions.



Good luck with that.

Meaning, not gonna happen.

Sure, you can install Apache, bind, Samba, and CUPS with the GUI for the basic functionality, but if you need to customize anything in any way (and you don't want to get pwned when you put your box on the Internet), you're going to have to use a command line at some point. It's going to be a helluva lot harder to get support if you try to do it otherwise.

I know it can be kinda daunting when you're coming off a bunch of Windows experience, but it really is a different frame of reference, and you might as well get used to it if you're determined to save a few thousand bucks on that 2k3 license.

OK, sermon over.

AFAIK, Samba can't serve AD. It handles being an NT-style PDC just fine, so if you're on a small/medium network, you might be able to get away with that.

---

### Post by farmer49 on 2006-07-17
I'm just trying to set up a server for the first time. Maybe this will help some. I played with the gui version to get a handle on it  and you can add server functions or, as I also wanted to get a bit of a handle on using line commands, I down loaded the server version. If you go to [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06) , it steps you through the setup and the programs you need for various funcitons. There are also places in the forum in the server section which discuss adding gui features to the server version. Good luck

---

### Post by gotname? on 2006-07-17
all of you make good points. lets see if i can address them. 

**@ Liam re: command line.** i agree with you, but how can a windows guy learn if i dont have something familiar to back me up? i dont mind migrating to command line... eventually, so when i said no command line, it was in the frame of reference that this was a noob sub-forum, and not the admins forum. but i get ur point. plus, most basic functions can be done remotely via a browser, so i'm ok with that.
[B]
@ rccharles re: feature set.[/B]

*purpose:*
> web/file server for soho lan serving an intranet site and an external portal to the network resources. serving 8 win xp clients, 2 linux desktops [1 suse, 1 mandriva <-not mine], and 1 nas device. and a cpl of lappy's and the occasional transient win 98 or win2k box i may be working on.

*features i need:*

```
*- ftp server* - not immediately, and i may be able to avoid it entirely by using cms [joomla or drupal] for my intranet site with file sharing enabled. we shall see. i have php/sql installed alongside my IIS, but i didnt use a cms for the intranet. in hindsight, that seems silly to have not done so.

*- active directory/dns.* be nice to be able to have my shared resources, printer, and users/comps integrated as well, but, at the very least, i do need some sort of windows client authentication. does not need to be as robust, but must be present. 

*- file server*. mostly resources spread over the lan. the new 2k3r2 has virtual directories which are great. i would like to find an equivelant feature in linux, but its pretty new to windows too.

*- print server *- 1 oki c5400n, 1 brother mfc 5200, both connected to windows machines. 
```
[B]
alt features:[/B]
> - i use **hyena** for remote management. it does everything from user management to dns records, to starting and stopping services. it requires the admin pak from m-soft, but it works flawlessly. i hope that webmin is as feature rich. 

- i use everest corp edition integrated into sql for desktop hardware analysis, performance and inventory. this can easliy be moved to a desktop, but it would be cool to ffind a linux alternative. [this is similar to sandra if your unfamiliar with it, but it does network testing/diagnostics a lot better. well, it does everything better imo]

- a/v - im confused here. are there linux server managed a/v's for win clients? if not, no big deal, i use kaspersky where i can afford it, and comodo free a/v where i cant. but what should i put on the ubuntu server?

thats all im using my win server for right now. its pretty much a no-touch kinda thing unless i get creative. i am not using any mail servers right now. google accepted me into the 'mail for domain' beta, so i wont be messing aorund with new mail for awhile, and exisiting domain mail is routed thru a pop server from one of my web hosts. hmm, maybe i might be interested in finding out if its possible to consolidate all the pop accounts and downloading them all to the server, and let the clients get from the server, but its not a 'right now' thing.

i considered using some special purpose network devices by re-using a few p2 and p3 boxes that are gathering dust, but i want to keep it simple at first. i also dont want to be tempted into running a windows server in conjuction with my linux project bcz if i get frustrated, you can guess which one will get unplugged.
 
thanks for the webmin link. everything [it seems] is going towrds that c-panelish look. probably cz it was a good idea :) i like it. 

@ Liam again. thanks for the samba tip. if this was an enterprise type environment, i wouldnt be looking for free help, i would want to throw a few bucks into the community. this is just a small network for my personal use and a small part-time business. so your suggestion might be sufficient for my needs.

**@ scxtt**, thanks for the tip. ill try it in about 4 more minutes :P

**@t700**, i getcha man. but im not gunna flame any1 who offers me help. that would not be wise.... thanks for your concerns. my take on security is this. if someone wants in, they will get in. even as a windows admin, my skills are not good enuf to keep out someone who is...motivated. if security could play offense instead of just defense, that might change....

**@farmer.** thanks for the link. i saw similar links a while back for other versions. a great starting point, but its package selection/translation from windows that concerns me. tho those points are well worth a bookmark anyway. thanks!

---

### Post by az on 2006-07-17
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

