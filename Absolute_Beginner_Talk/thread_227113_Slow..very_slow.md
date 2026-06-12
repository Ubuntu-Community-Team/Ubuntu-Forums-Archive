---
title: "Slow..very slow"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Milis on 2006-08-01
Hi

About yesterday I turned my four year old toshiba sattelite 1800-400 laptop into a xubuntu machine. For four years Windows 2000 and XP were on it. Windows 2000 worked pretty good and in all fairness... for me XP wasn't that bad either... Problem for me was that XP was running slow. But due to cd-rom problems reinstalling windows 2000 was not an option. But recently i found out a way to install linux on the laptop without using the cd. And now.. Xubuntu is running on it. 

Everything works like a charm. And I mean everything. But...is it normal that it runs slower than XP? For example: When I want to check my mails with Thunderbird while surfing with Opera, it takes almost one and a half minute to load Thunderbird. Also, simple progs like an xterm can take up to one minute to load?

Is this normal or should I do something?

Thanks in advance

---

### Post by jethro10 on 2006-08-01
Hi,

How much memory do you have and how big a swap file?

My PC with 256Mb was terribly slow but when I put in 1Gb it now flies.

J

---

### Post by MrHorus on 2006-08-01
```
sudo cpufreq-selector -g performance
```

May help.

It could be that some sort of CPU scaling is activated on your laptop and that command will tell it to run at full throttle.

---

### Post by Christmas on 2006-08-01
I don't know your system's specs, but optimal is a minimum 256 RAM and probably an Intel P4 with at least 1 GHz. I run Kubuntu on my box which has 512 RAM and P4 2800 MHz. 

Xterm - loads in less than a second
Konqueror - less than a second
Firefox - 1-2 seconds
Kopete - 2 seconds
Kate - 2-3 seconds
Konsole - 1 second
Amarok takes about 5-10 seconds until it completely loads a playlist with 1500 melodies

Again, it shouldn't be so slow (1 minute for a mail program?!) but I don't know your system's specs.

---

### Post by PaulFXH on 2006-08-01
Hi
Try this:

Go into Firefox and type about:config in the url box and press Enter
Then type ipv6 in the Filter box in the page that opens.
Right-click on the line network.dns.disbleIPv6 and toggle the Value to True (from false which is the Firefox default).
Check if this has solved your problem.

Paul

---

### Post by Milis on 2006-08-02
Thanks for your response

My laptop specifications are:

Intel® Celeron&#8482; processor, 800 MHz 
128 MB SDRAM standard 
15.0 GB hard disk 

Maybe 128 MB SDRAM is too little

---

### Post by yellowband on 2006-08-02
ya that's probably your problem.  128 is not a whole lot of RAM these days. also, an 800 Mhz celeron is pretty slow as well.

---

### Post by eXisor on 2006-08-02
First off, I suggest you get rid of as many running processes as you can. This link is excellent for that...

[http://ubuntuforums.org/showthread.php?p=487138](http://ubuntuforums.org/showthread.php?p=487138)

Second, investigate the alternatives to the mozilla programs. They are memory hungry. Try swifterfox for browser and gaim for email (I think gaim is what icewm uses).

Third, you can try using IceWm or Fluxbox instead of Xfce. Both are appeciably quicker, but not as feature rich. They also use lighter browser and mail clients which will also work well under Xfce, so you can build your own lighter Xfce in the longer term.

Do a 'top' pr 'ps -e' to see what you have running and uninstall everything you do not need. For instance... Once the system is stable you can disable the syslog and kernel logging via the link above. Consider blacklisting processes you will never need (do this in /etc/modprobe.d/blacklist)

Edit: I run a tolerably slow Xfce on a 233mhz 64mb box with the 686 kernel.

---

### Post by Frem on 2006-08-15
> **eXisor said:**
> Second, investigate the alternatives to the mozilla programs. They are memory hungry. Try swifterfox for browser and gaim for email (I think gaim is what icewm uses).

Third, you can try using IceWm or Fluxbox instead of Xfce. Both are appeciably quicker, but not as feature rich. They also use lighter browser and mail clients which will also work well under Xfce, so you can build your own lighter Xfce in the longer term.

Do a 'top' pr 'ps -e' to see what you have running and uninstall everything you do not need. For instance... Once the system is stable you can disable the syslog and kernel logging via the link above. Consider blacklisting processes you will never need (do this in /etc/modprobe.d/blacklist)

Edit: I run a tolerably slow Xfce on a 233mhz 64mb box with the 686 kernel.
Are you joking? Swiftfox uses the Mozilla rendering core and gaim dosen't have anything to do with email. Opera is a great choice, it's the fastest browser around that won't choke on most sites. It has built in email, so you should get that set up instead of using Thunderbird. It also works great on old systems, I've seen it go with as little as 32mb RAM on an old pII. (It will likely use more RAM on a modern system though, as it scales to make better use of the resources available.)

AreYouTalkingToMe (AYTTM) or the command line Pork make good lightweight AIM clients.

IceWM and Fluxbox are simply window managers. They don't "use" anything by default. Heck, you can run them in Gnome. They are light weight and great choices for old systems, though.

In my experience, you won't notice a huge speed boost, if any, by using the 686 kernel over a 386 one.

---

### Post by Adrian_b on 2006-08-15
> **Frem said:**
> ...
In my experience, you won't notice a huge speed boost, if any, by using the 686 kernel over a 386 one.

I did on my p3.0ghz though..
And also, his computer might be stressed faster to the maximum where that kernel might come in handy.

---

### Post by IYY on 2006-08-15
Something is not right here. I am running Xubuntu on a machine with half your specs and programs like xterm open instantly, and firefox/thunderbird in less than 10 seconds.

I don't know what the problem could be, though.

---

### Post by eXisor on 2006-08-16
@Frem: Yeah, I don't know why I typed 'gaim'. The rest of the advise is solid though.

---

### Post by oss_monkey on 2006-08-16
I run the same specs as you, being on a Satellite laptop myself.

When I installed Xubuntu, I came across this tutorial and it might help.

[Improve performance in Ubuntu]("http://www.ubuntuforums.org/showthread.php?t=189192")

HTH.

---

