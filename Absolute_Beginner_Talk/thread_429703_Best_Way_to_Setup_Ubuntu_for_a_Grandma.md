---
title: "Best Way to Setup Ubuntu for a Grandma?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by joshjani on 2007-05-01
I've been pleased with my 3 weeks of Ubuntu experience so far, especially with the friendly help I've received here on the forums. So I trust that this is where I'll find the best advice for my latest task.

My parents live in FL and have a friend who does not have a PC. They want me to outfit their old machine, a P-III 450mhx, 384mb RAM, 12gb HDD, so that their friend (a 65-ish great grandma) can use it. I tried installing an old copy of Win98se, but am baffled at how to get so much of the hardware running. I can't believe I ever used it!

I want to install ubuntu and set this machine up so that when I send it down to them, they'll be able to use the machine easily. My parents ran XP Home until just getting a new PC with Vista.
I think the lady in question just uses dialup for internet access.

So I have a few questions- firstly, and I know this is open to lots of debate, but what version of ubuntu would give her the easiest transition from windows? For the specs of the machine, I like Xubuntu. I have to keep in mind that this lady has very little computer experience at all, much less with a linux OS, so I have to make sure I set it all up as best as I can. I know, though, that she'll need help setting up dialup. Are there ISP's that have support for linux, and especially ubuntu? I know she used AOL before, but if I tried to swing her to a bare-bones ISP just for access, who could I suggest, or maybe even set up for her before I send the PC? Someone like Netzero?

Generally, any tips for a setup good for extreme novices would be greatly appreciated. 

Thanks a lot-
JC

---

### Post by oilchangeguy on 2007-05-01
i'd use ubuntu 6.06. and can she get highspeed internet access? as i'm sure you are aware of, getting dial-up to work is not easy. and she can still set the home page to aol.

---

### Post by GSF1200S on 2007-05-01
Im a KDE user now, but even with that being said, definitely go XFCE (I have high respect for XFCE, and its lighter than KDE). You can customize XFCE to look like windows for the most part. I would recommend not installing any video drivers, because as you probably know, its a pain to reinstall them if youre new to linux/computers. This means no Beryl, etc.

I would probably run Opera or Epiphany web browser, as Firefox likes memory that this machine doesnt have (its not that bad now, but Opera is full featured and light). Besides, she probably wont be messing with extensions, which is what Fox is about. 

Make sure all programs are labeled by function rather than by name- internet, email, word processor, etc, depending on the applications you might think she wants.

---

### Post by zetsumei on 2007-05-01
Go with XFCE.  And try to see if she can get highspeed internet.  Not wireless because wifi cards can be a bitch to setup.  I say get her XFCE, with the default look (or get it like windows) with no beryl, etc...and label the applications so that she'll know what they are and put them on the desktop.

---

### Post by tom56 on 2007-05-01
Anything other than Xubuntu would probably run far too slow to be of any use on that system

---

### Post by oilchangeguy on 2007-05-01
> **tom56 said:**
> Anything other than Xubuntu would probably run far too slow to be of any use on that system
i had ubuntu 6.06 running fine on this computer with 384mb of ram, recently upgraded to 1gb of ram. and can't tell much difference.

---

### Post by dca on 2007-05-01
The one thing I did for my parents and somebody else after building them a system running Ubuntu 606LTS was to remove the top panel and reconfigure the bottom to look like MSWin2k except larger...  Add the Ubuntu Main Menu to it all the way to the left which is nothing more than an icon that when you click on it, it pops up all the menu(s) (admin, system, etc)...   Then add a separator, then add 'show desktop icon', the Firefox icon and a few others...  Basically icons on the task/start bar relating to everything they would ever use...  Normally for people recently converting from Windows I'll try a KDE-based distro but Kubuntu never lived up to it.
 
Not to mention, the config utility for seriel modems is a lot quicker in Gnome than using kppp....

---

### Post by ubuntu27 on 2007-05-01
If you upgrade the RAM, you could use Ubuntu and install Epiphany-browser.


Ah, first thing first, got to change her ISP. Modem that has Ethernet will be a good choice. :)

---

### Post by kittyhawk63 on 2007-05-01
For dialup, I recommend "All2Easy." It is easy to setup and will only cost $4.95 a month. It is 24/7. I had only one time where I lost connection that I had to reconnect in over a year of use.
kh

---

### Post by vanadium on 2007-05-01
A Pentium III with 300 + Mb RAM will run the default Ubuntu just fine, Indeed, if it&#347; for grandma, things can't be much easier: the default install will be perfect for her.

---

### Post by cmost on 2007-05-01
If you want super, duper easy then skip Ubuntu altogether and go with PCLinuxOS.  Sorry guys, but the latest 2007 build is rock solid, setup like Windows by default and has an easy to use control panel similar to Windows.  Plus, there's little chance that an upgrade will break the X server as Texstar carefully controls everything that goes in the repositories.  Even though the distro is RPM based, it still uses apt-get and Synaptic for package management so you can't get much easier.  The XFCE version is called SAM Linux and can be had here:  [http://sam.hipsurfer.com/news.php](http://sam.hipsurfer.com/news.php)

Good luck!

---

### Post by compiledkernel on 2007-05-01
Cmost, the idea was to answer this question with Ubuntu in mind. Try to stay on that track please.

---

### Post by joshjani on 2007-05-01
Thanks so much for your responses- great suggestions!

Just to clarify- I DO have a network card in the pc that works perfectly; I'm just not sure she wants to pay the $ for hi-speed, and so my questions about linux-friendly dial-up.

And I'm just a little nervous about sending her an ubuntu-loaded pc because it's just different *enough* to be confusing. I don't really want to be her tech-support guy long distance from FL! I mean she's *A *grandma, she's not *MY* grandma!;) 

Seriously, though, thanks for the suggestions. Keep 'em coming, I'd love to see anything you have to offer.

JC

---

### Post by kittyhawk63 on 2007-05-01
Joshjani,
I would really check out All2Easy. It is extremely affordable and was as good as my $10 a month Juno connection. In fact, it was much better. Juno is so overcrowded and few people know about All2Easy. That's what makes it such a good connection. The lines are clear from overcrowding. Can't beat $4.95 a month for 24/7. It has been a few months since I used it. Therefore, it could have gone up a little. I still would not hesitate into checking it out.

Edit: Nope, it is still $4.95. (Type **all2easy** in Google.)
kh

---

### Post by Bartender on 2007-05-01
What if she wants to stick with dial-up?   
Are you thinking about using a hardware-based external modem?

---

### Post by joshjani on 2007-05-01
> **Bartender said:**
> What if she wants to stick with dial-up?   
Are you thinking about using a hardware-based external modem?

No, no-- there's a modem already in the machine, too. She'll have both options, but I think broadband via her NIC would be easier, as you can just leave everything on "auto", sort of. I checked out All2Easy, and it looks like they have local numbers where they are in FL, and they have tech support and actually list compatibility with Linux, so I'm sure she could get help setting up. 

I think I'm gonna do it with Xubuntu, taking some of the suggestions here and making her very clear, easy to follow desktop icons and a readme that will get her started. I'll setup the modem and network card as best I can, just make sure they work, etc. And hopefully she'll love it!

---

### Post by faithsnathan on 2007-05-02
> **kittyhawk63 said:**
> For dialup, I recommend "All2Easy." It is easy to setup and will only cost $4.95 a month. It is 24/7. I had only one time where I lost connection that I had to reconnect in over a year of use.
kh

Thanks for the recommendation!  I looked up [All2Easy]("http://www.all2easy.net") and they are even in my small town.  I'm setting up my old desktop for my mom who lives 5 hours off, and I can't find any broadband providers in her area.

I just hope it works alright.

---

### Post by jimrz on 2007-05-02
> **joshjani said:**
> I've been pleased with my 3 weeks of Ubuntu experience so far, especially with the friendly help I've received here on the forums. So I trust that this is where I'll find the best advice for my latest task.

My parents live in FL and have a friend who does not have a PC. They want me to outfit their old machine, a P-III 450mhx, 384mb RAM, 12gb HDD, so that their friend (a 65-ish great grandma) can use it. I tried installing an old copy of Win98se, but am baffled at how to get so much of the hardware running. I can't believe I ever used it!

I want to install ubuntu and set this machine up so that when I send it down to them, they'll be able to use the machine easily. My parents ran XP Home until just getting a new PC with Vista.
I think the lady in question just uses dialup for internet access.

So I have a few questions- firstly, and I know this is open to lots of debate, but what version of ubuntu would give her the easiest transition from windows? For the specs of the machine, I like Xubuntu. I have to keep in mind that this lady has very little computer experience at all, much less with a linux OS, so I have to make sure I set it all up as best as I can. I know, though, that she'll need help setting up dialup. Are there ISP's that have support for linux, and especially ubuntu? I know she used AOL before, but if I tried to swing her to a bare-bones ISP just for access, who could I suggest, or maybe even set up for her before I send the PC? Someone like Netzero?

Generally, any tips for a setup good for extreme novices would be greatly appreciated. 

Thanks a lot-
JC

I have feisty running on my old ThinkPad 600x PIII 500Mhz 384Mb ram and doing quite nicely. used to use xfce on that box but, since I prefer gnome, I tried it with the default install and it runs easily well enough that I have just stayed with it.

---

### Post by kittyhawk63 on 2007-05-02
> **faithsnathan said:**
> Thanks for the recommendation!  I looked up [All2Easy]("http://www.all2easy.net") and they are even in my small town.  I'm setting up my old desktop for my mom who lives 5 hours off, and I can't find any broadband providers in her area.
I just hope it works alright.

I found it really easy to setup. There is no program to download. There is only a small packet that you install that permits you to connect to All2Easy's server.

---

### Post by Bartender on 2007-05-03
> **joshjani said:**
> No, no-- there's a modem already in the machine
 
And the chances of that modem working are about zero.  That's why I ask if you're going to set it up with an external.

EDIT: I would also recommend PCLOS

---

### Post by faithsnathan on 2007-05-04
> **kittyhawk63 said:**
> I found it really easy to setup. There is no program to download. There is only a small packet that you install that permits you to connect to All2Easy's server.

I signed up for their service, but can't find how to use it with Ubuntu.  I can't seem to find any directions for Linux users on their site.  Where is the packet that you install?

Thanks!:popcorn:

---

### Post by cmost on 2007-05-06
> **compiledkernel said:**
> Cmost, the idea was to answer this question with Ubuntu in mind. Try to stay on that track please.

No, the idea was to get Grandma the easiest Linux setup.  My suggestion was right in line with that idea, and an appropriate response.  Linux distros should not be in competition with each other since they all have the ultimate goal of breaking into the main stream.  If Ubuntu holds itself higher than that, then perhaps I should switch to a new distribution.

---

### Post by hyper_ch on 2007-05-06
Well, if your grandmother doesn't have much experience with computers it does not matter what linux you install for her and what desktop. Just chose one that you can support if she calls you and that runs fine and that was setup nicely...

---

### Post by bodycoach2 on 2007-06-30
[COLOR=Black]Alternatively from dialup, you might be able to find a way if she can *borrow* signal from a nearby Access Point. If she lives in a neighborhood, most likely someone will have an open AP. I detailed how I helped my mother-in-law do it with THIS setup:
[http://coachdanny.blogspot.com/2007/05/boost.html](http://coachdanny.blogspot.com/2007/05/boost.html)
It worked perfectly. The Hawking Technologies signal booster wasn't really necessary to pick up signal, but it was necessary to make it fast.[/COLOR]

---

