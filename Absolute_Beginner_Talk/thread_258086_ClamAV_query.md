---
title: "ClamAV query"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by geezerone on 2006-09-15
Hi

I know there are a good few problems for some people with ClamAV but I have installed it and the daemon and GUI but doesn't appear in the Application menu. How does one place it here and how also do you update the version of app as I have 0.88.2 but command line freshclam command says the latest is .4?

Thanks! :)

---

### Post by Najand on 2006-09-15
Are you managing a server or you have just a desktop?

---

### Post by geezerone on 2006-09-15
Thanks for the prompt response. I am just using it as a desktop machine.

---

### Post by Najand on 2006-09-15
I see... Well, as far as the majority of Viruses are for Windows and Microsoft Applications, usually there is no need for installing a Virus Scanner on a Desktop Linux... There are also Firewalls Ubuntu has that can prevent spywares, etc. 
Anyway, if you really need it, let us see how can we configure it...
Did you install "clamtk", too?

---

### Post by geezerone on 2006-09-15
> **Najand said:**
> I see... Well, as far as the majority of Viruses are for Windows and Microsoft Applications, usually there is no need for installing a Virus Scanner on a Desktop Linux... There are also Firewalls Ubuntu has that can prevent spywares, etc. 
Anyway, if you really need it, let us see how can we configure it...
Did you install "clamtk", too?

I have a dual Windows / Ubuntu boot and have installed Firestarter but now trying to get ClamAV installed. I have installed 'clamtk' from the repositories (Synaptic Manager). I presume that Clam can be configured to autoupdate also with the daemon process, but for now want to access the GUI and try and update the Clam engine?

Thanks

---

### Post by Najand on 2006-09-15
As far as the Windows Partition is a ntfs filesystem, nothing can be written on it, when you are using linux... So if any spyware/virus etc. enter your Linux Machine the possibility to infect your windows partition is almost nothing. 

Can't you start clamav by starting it from a terminal. If you don't know its command use;
```

apropos clam

```
to find it.

---

### Post by geezerone on 2006-09-15
Tried typing apropos clam but the message 'nothing appropriate' appears. Would I have to browse to the directory it is in?

---

### Post by Najand on 2006-09-15
Then locate it using:
"locate clam"
it is usually in "/usr/bin"

---

### Post by xpod on 2006-09-15
If i remember correctly i had to use the alcarte menu editor to make it show up when i got it on my last install..not bothered getting it this time.
Or mabey it was the "debian menu".....cant mind which but i had to use both for getting a lot of stuff to show up in a menu

---

### Post by Najand on 2006-09-15
Maybe I should install calmav to help you... And uninstall it later.

---

### Post by geezerone on 2006-09-15
If it type 'clamtk' it opens the GUI now thanks but how do I add this to the applications menu as an icon and would firestarter be loaded automatically as not shown in system tasks?

---

### Post by RoyArne on 2006-09-15
The program is *clamscan*, located in

**/usr/bin/clamscan**

There is a GUI frontend to clamscan called avscan, named

**/usr/bin/avscan**

Note that you need to install avscan separately,

**sudo apt-get install avscan**

should do the trick. Alternatively, you can use the Synaptic Package Manager.

avscan is not placed in the menu, but you can add programs to the applications menu with the *Alacarte Menu Editor*:

Applications->Accessories->Alacarte Menu Editor

---

### Post by Brunellus on 2006-09-15
ClamAV is really not necessary for your Linux partition--Windows can't even access that partition, so even if a windows virus lived there, it wouldn't be able to infect the windows host.

For "shared" fat32 partitions, well, maybe.  sure. 

But the only reason I see for running ClamAV under Linux would be if the Linux box were a mailserver relaying mail to Windows users.

---

### Post by geezerone on 2006-09-15
> **RoyArne said:**
> The program is *clamscan*, located in

**/usr/bin/clamscan**

There is a GUI frontend to clamscan called avscan, named

**/usr/bin/avscan**

Note that you need to install avscan separately,

**sudo apt-get install avscan**

should do the trick. Alternatively, you can use the Synaptic Package Manager.

avscan is not placed in the menu, but you can add programs to the applications menu with the *Alacarte Menu Editor*:

Applications->Accessories->Alacarte Menu Editor

Thanks, have installed that and created menu item for AvScan which have to run as Root to update. 

Does Firestarter run when Linux starts as the system monitor isn't showing it unless manually started?

---

### Post by Najand on 2006-09-15
DDo you know ehy they call them Viruses; because they  cannot be  alive in the system they are designed for. So be sure there won't be any harm from viruses to your linux box/Windows and even fat32 shared partitions, because there are very few viruses that can be alive in Linux Environment. Also the viruses that are designed for Linux are ones always attack Web Servers/Mail Servers and they don't usually harm desktop computers.

---

### Post by RoyArne on 2006-09-15
According to [http://www.fs-security.com/docs/faq.php#reboot]("http://www.fs-security.com/docs/faq.php#reboot"), you can use:

**sudo /etc/init.d/firestarter status**

to find out whether it is running or not. I think it starts automatically, but I'm not sure. Don't know much about this.

---

