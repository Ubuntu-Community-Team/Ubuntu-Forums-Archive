---
title: "apt-get question?"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by cyclister on 2005-09-17
I have tried out apt-get some times now and always failed in some way.
Sometimes I reading that I am restricted from a specific folder in usr :(

I want to get a good firewall Ive heard much good about fprot should I write.
sudo apt-get install fprot?
Then i want the mplayer or what the name of that music/videoplayer cant really the name of the player.

And Ive even tried to search for packages in google with no luck

---

### Post by aysiu on 2005-09-17
Synaptic is the graphical version of apt-get. [Here's a graphical tutorial of using Synaptic to search for and install a program](http://www.psychocats.net/essays/winuxinstall.php).

You can also enable extra repositories (i.e., more software in Synaptic) by following [these instructions](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by Xian on 2005-09-17
You can search through the official Ubuntu package database online.

[Find Ubuntu Packages](http://packages.ubuntu.com/)

---

### Post by aysiu on 2005-09-17
fprot isn't a firewall; it's anti-virus, and [it costs money](http://www.f-prot.com/products/prices/price_unix_ws.html). All of the software you get via apt-get/Synaptic is cost-free (even if it's nonfree or proprietary). If you want a good firewall, try firestarter or guarddog.

You can also just do a search in Synaptic by name and description for the word *firewall*.

You don't really need anti-virus in Linux, but if you want one, you can check out clamav.

---

### Post by cyclister on 2005-09-18
Ok Ill trying to get this little by little now I guess I think it will be great in the end any way.
But the beep player I didnt find in synaptic :( some days ago.
I find some good players that I want to try out, by the way xmms I didnt find so good.

About the firewall is iptables a firewall?
And should I take away that applikation?
In windows is not good to have 2 firewalls running at the same time.

And in linux I do not have to worry about defragment of my hdd, have a fancy anti virus applikation or take away addwares?

---

### Post by aysiu on 2005-09-18
[QUOTE=cyclister]Ok Ill trying to get this little by little now I guess I think it will be great in the end any way.
But the beep player I didnt find in synaptic :( some days ago.
I find some good players that I want to try out xmms I didnt find so good.[/quote] It's in [my Synaptic](http://i22.photobucket.com/albums/b337/psychocats/438a5a02.png). Have you tried [enabling extra repositories](http://www.ubuntuguide.org/#extrarepositories)? For players, though, I'd recommend Rhythmbox or AmaroK.

> 
About the firewall is iptables a firewall? According to the description, which you can read in Synaptic: [i]netfilter and iptables provide a Linux kernel framework for stateful and stateless packet filtering, network and port addresss translation, and other IP packet manipulation. The framework is the successor to ipchains.

netfilter and iptables are used in applications such as Internet connection sharing, firewalls, IP accounting, transparent proxying, advanced routing and traffic control.

iptables web site: [http://www.iptables.org/](http://www.iptables.org/)[/i]

> 
And in linux I do not have to worry about defragment of my hdd, have a fancy anti virus applikation or take away addwares? Yes, you do not need to worry about either of those things.

---

### Post by cyclister on 2005-09-18
This forum is great its getting only better and better for everyday soon I can a little bit more about this.
 :) 

But to be a linux guru I think Ive have to work on this for many many years, but hey it would be nice  :wink:

---

### Post by aysiu on 2005-09-18
[QUOTE=cyclister]
But to be a linux guru I think Ive have to work on this for many many years, but hey it would be nice  :wink:[/QUOTE] It depends what you consider a "Linux guru." I think I've helped out a few people, but I've been using Linux for only five months, and I'm not a programmer or designer or anything.

---

### Post by cyclister on 2005-09-18
[QUOTE=aysiu]It depends what you consider a "Linux guru." I think I've helped out a few people, but I've been using Linux for only five months, and I'm not a programmer or designer or anything.[/QUOTE]

For me a linux guru dosent have to understand programming or webdesing only if he understand and can guide people thruw their problems.I think a ubuntu guru should have a picture of what all the packges does do for everyones system.
But yet he do not acctully be able to controll them, he do not have to be able to "hack" or "crack" another system either.
You are on your way and take long steps toward that stage to be a "guru" beacuse a guru help others.That was a religous guru does they come forward to him and he has some tools he like with diffrent types of yoga and stuff.And these whom seeking him does see another point beacuse they are in a new country and so forth.

I long to be lika a little linux guru some day me too, but your way a head of me.Do not compare to others, compare against your self.For everyone "aha "expirence you grow in everything you do.
I do not even had a "aha" moment with linux yet, but when I do I know my linux skill have grow a bit.

But now to my new question I cant acctully see all diffrent types of packages should I take one package that make me see them all?
I see like a debian package for example I want a new musicplayer, nor bmp, some gnomeplayers and even firewalls do I not see in my list, of all packages.Firestater for example and much much more.But I've seen achron music player.
Is it beacuse I have gnome instead of Kde?

---

### Post by aysiu on 2005-09-19
It has nothing to do with Gnome or KDE. Kubuntu and Ubuntu share the same repositories.

Did you enable extra repositories? The link I gave you before is down now, I think, but it was working when I linked to it originally.

Enabling extra repositories will let you see more packages in Synaptic.

---

### Post by cwaldbieser on 2005-09-19
[QUOTE=cyclister]
About the firewall is iptables a firewall?
And should I take away that applikation?
In windows is not good to have 2 firewalls running at the same time.

And in linux I do not have to worry about defragment of my hdd, have a fancy anti virus applikation or take away addwares?[/QUOTE]
iptables is a command-line front end to the firewall.  Generally speaking, all the GUI's like firestarter, guarddog, etc. are just more user friendly front-ends.  The actual firewall software (netfilter) is part of the operating system.

---

### Post by cyclister on 2005-09-19
[QUOTE=aysiu]Synaptic is the graphical version of apt-get. [Here's a graphical tutorial of using Synaptic to search for and install a program](http://www.psychocats.net/essays/winuxinstall.php).

You can also enable extra repositories (i.e., more software in Synaptic) by following [these instructions](http://www.ubuntuguide.org/#extrarepositories)[/QUOTE]

Yeah I see its down, that wasent so cool.Tried on my own with a home site to guide me but hey I think I am born stupid or some.
How many actions should I make?
Tried a long list of letter and words in terminal but I didnt get that right :(

Tried sudo apt-get update apt-get upgrade that even didnt do the tric.
But hey its a day tomorrow I leav in a northen part of europe so its over 12 at night, I guess I get that right tomorrow or after that.

Hey man our site is da bomb man for ubuntu now I have a "skunk" with matches in his little hand he is so cute, my little firestarter.
Thx man this site have everything, just klick, copy, cut and save.
Now I gonna do my system all over to the weekend with bigger swap smaller root, and it gonna be nice.I discovered a partitiontool pack I have now that gonna be sweet for starter, then I gonna trix and stuff so my brand new system is gonna be chill man, so chill and quite.

My new question is BSD like this with apt-get?
And get higher receptories?

---

