---
title: "Fedora Core 5 vs Ubuntu 5.10"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-04-20
Hi i wanna know what are the advantages/disadvantages of both Fedora Core 5 and Ubuntu 5.10.  i'm talking about a compare/contrast between the two. (sorry for the school-like phrase :))

---

### Post by htinn on 2006-04-20
FC5 is bluer. That's the main thing I've noticed.

---

### Post by taurus on 2006-04-20
If you want to do a comparison, head over to [http://www.distrowatch.com/](http://www.distrowatch.com/) and do that yourself.  By the way, it's not fair to compare Breezy (over 6 months old) to FC5 (a few weeks old)!  It should be Dapper (when it comes out in June) against FC5...

---

### Post by catlett on 2006-04-20
To someone who doesn't use the computer as a tool (as in a programmer or IT person,administrator etc) there isn't much difference. They both come with the Gnome desktop. So they look the same. Same choices of icons and themes. Just FC5 comes with a Fedora background and Ubuntu has an Ubuntu background. They both are Linux based. They both have a terminal for commands and both give you access to the same open source software. 
They differ in small ways. There is no sudo with Fedora, You have to switch users with su and do a command. They use RPM instead of DEB files. The difference is in the etiquette of commands and some of the compilimng but if your a casual user none of the big distros are much different. They will all look like Kubuntu or Ubuntu. Meaning they will come with either the Gnome desktop or the KDE desktop.
The distros will get different when you get to the lesser known and/or popular ones. Those will be more stripped down and use the command line more. But there isn't a great difference between the "popular" ones. They are all Linux kernel based distros with KDE or Gnome as their desktop.

---

### Post by user1397 on 2006-04-20
Ah, I c....

---

### Post by jonathansizz on 2006-05-08
> By the way, it's not fair to compare Breezy (over 6 months old) to FC5 (a few weeks old)! It should be Dapper (when it comes out in June) against FC5...

Of course it's fair; FC5 is the most recent release of Fedora, and Breezy is the most recent release of Ubuntu. Having said that, although I find Fedora to have a more professional, solid and polished feel to it, I switched back to Ubuntu as I immediately ran into trouble with dependencies on Fedora. If it wasn't for that (along with Ubuntu's superior package management) I'd say Fedora was better.

---

### Post by user1397 on 2006-05-08
But can you install .deb packages in FC5, or only .rpm packages? how about tarballs?

---

### Post by xXx 0wn3d xXx on 2006-05-08
[QUOTE=erik1397]But can you install .deb packages in FC5, or only .rpm packages? how about tarballs?[/QUOTE]
You can compile packages from source just like in Ubuntu. I think that there is a way to install debian files (something like alien for Ubuntu but in reverse) anyway there is alot of dependency problems on rpm based distros.

---

### Post by browndog on 2006-05-08
[QUOTE=erik1397]But can you install .deb packages in FC5, or only .rpm packages? how about tarballs?[/QUOTE]

As far as I know there is no installing .deb packages (in any real or effective way...just more trouble than its worth), and yes you can install tarballs.

---

### Post by user1397 on 2006-05-08
If you can't install .deb's or if it's very hard to, then i would find ubuntu to be more practical, as it has so many programs available (and almost all of them are deb's! :))

---

### Post by xtacocorex on 2006-05-08
If I remember correctly, I think there is a version of alien on Fedora to convert .deb to .rpm. 

A reference to the man page for alien says it will do .deb files.

I'd use Fedora, but got tired of dependency problems as jonathansizz said earlier. I don't mind compiling from source, I really enjoy it sometimes.

---

### Post by ComplexNumber on 2006-05-08
**erik1397**
i use FC5 only at the moment. its superb. typical fedora-like and gnome-like rock solid stability.
i much prefer rpm systemsto debian systems (probably because i'm much more familiar with them). when i used ubuntu, i had a horrible time trying to manually install deb packages whereas rpm is a a lot easier (for me). using dpkg didn't seem as friendly or as intuitive as i remember the first time i used rpm. considering that i first used a debian package after many years experience with linux didn't put debian systems in a favourable light (in my eyes).
i personally prefer the default look and feel of fedora. i'm not too keen on the new ubuntu orange at all. i prefer the darkish blue of fedora and i also prefer the bluecurve icon theme.
fedora gravitates more towards gcj java rather than sun's java, so if you're a java programmer, you may not like this aspect of fedora. 
FC5 used gnome 2.14 whereas ubuntu breezy uses gnome 1.12. 
if you want to ask any questions about FC5, then feel free.


[QUOTE=MasterChief1234]
anyway there is alot of dependency problems on rpm based distros.[/QUOTE]

there is absolutely zero more dependency problems on rpm systems as there is on debian systems. why do people STILL keep on coming out with this crap. btw no offence to you, mate, and i'm not directing it at you. its just that its a fallacy, and the sooner this fallacy is put to sleep the better.

[QUOTE=jonathansizz]
along with Ubuntu's superior package management[/QUOTE]
exactly the same apt-get and all that exists for fedora. ubuntu does not have a superior package management system. if it did,  one has to question why rpm has been chosen as the standard for LSB.

[QUOTE=MasterChief1234]
I think that there is a way to install debian files (something like alien for Ubuntu but in reverse)[/QUOTE]
alien can be used for rpm systems and does the job of converting debs to rpms's. it converts between them all.

> 
But can you install .deb packages in FC5, or only .rpm packages? how about tarballs?
its an rpm based system. as i've said, you can use alien to convert debs to rpms. you can also install tarballs in exactly the same way as on ubuntu. i use [this]("http://gnomefiles.org/app.php?soft_id=447") for installing tarballs. you can also use checkinstall ([click]("http://asic-linux.com.mx/%7Eizto/checkinstall/")) to turn tarballs into rpm's.

---

### Post by zerhacke on 2006-05-08
As someone who's running Breezy, Dapper, and FC5 (and FreeBSD, and an astoundingly old version of Atheos, and SolarisX86, and Darwin, but those don't factor into this discussion), I can resoundingly state that apt-get is beating the living h&#l out of yum.  Try a side by side comparison of searching the repository systems on both machines.  Apt clearly lists the name of the package on the left with a description on the right after a few seconds to compose the list.  Yum requires a long... long... long wait to provide any output, then gives you the information is a semi confusing format. Sure, the format is easy to learn if you google for it, but to a newbie it's gibberish.

I also dislike how yum requires an update of the repositories the first time you use it every boot.  If I want to update the repositories metadata, I'll do it myself.  Yum's test transaction seems spurious as well.

Then there's the comparison between Synaptic and Yumex.  No comparison, I should say.  Yumex tries to be Synaptic and fails.  Yumex needs streamlined in a bad way.

To defend yum(ex)/FC5, apt and Synaptic have a problem with repositories.  Namely, needing extra ones enabled in order to get any real use out of the system.  With FC5, the extras repository is enabled by default.  Ten seconds on the Ubuntu forum would fix this, however, so it's not a real handicap for Ubuntu nor a victory for FC5.

---

### Post by jonathansizz on 2006-05-08
> if you want to ask any questions about FC5, then feel free

Sure.

1] Where do I go for info on resolving software installation issues? I had no problems installing stuff from yum, but that wasn't much choice compared to Synaptic. For instance - flightgear. I downloaded flightgear plus four dependencies but still ran into problems.

2] What are the best websites/mailing lists/information sources for running a Fedora Desktop for the beginning-intermediate level user?

I'd love to dual-boot Ubuntu & Fedora, so if I can resolve the software installation issues I've run into, that would be excellent.

---

### Post by user1397 on 2006-05-08
And the war rages on! :)

---

### Post by ComplexNumber on 2006-05-08
**zerhacke**
why don't you install apt-get? [here]("http://rpm.pbone.net/index.php3/stat/4/idpl/2809930/com/apt-0.5.15cnc7-1.2.fc5.rf.i386.rpm.html") is a list of repositories that you can download it from. you're not being forced to use yum.
also, synaptic is also used for rpm based distros because i have installed and used synaptic on suse. it wasn't as good as Smart, so i gave up on it after a bit.
> 

1] Where do I go for info on resolving software installation issues? I had no problems installing stuff from yum, but that wasn't much choice compared to Synaptic. For instance - flightgear. I downloaded flightgear plus four dependencies but still ran into problems. not quite sure what you mean by "info". use something like Smart. if you install something that has dependencies, it lists the dependencies and installs those too (after verification with the user).


.

---

### Post by daacosta on 2006-05-08
I love Fedora.  I think it is a very slick distro with good qualities.  I also like Ubuntu that for some strange reason runs better than Fedora on my box [Dial-up is faster...]

Fedora? Ubuntu? I believe it is just a matter of taste.  I like better the package management of Debian derived distros than Red Hat's.  On the other hand, I much prefer the security protocols of Fedora [It comes with a firewall... Sure, you can install Firestarter in Ubuntu but why don't the developers concentrate on this?]  I also like better the management of accounts in Fedora [root is root and it exists explicitly...]  In regards to repositories I think that Debian based distros are a lot better because of the vast amount of software that you can install.

I haven't tried FC5 but I will because I truly consider that project worth following up [Sure, I am a chicken and I will do so only when I see a DVD on the cover of Linux Format or any other magazine.]  Similarly, I will continue using Ubuntu at home because it just works the way I want it [Then again, once the next version appears on a magazine, I will try it... Not into downloading things :mrgreen: ]

---

### Post by ComplexNumber on 2006-05-08
> I haven't tried FC5 but I will because I truly consider that project worth following up [Sure, I am a chicken and I will do so only when I see a DVD on the cover of Linux Format or any other magazine.] Similarly, I will continue using Ubuntu at home because it just works the way I want it [Then again, once the next version appears on a magazine, I will try it... Not into downloading things the dvd is on the latest edition of Linux User & Developer magazine available in WHSmiths and other retail outlets. thats where i got mine.
theres also the Getting Started with Fedora Core 5 (same guys as linux format magazine) that comes with 5 disks.

---

### Post by Gomez Akita on 2006-05-08
The argument is a little pointless everyone has different tastes.
For the origional question try as many distros as you are interested in and go with the one that best suits your needs and likes.

P.S. Dont discount some of the smaller distros either like Vector etc.

---

### Post by user1397 on 2006-05-09
I don't get why Fedora doesn't have a live cd on their official site, that doesn't attract as many people as for ex. ubuntu...is there an unofficial live cd or something?

---

### Post by ComplexNumber on 2006-05-09
[quote=erik1397]I don't get why Fedora doesn't have a live cd on their official site, that doesn't attract as many people as for ex. ubuntu...is there an unofficial live cd or something?[/quote] i thought they did. you may want to have a look [here]("http://fedoraproject.org/wiki/DerivedDistributions/LiveCDs") and [here]("http://clunixchit.blogspot.com/2006/03/livecd-enhanced-step-by-step.html").

---

### Post by user1397 on 2006-05-09
ah there they are. i'm downloading the basilisk live cd now (based on FC3:().   i just wish that fedora had an official live cd on their website that is FC5, not an older version...

---

### Post by ComplexNumber on 2006-05-09
[quote=erik1397]ah there they are. i'm downloading the basilisk live cd now (based on FC3:().   i just wish that fedora had an official live cd on their website that is FC5, not an older version...[/quote] why use FC3 when you can get FC5 [here]("http://www.fedora-france.org/modules/news/article.php?storyid=168"). it seems to have been built by a french person...hence the french language in the forum. i arrived there from the link [here]("http://fedoraproject.org/wiki/Kadischi/LiveCD?action=show&redirect=LiveCD").

---

### Post by user1397 on 2006-05-09
[quote=ComplexNumber]why use FC3 when you can get FC5 [here]("http://www.fedora-france.org/modules/news/article.php?storyid=168"). it seems to have been built by a french person...hence the french language in the forum. i arrived there from the link [here]("http://fedoraproject.org/wiki/Kadischi/LiveCD?action=show&redirect=LiveCD").[/quote]
Hmmm the first link doesn't work...

---

### Post by ComplexNumber on 2006-05-09
[quote=erik1397]Hmmm the first link doesn't work...[/quote] i don't see why not. have you tried the 2nd link and accessed it that way?
you will see the following:
>  01/03/2006 - [ChitleshGoorah]("http://fedoraproject.org/wiki/ChitleshGoorah") [[IMG]http://fedoraproject.org/wikidata/kindofblue/img/moin-www.png[/IMG] created]("http://www.fedora-france.org/modules/news/article.php?storyid=168") a livecd based on the Fedora Core 5 Test 3 which was available for download. Thanks to [JonFautley]("http://fedoraproject.org/wiki/JonFautley"). click on where it says "created".

EDIT: actually, i see what you mean now. you meant the link to the iso.

---

### Post by LanDroid on 2006-05-09
I'm interested in Security Enhanced Linux, developed by the NSA and included in Fedora.  Does this make a system more difficult to work with?  Does it provide significant security benefits?  Is Ubuntu considering incorporating SELinux?  Thanks for any info...

---

### Post by user1397 on 2006-05-09
[quote=ComplexNumber]actually, i see what you mean now. you meant the link to the iso.[/quote]
yea that's what i meant, my bad for not clarifying ;)
still I wouldn't like to download the FC5 test 3 cd, I would want the FC5 final release live cd, alas it does not exist...

---

### Post by kencoe on 2006-05-24
[QUOTE=erik1397]If you can't install .deb's or if it's very hard to, then i would find ubuntu to be more practical, as it has so many programs available (and almost all of them are deb's! :))[/QUOTE]
I personally prefer the Debian Base, but I DO have to point out that Fedora has a huge application base in the RPM repository. 

That said, linux mag, and distro watch both have thorough reviews. You should check what they say.

---

### Post by youthforlinux on 2006-05-24
I liked FC5 better than breezy but i liked dapper the best of them

---

### Post by bluenova on 2006-05-24
I used Fedora for 1 year before changing to Ubuntu a month ago. The reason for moving is because apt-get works soooo much better than yum and because fedora is bleeding edge software, and I wanted stability.

---

### Post by ComplexNumber on 2006-05-24
[quote=bluenova]I used Fedora for 1 year before changing to Ubuntu a month ago. The reason for moving is because apt-get works soooo much better than yum and because fedora is bleeding edge software, and I wanted stability.[/quote] i'm surprised at your switch given that you want stability. also, why don't you use apt-get on fedora if you're so tightly bonded with it. click [here]("http://rpm.pbone.net/index.php3/stat/4/idpl/2807830/com/apt-0.5.15lorg3-0.1.fc5.i386.rpm.html").


> 
fedora is bleeding edge software what? and ubuntu isn't? :confused:

---

### Post by bluenova on 2006-05-24
Because after looking at ubuntu and the friendly :) community there is here, ubuntu seemed the better option. Ubuntu claims on making stable releases every 6 months (not counting backports etc), where as Fedora always uses the most cutting edge software. Basically ubuntu seemed a much nicer all round package, and after having used it for a month, I know I made the right choice for me.

---

### Post by ComplexNumber on 2006-05-24
i agree about the community. i don't know if its to do with the way ubuntuforums is laid out and structured or what, but it has a more 'homely' appeal. fedora forums seems somewhat detached and cold.....more formal and clinical. both fedora and ubuntu use cutting edge software. if i remember corrctly breezy was released not long after FC4, yet breezy has gnome 2.12 whilse FC4 has 2.10.

---

### Post by youthforlinux on 2006-05-24
yea i didnt like yum

---

### Post by user1397 on 2006-05-24
i think i'll try fedora in the summer, but i doubt ill ever switch, cuz ubuntu is the best option for me right now.

---

### Post by benuski on 2006-05-26
I am right now reinstalling Breezy Badger after experimenting with FC5.  And I must say, the only advantage FC5 has over Ubuntu, in my opinion, is that its faster.  Other than that, Ubuntu works a lot better with all of my hardware, and it looks prettier.  I'm coming back to a place I know is better.

---

### Post by NeoGreen on 2006-05-28
I have a FC5 machine and an Ubuntu machine, they are both great.  I still like Ubuntu more because it has taught me alot about linux.:)

---

