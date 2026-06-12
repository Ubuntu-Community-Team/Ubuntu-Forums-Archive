---
title: "Things to not do again."
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by huzzak on 2007-03-29
So, I tried to install the Cairo-dock using the guide at [<this website>]("http://www.macewan.org/2007/01/11/how-to-install-cairo-dock-on-ubuntu-edgy/").  It didn't work, so I thought, no worries, I'll just undo what I've done did.  I inverted where I had gotten to and ran this line: sudo apt-get remove librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev.  I realized a little bit late that instead of just removing Cairo it was also removing Nautilus, Desktop and a couple of other things I can't remember before I hit <ctrl-c>.  Now I can only get a command line prompt.

Is there a way to undo my trying to undo what I did without having to reinstall Ubuntu completely?  Please say yes.  Also, follow that yes with detailed descriptions of how.  Thanks.

---

### Post by zekopeko on 2007-03-29
try running in comand line this:

sudo apt-get install ubuntu-desktop

that should install the missing things. if i'm wrong please correct me.

---

### Post by charles.g.moore on 2007-03-29
> **zekopeko said:**
> try running in comand line this:

sudo apt-get install ubuntu-desktop

that should install the missing things. if i'm wrong please correct me.

Sounds right to me...

---

### Post by huzzak on 2007-03-29
It needs to access the internet ... is there a way to do that from the terminal?  I've only got my wifi right now, but can get ethernet when I get home.

---

### Post by dannyboy79 on 2007-03-29
I always suggest before running any aptitude remove or apt-get uninstall or whatever, use the -s option which is like a dry run, it'll show what it would do, you can read the terminal where it'll tell you what it's going to remove and what not. Or you can make sure always run aptitude interactively using the -P option, which will always prompt whether you really want to do this. You can set this within the /etc/apt/apt.conf, just add this so it'll always be liek this without even having to use hte -P option.

Aptitude::CmdLine::"Always-Prompt";


As far as undoing waht you did, what the other person has suggested sounds right to me. It's always a good idea to have a backup of everything daily, then you could simply restore it. good luck

---

### Post by huzzak on 2007-03-29
Thanks for the suggestions.  I'll definitely do the backup daily once I get myself out of the mire I am currently in.  It seems the safest option for a novice likely to break things often.  When I try to run the suggested code it attempts to fetch things off the internet, but I don't know how to connect from the command line.  Is there a way to?

---

### Post by houstonbofh on 2007-03-29
It needs to get the files somehow.  You could use the CD, but older versions will be a problem.  A net connection is the best way.

PS:  More posts while I was posting... :)
Just plug it in.  Ethernet will come up.  WiFi with no X can be tougher depending on on how you are doing wireless.  What card and driver are you using?

---

### Post by huzzak on 2007-03-29
I have an intel card, but I'm not sure about the driver.  I'll plug it in as soon as I can find a stray cable.  Seriously, thanks a ton for all the help.

---

### Post by mannequin on 2007-03-29
> **huzzak said:**
> When I try to run the suggested code it attempts to fetch things off the internet, but I don't know how to connect from the command line.  Is there a way to?

Do you have a cable to connect your computer to the network? Does your network automatically assign you an IP address (using DHCP)?

If you answered 'yes' to both of these, connect your computer to the network via a cable, then type:
```
sudo dhclient
```If it's successful, then you _should_ have access to the internet via your network. Try the suggested code again. :)

HTH!
-M.

---

### Post by dannyboy79 on 2007-03-29
well I beleive that all you're missing is the x-server. So just tell us if this returns anything.

sudo ifconfig -a

if it returns your ip address than you'll still be able to install anything thru aptitude. just type in 

sudo aptitude install ubuntu-desktop

then after this finishes, try to type in 

start x

or is it

startx

this should start your x-server if it's working. If that doesn't start the xserver or say you don't even have internet access, try to add the cd-rom to your /etc/apt/sources.list by using this command:

sudo apt-cdrom add

then it should ask for the cd, pop in your live cd and it should do the rest. once this is done, simply do

sudo aptitude update && sudo aptitude upgrade

sudo aptitude install ubuntu-desktop

then 

also maybe do this since we really don't knwo if your problem is related the x-server crashing.

sudo dpkg-reconfigure xserver-xorg
(NOTE: just pick most all the defaults for answers you don't know what to pick and you'll be fine)

maybe restart the machine and see if that gets you into your x-server and gdm (login in gui)  good luck

---

### Post by huzzak on 2007-03-29
So, once I got home and connected my computer through my ethernet cable to the internet I could do the sudo apt-get ubuntu-desktop just fine.  Computer is working again.  Thanks so very much.  I'm gonna figure out how to backup so that I can do that from now on.  THANKS GUYS!  FOR REALS.

---

### Post by dannyboy79 on 2007-03-30
glad you got it working!!!

---

