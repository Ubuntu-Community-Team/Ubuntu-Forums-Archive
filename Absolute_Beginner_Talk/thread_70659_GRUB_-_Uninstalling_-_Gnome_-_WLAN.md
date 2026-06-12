---
title: "GRUB - Uninstalling - Gnome - WLAN"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by ZoZ on 2005-09-30
Hey, I just installed Ubuntu yesterday as a dual boot -made a second partition next to win98 - and decided to toy around with it to get to somewhat familiar with linux. All these great stories I hear about it got me thinking it was worth sacrificing some time to it.

Now, I've bumped into some problems obviously, which lead me to the following questions:

- Sorry to say, but I think the desktop is ugly. I seems to be a layout called GNOME. What other interfaces are available, where, and how do i install them? (The linux boot gets me straight to the gnome thing, not giving me any obvious options to change it anywhere).

- I installed it on a laptop. On the win98 partition it connects fine with a winXP PC through both network cable and WLAN card.  However, In the linux partition, looking at all possibilities in the Ubuntu/ gnome menus, i don't see any option to get that WLAN card installed. The fact the CDROMs from the card are windows only doesn't really help. Any tips or perhaps even a step by step walkthrough with amazing screenshots available? Also, is there a way to connect the linux partition filesystem with the WINXP PC through a network cable?

- If I, by some miracle, would get the WLAN card installed, I'd probably manage to get it to work to get on the internet, but any tips there would be welcome too in advance.

- Lastly, If you think this linux newbie would have better stick with windows or try a more broad/easier linux version (or if you prefer answering 1 question instead of 3), how do I unistall Ubuntu? 
Two options possible here; either i get rid of the entire partition and somehow magically readd it to the win98 partition, either i keep the partition but decide to give the Mandriva distro a try (but still removing the Ubuntu one). I'm weary however of messing with the GRUB thing. I learned that the earlier a proces comes when booting, the more dangerous it is to mess with. 


Thanks in advance for answering.

---

### Post by Ampersand on 2005-09-30
Hi
There are a few other themes available for Gnome, go to System - Preferences - Themes. If you want something completely different, open Synaptic (System - Administration), and install Kubuntu. You will then be able to select KDE from the sessions menu on the login screen after you next log out. There are a few other environments available (such as Windowmaker, Xfce, enlightenment &c), but they're possibly not as beginner friendly as Gnome and Kde. 

I'd recommend sticking with Ubuntu for a while. A new OS will take a while to get used to.

For the network interfaces, have a look at System - Administration - Networking. 

(If you don't have a menu in a corner of your desktop, right click on one of the bars, add to desktop, then select one "Main menu" or "Menu bar"

---

### Post by nitricacid on 2005-09-30
I have to agree that the GNOME desktop is ugly and can be anoying at time.
I would not recomend instaling Mandriva, i have and it just rite out blows for the newcomer to linux.
I have used Mandrake from 8.0 up to 10.1 and loved the system but i find Ubuntu to be a much better choice when it comes to Noobies looking to switch operating systems.

As Ampersand said it will take time to get use to a new OS.
Stick with it and learn all you can.
In the long run you will most likey prefer linux then WindBlows for the most part.

You just have to remember that everything you know about windows can not always be applied in linux.
Software installs much differently then on windows.
You might want to check out this site on how to install packages on Ubuntu [http://www.psychocats.net/essays/winuxinstall.php](http://www.psychocats.net/essays/winuxinstall.php)

If you are a hard core gamer or would like to play games on linux check out [http://www.transgaming.com/](http://www.transgaming.com/) and something called Cedega along with point2play

If you have anymore questions feel free to ask, we are all here to help one another.

---

### Post by ZoZ on 2005-09-30
Thanks for the replies!

Ampersand

Thanks for the Theme tip. However, Kubuntu seems to be absent from the packages i am able to install. Looking in other forums here I see Breezy Badger is still in development. As I randomly picked Ubuntu 5.10 "Breezy Badger" for a distro, maybe that has something to do with it.

Also, network connections only gets me one possible choice without the possibility to add a network card. Modem Connection (the interface ppp0 is not configured) is all i can see to do something with. Nothing that remotely looks like having anything to do with a WLAN card.

Am i missing something horribly obvious, or is the Badger distro missing it?

nitracid:

Thanks for the links. If you have any more like that concerning networking or WLAN and linuxclients, thanks in advance.
If not, I'll have to give mandriva a go just yet :)  It's a 3 CD distro, I'm thinking it should have more helpfiles or options to experiment with.

---

### Post by Ampersand on 2005-09-30
Is there a 'kubuntu-desktop'? If you install that and go into kde, you'll be able to set up your network interfaces using kcontrol. 

What happens if you type iwconfig in a terminal?

---

### Post by nitricacid on 2005-09-30
ZoZ.
Open the Synaptic package manager.
On the left panel and scroll down a bit.
You should find something like 'KDE Desktop Enviroment' Install that.
Half way through it should ask if you want to use KDM or GDM (i think), pick the KDM.
Restart the computer and when you come back you should see a new login screen.
Under the menu selection click KDE and log in as you would normally do.

Welcome to your new KDE Desktop Enviroment.
---


If anyone feels i have given some wrong info along the way of this short walkthrough please feel free to chime in. SInce i know you will anyway... :D

---

### Post by ZoZ on 2005-10-01
The was only on GNOME desktop environment on the left side. The search option found me a kde with 4 packages, but that is already fully installed.

Also found kcontrol with the search option, but it gives no packages that i can install, it's like an empty folder.

iwconfig gets me:
lo  no wireless extensions
sito  no wireless extensions


Is it perhaps the breezy badger distro thats missing stuff?

---

### Post by nitricacid on 2005-10-01
Hmmm... that is wierd that the KDE Desktop Enviroment isn't on the list.
~Anyone have any ideas about this?!~

It shouldn't be Breezy, I installed my preview version of breezy by downloading,burning and then installing and everything was there when I finally logged in to the GNOME desktop.

I would tell you to try to install Kubuntu but lately i have been having problems when it comes to installing that version.
It seems Ubuntu runs better (for me anyway) when i install Ubuntu then Just install the KDE.

Have you done any repository updates\upgrades since you installed ubuntu?
I don't know if that might be a factor or not.
I am still learning this stuff as i go along and each time i come to this forum i learn something new about my linux.

I will get back to you if I find anything else out, in the mean time i am sure others will be able to tell you faster then i will.

---

