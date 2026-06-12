---
title: "Firewall and Anti-Virus"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Maxwell Smart on 2007-07-03
Being new to Linux I have googled about installing anti-virus and firewalls with ubuntu and get many varied comments.  I would not be without either (including spyware programs)  in the windows OS.  I know there must be many experienced long term users who have browsed the web using Ubuntu and other linux programs that could tell me for certain if using a firewall and some anti-virus program is required in linux systems.

Some reasoning behind the suggestion would also be appreciated.  Thanks.

---

### Post by dpar on 2007-07-03
Not really needed in Linux, but they are available if your paranoid.

---

### Post by Megaqwerty on 2007-07-03
There has only been one virus for Linux that I've heard of, and it was a very long time ago. Ubuntu already has a firewall called iptables, but if you want a graphical firewall, you can get firestarter ```
sudo aptitude install firestarter
``` You won't need anti-spyware, and if you want to scan your computer for viruses that would affect windows, (in case you are sharing files with Windows computer, you can install clamav.

---

### Post by dpar on 2007-07-03
Also, heres a good read on security in linux.......[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by gerrymoth on 2007-07-03
As a new user to Linux (Started in Jan 2007) this was one area I just couldn't get my head around after years of Windows security prevention (ZoneAlarm, Avast Anti-Virus, Spybot, SpyBlaster, SpyGaurd, etc..). 
I installed firestarter when I first started using Ubuntu Fiesty, installed the Linux version of Avast as I share files with friends and installed chkrootkit as I've not got over they Windows paranoia yet.
With Firestarter on the only times I've seen it show attacks is when I'm running Ktorrent, but you would expect that cos its a sharing app, but the firewall has blocked it so why worry.
What you need to remember with linux is that you start with everything blocked and its only you who can allow others access, so I always try to install only from the ubuntu repositories and will not allow any remote access to the PC. As recommended read [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Malibu Illusion on 2007-07-03
It's worth noting that Firestarter itself is not a firewall, it is merely a graphical frontend to the firewall that is already operating by default within Linux called iptables; you're already protected right out of the box.  

Linux also doesn't have any services listening on ports unless you set them up to do so, unlike other operating systems that have a number of potentially insecure services listening for connections by default.  You're only as secure as the daemons that you have configured listening to the outside network and, if there are none, then you don't have much to worry about to begin with.

In regards to anti-virus, spyware and whatnot, they're just not needed with Linux.  There's basically no in-the-wild viruses or malware for the OS and if their was it'd be severely limited in what it could do as it would only have user priveleges.  Unfortunately, other operating systems are not as secure in this area as they encourage users to be perpetually logged in as an administrator, which is bad computing practice as this means that any program executed by the user, including malware, will have free reign over the entire system making it faily easy for applications to do some severe damage.  Always be careful of what you're doing as a root user.

The only time anti-virus solutions are used by Linux users, typically, is when they're being used as mailservers and will be forwarding on messages to machines using other operating systems; this allows the filtering of potentially unsafe attachments before they're able to infect these boxes.

Take care.

---

### Post by Maxwell Smart on 2007-07-03
Thanks for all the info.  Just for now I would prefer to be cautious (old windows hang up) and use a firewall and anti-virus.  I have installed firestarter and understand it is only a GUI for the already installed iptables.

As for anti-virus, I installed Aegis for the add/remove section and it went alright but there is no option to select it from the accessories, applications etc.  Can anyone tell me where it is or how I cna manually activate it.

Also I installed Rkhunter and chkrootkit but these also do not show up as a 'program' where I can manually use them.  Is this normal.  I will get used to it but for now I have to ask a lot of questions so please bear with. 

Finally, does the anti-vrius update or is it just for known linux virus's.  

Thanks all

---

### Post by lisati on 2007-07-03
The Linux version of Firefox, like the Windows version, has an option to "clear private data" like cookies and other stuff. You can find it on the "tools" menu of Firefox.

---

### Post by HotShotDJ on 2007-07-03
Just to let you know... I've been running Linux for over 5 years as my primary OS (actually, my ONLY OS for most of that time) without any Anti-Virus software.  Linux is secure by default.  No matter HOW popular Linux gets, viruses just will not be a problem.  For a good primer on why this is true, see [HERE]("http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses") and also [HERE]("http://librenix.com/?inode=21").

---

### Post by Megaqwerty on 2007-07-03
> **Maxwell Smart said:**
> Thanks for all the info.  Just for now I would prefer to be cautious (old windows hang up) and use a firewall and anti-virus.  I have installed firestarter and understand it is only a GUI for the already installed iptables.

As for anti-virus, I installed Aegis for the add/remove section and it went alright but there is no option to select it from the accessories, applications etc.  Can anyone tell me where it is or how I cna manually activate it.

Also I installed Rkhunter and chkrootkit but these also do not show up as a 'program' where I can manually use them.  Is this normal.  I will get used to it but for now I have to ask a lot of questions so please bear with. 

Finally, does the anti-vrius update or is it just for known linux virus's.  

Thanks all

Seeing as these programs do not get entries in the menus, I can pretty safely assume that they are commandline programs. To run them, you need to open a terminal **Applications>Accessories>Terminal** and enter the name of the program, followed by pressing enter. Normally, this will either execute the program, or show you a list of parameters you can add to a program '-v' for example. To learn more about the program and how to use it, run: ```
man program-name
``` replacing 'program-name' with the name of the program you want to read the manual for.

Hope that helps,

Megaqwerty

---

### Post by kevinlw on 2007-07-10
Greetings,

I'm trying out Ubuntu 6.06 64-bit, have installed it last night, downloaded Firestarter bu twas not able to install it.  I've tried the RPM files but my app manager can't read it so I've now got the tar ball version.  I'm old time windows user so looking at the firestarter files doesn't make any sense to me.

I need some guiding in installing firestarter and avast... i know, I know, Linux doesn't need these but I don't want to get complacent as Linux is very rare in my neck of the world.

Advanced Thanks for your advices, gurus ;-)

regards,
kevin

---

### Post by Outrunner on 2007-07-10
> **kevinlw said:**
> Greetings,

I'm trying out Ubuntu 6.06 64-bit, have installed it last night, downloaded Firestarter bu twas not able to install it.  I've tried the RPM files but my app manager can't read it so I've now got the tar ball version.  I'm old time windows user so looking at the firestarter files doesn't make any sense to me.

I need some guiding in installing firestarter and avast... i know, I know, Linux doesn't need these but I don't want to get complacent as Linux is very rare in my neck of the world.

Advanced Thanks for your advices, gurus ;-)

regards,
kevin

```
sudo aptitude install firestarter
```

Download avast from [here]("http://www.avast.com/eng/avast-for-linux-workstation.html") - make sure you get the .deb

```
sudo dpkg -i avast*.deb
```

---

