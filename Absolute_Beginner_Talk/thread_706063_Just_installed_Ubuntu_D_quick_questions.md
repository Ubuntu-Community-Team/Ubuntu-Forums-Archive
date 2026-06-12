---
title: "Just installed Ubuntu :D quick questions"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by biffinson on 2008-02-24
Love it so far.. but 
When I go to add/remove applications and hit the check on  an application (amarok to be specific) it says the list of applications is not available i need a properly working internet connection to reload the list, so i hit refresh, it refreshes and it does it again.
 
obviously since ia m posting this, my internet connection working so what's up?

also, i have a broadcam BCM4306 and tere seems to be a ton of way to get drivers for this, what's the best way do you think?

and I think that's about it, but i'm sure i'll have more

thanks

---

### Post by oedha on 2008-02-24
have you activate your repository server ?
go to system - administration - software source

---

### Post by intel on 2008-02-24
go to System > Administration > Synaptic Package Manager

search for amarok,

try to install it from there.

---

### Post by biffinson on 2008-02-24
I don't know how to do that :\ i went to the menu and i don't know what to do

---

### Post by biffinson on 2008-02-24
> **intel said:**
> go to System > Administration > Synaptic Package Manager

search for amarok,

try to install it from there.

it's not on the list :\

---

### Post by oedha on 2008-02-24
in software sources.....mark all boxes then click close....click reload
from synaptic : click setting - repositories

---

### Post by uberlube on 2008-02-24
I believe that Amarok will need you to install several KDE dependencies to be able to work in gnome, so expect that.

---

### Post by biffinson on 2008-02-24
> **oedha said:**
> in software sources.....mark all boxes then click close....click reload
from synaptic : click setting - repositories

I did that and amarok still isn't showing up on synaptic

---

### Post by uberlube on 2008-02-24
Try downloading it from its site here:
[http://amarok.kde.org/](http://amarok.kde.org/)

Have you also considered use Exaile, i think its called. Pretty much sam as Amarok, but made for gnome, xfce.

---

### Post by oedha on 2008-02-24
> **biffinson said:**
> I did that and amarok still isn't showing up on synaptic
mm......
can you open terminal......( applications - accessories - terminal )
type sudo apt-get update
after that....
sudo apt-get install amarok
if none can be done.....can you post /etc/apt/sources.list ?

---

### Post by zakirs on 2008-02-24
hey make sure that u check all boxes in system>administraton>software sources

---

### Post by biffinson on 2008-02-24
It randomly decided to work on add/remove applications :D

now about that 43xx broadcom driver?

---

### Post by uberlube on 2008-02-24
I just made a tutorial for that today, check it out here and let me know if it works:
[http://ubuntuforums.org/showthread.php?t=706034](http://ubuntuforums.org/showthread.php?t=706034) :)

---

### Post by oedha on 2008-02-24
> **biffinson said:**
> It randomly decided to work on add/remove applications :D

now about that 43xx broadcom driver?

so...you 've got amarok ?
for your broadcom...maybe
[http://ubuntuforums.org/showthread.php?t=664765](http://ubuntuforums.org/showthread.php?t=664765)
[http://ubuntuforums.org/showthread.php?t=634274](http://ubuntuforums.org/showthread.php?t=634274)
**[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)**
[http://ubuntuforums.org/showthread.php?t=470027](http://ubuntuforums.org/showthread.php?t=470027)

---

### Post by biffinson on 2008-02-24
ok, well the blue light is finally showing on my computer on the "is the wireless working" area, but when i right click the internet thing in the top right hadn corner it only talks about  enabling networking, it doesn't even mention wireless..

what do i do?

---

### Post by biffinson on 2008-02-24
:O

Huge update!  I was able to connect to the network, but i don't think i'm getting packets :\  what can i do?

---

### Post by uberlube on 2008-02-24
Install wi-fi radar:

sudo apt-get install wifi-radar

And use that to see if you can see your network

---

### Post by uberlube on 2008-02-24
Sorry disregard that. Can you log into firefox?

---

### Post by biffinson on 2008-02-24
No, it comes up with the 404 message

also, it gets really laggy whe i mess with teh wireless/wired settings... it just froze last time and wouldn't change between wired/wireless so it was stuck on wireless and forced me to reboot :\right now i can see all nearby connections and their strength using the restricted drivers

---

### Post by miesnerd on 2008-02-24
wifi radar works okay. 
Take it from me, though, you might just be better off spending $30 bucks and trashing that card. Broadcom is known to suck for linux, ie, they withold their firmware, whcih stops the hardware from working properly in most linux distros.

Ive been playin the linux game for two years, and just this week i pulled out my broadcom card, gave it to my boss, asked him to "use it on some windows machine, or trash it, so basically, trash it" and have been loving my atheros based card ever since. 
With my $30 card, every live cd and installed distro ive put in works perfectly.

Also, as food for thought: Broadcom wont work with linux, why should you work with them?

---

### Post by uberlube on 2008-02-24
hmm well this always works for me using KDE. Perhaps try the link that the other dude gave and if they dont work, conside using Kubuntu. They will work in there for sure :)

---

### Post by miesnerd on 2008-02-24
uberlube not only has a great name, but makes a good point. In general, KDE has better wifi tools, imo. Having a broadcom card doesnt help though.

---

### Post by miesnerd on 2008-02-24
oh, and if you really just cant stand it, I know sabayon linux tends to work for broadcom "out of the box" but in general, although I like sabayon, i think ubuntu is much easier to manage and work with.

---

### Post by uberlube on 2008-02-24
Thanks for the props :) And I agree, Sabyon, based on Gentoo is for more experienced users.

---

### Post by biffinson on 2008-02-24
:\  at this point i think i'm just going to head back to windows

if i can't get this working i doubt my ability to be able to use linux

---

### Post by miesnerd on 2008-02-24
oh you're so close. 
Let me point out my rationale. You already have the system installed and are able to use almost all of it, except for the internet. Why not spend $30 bucks to get a (better) wifi card (i got a Super G card for $30 and I can tell it works better) and save money on EVER buying software again.. or paying for an upgrade, or... the list goes on. Certainly, you can use open source software on windows, but it just doesnt compare to the beauty that is linux.

---

### Post by uberlube on 2008-02-24
i think that the wifi problems in gnome and xfce are mostly due to the imperfect keyring manager. Where as in kde, when you first boot into desktop, the kwallet prompts for your password and lets you connect easily.

---

### Post by biffinson on 2008-02-24
i don't have the money right now to buy a new wireless card, so that's out of the picture :\

---

### Post by biffinson on 2008-02-24
well i'm downloading kde right now, so hopefully that'll fix this

---

### Post by miesnerd on 2008-02-24
with that being the case, I'd advise going to Kubuntu then (with the KDE desktop). Plus, they just got KDE 4.0 and they're all really really excited about it :)
EDIT: KDE 4.0 wont be on the Kubunt 7.10 CD, but you can run update-manager after install and you can get it that way.

---

### Post by uberlube on 2008-02-24
are you downloading kubuntu gusty?

---

### Post by biffinson on 2008-02-24
> **uberlube said:**
> are you downloading kubuntu gusty?

kubuntu-desktop is the exact file i'm downloading

edit: it just finished downloading...should i choose kdm or gdm for m default display manager?

---

### Post by uberlube on 2008-02-24
Are you downloading it from the synaptic package manager or from the ubuntu website? If you are just installing KDE ontop of the ubuntu desktop, there may be some problems. Your better off burning a copy of the Kubuntu live CD and doing a clean install in my opinion. unless thats what your already doing.

---

### Post by miesnerd on 2008-02-24
> **biffinson said:**
> kubuntu-desktop is the exact file i'm downloading
to intro you to ubuntu's nomenclature of sorts, gusty = 7.10. Hardy =8.04.

---

### Post by uberlube on 2008-02-24
Log into KDE desktop session, from the login window.

---

