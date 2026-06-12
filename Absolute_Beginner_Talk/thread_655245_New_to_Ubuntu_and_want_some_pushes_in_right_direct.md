---
title: "New to Ubuntu and want some pushes in right direction (long descriptive post)"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Humpty_newbie on 2008-01-01
G'day guys / gals,

Firstly I am excited to be trialing ubuntu for myself. I have installed and fiddled and that is about it but now i have done what a lot of you might think a dumb move but I have killed windows completely and installed ubuntu instead.

I am a complete newbie but have needs beyond that of normal noob i think. ...hope you can help (the idea was to jump in head first and learn it because i have to instead of when i have time to (I don't get spare time)).

Here are some of my more immediate needs (wishes really) and I am sure that you guys could help out:

**What I have already done and started to do:**
* Kill windows (I think i hear some cheering)
* Install a desktop versin of UBUNTU (not kubuntu or similar)
* Configured my wireless network ...twice (suprised at the ease)
* Setup my ICQ and MSN chats
* Setup 1 email account of approx 20 required
* Found my way here and done a bit of reading
* Found other usefull links and now have a bookmark list full of only ubuntu / linux stuffs

**What I don't know:**
* I haven't un-learned windows yet so some stuff might be hard to comprehend
* I don't fully understand how the partions work or the directory structure.
* How to install things not installed (I tried installing a game in a kubuntu install once and went down in flames....very disapointing, but again it is my lack of knowledge not any problems with kubuntu
* ...and i don't know everything else :D

**Goals:**
I am a Computer Technician by trade, I do web programming and USED TO do Visual Basic programming. I decided that most of what I NEED is free and available in Ubuntu. I wish to start installing ubuntu on EU computers but need to learn it first (hence the jump in the deep end)  ...in the end I'd like to be an Ubuntu guru and also do programming, perhaps even become a constructive user of the this community

**Resources Available to Me:**
* Internet
* Some mates
* No money (but i think i need a step-by-step dummies guide if anyone knows of a free one (not a copyrighted one reprinted for web and distributed illegally)


**My more immediate needs**
**1)** Email client most similar to MS Outlook (preferably with importability) I have started with evolution and a PST import failed
**2)** Web Editor similar to Dreamweaver (I understand NVU to be this, not yet installed it waiting on some feedback)
**3)** Webserver setup on my PC (no access from outside world required as it is for my benefit of design) (I am familiar with APACHE, PHP. and MySQL....would love to fiddle with some email stuff....couldn't find a free windows based email server to work with apache).
**4)** Later needs include that of a VM to install windows in case I get into a Jam and need to revert to something more familiar to me to get out of the jam)

**Will I need**:
* Firewall (other than NAT in router)
* Virus Protection
* Spyware Protection

**Wow,** that was long, I really hope that you can help with those more immediate needs (as I need them for work when i am called upon and have no idea when that will next be, however the bloke I work for (in another state) uses Linux and would be able to help me with config issues with the webserver side of things.

I look forward to replies and also to be barked at as a noob, haze me baby haze me.
-Humpty

---

### Post by hopelessone on 2008-01-01
> **Humpty_newbie said:**
> 

**Will I need**:
* Firewall (other than NAT in router)
* Virus Protection
* Spyware Protection


Naaa mate Linux dosen't ave spyware or Viruses...it it does she only infects home user account...so far i aint ad none...

firewall...Ubuntu takes care of that... i have a password upper lower case numbers and special characters about 15 characters long...

---

### Post by Humpty_newbie on 2008-01-01
sweet, thanks for making fun of my (written) accent, made me feel more welcomed :D

---

### Post by Xavieran on 2008-01-01
You *do* hear cheering! Go mate!

You could use thunderbird for email 
```
sudo apt-get install thunderbird
```

Apart from NVU there is also Komposer which I personally have not tried,though NVU worked pretty well for me (I am not a web-anything so your needs may be different)
Other people will probably fill you in on other apps though I know VirtualBox is a pretty good free VM client...

Don't be afraid to ask questions but always remember the golden rule :"Search before you post":)

---

### Post by oldb0y on 2008-01-01
Go on m8:-D
Here is a nice page for you: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
And don't be afraid of asking any "newbie" questions here on the forum, it will only help you.

---

### Post by candtalan on 2008-01-01
Welcome!
I think you are brave to cast windows off to abruptly (!) it took me ages to fully detox :-(

Consider you will get mainstream support here best when using a mainstream distro such as straight  Ubuntu or (I use) Kubuntu. Also xubuntu-desktop, edubuntu-desktop. Easy to use *all* with the desktop for each installed (such as kubuntu-desktop package). The advantage is you may get less frustration if you stay mainstream initially. Also advantage is you see various levels of environment available for your potential customers.

You can also examine partitions with a live CDs such as parted magic live CD or gparted live CD - do not change anything, just look and question.

Directory structure - not too important initially. Important places are  /etc/fstab for mounting filesystems, and /boot/menu.lst and /etc/X11/xorg.conf and of course /home/user
also see the Linux Documentation Project. Note you can set view to see hidden files.

Take notice of file permissions, they are a serious part of linux and very much more powerful than in ntfs.

Installing stuff - a totally different culture - beware: initially mostly use add/remove programs in the main menu, otherwise use the package manager (synaptic for example). These offer choices of many thousands from the compatible 'repositories'. If you later feel inclined then use .deb packages (use synaptic to install them?). Later still, consider compiling from source, and use a bit more experience, and you will be more like on your own.

No money - no problem. Get everyone to give you their junk hardware and most of it will be good with 'ubuntu! (I did!)   :-)

Antivirus - not used in ubuntu except to clean windows stuff from windows viruses preventing passing along to other windows using unfortunates.
Firewall - important. Iptables is already built in with ports closed by default but if you wish, install a gui frontend such as say firestarter.

hth. good luck!

---

### Post by .nedberg on 2008-01-01
I like Quanta for web-editing. It is a part of the kdewebdev-package.

Welcome to the world of Ubuntu!

---

### Post by Xavieran on 2008-01-01
You will come to love the linux directory structure...it is so beautifully organized...whenever I have to use windows (Never on my computer...at a friends house etc.) I find it hard to navigate around because the Directory structure is so disorganized...and nothink is labelled correctly ...

---

### Post by snakeeyes on 2008-01-01
> **Humpty_newbie said:**
> G'day guys / gals,

Firstly I am excited to be trialing ubuntu for myself. I have installed and fiddled and that is about it but now i have done what a lot of you might think a dumb move but I have killed windows completely and installed ubuntu instead.

I am a complete newbie but have needs beyond that of normal noob i think. ...hope you can help (the idea was to jump in head first and learn it because i have to instead of when i have time to (I don't get spare time)).

Here are some of my more immediate needs (wishes really) and I am sure that you guys could help out:

**What I have already done and started to do:**
* Kill windows (I think i hear some cheering)
* Install a desktop versin of UBUNTU (not kubuntu or similar)
* Configured my wireless network ...twice (suprised at the ease)
* Setup my ICQ and MSN chats
* Setup 1 email account of approx 20 required
* Found my way here and done a bit of reading
* Found other usefull links and now have a bookmark list full of only ubuntu / linux stuffs

**What I don't know:**
* I haven't un-learned windows yet so some stuff might be hard to comprehend
* I don't fully understand how the partions work or the directory structure.
* How to install things not installed (I tried installing a game in a kubuntu install once and went down in flames....very disapointing, but again it is my lack of knowledge not any problems with kubuntu
* ...and i don't know everything else :D

**Goals:**
I am a Computer Technician by trade, I do web programming and USED TO do Visual Basic programming. I decided that most of what I NEED is free and available in Ubuntu. I wish to start installing ubuntu on EU computers but need to learn it first (hence the jump in the deep end)  ...in the end I'd like to be an Ubuntu guru and also do programming, perhaps even become a constructive user of the this community

**Resources Available to Me:**
* Internet
* Some mates
* No money (but i think i need a step-by-step dummies guide if anyone knows of a free one (not a copyrighted one reprinted for web and distributed illegally)


**My more immediate needs**
**1)** Email client most similar to MS Outlook (preferably with importability) I have started with evolution and a PST import failed
**2)** Web Editor similar to Dreamweaver (I understand NVU to be this, not yet installed it waiting on some feedback)
**3)** Webserver setup on my PC (no access from outside world required as it is for my benefit of design) (I am familiar with APACHE, PHP. and MySQL....would love to fiddle with some email stuff....couldn't find a free windows based email server to work with apache).
**4)** Later needs include that of a VM to install windows in case I get into a Jam and need to revert to something more familiar to me to get out of the jam)

**Will I need**:
* Firewall (other than NAT in router)
* Virus Protection
* Spyware Protection

**Wow,** that was long, I really hope that you can help with those more immediate needs (as I need them for work when i am called upon and have no idea when that will next be, however the bloke I work for (in another state) uses Linux and would be able to help me with config issues with the webserver side of things.

I look forward to replies and also to be barked at as a noob, haze me baby haze me.
-Humpty


Hi, ok first of all welcome to Linux. You will need a firewall only, no need for virus or spyware protection. A good firewall is firestarter, it provides a GUI interface for iptables which is Linux's built in firewall.
"sudo apt-get install firestarter"

In Linux I have 3 partitions, one is the root partition with the "/" mount point, this is where Linux will be installed. This partition is usually not more than 20 gb maximum and this is where most of ur programs except ones u compile your self will be installed as well. The second partition I have is the "/home" partition which is like My documents in Windows, this partition has most of my disk space and this is where I keep or u should keep all ur data and compiled programs. The third partition is the swap partition with the "swap" mount point. This is like virtual memory in Windows and mine is of 2 gb. Usually the size of this partition is twice ur ram and it is necessary for power management features like suspend to disk or u may be more familiar with hibernate.

An excellent virtual machine software is already in the repositories and its called virtual box, u can install it by typing:
"sudo apt-get install virtualbox-ose"

In Linux to do things that require administrative access we use the command sudo. You may already know this for example when u want to configure pppoe u type in konsole:
"sudo pppoeconf"
Configuring pppoe is requiring administrative access so u use sudo. This command should be easy for u to understand and I hope u don't find this sudo stuff difficult cause Mac OS X uses this command as well and is the one of the easiest OS around.

For something like outlook why not try Evolution or Iceape Mail composer should be in the repos as well and though I don't use them they should be easy enough to use.

You may also want to use synaptic to install applications and in ur applications menu there should be something like add/remove programs to install other software, sorry I am a kde user and don't remember the gnome interface much.

You will want to be able to play some multimedia codecs such as mp3's as well right and have flash and java so I recommend u install:
"sudo apt-get install ubuntu-restriced-extras"
You can search for this in synaptic as well.

You may want a p2p program as well, u can use frostwire which is in the repos or u can try Limewire, I am using it without problems and u can a .deb package from:
[http://www.limewire.com](http://www.limewire.com)

Remember Ubuntu is a debian based distribution and uses .deb packages to install software as well if u r not using the repositories. You can also convert .rpm packages into .deb packages if u want using a command line program called Alien.
"sudo apt-get install alien"

You can use Wine for installing some windows software.
"sudo apt-get install wine"

You must already have your 3d effects enabled, if not install ur vga card drivers from the restricted drivers manager and enable 3d effects. To configure compiz fusion u need:
"sudo apt-get install compizconfig-settings-manager"

Oh yeah if u want Windows media codecs support and encrypted dvd play back then add the medibuntu repositories or see the community documentation for instructions.

Sorry if my post is a bit long but this should answer most of ur questions.

Welcome to Linux! :)

---

### Post by jken146 on 2008-01-01
Apache, PHP and MySQL will be very happy on a Linux box.  They're all in the repos.

---

### Post by Humpty_newbie on 2008-01-01
Okies,

You guys have been great, atm I have decided to do the whole mail thing first and am going  to go with thunderbird (for now anyway) for familialarity reasons)

It has been a huge headache trying to do it and as of yet unsuccesfull, is a big turn off, but I think it still boils down to my windowness more than anything else.

Decided to goto bed and install Kubuntu in the morning, then at last minute a mate got me change the Settings > repositories in synaptic, I had nothing ticked, now we have ticks left right and centre (still only 1/2 understand this part atm)

From there i went to add/remove (as i read in an above post), now there are no error messages, no messages confusing me by telling me that someone has chosen not to support me at this time, instead the install of thunderbird was quick and painless,


....although i would have prefered do it via command line, not to worry I can do that for the next thing i choose.

...staying with ubuntu / gnome at this stage, will configure emails in morn and then i think i am a happy bunny and ready to read and soak in your messages a bit more.

you lot are GREAT :D

---

### Post by bapoumba on 2008-01-01
> **Humpty_newbie said:**
> 

From there i went to add/remove (as i read in an above post), now there are no error messages, no messages confusing me by telling me that someone has chosen not to support me at this time, instead the install of thunderbird was quick and painless,


....although i would have prefered do it via command line, not to worry I can do that for the next thing i choose.

You can have a look at your repo config file from the terminal:
```
cat /etc/apt/sources.list
```

And run the update/install/upgrade with apt-get:
```
man apt-get
```
Basically:

Read the sources.list file:
```
sudo apt-get update

```
Upgrade:
```
sudo apt-get upgrade
```
Install a package named foo (this is just an example):
```
sudo apt-get install foo
```

Please get yourself familiar with the root permissions with Ubuntu:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Have fun!

---

### Post by blueridgedog on 2008-01-01
> My more immediate needs
1) Email client most similar to MS Outlook (preferably with importability) I have started with evolution and a PST import failed
2) Web Editor similar to Dreamweaver (I understand NVU to be this, not yet installed it waiting on some feedback)
3) Webserver setup on my PC (no access from outside world required as it is for my benefit of design) (I am familiar with APACHE, PHP. and MySQL....would love to fiddle with some email stuff....couldn't find a free windows based email server to work with apache).
4) Later needs include that of a VM to install windows in case I get into a Jam and need to revert to something more familiar to me to get out of the jam)

Email you seem to have sorted out.  I have yet to get a pst into evolution, but hope one day there is a way.  Some have had success importing it into Tbird, then in to evolution. 

A web editor similar to Dreamweaver...I think NVU is deprecated in feisty.  You may be limited to Komposer.  However, if you are accustomed to dreamweaver you will be disappointed.  It is great, but most linux web development is not WYSIWYG (IMHO).

That said, I find that the environment is great for web development.

---

### Post by gn2 on 2008-01-01
This morning I switched from a dual-boot of Xp Home and Xubuntu 7.04 32-bit to a single booted Xubuntu 7.10 64-bit, wiping away my Xp partitions.

It has taken me a year of using Ubuntu to get to the stage where I no longer need or feel any desire to have Windows on my PC.

Give Ubuntu a try, there's nothing to lose and much to gain. :)

---

### Post by hyper_ch on 2008-01-01
As Webeditor you can try "Kompozer" --> it's in the repos and also a WYSIWYG editor.

And for setting up LAMP. If you'd like sort of a total ISP environment check this out:
[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

### Post by bobpur on 2008-01-01
* No money (but i think i need a step-by-step dummies guide if anyone knows of a free one (not a copyrighted one reprinted for web and distributed illegally)

I have a book called called "Ubuntu Hacks" that has been pretty helpful to me in my early noob days. It's, now, two years later and I'm only in my late early noob days:D :D

OOPS!  "Ubuntu Hacks" is about $30.00 American. The forums are free (and probably your safest and best bet).

Good Luck!

---

### Post by Linuxratty on 2008-01-01
Hi and welcome. I'm also Windows free...
  I thought you might be interested in getting a Linux book to help you along your way. 
 It's Linux Pocket Guide
by Daniel J. Barrett 
Enjoy!
Linky:
[http://tinyurl.com/2999n9](http://tinyurl.com/2999n9)

---

### Post by Zimmer on 2008-01-01
[http://www.linuxnewbieguide.org/chap11.php](http://www.linuxnewbieguide.org/chap11.php)

The ultimate Linux Newbie Guide may address some of your general Linux questions.

The link above refers to the file structure.

---

### Post by dr.silly on 2008-01-01
Aptana is a must see for all web development.

aptana.com

---

### Post by maniac_X on 2008-01-01
If you use/like Dreamweaver (and most web-developers do), Dreamweaver 8 is on the Platninum list for apps that run fairly well when using WINE. [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by ShelJ on 2008-01-01
Despite what my profile says, I'm not totally new to Linux (I keep Linux Bible 2005 on my desk).  After about a year using Ubuntu, I went back to Wind'hos b/c certain features i _thought_ I needed.  Then i spent about a year or so complaining everyday about it  ...  :mad:  So, I switched back to Ubuntu (I'm currently using Xubuntu).  The only thing is that it does require a little tweaking, but I'm happy, and I'm **_*NEVER*_** going back!

---

### Post by dr.silly on 2008-01-01
i run dreamweaver 8 and flash 8 in wine work like a charm

---

### Post by Humpty_newbie on 2008-01-02
I have cut all other plans short and installed a VM (going with the easliy accesible VirtualBox) to install windows for the SOLE purpose of trying to recover my emails :(

...this is what happens when you jump head first into stuff. :D

I do however intend to not only kill the XP install but fully remove the VM when done to avoid any temptation to use the more familiar windows.

(BTW have read all the posts, and pretty much want to say thanks to everyone, would there be a point in clicking "thanks" for every single post?)


...next step would be WebDev applications and then LAMP.......LAMP will be a fun excercise :D

---

### Post by blueridgedog on 2008-01-02
I was considering some way to get my PST into my current program and just decided to move on.  My PST has emails in it back to 1994.  Call it a mid life crisis, but they will be there for me one day when I need them.  Right now, I am starting clean and fresh.

---

### Post by Humpty_newbie on 2008-01-02
> **blueridgedog said:**
> ....decided to move on.


Yep hit that point about an hour ago, In fact I couldn't even import my PST into outlook on my VM.  Possibly I installed an earlier version or something but i don't care anymore, with me things have a time value, and it's not worth spending anymore time, am also deciding if to stick to webmail instead, because if i ever revert it won't matter :D

At this stage I have moved on to installing NVU (now gotta workout how to do it LOL, I DL the tar.bz2 and extracted to my home folder....sigh, comfort zone now exceeded :D

---

### Post by gn2 on 2008-01-02
> **Humpty_newbie said:**
> At this stage I have moved on to installing NVU (now gotta workout how to do it LOL, I DL the tar.bz2 and extracted to my home folder....sigh, comfort zone now exceeded :D

Just install Kompozer using either Add/Remove or Synaptic Package Manager.

---

### Post by candtalan on 2008-01-02
> **gn2 said:**
> Just install Kompozer using either Add/Remove or Synaptic Package Manager.

Note that Kompozer is the successor to NVu which is now beginning to become obsolete

---

### Post by Techwiz on 2008-01-02
Welcome to Ubuntu!
For your mail you could use Thunderbird (I use Evolution, but I hear that Thunderbird works really well).
And don't worry about "unlearning windows" Ubuntu is relatively straightforward but if you run into something you can't handle don't hesitate to post!
Best of luck to you!

---

### Post by rubicon on 2008-01-02
> I tried installing a game in a kubuntu install once and went down in flames.Wow! Guy, you do have a talent!

For programming I recommend Python since it is powerful, easy to learn and understand and looks like VB.

If you want virtual machine to run Windows, look closer at VirtualBox and VMWare. All this are in repos.

And yep -- welcome to the Ubuntu!

---

### Post by rubicon on 2008-01-02
Oh, I almost forgot. It is rare but happen. If you want to run a windows program in your Ubuntu without starting and booting virtual machine etc, you can use Wine (Windows compatibility layer, briefly -- Windows emulator).

Get it at [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by t0p on 2008-01-02
> **rubicon said:**
> Oh, I almost forgot. It is rare but happen. If you want to run a windows program in your Ubuntu without starting and booting virtual machine etc, you can use Wine (Windows compatibility layer, briefly -- Windows emulator).

Get it at [http://www.winehq.org/](http://www.winehq.org/)

**BOOO!!!**  Wine is crap!!  :)

---

### Post by Humpty_newbie on 2008-01-02
Probably the most important question I should have asked:

Pre Question Information:
On windows I was never too concerned about lossing data due to a system crash, I could just chuck the HDD (if it worked) into another PC and copy most stuff over,

Question:
Given the file permisions and stuff with linux what should I do here?  Should I create a fat(32)/ntfs partition and make my home folder in there? or in reality could I just chuck this HDD into another linux machine and copy it like I would have done with windows?

...the point being that I only ever protected my windows from ppl loging in (and we all know that can be by-passed).

I NEVER protected the files because too many times I have had lost files from EU that is due to them not knowing thier password and having password protected folders or from same thing but due to system crash.

BTW: doing the LAMP thing today, That will be fun, but using Synaptic to do it. ...a greater understanding would probably help but what the hey, nothing important on there

-Humpty

---

### Post by Humpty_newbie on 2008-01-02
Okies,

Need the help now, I need some sort of I'm-an-idiot-step-by-step-understand-it type of tutorial on LMAP.  (well the MAP part anyway)

I have installed:
Apached
PHP
MySQL
PHPMyAdmin

I have NO idea what the hell I did and where what went.  I did manage to find a www folder which appears to be apache server / local host :D

For that I am greatfull, the rest I am unsure about.


Would now be a better time to learn the directory structure and where everything goes etc BEFORE I get to into the (L)AMP stuff?

---

### Post by Xavieran on 2008-01-02
I'd say to make an ext3 home partition...this is extremely useful if you break your system...you can just reboot and mount your previous home partition as /home...

That might be helpful with LAMP ...if you break anything ,at least you have all your configs etc.

Have Fun!:)

EDIT:To execute those apps just type in their name in the command line...sometimes names differ but you'll get used to it...
P.S.To create your home folder after installation just follow this tutorial by aysiu:[http://psychocats.net/ubuntu/separatehome]("http://psychocats.net/ubuntu/separatehome")

---

### Post by blueridgedog on 2008-01-02
> **Humpty_newbie said:**
> 
Need the help now, I need some sort of I'm-an-idiot-step-by-step-understand-it type of tutorial on LMAP.  (well the MAP part anyway)

You might start here:

[http://www.onlamp.com/](http://www.onlamp.com/)

But, tell me what you know in the list.  Do you have any experience with Perl or PHP?

If this is all new to you, then I suggest an order of things.  You learn apache2 and Perl at the same time:

[http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)

[http://www.oreilly.com/catalog/learnperl4/index.html](http://www.oreilly.com/catalog/learnperl4/index.html)

[http://www.oreilly.com/catalog/cgi2/index.html](http://www.oreilly.com/catalog/cgi2/index.html)

Then you move on to PHP and MySQL:

[http://www.oreilly.com/catalog/learnphpmysql/index.html](http://www.oreilly.com/catalog/learnphpmysql/index.html)

I would start by looking in /etc/apache2/

---

### Post by Humpty_newbie on 2008-01-02
> **blueridgedog said:**
> 
But, tell me what you know in the list.  Do you have any experience with Perl or PHP?

If this is all new to you, then I suggest an order of things.  You learn apache2 and Perl at the same time:

G'day blueridgedog:

Some info:
I had WAMP (I guess that is what you call AMP on windows)

Apache, Installed it, had help with the CONF file.

PHP: Installed it, can't recall if i did any config alterations. I have done plenty of PHP programming however I am by no means an expert (after years of programming stuff I only just found out 2 months ago how to use classes)

MySQL: Installed it with some help, learned a bit of command line stuff but really used PHPMyAdmin or MySQL Administrator to do stuff in it.

From there I did a lot of PHP / (My)SQL programming for websites and the likes.

So from a WebDev point of view I can do these things, from an admin point of view I have little idea at all.

To save things onto my webserver I'd save them in c:\program files\apachegroup\apache2\htdocs\

so this is why I am a little lost, I edited the windows hosts files to give my localhost a domain name,

so really I guess I need to start from the begining,

Short Term:
Start using apache to test stuff that I do (need php for that too) and use mysql again to test the stuff that I do (stuff = webdesign)

Long Term:
Learn how to administer (command lineand remote logins as well) LAMP for the purposes of webhosting and perhaps even get into some radius stuff)

Any suggestions / recomendations from there?

---

### Post by blueridgedog on 2008-01-02
> **Humpty_newbie said:**
> G'day blueridgedog:

From there I did a lot of PHP / (My)SQL programming for websites and the likes.

So from a WebDev point of view I can do these things, from an admin point of view I have little idea at all.

Short Term:
Start using apache to test stuff that I do (need php for that too) and use mysql again to test the stuff that I do (stuff = webdesign)

Long Term:
Learn how to administer (command lineand remote logins as well) LAMP for the purposes of webhosting and perhaps even get into some radius stuff)

Any suggestions / recomendations from there?

OK, look at the apache link I sent, but:

you will configure it via the files:

/etc/apache2/apache2.conf
and
/etc/apache2/sites-enabled/000-default
(which is lust a link).

You can add other sites using the "sites-available" and "sites-enabled" directories, using the defaults as an example.

Your default web root will be in /var/www and you can place files there.

If your server is running you can access the files via:

[http://localhost](http://localhost)

The default install should work out of the box.

Starting/Stopping apache:

/etc/init.d/apache2 start
/etc/init.d/apache2 stop
/etc/init.d/apache2 restart

If things don't work, 

tail /var/log/apache2/error.log

Please the attached file there and access it with:

[http://localhost/test.php](http://localhost/test.php)

And you should get a test your php rig.

From there, code away.

---

### Post by blueridgedog on 2008-01-02
Second attempt at posting the file.

Rename it test.php.

---

### Post by bomanizer on 2008-01-03
advice #1:

Be patient and make backups. I've learned this the hard way:-|

---

### Post by rubicon on 2008-01-03
**_tOp_** > **BOOO!!!**  Wine is crap!!  :smile:Arguments, please.

---

### Post by adam.tropics on 2008-01-03
Free training.....download the [course materials]("https://wiki.ubuntu.com/Training") and give it a go! (available in pdf)

---

### Post by Humpty_newbie on 2008-01-03
> **blueridgedog said:**
> OK, look at the apache link I sent, but:......

Thanks for that I am familiar with the phpinfo() command / function / feature, I will check out all that other stuff in the morning and make notes of the console commands you gave me.


> **bomanizer said:**
> advice #1:

Be patient and make backups. I've learned this the hard way:-|
....yeah already thought that a good idea at this stage

I have even gone to the point of deciding not to use any email client, instead use webmail, not sure how that will go, but I have control over most of my mailbox sizes and most of the webmail is squirelmail.


> **adam.tropics said:**
> Free training.....download the [course materials]("https://wiki.ubuntu.com/Training") and give it a go! (available in pdf)
I have only had a partial look, but looks like the sort of thing i am after now and into the future with all my 'training' needs in all aspects of linux.

The only problem with that is it appears to be a little more EU orientated.  ...i do realise though that at this stage i am just an EU....

---

### Post by zach12 on 2008-01-03
For web programing try[ KompoZer]("http://www.kompozer.net/")

---

### Post by adam.tropics on 2008-01-03
Like anything else new though, reinforce the basics, and the rest will fall into place fairly quickly.

---

### Post by Humpty_newbie on 2008-01-03
> **adam.tropics said:**
> Like anything else new though, reinforce the basics, and the rest will fall into place fairly quickly.

Yes I am following the tutorial (instructor version) and although I find the way it's written a little bit beyond what I need I am actually enjoying the learning and have created an excel spreadsheet for win vs ubuntu differences (that I have come accross so far).  It will be little lacking i think, but it is a start.

....I'm also learning a bunch of other interesting information that is just nice to know as a trivial thing.

Point is I have gone through some changes:
Anticipation
Happiness
Want (for windows)
Need (for windows, but that was regarding the retrieval of my emails, a shocking failure)
Acceptence (that the last two were useless)
Withdrawal (again windows, just for that something familiar)
Acceptence (again)
and then back to happiness and joy, and excitment too.

So many emotions from a bunch of comprehendable colours on a PC Monitor in just 2 days :D

---

