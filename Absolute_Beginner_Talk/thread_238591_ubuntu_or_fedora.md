---
title: "ubuntu or fedora?"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by quigz on 2006-08-17
ive been told that fedora is good to start out for linux and that ubuntu is good for beginners also. i have some experience with comand line (cygwin) and own a sobell command line book. but what worries me the most is that my computer has 2 nfts partions and i know that fedora does not come with nfts support that there are some groups that make it possible. so i was wondering if ubuntu supports nfts drive so i can use and work with the information on those3 partions

i am going to install a 20 gb hard drive to install linux on my box and i want to keep i dual boot (other family memebers use my computer and they would get confused my linux they have trouble went they have to repair the wireless connection)

also i was wondering if ubuntu has wireless support. i have a linksys wireless-b pci card.

i also have a asus sli motherboard, i want to if ubuntu or fedora support sli? or dual (not sli but running side by side) gpus?

if anyone could please help me deciede that would be helpful.

---

### Post by Kilz on 2006-08-17
> **quigz said:**
> ive been told that fedora is good to start out for linux and that ubuntu is good for beginners also. i have some experience with comand line (cygwin) and own a sobell command line book. but what worries me the most is that my computer has 2 nfts partions and i know that fedora does not come with nfts support that there are some groups that make it possible. so i was wondering if ubuntu supports nfts drive so i can use and work with the information on those3 partions

i am going to install a 20 gb hard drive to install linux on my box and i want to keep i dual boot (other family memebers use my computer and they would get confused my linux they have trouble went they have to repair the wireless connection)

also i was wondering if ubuntu has wireless support. i have a linksys wireless-b pci card.

i also have a asus sli motherboard, i want to if ubuntu or fedora support sli? or dual (not sli but running side by side) gpus?

if anyone could please help me deciede that would be helpful.

I would recommend Ubuntu to anyone installing Linux for the first time. The community is second to none. Any questions you have will be answerd fairly fast. There is also a lot of documentation here that is in easy to understand form. You will also not get attitude for asking questions. Not that I'm saying Fedora's community will give you attitude. But I have never seen it here.
My advice for the hardware is to download a livecd and take Ubuntu for a spin.
As for ntfs partitions, it will be easy to set them up to be read. There is experimental support for writing. But I don't recommend writing for any Linux distribution unless you dont mind corupting the drive.

---

### Post by scxtt on 2006-08-17
i used RedHat/Fedora for years (from RH6.0 to FC4) and i'd say the only disadvantage it has is package management ... not that it's bad or horrible, but the repos here seem to possess much more usable, easily installable software - which is always helpful :D

---

### Post by quigz on 2006-08-17
thank you for the information tonight i am going to download ubuntu and get it started. thanks for the help!

---

### Post by bodhi.zazen on 2006-08-17
Fedora core 5 is very nice. Not as easy to sys admin as Ubuntu.

Check out BLAG, based on Fedora. Also check out Fedora Frog.

Fedora : [http://www.fedorafaq.org/](http://www.fedorafaq.org/)

Frog : [http://easylinux.info/wiki/Fedora_frog](http://easylinux.info/wiki/Fedora_frog)

BLAG : [http://www.blagblagblag.org/](http://www.blagblagblag.org/)

---

### Post by anaconda on 2006-08-18
Both are good, but I like ubuntu more..

Fedora comes in too many CD:s.. is the installation package now 6CD:s?? vs. ubuntus 1CD download..

I like .deb more than .rpm packages.. Yes you can use apt-get also in Fedora, but..

I think the same ntfs support can be installed to both, but neither comes with ntfs writing support pre-installed. (And it IS still experimental)

---

### Post by aysiu on 2006-08-18
I second the nomination for Blag, software-wise.

For the community support, though, Ubuntu can't be beat.

---

### Post by givré on 2006-08-18
> **anaconda said:**
> 
I think the same ntfs support can be installed to both, but neither comes with ntfs writing support pre-installed. (And it IS still experimental)
The difference on that point is only that the fedora/redhat kernel don't come with the ntfs driver, because they are affraid of microsoft patent, but there is rpm to install it easily.

---

### Post by bodhi.zazen on 2006-08-18
> **anaconda said:**
> Both are good, but I like ubuntu more..

Fedora comes in too many CD:s.. is the installation package now 6CD:s?? vs. ubuntus 1CD download..

I like .deb more than .rpm packages.. Yes you can use apt-get also in Fedora, but..

I think the same ntfs support can be installed to both, but neither comes with ntfs writing support pre-installed. (And it IS still experimental)

I agree completely. If you do a desktop install with say KDE or Gnome, you will use only 1-2 CD's worth of applications. The problem is it is spread across the 5-6 CD set.

I posted this in the Fedora site a few months ago and was told it is the fedora way...  go figure. I understand why they do it, but it is a waste.

Fedora should come out with a desktop install (1 for KDE, 1 for Gnome) and sever install with the additional applications available as on say an extra CD(s). After the install I use the repository anyways.

A potential solution is therefore BLAG, which is a 1 CD install of Fedora desktop. If you want more use the Fedora repository.

I also agree the the Fedora update and install process is slow and clunky compared to synaptic on Debian based distros.

If you are up for a challenge, try Arch Linux. The install is a bit intimidating, but post install nothing is faster then pacman.

---

### Post by ComplexNumber on 2006-08-18
[quote=bodhi.zazen]Fedora core 5 is very nice. **Not as easy to sys admin as Ubuntu.**[/quote]
i'm unclear as to why you believe this.


[quote=bodhi.zazen]
I also agree the the Fedora update and install process is slow and clunky compared to synaptic on Debian based distros.[/quote]
you couldn't be more wrong.  synaptic is painfully slow. i mean *really slow*. try comparing it with Smart to see how fast it should be done.

> 
Fedora should come out with a desktop install (1 for KDE, 1 for Gnome) and sever install with the additional applications available as on say an extra CD(s). After the install I use the repository anyways. why is this a disadvantage? many magazines have stopped using cd's for their cover disk ages ago and now issue dvd's only. there are only advantages to be gained from having more packages to get the user up and running. especially for people who either have no internet or who rely on a wireless connection,.........but because ubuntu's measly 1 cd is so sparse, there aren't enough resources to get up and running. thats why i had to go back to fedora.

---

### Post by givré on 2006-08-18
> **ComplexNumber said:**
> 
you couldn't be more wrong.  synaptic is painfully slow. i mean *really slow*. try comparing it with Smart to see how fast it should be done.

He is comparing apt-get and yum, and on that point he is totaly right, even fedora guy aggree on that

---

### Post by bodhi.zazen on 2006-08-18
> **ComplexNumber said:**
> i'm unclear as to why you believe this. 

Must be the lack of experience I have with Fedora. Always found Debian more intuitive.

> **ComplexNumber said:**
> you couldn't be more wrong.  synaptic is painfully slow. i mean *really slow*. try comparing it with Smart to see how fast it should be done.

I have had the opposite experience. I was using YUM and have not tried Smart. Perhaps SMART is an improvement over yum. Perhaps it is dependent on the repository server and not Ubuntu/Fedora/or Synpatic/Smart?

> **ComplexNumber said:**
>  why is this a disadvantage? many magazines have stopped using cd's for their cover disk ages ago and now issue dvd's only. there are only advantages to be gained from having more packages to get the user up and running. especially for people who either have no internet or who rely on a wireless connection,.........but because ubuntu's measly 1 cd is so sparse, there aren't enough resources to get up and running. thats why i had to go back to fedora.

Spoken in the Fedora tradition, this is almost the same response I got on the Fedora site.

First, Nowadays I prefer a lighter system and prefer to have more control over what I install. Why would I want to download a whole DVD if I only need 200 Mb of applications?  I think the Ubuntu CD is bloated and when I install Ubuntu I use  the "server install" from the alternate CD. With SUSE there is the network install. Would be nice if Fedora had a lighter version/install option. At any rate, Ubuntu is not "sparse". If you want sparse, try DSL or Puppy.

Second, the applications on the DVD become outdated so it is not long before you need the repositories if you want to keep up to date. This negates the " people who either have no internet or who rely on a wireless connection" needing a whole DVD, unless of course they never intend to update. 

And why wireless? Does Fedora not do wireless connections?

How about those who do not own a DVD burner? What then?

Third, why not give options? So Fedora offers a series of 1 CD installs as above, some extra CD's, and a DVD. That way we would all be happy. These options are not mutually exclusive.

---

### Post by givré on 2006-08-18
Smart isn't an improvement over yum, it's just a transplatform transformat package management that could be install on both ubuntu & fedora but which isn't default on both of them.
Did you try
```
sudo apt-get install smartpm
```
It's probably faster and smarter, but the UI in synaptic is so much intuitive. :D

---

### Post by bodhi.zazen on 2006-08-18
Thanks givré. For now I am happy with, to be honest, aptitude.

---

### Post by ComplexNumber on 2006-08-18
> First, Nowadays I prefer a lighter system and prefer to have more control over what I install. Why would I want to download a whole DVD if I only need 200 Mb of applications? I think the Ubuntu CD is bloated and when I install Ubuntu I use the "server install" from the alternate CD. With SUSE there is the network install. Would be nice if Fedora had a lighter version/install option. At any rate, Ubuntu is not "sparse". If you want sparse, try DSL or Puppy. i'm not too sure why you believe that ubuntu is going to give you any lighter system than fedora. just install what you need - nobody is forcing you to install the whol dvd's worth. fedora has the added advantage that the extra packages are there if necessary.



> Second, the applications on the DVD become outdated so it is not long before you need the repositories if you want to keep up to date. This negates the " people who either have no internet or who rely on a wireless connection" needing a whole DVD, unless of course they never intend to update. when i installed ubuntu, i couldn't for the life of me get my wireless car to work with it....so what good is having a measly 1 cd full of applications when there is not enough there to get my wireless up and running.  fedora gave the necessary extra utilities such as network manager etc to get me up and running with my wireless connection. and even if it didn't work, there was still significantly larger amount of packages to do most everything that i need to do. 

> 
And why wireless? Does Fedora not do wireless connections? it was fedora that did wireless, and ubuntu that didn't.


>  How about those who do not own a DVD burner? What then? who said anything about needing a dvd burner? many people (me included) get there distros from the cover of magazines such as linux format where cd's have been phased out.


as for the administration capabilities of fedora and ubuntu, fedoa has all the necessary ones. which ones does ubuntu have to compare? answer: not a lot. for example, controlling the services (see [this]("http://www.ubuntuforums.org/showthread.php?t=237715&page=2") thread comparing ubuntus with fedoras. ubuntus version is lame).

---

### Post by givré on 2006-08-18
```
it was fedora that did wireless, and ubuntu that didn't.

```
I don't understand how fedora could "do" wireless better than ubuntu.

There is a lot of tread about "ubuntu don't do wireless" but i don't really understand how you can "do" wireless. You can provide driver & tools for it, but you can't really "do" wireless, and on that point, both are quite the same. :cool: 

Anyway it's would be stupid to start a flame between fedora & ubuntu in this thread. Both are excelent distro, we shouldn't bash each other, but work together.

---

### Post by bodhi.zazen on 2006-08-18
ComplexNumber:

I can certainly see why you prefer a DVD. I only hope you understand my perspective as well.

As far a Ubuntu, I did look at your link and I can not either help you or comment regarding you issues with wireless cards as I hard wire.

Outside of that issue, Ubuntu obviously has administration capabilities, they are different then Fedora. It sounds as if you are as lost in Ubuntu sys admin as I am in Fedora. Lol.

Do not get me wrong, I like Fedora as much as Ubuntu, each has strengths and weaknesses.

If you must know I run Arch as primary. Most sys admin is text files and the admin tool I use is vim. Close second is Zenwalk, but outside of the base install it is harder to find the applications I want.

---

### Post by ComplexNumber on 2006-08-18
>  I don't understand how fedora could "do" wireless better than ubuntu. its what i found. 


> 
Anyway it's would be stupid to start a flame between fedora & ubuntu in this thread. Both are excelent distro, we shouldn't bash each other, but work together. thats correct. both a very good, but i'm just clarifying ths situation to give a balance. for example, even though another poster stated the reverse, the admin tools on fedora are way ahead of ubuntu....not just in quantity, but in ease of use too. it even has a central place to go for them too(see screenshot) :cool:....just like suse and mandriva.
[B]
bodhi.zazen[/B]
i'm not arguing with you :). i'm just clarifying(eg about the admin tools) to get a balance. in a thread discussing fedora and ubuntu on a ubuntu forum, there is always a tendency for ubuntu to be seen in a better light and fedora to be seen in a worse light that what is deserved.

---

### Post by givré on 2006-08-18
> **ComplexNumber said:**
> 
 thats correct. both a very good, but i'm just clarifying ths situation to give a balance.
Ok so we all agree :cool: :D 
In fact we should say, "just try it", it's not a matter of "this one is better", but it's more a matter of taste. Like say bodhi.zazen, both have strengths and weaknesses, and people have to find what fitt the best to them (and their hardware).

Just try it.

---

### Post by bodhi.zazen on 2006-08-18
ComplexNumber:

Nice screen shot.

What I think you are saying is you prefer the Fedora sys admin GUI over Ubuntu.

I find most sys admin is easier at the CLI. More options. More control. Faster then waiting for a GUI to launch, enter password, scroll through options I may or may not want, select option I want, etc.

I do minimal sys admin on a GUI, either Ubuntu or Fedora. What could be easier then "ifup eth0" or "dhcpclient eth0" at the CLI? to set up network vi /etc/network. Easy? If you know what you are doing. Faster then the GUI.

Not to imply you do not know what you are doing, just "clarifying(eg about the admin tools) to get a balance".

I am afraid my sys admin screen shot is very boring, although I do colorize and customize the command prompt, a few aliases here and there, a few soft links, transparency, a heavy dose of Fluxbox, dual monitors for good measure, viola. Light and fast. No bloat.

For what it is worth, I think Fedora is, in some ways, a little more polished and faster then Ubuntu. Ubuntu has more colorful forums.

---

### Post by quigz on 2006-08-18
> **ComplexNumber said:**
>  there are only advantages to be gained from having more packages to get the user up and running. especially for people who either have no internet or who rely on a wireless connection,.........but because ubuntu's measly 1 cd is so sparse, there aren't enough resources to get up and running. thats why i had to go back to fedora.

so what does it take to get wireless up on ubuntu?

---

### Post by ComplexNumber on 2006-08-19
> **quigz said:**
> so what does it take to get wireless up on ubuntu?
no idea. i never managed it, but i did on fedora. obviously many dependencies lacking on that 1 provided cd. in addition to that, finding the dependencies on the net, then installing them locally after burning a cd on a different pc is a total nightmare on deb systems compared to rpm systems. i ended up giving up.

---

### Post by bodhi.zazen on 2006-08-19
> **ComplexNumber said:**
> in addition to that, finding the dependencies on the net, then installing them locally after burning a cd on a different pc is a total nightmare on deb systems compared to rpm systems.

Not so, this is just plain wrong. It is different, (dpkg vs rpm), but no harder. And you certainly do not have to burn the .deb to CD to transfer/install. You can transfer the files over a LAN, Flash, set one box up as a local repository, there are several options.

---

### Post by givré on 2006-08-19
Please for the last time, the majority of the wireless card work out in ubuntu as in fedora, it's just that some card need more work than other.
I have an intel iwp2100 wireless card and it worked literaly 'out of the box' for me, so the question is not 
- I have a wireless card what to do ?
but
- I have a <name of the card> <chipset if it's possible> what to do ?
and this is not the thread for that kind of question, there is a wireless section for that.
Thanks 8)

---

### Post by givré on 2006-08-19
> **ComplexNumber said:**
> in addition to that, finding the dependencies on the net, then installing them locally after burning a cd on a different pc is a total nightmare on deb systems compared to rpm systems. i ended up giving up.
Please could you develop on that point, i'll be really interested.
Could it be easier than searching dependency on [packages.ubuntu.com](packages.ubuntu.com) ?

---

### Post by Blondie on 2006-08-19
In the grand scheme of currently popular Linux distros Fedora and Ubuntu are relatively very similar IMO. But Ubuntu's massive and helpful community and it's greater number of packages give it the edge.

---

### Post by ComplexNumber on 2006-08-19
> **givré said:**
> Please could you develop on that point, i'll be really interested.
Could it be easier than searching dependency on [packages.ubuntu.com]("http://packages.ubuntu.com") ?
yes, i know. 4 key presses for each application :shock:. that was the only one i ever found. there didn't seem to be any others. just go to google and type in "deb gedit download" and see how many valid hits you can get for a list of places where you can download it (or any mirrors to download applications for that matter). then type in "rpm gedit download" and compare the difference. then you'll see begin to see the difficulty people have   ;). every rpm mirror i've ever known is just 1 keypress per application. for example:
[http://dl.atrpms.net/fc5-i386/atrpms/stable/](http://dl.atrpms.net/fc5-i386/atrpms/stable/)
they're all like that. it was awhile ago, but i couldn't find any(from that oen that i found) convenient mirrors to donwload debs manually. when they were burnt and on my hard drive, i had terrible problems with manually installing them using dpkg. it was just too much hassle.

---

### Post by TFX360 on 2006-08-19
> **Blondie said:**
> In the grand scheme of currently popular Linux distros Fedora and Ubuntu are relatively very similar IMO. But Ubuntu's massive and helpful community and it's greater number of packages give it the edge.

Right on! This is what did it for me! :D

---

