---
title: "Absolute Linux NEWBY - Firewall &amp; AV Help"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by jrfoleyjr on 2005-12-28
My install of Ubuntu went like a dream. I had previously beat my head against the wall trying to install SUSE 9.1 and 10. Neither worked as advertized. Ubuntu installed and came up the first try. I hooked it to my home network (behind a router) and used the Firefox browser, OK! 
I am NOT a computer newby. I have used the Commodore Amiga, Windows 95, 98, 2000, and XP for a long time and am currently on XP Pro with my own Apache 2.0 web server and blog using ThingaMaBlog. I am familiar with networking in the Windows environment and have a 5 computer system in my home network, mixed ethernet and wireless (with WEP minimum security). A hotspot wardriver would have to drive half way up my driveway to get a signal anyway.

My linux box will be offline until I can find out how to enable a firewall and some sort of antivirus. 

Also is there a way to switch to the KDE desktop? Or do  I have to reinstall a different version of Ubuntu? 

Someone point me to the FAQs please!!!

---

### Post by jamesford on 2005-12-28
install kubuntu-desktop for kde i think
firewall, get firestarter
both the above u get in synaptic

u probably wont need an antivirus but there might be some info in the links below

the faq/guides i use are
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)
[http://help.ubuntu.com/starterguide/C/index.html](http://help.ubuntu.com/starterguide/C/index.html)

---

### Post by piedamaro on 2005-12-28
For a personal firewall you need to install "firestarter". The AV on linux is usually used on mail servers to scan for windows virus, don't know if a "norton" like antivirus exists for linux yet, don't think so.

Here you are:
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)
[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

Also search the forums! ;)

---

### Post by jrfoleyjr on 2005-12-28
[QUOTE=jamesford]install kubuntu-desktop for kde i think
firewall, get firestarter
both the above u get in synaptic

u probably wont need an antivirus but there might be some info in the links below

the faq/guides i use are
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)
[http://help.ubuntu.com/starterguide/C/index.html](http://help.ubuntu.com/starterguide/C/index.html)[/QUOTE]

Wow...thanks for the quick reply. In the windows world I am used to getting a dozen troll replies before anyone makes a serious attempt to answer.
I will look for Firestarter and check out the links listed above.
Thanks again, Jim :cool:

---

### Post by prizrak on 2005-12-30
If you want an A/V there is Clam for Linux I believe it's in repos, you won't need it as Linux doesn't get the random worms Windows does :)

---

### Post by sapo on 2005-12-30
You dont need any antivirus for linux, you just need one if you want to protect your windows pcs, so you install an antivirus in a server.

And the firewall:

```
sudo apt-get install firestarter
```

them search for it in the menus ;)

---

### Post by Suger on 2005-12-30
Well, it's not impossible to have a virus in Linux, and with the market share of non windows systems growing, it might happen (remember that Firefox had a *nix only security flaw last september). So I would recommend to install clamav, even if it's for the moment of no use.

---

### Post by randlieb on 2006-01-01
i have clamav installed on breezy and ran a scan. it shows 9 viruses found but no indication of what it did with them. any way to find out?

i dual boot with breezy kubuntu...no windows any longer on my hard drive.

---

### Post by anil_robo on 2006-01-01
See these links:
Spyware cleaners for linux: [http://www.ubuntuforums.org/showthread.php?t=108756](http://www.ubuntuforums.org/showthread.php?t=108756)
Does Linux need antivirus and firewall?
[http://www.ubuntuforums.org/showthread.php?t=107634](http://www.ubuntuforums.org/showthread.php?t=107634)

---

### Post by anil_robo on 2006-01-01
[quote=randlieb]i have clamav installed on breezy and ran a scan. it shows 9 viruses found but no indication of what it did with them. any way to find out?[/quote]
Clamav includes five "test files" to check its proper functioning. The other four files you got could be something else! Please check what the files were, and if possible try to send them to yourself as email attachments on yahoo or gmail because they'll check the attachments for viruses and let you know.

Most likely they'll be windows viruses and you don't need to worry about them. But you still would like to clear those viruses because those files could accidentally be sent to windows users, where they'll cause infection.

---

