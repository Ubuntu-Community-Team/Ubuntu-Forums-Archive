---
title: "Why does it take so long for internet to boot up?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by BioGene on 2007-01-18
Hey everyone,

I noticed something strange about my Linux Ubuntu installation. Is this normal and if so can it be made to run faser. When ever I turn on Firefox browser the Internet takes a while to load up pages in the beginning, but when it goes to homepage after that all pages load in seconds.
 
Sometimes I also nee to write in terminal to start up the Internet or at least I think restart it! Why does it do this and can I speed up the first Internet boot up, as in when it just turns on?

---

### Post by irish_flu on 2007-01-18
A couple of questions for you, which should get you more accurate help:

1) what sort of internet connection do you have?  Is it dial-up, or some sort of "always-on" like DSL or cable, or satellite?

2) I'm not sure what you mean about using the terminal;  What are the commands you type when you're doing it?

---

### Post by TrikkeDaddy on 2007-01-18
Hey Hey, newbie here.  Caught my interest for this question as well.  I have cable and I do see the internet browser is slow at first and then gets a little faster.  I am using a system with about 266 memory and a 12G hhd, and want to save on resources.  Coming from dial-up, what a difference, but still not speeding up as fast as I would like.

---

### Post by zerhacke on 2007-01-18
You need to disable IPv6 if your broadband connection is sluggish.  I don't know why they turn that on by default, it's not like it's a standardized thing yet.  If ever.

---

### Post by irish_flu on 2007-01-18
zerhacke - Do you mean in Gnome, or in Firefox?

---

### Post by zerhacke on 2007-01-18
You could disable it in firefox, but then every other program connecting to the network would be sluggish at first.

Gnome is a window manager.  It doesn't connect to any networks so there's no way to disable IPv6 for Gnome.

I'd disable it across the entire system, which would disable it no matter what window manager you use.  You also wouldn't have to screw with firefox or Konqueror and every other program you use that connects to the network.

To do this:

1. sudo gedit /etc/modprobe.d/aliases (or your preferred text editor)
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off
4. Save the file and reboot

---

### Post by BioGene on 2007-01-18
> **irish_flu said:**
> A couple of questions for you, which should get you more accurate help:

1) what sort of internet connection do you have?  Is it dial-up, or some sort of "always-on" like DSL or cable, or satellite?

2) I'm not sure what you mean about using the terminal;  What are the commands you type when you're doing it?

1. Yes I do have a DSL [PPPOE] Connection and I told Linux to connect on start-up!
2. I use the code: pon dsl-provider to restart it or something I guess!

The issue here is like trikkedaddy said, Firefox will startup, then when it is connecting to my homepage which is Google, it will take almost forever to connect. This actually happens always and I seem to have to use the terminal code ¨pon dsl-provider" to make it start up again I guess. But the weird thing is that once it connects to my homepage [Google] I can connect then to any page within seconds! Why does it do this and how do I fix it?

P.S. 

This only happens on startup of the whole Gnome system!

---

### Post by TwistesdTexan on 2007-01-18
On the Address bar type in about:config . This will bring up a whole list of items. In a space near the top you'll see a filter with an entry area next to it. Type in ipv6 and this will leave the item you want to change "network.dns.disableIPv6". place your curser over the item and right click. toggle it to false. this should make things a bit faster.:-D

---

### Post by zerhacke on 2007-01-18
> **TwistesdTexan said:**
> On the Address bar type in about:config . This will bring up a whole list of items. In a space near the top you'll see a filter with an entry area next to it. Type in ipv6 and this will leave the item you want to change "network.dns.disableIPv6". place your curser over the item and right click. toggle it to false. this should make things a bit faster.:-D

If you do this, only Firefox will access the net quickly.  If you follow my outline you don't have to toggle wierd settings in Firefox.  My method "speeds up" everything that uses the network, not just Firefox.

---

### Post by BioGene on 2007-01-18
> **zerhacke said:**
> You could disable it in firefox, but then every other program connecting to the network would be sluggish at first.

Gnome is a window manager.  It doesn't connect to any networks so there's no way to disable IPv6 for Gnome.

I'd disable it across the entire system, which would disable it no matter what window manager you use.  You also wouldn't have to screw with firefox or Konqueror and every other program you use that connects to the network.

To do this:

1. sudo gedit /etc/modprobe.d/aliases (or your preferred text editor)
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off
4. Save the file and reboot

The broadband connection is pretty fast throughout most usage, only when I try to use it for the first time on Linux start-up does it act very slow! Is this the cause of having IPV6 on?

---

### Post by BioGene on 2007-01-18
> **zerhacke said:**
> If you do this, only Firefox will access the net quickly.  If you follow my outline you don't have to toggle wierd settings in Firefox.  My method "speeds up" everything that uses the network, not just Firefox.

Will it do this at start-up as well? As in when I just use Firefox for the first time?

---

### Post by 454redhawk on 2007-01-18
Sounds like the DNS problem that many have encountered.

Here is a suggestion.

Ping all 4 of these address, find the fastest 2 and make them your primary and secondary DNS's. 

4.2.2.2 and 4.2.2.1 and 208.67.222.222 and 208.67.220.220


Edit the /etc/resolv.conf file and add your DNS values.

Then apply this
```
sudo chattr +i /etc/resolv.conf
```

That will lock down that file and prevent overwriting.

To unlock it, 

```
sudo chattr -i /etc/resolv.conf
```

This has created much disscussion and would appear to be a bug. It seems alot of people are having a similar problem (myself included). The above is a fix that has worked for me and others.

---

### Post by zerhacke on 2007-01-18
Yes.  See, what's happening is that everything using your network is trying to resolve IPv6 first, and nobody, no ISP I know of, uses IPv6... that goes for just about every router I know of too.

Turning it off resolves your IP configuration quicker (at boot) and therefore boots the system faster.  Also, since Firefox isn't trying to figure out your nonexistant IPv6 configuration it'll go straight to IPv4, which is what you almost definitely use.

---

### Post by zerhacke on 2007-01-18
> **454redhawk said:**
> Sounds like the DNS problem that many have encountered.<snip>

I'm 120% sure it's IPv6.  His addresses are not consistantly resolving slowly.  It's only happening when he first starts Firefox, and not all the time.

---

### Post by irish_flu on 2007-01-18
> **zerhacke said:**
> 
Gnome is a window manager.  It doesn't connect to any networks so there's no way to disable IPv6 for Gnome.


Thanks for clarifying, I meant from the Network Manager you can access from within Gnome. :p

---

### Post by BioGene on 2007-01-18
> **zerhacke said:**
> Yes.  See, what's happening is that everything using your network is trying to resolve IPv6 first, and nobody, no ISP I know of, uses IPv6... that goes for just about every router I know of too.

Turning it off resolves your IP configuration quicker (at boot) and therefore boots the system faster.  Also, since Firefox isn't trying to figure out your nonexistant IPv6 configuration it'll go straight to IPv4, which is what you almost definitely use.

Just one question what does it mean when that file I am trying to edit appears to be totally empty? As in a pure white file?

---

### Post by BioGene on 2007-01-18
> **454redhawk said:**
> Sounds like the DNS problem that many have encountered.

Here is a suggestion.

Ping all 4 of these address, find the fastest 2 and make them your primary and secondary DNS's. 

4.2.2.2 and 4.2.2.1 and 208.67.222.222 and 208.67.220.220


Edit the /etc/resolv.conf file and add your DNS values.

Then apply this
```
sudo chattr +i /etc/resolv.conf
```

That will lock down that file and prevent overwriting.

To unlock it, 

```
sudo chattr -i /etc/resolv.conf
```

This has created much disscussion and would appear to be a bug. It seems alot of people are having a similar problem (myself included). The above is a fix that has worked for me and others.

Could you just explain to me how I would ping in Linux? I am not entirely sure!
Ok got it, same as Windows! Just type ping and ip address!

---

### Post by irish_flu on 2007-01-18
> **BioGene said:**
> Could you just explain to me how I would ping in Linux? I am not entirely sure!

You can Either load up "Network Tools" from the "Administration" menu in Gnome, then select the "Ping" tab and type an address

or

start up a terminal window and type "ping 123.45.6.78" (no quotes, and use whatever address you want)

---

### Post by zerhacke on 2007-01-18
> **irish_flu said:**
> Thanks for clarifying, I meant from the Network Manager you can access from within Gnome. :p

Oh.  I knew that... er, I was testing you, that's it.

From the network monitor in Gnome you can remove the IPv6 bindings, but that doesn't shut off IPv6.  As a matter of fact, that'll kill your network connection sporadically when IPv6 goes searching for its bindings.  You'd have to kill and restart your network constantly.  I speak from experience.

[quote=BioGene]Just one question what does it mean when that file I am trying to edit appears to be totally empty? As in a pure white file?[/quote]

You must have typed something wrong in the line after sudo gedit.  Just tell gedit to open a new file and go searching in /etc/modprobe.d/ for the aliases file.

---

### Post by BioGene on 2007-01-18
> **zerhacke said:**
> 
You must have typed something wrong in the line after sudo gedit.  Just tell gedit to open a new file and go searching in /etc/modprobe.d/ for the aliases file.

LMAO, I just found out what it was! Instead of writing aliases, I wrote allases! K I just did it going to reboot and tell you if it worked!

EDIT:
Zerhacke you&#341;e awesome it worked! My homepage [Google] loaded up in less than a second! Thanks a lot man! Now I was wondering is there anyway I could teak Linux up so that apps startup faster or just get more RAM! Currently I have 512MB but I was thinking of doubling it!

---

### Post by BioGene on 2007-01-18
> **454redhawk said:**
> Sounds like the DNS problem that many have encountered.

Here is a suggestion.

Ping all 4 of these address, find the fastest 2 and make them your primary and secondary DNS's. 

4.2.2.2 and 4.2.2.1 and 208.67.222.222 and 208.67.220.220


Edit the /etc/resolv.conf file and add your DNS values.

Then apply this
```
sudo chattr +i /etc/resolv.conf
```

That will lock down that file and prevent overwriting.

To unlock it, 

```
sudo chattr -i /etc/resolv.conf
```

This has created much disscussion and would appear to be a bug. It seems alot of people are having a similar problem (myself included). The above is a fix that has worked for me and others.

So if I did this would my Internet speed increase dramatically or nothing would happen?

---

### Post by irish_flu on 2007-01-18
> **zerhacke said:**
> 
I'd disable it across the entire system, which would disable it no matter what window manager you use.  You also wouldn't have to screw with firefox or Konqueror and every other program you use that connects to the network.

To do this:

1. sudo gedit /etc/modprobe.d/aliases (or your preferred text editor)
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off
4. Save the file and reboot

Thanks for this Zerhacke, that made a performance diffence on my box too.

---

### Post by 454redhawk on 2007-01-18
> **BioGene said:**
> So if I did this would my Internet speed increase dramatically or nothing would happen?

If you load a web page and see down at the bottom left "looking for www.some-web-page.com" for more than a second or two you can benefit from this (load a web page faster). Otherwise your current DNS is working fine.

---

### Post by zerhacke on 2007-01-19
> **BioGene said:**
> LMAO, I just found out what it was! Instead of writing aliases, I wrote allases! K I just did it going to reboot and tell you if it worked!

EDIT:
Zerhacke you&#341;e awesome it worked! My homepage [Google] loaded up in less than a second! Thanks a lot man! Now I was wondering is there anyway I could teak Linux up so that apps startup faster or just get more RAM! Currently I have 512MB but I was thinking of doubling it!

Thank you thank you, I'll be here all week.

As far as more RAM goes... well, I run 256MB PC-133 and it's acceptable.  At the 512 mark unless you're running a lot of graphic editing and viewing apps I wouldn't really say more would do you any good, especially if it's faster than PC-133.  All the DDR's are plenty fast for application loads.  What you could look into are faster drives, as most of the lag you get with loading a program anymore is disk access times.

Unless, that is, you're running a really old computer like me.  If you're running something really old, there's no real way to speed it up as the parts that would fit to upgrade your motherboard are not sold anymore.  That's the case with me.

---

### Post by webdr on 2007-01-19
Internet speed rocks :guitar:

After disabling the IPV6 via the /etc/modprobe.d/aliases file.
I sure am glad someone thought to post that fix!

Now if someone can just figure out touch screens, I'll be set!
Any way big props to the folks who share these ideas.

Thanks guys / gals, which ever the case may be.
RacerX

---

