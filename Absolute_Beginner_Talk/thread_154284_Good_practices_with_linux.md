---
title: "Good practices with linux?"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by Blazeix on 2006-04-02
Hi. I am dual booting linux\windows XP, and in windows there is a whole slew of things you need to do for basic system maintenance (firewall, virus protection, spyware protection, defrag, etc). I know that linux is less targeted than windows. I haven't seen a defragmenter in linux, so do I need to do defrag? can someone enlighten me on basic linux maintenance? I've read the starter guide and I'm doing most of the things in it already.
[http://ubuntuguide.org/#basicsecuringubuntu](http://ubuntuguide.org/#basicsecuringubuntu).

Thanks

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=Blazeix]Hi. I am dual booting linux\windows XP, and in windows there is a whole slew of things you need to do for basic system maintenance (firewall, virus protection, spyware protection, defrag, etc). I know that linux is less targeted than windows. I haven't seen a defragmenter in linux, so do I need to do defrag? can someone enlighten me on basic linux maintenance? I've read the starter guide and I'm doing most of the things in it already.
[http://ubuntuguide.org/#basicsecuringubuntu](http://ubuntuguide.org/#basicsecuringubuntu).

Thanks[/QUOTE]
You don't need to defrag, clean the registry, virus protection, or scan for spyware. Linux has a built in firewall for extra protection too. For maintenance, check tutorials under the How To section.

---

### Post by NeghVar on 2006-04-02
defrag doesnt need to be done since linux uses a hd more efficiently.

spyware doesnt exist... its all just a ms based conspiracy eh...

u should probably get a virtus scanner so u dont accidently transmit a virus to yr windows or afriends

and if u dont have a router a firewall is a good idea

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=NeghVar]defrag doesnt need to be done since linux uses a hd more efficiently.

spyware doesnt exist... its all just a ms based conspiracy eh...

u should probably get a virtus scanner so u dont accidently transmit a virus to yr windows or afriends

and if u dont have a router a firewall is a good idea[/QUOTE]
Ubuntu has a built in firewall....it's called iptables.

---

### Post by nealklomp on 2006-04-02
yeah you know how you'll be surfing in windows and suddenly the hard drive will start doing somthing and you don't know why?
that never ever happens in linux.
never ever.
Unless you sign in as the Root or Su you can't be hacked.

Windows will be out of date one day.

---

### Post by NeghVar on 2006-04-02
> Unless you sign in as the Root or Su you can't be hacked.

That is incorrect, you can be hacked the same as in root, the damage that can be inflicted is MUCH less but it can still happen.

---

### Post by Blazeix on 2006-04-02
Wow. Those were some quick responses!
The guide i'm using talks about the firewall [firestarter](http://ubuntuguide.org/#firestarter), but it never talks about whether not its needed or mentions iptable. linux is slowly becoming more popular, so eventually I suppose it will become targed more. Does anyone here use firestarter?

---

### Post by xXx 0wn3d xXx on 2006-04-02
Firestarter is _NOT_ a firewall. It is a gui frontend for iptables. I really hate it when people call firestarter a firewall. You don't need firestarter. Even if someone gets acess to your system, what are they going to do, lol. I used to use firestarter but what use is it if I don't have a root account, linux has almost no viruses, no spyware, and you already have a firewall ?

---

### Post by NeghVar on 2006-04-02
firestarted is a graphical frontend of iptables, in otherwords iptables works int he bakround and can be configured via command line but firestarter makes it all pretty like with a nice gui

---

### Post by Blazeix on 2006-04-02
[QUOTE=MasterChief1234]Firestarter is _NOT_ a firewall. It is a gui frontend for iptables. I really hate it when people call firestarter a firewall. You don't need firestarter. Even if someone gets acess to your system, what are they going to do, lol. I used to use firestarter but what use is it if I don't have a root account, linux has almost no viruses, no spyware, and you already have a firewall ?[/QUOTE]

Sorry, the guide that i'm using implies its a firewall. So basically firestarter is to iptables as synaptic is to apt-get.

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=Blazeix]Sorry, the guide that i'm using implies its a firewall. So basically firestarter is to iptables as synaptic is to apt-get.[/QUOTE]
Basically. One gives more options but it is also not needed ;)

---

### Post by John.Michael.Kane on 2006-04-02
those who wish to edit iptables manually [http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)
[http://www.linuxguruz.com/iptables/howto/](http://www.linuxguruz.com/iptables/howto/)
[http://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO.html](http://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO.html)

---

### Post by dcstar on 2006-04-02
[QUOTE=NeghVar]firestarted is a graphical frontend of iptables, in otherwords iptables works int he bakround and can be configured via command line but firestarter makes it all pretty like with a nice gui[/QUOTE]
A "Firewall" in the Windows world is a necessary protection against the various Scumware that can get into a Windows environment by exploiting the many, many vulnerabilities that these things target.

A "Firewall" in the Linux world is sometimes handy if you expose your system to the outside world through direct IP exposure, but isn't much use otherwise to the significant difference in inherent security and level of threat.

If you connect to the Internet through NAT and don't forward ports, you don't really need a Linux firewall.

---

