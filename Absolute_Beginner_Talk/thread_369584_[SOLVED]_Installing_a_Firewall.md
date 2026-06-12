---
title: "[SOLVED] Installing a Firewall"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-02-24
I attempted to install a firewall using 
sudo aptitude install firestarter, however, I received an error saying that it couldn't find any package called firestarter. Can someone help me with this?

---

### Post by Maestro23 on 2007-02-24
> **noorez said:**
> I attempted to install a firewall using 
sudo aptitude install firestarter, however, I received an error saying that it couldn't find any package called firestarter. Can someone help me with this?

You need to enable extra repositories.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

or the GUI way:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then try again either thru command line or chrome307's way.

---

### Post by chrome307 on 2007-02-24
I did it this way:

System - Administration - Synaptic Package Manager

Once you have the dialog box up, SEARCH (top right) and enter Firestarter
it will locate it for you and then select it to install.

Once you have set it up it should look like this

[IMG]http://1pix.org/out.php/i532_Untitled.png[/IMG]

---

### Post by overdrank on 2007-02-24
> **noorez said:**
> I attempted to install a firewall using 
sudo aptitude install firestarter, however, I received an error saying that it couldn't find any package called firestarter. Can someone help me with this?

What verson are you using 6.06, 610? Do you have all your repositories enabled? The repositories are under settings, Synaptic manager if you are using 6.06.

---

### Post by Platinum89 on 2007-02-25
Using 6.06 here and all repositories for 6.06(except for the last one as it gives an error that it cannot be found) are highlighted. Using the search function also came up with no results for Firestarter. Was the program for lower versions or was it dropped for some reason?:confused:

---

### Post by oilchangeguy on 2007-02-25
ubuntu comes with a firewall already installed. firestarter is just a control panel (not needed)  that allows you to configure the firewall

---

### Post by freesitebuilder on 2007-02-25
So if we don't install the control panel, how does Ubuntu firewall know what's OK and what isn't? 

Can you tell I'm more used to Windows? :)

---

### Post by John.Michael.Kane on 2007-02-25
Those of you who want to edit iptables by hand. You may want to look at this.
[http://www.ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://www.ubuntuforums.org/showthread.php?t=159661&highlight=iptables)

---

### Post by chrome307 on 2007-02-25
Is Firestarter running all the time ??

As I tend to use 

[LIST]
[*]System
[*]Administration
[*]Firestarter
[/LIST]

to load up the GUI and see the icon in my Panel bar

Is this not necessary ???

---

### Post by oilchangeguy on 2007-02-25
while no os is totally immune from getting a virus. linux comes close. remember even thou xp comes in 3 flavers, home, pro, and media center. it's still xp, and the idiots who write viruses have it easy because they only have one os to pick on. with linux there are many versions. and if a virus did manage to get into ubuntu from what i've read you would have to enter your admin password for it to be able to run. i have 2 computers running a diffrent version of linux, ubuntu 6.06 on one and xandros 3.0 oce on the other. and no virus or spyware protection on either. never had a problem. not even sure if xandros has a built in firewall or not.

---

### Post by chrome307 on 2007-02-25
As true as it  may be that M$ is targeted more ............. I was also under the impression that Apache Web Servers are a legitimate target for these groups/individuals.  

The benefit of these attacks usually mean that the person(s) could end up with a commerical shell with a lot of bandwith to play around with.

---

### Post by skiddly on 2007-02-25
[SIZE="5"][/SIZE][COLOR="Blue"][/COLOR]Hi i had the same reservations as yourself and installed firestarter but kept getting messages saying pc had been hit by other ips but enquired in forums and was assured all is safe as long as nothing has asked for password or you have not opened a hole whatever that means anyway all seems well at pres everyone i ask assures linux is safe and secure but nothing in life is guarenteed 100% other than death so dont worry be happy:guitar: linux rocks

---

### Post by Platinum89 on 2007-02-25
> **SD-Plissken said:**
> Those of you who want to edit iptables by hand. You may want to look at this.
[http://www.ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://www.ubuntuforums.org/showthread.php?t=159661&highlight=iptables)

Wouldn't a control panel be easier for those who are new to this?:-k

---

### Post by RedSquirrel on 2007-02-25
> **chrome307 said:**
> Is Firestarter running all the time ??

As I tend to use 
[LIST]
[*]System
[*]Administration
[*]Firestarter[/LIST]
to load up the GUI and see the icon in my Panel bar

Is this not necessary ???

Not necessary. The GUI just allows you to easily watch what's going on (and have a nice decoration on your panel!).

---

### Post by RedSquirrel on 2007-02-25
> **Platinum89 said:**
> Wouldn't a control panel be easier for those who are new to this?:-k

Yes and no. Everyone's different. Even people who are "new to this" might want a solution that doesn't involve installing extra stuff. That's one of the great things about linux: OPTIONS!

---

