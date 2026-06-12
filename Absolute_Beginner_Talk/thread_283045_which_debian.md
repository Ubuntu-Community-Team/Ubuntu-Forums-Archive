---
title: "which debian??"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by unlokia on 2006-10-23
Hi people!. Having been so very impressed with Ubuntu and an AVID user :D - I want to try Debian out. Does anyone know WHICH dvd iso image I need to be able to begin??. I want the current release. Many thanks people!!.

---

### Post by chuckyp on 2006-10-23
With debian there are basically three version to choose from.

Stable - latest stable release Definately use for servers
Testing - Next version to be released may have bugs
Unstable - Cutting edge version may be lots of bugs

For normal desktop use I would use testing.  However, I've typically used unstable just to get newer versions of apps that I use.  Its completely up to you.  The [www.debian.org](www.debian.org) will go into detail about these different versions.

---

### Post by unlokia on 2006-10-23
Hey thanks!. But which DVD iso do I use as there are TWO :confused:

---

### Post by Anonii on 2006-10-23
Debian is devided in three categories.

Stable (Sarge) - Which is, well, stable. Really stable. It uses the old and one-thousand-times tested applications, to be sure that your system wont crash except if you really **** with it. (I'dnt reccomend that, if you are not thinking of a server, or if you want flashy graphics and top-notch apps)

Testing (Etch) - Tested but not that stable apps. Dont think that it will crash, tho. Its really ******* stable. Stabler than, lets say, Breezy, imo. But well, you will have the latest GNOME/KDE versions there, along with Amarok etc.

Unstable (Sid) - Unstable, they say. I say, less stable. I tried it once or twice, it was really rock solid. I'd say its not worse than my current Ubuntu.


Obviously, you can install any application you want in any version you want, using unnoficial .debs etc, but the default reps will only give you the suggested apps you need for the system you selected.

Now about the ISO image. If you have a  high-speed connection, I'd suggest a net-inst iso, because its much faster, easier, and it will let you select fast and easy the packages you want to install.  Find them here:
[http://www.us.debian.org/CD/netinst/](http://www.us.debian.org/CD/netinst/)

Now there are the normal disks which contain all the programs etc, you wish to install inside. They are huge, and I havent tried them out, yet. If you have a slow connection, you can let a friend of yours download and burn them, and pass them to you.

Finally, the installation is really straightforward, and I dont understand why people are freaking out with it. Probably because it doesnt have a GUI, and its not a live CD. I find it great, tho.


Give Debian a try, it wins!

Good luck!

---

### Post by unlokia on 2006-10-23
I have 6mb ADSL so its fine... so I have to download 2 or 3 DVD's if I want the whole thing, right?? :eek: 

wow!!

thats 7 hrs :(

---

### Post by taurus on 2006-10-23
Why download the whole thing since you are not going to need every single package on the DVD!!!  Download the minimal image to get your system up and then use aptitude to download the rest.  Since you have a fast network connection, installing them with aptitude won't take that long...

---

### Post by unlokia on 2006-10-23
because I want to have the WHOLE package to hand so that I may install on other machines that are without connectivity :).

I think I shall download this overnight ;)

---

### Post by Anonii on 2006-10-23
As I said, you are better off with the net-inst then. 

Chose your architecture in this page:
[http://www.us.debian.org/CD/netinst/](http://www.us.debian.org/CD/netinst/)
in the **Official netinst images for the stable release** "chapter",
if you want a stable release.

If you want a testing, download one from here:
[http://www.us.debian.org/devel/debian-installer/](http://www.us.debian.org/devel/debian-installer/)
in the **netinst CD image (100-150 MB)** "chapter".

_EDIT: Aw then, you have no choice but downloading the DVDs afaik._

---

### Post by skymt on 2006-10-23
If you need to install it onto machines without Internet access, you will need *both* DVDs, or all 15 CDs. Debian is too big to fit on less. For machines with Internet access, netinstall is the best option.

That's one big flaw with Ubuntu. It assumes the user has an Internet connection. If they don't, they will need to find a computer that does and download/burn the .deb, plus .debs for all the dependencies. With Debian, you can download a set of .isos with *every* package in the distribution. That's inefficient for most users, but in some cases it can be very useful.

---

### Post by unlokia on 2006-10-23
I take it Debian is FREE as in Free speech?!. Then I can give away and/or sell the DVD's for small cost

---

### Post by Anonii on 2006-10-23
> **unlokia said:**
> I take it Debian is FREE as in Free speech?!. Then I can give away and/or sell the DVD's for small cost
Of course you can! 
(You can also remove the "small" if you like :P )

---

### Post by unlokia on 2006-10-23
hehe ;) Yeah but unlike MS I am not greedy. £15 for set will be more than enough I say. Im trying debian livecd now. It is MASSIVE download and I don't even know if it will support my WIFI or soundcard yet :confused: ipw2200 by intel is the wifi card. I think a 500mb livecd is a better start than 15 gigs of stuff I won't even use LOL.

---

### Post by taurus on 2006-10-23
Hey, with those two DVDs, you have everything including a kitchen sink!!!  :mrgreen:

---

### Post by unlokia on 2006-10-23
Ahh but will it contain WIFI for ipw2200 and ALC883 codecs??

---

### Post by taurus on 2006-10-23
Maybe you want to download the netinstall first to check it out.  Small and fast instead of waiting for 7 hours...

---

### Post by furiousV on 2006-10-23
> **unlokia said:**
> Ahh but will it contain WIFI for ipw2200 and ALC883 codecs??

The IPW2200 is an Intel wireless chipset, and they do provide drivers.

If I remember correctly, my friend has a Toshiba laptop which has the same wireless chipset, and it worked out the box with Ubuntu 6.06

I assume it will be the same with Debian. If not, [www.intel.com](www.intel.com)

---

### Post by cunawarit on 2006-10-23
I recommend Etch Beta 3 over Sarge. Sarge is aging to say the least and Etch is going to be out in December. Sarge is very good, but some key applications are rather old. And despite the testing name, Etch is already stable and very much usable. I've been using it every day for a bit and I haven't noticed any problems. 

Etch Beta 3 installer is great, and Etch stacks well against Ubuntu with its more up to date apps.

Anyway, Ethc Beta 3 is here:
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

---

### Post by furiousV on 2006-10-23
Just watch out though, going with the *non-stable* releases means that the Debian security team probably wont provide security patches, unless it is critical.

The Stable release is officially supported by Debian, just keep that in mind.

---

### Post by cunawarit on 2006-10-24
> **furiousV said:**
> Just watch out though, going with the *non-stable* releases means that the Debian security team probably wont provide security patches, unless it is critical.

True, however, I suggested Etch because it would be a shame for someone to test Debian and conclude it is an old OS not worth looking into further. In any case Etch should be out in December, the likelihood of any serious security problems from now till then is negligible.

---

### Post by scheuri on 2006-10-24
> **unlokia said:**
> hehe ;) Yeah but unlike MS I am not greedy. £15 for set will be more than enough I say. [..]
I dont want to spoil the fun, but...that IS pretty greedy!
Debian comes with GNU Software only actually. On these DVDs you will not likely find anything that does not apply to the GPL. Therefore selling it is not allowed. However, you MAY charge your discs. This is fine. But anything more is considered selling and is not allowed.

Well, of course...its very unlikely anyone (read: gouverment) is knocking on your doors and will punish you.
But if you'd ask me to buy on or two of your disks for 15 pounds I pretty much gave you a lesson or two to think about.

And do not tell me that your pay more than 2 pounds per disc!

sorry, I had to say that.
Scheuri

---

