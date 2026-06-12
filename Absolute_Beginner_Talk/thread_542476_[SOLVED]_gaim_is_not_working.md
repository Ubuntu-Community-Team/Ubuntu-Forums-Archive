---
title: "[SOLVED] gaim is not working"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by arai on 2007-09-04
gaim is not working (ubuntu 6.10). can anybody help.

---

### Post by finer recliner on 2007-09-04
upgrade to the latest version of pidgin

(gaim was renamed to pidgin when v2.0 was released)

---

### Post by arai on 2007-09-04
> upgrade to the latest version of pidgin

How to do that ? 

[I use 6.10 Edgy]

---

### Post by niceguy123 on 2007-09-04
> **arai said:**
> How to do that ?

I installed Pidgin, but I can't figure out how to find/run it?

---

### Post by arai on 2007-09-04
How to install Pidgin? 

Should I first uninstall Gaim ? Or just download Pidgin ?

---

### Post by niceguy123 on 2007-09-04
> **arai said:**
> How to install Pidgin? 

Should I first uninstall Gaim ? Or just download Pidgin ?

I followed[ this]("https://help.ubuntu.com/community/InstallPidgin2%2e0?highlight=%28pidgin%29#head-718cafbd56c6fde04b38647247dfafef01c5aa92").

But after I finished installing, I can't figure out how to run it or how to get in in the menu bar.

---

### Post by Tiger-Smith on 2007-09-04
Have a look at this [**link**]("http://www.ubuntugeek.com/install-pidgin-instant-messanger-in-ubuntu.html")

---

### Post by niceguy123 on 2007-09-04
> **Tiger-Smith said:**
> Have a look at this [**link**]("http://www.ubuntugeek.com/install-pidgin-instant-messanger-in-ubuntu.html")

Thanks for the link.

> #  cheryl Says:
June 20th, 2007 at 10:57 pm

you can press ALT + F2 and type pidgin


I tried that and got

> Could not open location 'file:///pidgin'

The location or file could not be found.

What have I done wrong and what should I do now?

---

### Post by [Alsharifi] on 2007-09-04
pretty much its saying its not installed

the easyest way to install it is.

remove gaim from synaptic package manager.

then ..

in terminal type 

```
sudo gedit /etc/apt/sources.list
```

then add these to the bottom 

```
deb http://falcon.landure.fr feisty pidgin
deb-src  http://falcon.landure.fr feisty pidgin
```


SAVE and exit

then in terminal 

```
sudo apt-get update 
sudo apt-get install pidgin
```

and u should be set


thats what worked for me :D


i read this somewere else u might want to do it before u restart 

```
One correction - after doing desctribed steps you must REINSTALL the following packages:

gdm (2.18.1-0ubuntu1)
gnome-bin (1.4.2-35)
gnome-core (1:2.14.3.3ubuntu1)
gnome-desktop-environment (1:2.14.3.3ubuntu1)
gnome-libs-data (1.4.2-35)

if you want to load into GNOME 
```

---

### Post by niceguy123 on 2007-09-04
> **'[Alsharifi] said:**
> pretty much its saying its not installed

the easyest way to install it is.

remove gaim from synaptic package manager.

then ..

in terminal type 

```
sudo gedit /etc/apt/sources.list
```

then add these to the bottom 

```
deb http://falcon.landure.fr feisty pidgin
deb-src  http://falcon.landure.fr feisty pidgin
```


SAVE and exit

then in terminal 

```
sudo apt-get update 
sudo apt-get install pidgin
```

Did that and got this message:

[QUOTE]W: GPG error: [http://falcon.landure.fr](http://falcon.landure.fr) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1CA3E3239FA7DC39
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

..

---

### Post by niceguy123 on 2007-09-04
Did this too. Still no change.

> 
i read this somewere else u might want to do it before u restart 

```
One correction - after doing desctribed steps you must REINSTALL the following packages:

gdm (2.18.1-0ubuntu1)
gnome-bin (1.4.2-35)
gnome-core (1:2.14.3.3ubuntu1)
gnome-desktop-environment (1:2.14.3.3ubuntu1)
gnome-libs-data (1.4.2-35)

if you want to load into GNOME 
```



---

### Post by Kitsun on 2007-09-04
Another way of installing Pidgin would be downloading it from getdeb.net ([http://www.getdeb.net/release.php?id=1307](http://www.getdeb.net/release.php?id=1307)).

It is better to install from a repository however.

---

### Post by niceguy123 on 2007-09-04
> **Kitsun said:**
> Another way of installing Pidgin would be downloading it from getdeb.net ([http://www.getdeb.net/release.php?id=1307](http://www.getdeb.net/release.php?id=1307)).

It is better to install from a repository however.
Is that just another place to download the same? That doesn't seem to be the problem. I think that I followed all of the above directions and I don't see pidgin on my system. Maybe it just because I'm new at this and I'm skipping something that old timers don't even think needs to be mentioned.

Any ideas?

---

### Post by jw5801 on 2007-09-04
It makes no difference if you install from a repository or from a .deb file: they are effectively the same thing. debs are what you download from the repositories and apt-get simply calls "dpkg" to install them. The only difference is that if it's not a repository package then you won't know when it's updated.

The error you got on the previous page was because you had another package manager open when you tried to call apt-get from the command line. So if you make sure you don't have another open then it should work. I installed from the .deb which is generally easier than adding extra repositories though.

Download the pidgin and pidgin-data .deb files from the link given above and save them to your desktop then open a terminal and copy and paste the following:
```
cd ~/Desktop
sudo dpkg -i pidgin*

```

Given that you've already added the repository though, just install it from that: close Update Manager, Package Manager and anything else similar that you have open, open up a terminal and input:
```
sudo apt-get install pidgin
```and you should be right.

---

### Post by [Alsharifi] on 2007-09-04
well i uninstalled pidgin and did it again following my directions just to see whats up,and i got the same error that u reported,but i went ahead and ran

```
sudo apt-get install pidgin
```

and pidgin install correctly,and works just fine!

---

### Post by jw5801 on 2007-09-04
By the way, Pidgin will be under Applications > Internet > Pidgin, just like where Gaim was. Alternatively you can run it simply by typing pidgin into a terminal. This is useful if it's not working properly and you want to see any errors that it might be outputting.

What happened when you tried to run gaim before anyway?

---

### Post by nikef on 2007-09-04
i tried to uninstall gaim
but it said if i uninstalled it i would also uninstall ubuntu :confused:

---

### Post by ralyon on 2007-09-04
It says to uninstall ubuntu-desktop which is an empty package used to easily install the desktop environment by having all the default programs for gnome as dependencies. Since gaim is one of the default packages it no longer meets the dependencies for the ubuntu-desktop which is why it asks to to remove it as well, this is normal.

Long story short, its ok to remove because its not an actual program.

Also, from the list of recommended reinstall, the only one that was installed was gdm. None of the listed gnome packages were installed (and yes I am using gnome). I reinstalled gdm to be safe and rebooted with no problems and pidgin is working fine.

Now if only I can figure out how to get the yahoo chat rooms working.... :???:

ralyon

---

### Post by arai on 2007-09-04
i have the built in gaim client that comes with ubuntu (edgy 6.10). i tried to connect with google talk so many time and it is not connecting. i don't know why.

---

### Post by belaflek on 2007-09-04
Am I correct in that it still will not work behind an ISA firewall? At least the yahoo part never has and still isnt

---

### Post by arai on 2007-09-04
so what to do now? use the already existing gaim or do i need to download & install pgdin?

[COLOR="Red"]Update[/COLOR] : Gaim working [this helped]("http://ubuntuforums.org/showthread.php?t=125185").

---

### Post by nikef on 2007-09-04
> **ralyon said:**
> It says to uninstall ubuntu-desktop which is an empty package used to easily install the desktop environment by having all the default programs for gnome as dependencies. Since gaim is one of the default packages it no longer meets the dependencies for the ubuntu-desktop which is why it asks to to remove it as well, this is normal.

Long story short, its ok to remove because its not an actual program.

Also, from the list of recommended reinstall, the only one that was installed was gdm. None of the listed gnome packages were installed (and yes I am using gnome). I reinstalled gdm to be safe and rebooted with no problems and pidgin is working fine.

Now if only I can figure out how to get the yahoo chat rooms working.... :???:

ralyon

thanks for this info
so its ok to uninstall
also it reports on removing nautilu-sendto is this also safe to remove

---

### Post by ralyon on 2007-09-04
The only thing that I see you will loose is the option to select a file and tell it to send to mail recipient or file transfer to someone in gaim from nautilus. Since it only works with evolution mail anyway and I use thunderbird I didn't think I would miss it.

ralyon

---

### Post by nikef on 2007-09-04
thank you very much
i use kmail for my emailing any way so i wont be missing it either :)
off to unistall gaim now

many thanks  :)

---

### Post by niceguy123 on 2007-09-04
Given that you've already added the repository though, just install it from that: close Update Manager, Package Manager and anything else similar that you have open, open up a terminal and input:
```
sudo apt-get install pidgin
```and you should be right.[/QUOTE]

jw5801,

Thanks, Its working fine now. :)

---

### Post by [Alsharifi] on 2007-09-04
glad it worked for you.

---

### Post by nikef on 2007-09-05
> **'[Alsharifi] said:**
> pretty much its saying its not installed

the easyest way to install it is.

remove gaim from synaptic package manager.

then ..

in terminal type 

```
sudo gedit /etc/apt/sources.list
```

then add these to the bottom 

```
deb http://falcon.landure.fr feisty pidgin
deb-src  http://falcon.landure.fr feisty pidgin
```


SAVE and exit

then in terminal 

```
sudo apt-get update 
sudo apt-get install pidgin
```

and u should be set


thats what worked for me :D


i read this somewere else u might want to do it before u restart 

```
One correction - after doing desctribed steps you must REINSTALL the following packages:

gdm (2.18.1-0ubuntu1)
gnome-bin (1.4.2-35)
gnome-core (1:2.14.3.3ubuntu1)
gnome-desktop-environment (1:2.14.3.3ubuntu1)
gnome-libs-data (1.4.2-35)

if you want to load into GNOME 
```

just to thank you
i now have pidgin installed,gaim unistalled
and re installed the gnome packages  :)
thanks that's another problem solved today  :lolflag: i am on a roll today,now lets see what else i can fix  :)

---

### Post by Tiger-Smith on 2007-09-10
You need the security key for that paticular repo, ask for the error below that close all app managers you have open, also close any update software that you might have open Ie, update-manager or synpatic, then once done follow that link and follow the steps shown, should work.

---

