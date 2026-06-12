---
title: "Looking for light-weight Linux distro"
date: 2011-07-24
forum: Any Other OS
---

### Post by Italic_Rendezvous on 2011-07-24
Hey guys, got myself stuck, but I want your opinions rather than straight tech help or "do this or that." Thought I'd come to Linux-central. 

**Some background:** I have myself a Toughbook CF-50 my step-dad bought off Ebay a couple years ago. He has since died and given it to me, but I needed to reload it to get a full OS back on it. I've put Windows XP on it so far, and that works well, but I want to dual-boot with some Linux distro as well. 

**My main problem is this:** Windows XP has a CPU idle rate of 1% usage. I installed Ubuntu 11.04 through Wubi, only to discover that the CPU idle rate was 12% usage or more. I found this very unexpected and decided to look around for other distros to use. Lo-n-behold, all the distros I've tried tonight have come up with the same CPU usage while idling, with the exception of one: [Fedora LXDE]("http://spins.fedoraproject.org/lxde/").

**My question:** What do you guys consider a light-weight distro? I'm looking for a GUI, but one that's not so fancy as to slow the entire machine down. As far as familiarity with Linux, I am MOST familiar with Ubuntu, but I'm willing to work with pretty much any other distro; I'm ok with either Gnome or KDE for a GUI. 

I'm just about out of CDs after trying these from tonight, so while I wait to go to the store I might as well see the public opinion. 

CF-50 Specs:
Intel Pentium M - 1.7 GHz
512 MB SDRAM (I'm assuming, at least) 
75 GB HDD
ATI Mobility Radeon 9600

The reason I want to use Linux on it is because it utilizes all of the features right off the bat: function keys, wireless, LAN, display, and SOUND (important stuff there, sound). XP won't use function or sound, which bugs the hell outta me. 

Any opinions would be great. I've got plenty of time to ponder this, but I can't buy CDs right away. ~Thanks~

---

### Post by el_koraco on 2011-07-24
Crunchbang with Openbox. I have it on a machine with similar specs, and it uses 1% CPU and never more than 300 MB ram. Plus, it's Debian stable based, so you're set for like three years.

---

### Post by HermanAB on 2011-07-24
Oh, just turn off the desktop search nonsense that almost all distros have nowadays (including Windoze).  That will free up your CPU again.

If you want a light weight distro, I would second Fedora with LXDE.  That is what I'm typing on now on my netbook.

---

### Post by hakermania on 2011-07-24
tinyCore Linux :D (or too light-weighted? :/)

---

### Post by Ezlivin on 2011-07-24
+1 Crunchbang it's very well put together to be as light as possible. Also Archbang is the Arch alternative, also there is Puppy Linux ect. There are lots of options... or you can use a minimal Ubuntu iso and install Openbox etc yourself.

There are some very good guides out there so have a look around to see what you feel would suit you best.

---

### Post by snowpine on 2011-07-24
Fedora LXDE is a great choice, why not stick with that? Ubuntu also has an LXDE remix called Lubuntu. Personally I enjoy using CrunchBang, however keep in mind it is based on Debian Stable and has a much slower development cycle; this could be either a pro or a con depending on your preferences. :)

---

### Post by mips on 2011-07-24
> **snowpine said:**
> Fedora LXDE is a great choice, why not stick with that? Ubuntu also has an LXDE remix called Lubuntu. Personally I enjoy using CrunchBang, **however keep in mind it is based on Debian Stable and has a much slower development cycle; this could be either a pro or a con depending on your preferences**. :)

There's also Archbang if he likes new & up to date packages.
I have a vanilla Arch+Openbox install on lower spec cpu than his that idles at 1%.

---

### Post by snowpine on 2011-07-24
> **mips said:**
> There's also Archbang if he likes new & up to date packages.
I have a vanilla Arch+Openbox install on lower spec cpu than his that idles at 1%.

I would heartily recommend vanilla Arch+Openbox for an intermediate/advanced user, but my experience with ArchBang was underwhelming. It is not "CrunchBang based on Arch" but in fact a completely separate project with a similar name. :)

---

### Post by Ichtyandr on 2011-07-24
Considering your information:
- familiarity with ubuntu
- not so fancy graphics
- utilizing all resources
- specs
you are probably happy doing Xubuntu. 10.04 is snappy, modern and your ubuntu knowledge will be useful, and there is high probability that your hardware will work OTOB. try a live usb or cd to see for yourself.
lubuntu might be faster, but its not as polished as xubuntu yet.

You can also try Debian Squeeze (stable) with xfce, there is an iso with xfce and lxde. Its very lightweight, very stable, you can rely on your apt-skills and use synaptic etc. It uses older xfce than xubuntu though as of now.

---

### Post by mips on 2011-07-24
> **snowpine said:**
> I would heartily recommend vanilla Arch+Openbox for an intermediate/advanced user, but my experience with ArchBang was underwhelming. It is not "CrunchBang based on Arch" but in fact a completely separate project with a similar name. :)

When's the last time you tried it? When I tried it back in the day it was a seperate project but from what I've read they have essentially copied the Cruncbang setup to make things easier for and less time consuming for the devs. I could be wrong as I have not tried either CB or AB as of late.

---

### Post by snowpine on 2011-07-24
> **mips said:**
> When's the last time you tried it? When I tried it back in the day it was a seperate project but from what I've read they have essentially copied the Cruncbang setup to make things easier for and less time consuming for the devs. I could be wrong as I have not tried either CB or AB as of late.

I tried ArchBang about a year ago. It is a completely separate project from CrunchBang. There are some similarities but the default artwork/theme/fonts are not as elegant, IMHO.

I won't say anything bad about ArchBang; however I feel strongly that anyone interested in Arch should try "The Arch Way" following the [Beginners Guide]("https://wiki.archlinux.org/index.php/Beginners'_Guide").

---

### Post by handy on 2011-07-24
Going for one of the quick Arch installs might be appropriate for some people. It gives them the chance to experience the rolling release upgrade system & have a bit of a poke around inside of Arch.

If they like it then as has already been stated, doing a Beginners' Guide installation will truly serve them well into the future, due to the basic understanding of how Arch works that is instilled to a greater or lesser degree during the installation.

---

### Post by kohlif on 2011-07-24
With my experience and i have tested almost every distro now for your specs i would go with zenwalk linux it is screaming fast and verry verry stable it is slackware linux and super easy to install it plug and plays everything for hardware even wireless drivers. If you want fast stable and with wine installed for Microsoft games and apps..  Uses Zorin OS 5 it is Ubuntu 11.04 but with no unity it runs Gnome very nicely and also can look like windows xp or windows vista (Thats the free version) If you make a donation you can also make it look like mac OS and a few others .. Gnome is most stable and no errors or glitches. True to Ubuntu you have use of the Ubuntu Software Center. But for pure speed reliability and use of everything you need for INTERNET office use and much more use Zenwalk as slackware is the oldest as it was the first linux back in 1991 thus it has a huge community it can do anything you want but uses alot of terminal use for some stuff ... I can use wine but it is complicated getting it setup and working with wine..   But if you dont use wine then by all means use Zenwalk it will give you everything you need and all the performance you desire with your system specs.



   I almost forgot 

  [http://zorin-os.com/free.html](http://zorin-os.com/free.html)

  [http://www.zenwalk.org/](http://www.zenwalk.org/)

---

### Post by teejay17 on 2011-07-24
I wouldn't hesitate to use Lubuntu, the most recent release. I've had great luck with Lubuntu "just working" out of the box with minimal configuration necessary.

---

### Post by kohlif on 2011-07-24
The only reason why i  went through all the distros is my sister wanted me to put linux on her computer after seeing how fast and secure a System it was but her computer is a old AMD 700MHz with 512 ram .. Her system runs Awesome on Zenwalk and it looks beter then windows xp by far ;)

---

### Post by ubume2 on 2011-07-24
Lubuntu  --lightest
Xubuntu  --a little more user friendly 
PCLINUX OS Phoenix  (XFCE)  --user friendly, good selection of                      
                            apps, easy on the eyes (imo).

All just nearly work "out of the box"

---

### Post by IWantFroyo on 2011-07-24
I would recommend Ubuntu 10.04.3 (LTS).

It isn't the most lightweight, but it has the old GNOME interface, no desktop effects by default, and no Unity.

Its programs are slightly outdated, but most Internet tutorials are written for it and its stable as a rock.

---

### Post by Italic_Rendezvous on 2011-07-24
WOW! I didn't expect this. Not only have I found a secret stock-pile of CDs in my living room, but there are two pages of responses. Looks like I've got a lot of burning to do~

Thanks for all the great feedback, everybody. It's greatly appreciated, but where am I going to find the time to try all of these? 

By the way, I have a favorite Linux forum now.

---

### Post by handy on 2011-07-24
You could just start at the top of the Distrowatch top 100 & work your way down. If you find something (hopefully you do) on the way down that just says this is it. Then make it your prime distro & keep checking out the others until you get tired of it.

Or get tired of it without finding something that you like better than Ubuntu, & just go back to Ubuntu.

We have so many choices, isn't it wonderful? :)

---

### Post by Italic_Rendezvous on 2011-07-24
> **handy said:**
> You could just start at the top of the Distrowatch top 100 & work your way down. If you find something (hopefully you do) on the way down that just says this is it. Then make it your prime distro & keep checking out the others until you get tired of it.

Or get tired of it without finding something that you like better than Ubuntu, & just go back to Ubuntu.

We have so many choices, isn't it wonderful? :)

There are times when I think there are just too many. I'll get some of the advanced distros once I head towards making it my main OS, since Dindoze still dominates the application world.

EDIT: I'm with CrunchBang so far. It's incredibly small, takes almost no time to boot (even on this thing), and supports all my drivers and hardware perfectly. Fedora LXDE was perhaps a bit TOO simplistic for my views of a pretty GUI, while other mentioned distros were still a bit much for my toughbook. What I find ironic about GUI simplicity: CB is SO simplistic that I love it. It uses a right-click menu for pretty much every app you want, therefor removing icons. Plus, it got rid of the screwups I made in GRUB installing other distros. Thanks to el_koraco for suggesting!

---

### Post by mips on 2011-07-25
> **Italic_Rendezvous said:**
> 
EDIT: I'm with CrunchBang so far. It's incredibly small, takes almost no time to boot (even on this thing), and supports all my drivers and hardware perfectly. Fedora LXDE was perhaps a bit TOO simplistic for my views of a pretty GUI, while other mentioned distros were still a bit much for my toughbook. What I find ironic about GUI simplicity: CB is SO simplistic that I love it. It uses a right-click menu for pretty much every app you want, therefor removing icons. Plus, it got rid of the screwups I made in GRUB installing other distros. Thanks to el_koraco for suggesting!

Good choice ;)

You can stick with it if it does what you want. I love it's simplicity. If you want you can also have a application launcher on your tint2 panel for the most frequently used apps (I have 5 small icons) but it requires tint2-svn.

See,
[[img]http://ompldr.org/tOWwzdg[/img]](http://ompldr.org/vOWwzdg)

---

### Post by wolfen69 on 2011-07-25
> **handy said:**
> You could just start at the top of the Distrowatch top 100 & work your way down. If you find something (hopefully you do) on the way down that just says this is it. Then make it your prime distro & keep checking out the others until you get tired of it.

Or get tired of it without finding something that you like better than Ubuntu, & just go back to Ubuntu.

We have so many choices, isn't it wonderful? :)

Wow. I agree with you 100%. Miracles never cease. ;)

With all due respect, this type of thread has been beat to death *many* times over the years. Doing a google search for "lightweight distros"/"best lightweight distros", yields *many* 1000's of results with similar answers. And many of the threads are recent and relevant. Chances are you'll see an ubuntuforum result from a thread last posted in recently, and you can just join in on it.

It's kind of like asking OSX vs. Win7? 32 vs. 64? Firefox vs. IE?

It's off my chest now, carry on.

---

### Post by el_koraco on 2011-07-25
> **Italic_Rendezvous said:**
>  Thanks to el_koraco for suggesting!

Yeah, LXDE is still a young desktop environment, based on Openbox. Openbox itself is a long established favorite among lightweight window managers. Crunchbang also has a very nice implementation of the Debian base with Openbox and relieves the hassle of setting up the non-free stuff. I think I might put it on my main laptop as well myself!

---

### Post by handy on 2011-07-25
**@wolfen69:** There aren't many things that haven't been beaten to death one way or another in this forum.

Every now & then something new comes up, but in the end this forum is like life, the longer you have been around the more boring it gets unless you put some effort into learning something new.

The older you get the harder it gets to put effort into anything, most especially something new!

So it all comes down to the amount of energy you have in the end.

---

