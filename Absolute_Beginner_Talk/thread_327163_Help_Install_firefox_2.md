---
title: "Help Install firefox 2"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by madHatterCutsTheChatter on 2006-12-28
HI all! Im v.v new to Linux. I wanted to install firefox 2 on my comp.

Why isnt firefox 2 in my repository?(I've enabled universe & multiverse).
It only shows firefox 1.5.:( :( :( 

I also tried the usual way of downloading the tar from Mozilla's website and did everything according to ---   [http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories).
But it shows----- make: *** No targets specified and no makefile found.  Stop.
& nothing happens after that.

Help](*,)

---

### Post by KenSentMe on 2006-12-28
You probably have Ubuntu 6.06 Dapper Drake installed. That comes with Firefox 1.5. There's a newer version of Ubuntu called 6.10 Edgy Eft and it has Firefox 2 in it's repositories.

It's not hard to upgrade from Dapper to Edgy, just check here: [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by deadgobby on 2006-12-28
here is a link to install FF 2.0
[http://psychocats.net/ubuntu/firefox](http://psychocats.net/ubuntu/firefox)
Here is link to get the newest Flash Player installed.
[http://www.ubuntuforums.org/showthread.php?t=279990](http://www.ubuntuforums.org/showthread.php?t=279990)
Gobby

---

### Post by Sweet Spot on 2006-12-28
I have no interest in updating to Edgy, but would like to know why there has been no signs of FF 2.0 making it to Dapper. After all, Dapper is supposed to be LTS right ? So why is it taking so long for this ? It makes no sense since Edgy is technically supposed to be more experimental than anything, while Dapper is the official stable build. 

This is one of the things which is driving me crazy about Ubuntu atm. I'd really like not having to rely on waiting for a repo release, and would rather be able to use the real/direct FF upgrades (as built by the FF team, and not a port), but as that's not going to happen for me right now, I've no choice and am at the mercy of the coders. ](*,)

Please, I never ask for anything..... *words fall like snowflakes on a lake upon a foggy night*

---

### Post by KenSentMe on 2006-12-29
> **Sweet Spot said:**
> I have no interest in updating to Edgy, but would like to know why there has been no signs of FF 2.0 making it to Dapper. After all, Dapper is supposed to be LTS right ? So why is it taking so long for this ? It makes no sense since Edgy is technically supposed to be more experimental than anything, while Dapper is the official stable build. 

Well you're not the only one with this problem and surely not the onlyone who has questions about Firefox 2 not being in Dapper repositories. I believe Firefox can't be backported from Edgy to Dapper because it needs other packages need to be backported too. That's the official backporting policy, but i think they should make a exception for this.

---

### Post by manutdfan2850 on 2006-12-29
so you are saying firefox 2.0 can not be installed on Dapper? 

that doesn't make sense.

---

### Post by _simon_ on 2006-12-29
Just because something is not in the official repository does not mean it's the end of the world.

You could just download it from the mozilla website, extract the folder and place it in /home then link to it. - It really is THAT simple. As regards plugins, I find it easier to just copy and paste them from the plugin folder in your existing firefox to the plugin folder in the new one.

---

### Post by manutdfan2850 on 2006-12-29
> **_simon_ said:**
> Just because something is not in the official repository does not mean it's the end of the world.

You could just download it from the mozilla website, extract the folder and place it in /home then link to it. - It really is THAT simple. As regards plugins, I find it easier to just copy and paste them from the plugin folder in your existing firefox to the plugin folder in the new one.

i donwloaded it from the website. extracted it. but then i dont know what to do. could you explain it a little better? 
i want to install 2.0 and then uninstall 1.5 completely from my system.

---

### Post by _simon_ on 2006-12-29
Once extracted just copy the entire folder to where you want it, for example /home

Your existing plugins if you have them installed will be in /usr/lib/firefox/plugins/ just copy and paste them into the plugins folder in your new firefox e.g. /home/firefox/plugins/ If they are links only then you either need to create new ones or locate where the plugin is and copy the actual plugin.

To create sym links in case you don't know:

ln -s location destination

e.g. ln -s /usr/lib/totem/libtotem-basic-plugin.so /usr/lib/firefox/plugins/

Now all you need to do is change any existing Firefox links / icons you may have to point to the new location. 

So, from terminal:

cd /usr/bin
sudo rm firefox
sudo ln -s ~/firefox/firefox

As to uninstalling the old firefox, I guess you could do it via Synaptic or manually remove it. Personally I'm using Firefox 3 Alpha 1, so I've kept Firefox 2 to fallback on.

---

### Post by dancallo on 2006-12-29
Madhatter,

Have you tried the Firefox 2 [Download site for Linux i686]("http://www.mozilla.com/en-US/firefox/all.html")?  The download link for English, for instance, is firefox-2.0.0.1.tar.gz.

---

### Post by jpneal on 2006-12-29
I installed Firefox 2 on Dapper by downloading from [www.getfirefox.com](www.getfirefox.com)

Then extract to your home folder (creates a folder called firefox), and replace the symbolic link:-

cd /usr/bin
sudo rm firefox
sudo ln -s ~/firefox/firefox firefox

---

### Post by KenSentMe on 2006-12-29
There is also a guide for install FF 2 on Dapper here: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by triplep on 2006-12-29
Ok, I've been under the impression that just uncompress the tarball in an arbitrary location ($HOME for example) (re)move ~/.mozilla and execute the binary ~/firefox/firefox in this case. 

I keep getting 1.5.0.8 loading, even after modifying the moz_home path in the firefox script.

There is something here that i'm just not understanding?

---

### Post by mastergunner on 2006-12-29
Simon I am new to Linux and having the same problem. Could you please tell me what I supposed to type exactly cause I was a little lost after I download and extract FF 2. Thanks.

---

### Post by mastergunner on 2006-12-29
What is the home folder and how do I extract it to there. I am lost on this as wel.

---

### Post by ieee488 on 2006-12-29
any chance that there will be an update for the Ubuntu Firefox without having to go through all the hassle?

---

### Post by KenSentMe on 2006-12-29
> **mastergunner said:**
> What is the home folder and how do I extract it to there. I am lost on this as wel.

Your personal files/settings are saved in your personal folder, because it's in /home/yourname it's called the home folder.

---

### Post by _simon_ on 2006-12-29
> **mastergunner said:**
> Simon I am new to Linux and having the same problem. Could you please tell me what I supposed to type exactly cause I was a little lost after I download and extract FF 2. Thanks.

I am assuming that you are using Ubuntu 6.06, your profile does not say.

To simply things for now lets forget the plugins altogether.

Ok, so you have extracted Firefox2.

I'll assume you currently have a folder on your Desktop saying "firefox"

If you go to your Gnome Menu and click PLACES, you will see the first item is "Home Folder" so select that and Nautilus should open up with the current contents of your home folder.

All you need to do is move the firefox folder from your desktop into your Home Folder.

Inside the firefox folder you will see a file simply labled as "firefox", that is the executable. You can double click it and choose RUN to start firefox.

To update your links:

You can either from terminal do:
cd /usr/bin
sudo rm firefox
sudo ln -s ~/firefox/firefox

The above path may be different, it depends what you have called the folder and I think it's case sensitive as well.

Note: Make sure that you close any instances of your older firefox before trying to run the new one.

You can also do this with Firefox 3 Alpha 1 (Gran Paradiso) if you want.

---

### Post by IanGB on 2006-12-29
You do not need to remove the FF from your computer to install FF2. it does it automatically. Just download the linux version and run it.

---

### Post by Frak on 2006-12-29
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
aysiu put that howto together, works perfectly for me.

(P.S. FF2 isn't in Ubuntu Repos for Dapper, because Dapper is built for stability, and the general nature of packages in Ubuntu, it won't be in the main repo's, may be in the backports.)

---

### Post by manutdfan2850 on 2006-12-29
thanks for your help

---

### Post by Sweet Spot on 2006-12-29
> **_simon_ said:**
> Just because something is not in the official repository does not mean it's the end of the world.

You could just download it from the mozilla website, extract the folder and place it in /home then link to it. - It really is THAT simple. As regards plugins, I find it easier to just copy and paste them from the plugin folder in your existing firefox to the plugin folder in the new one.

While I agree that it's not the end of the world, (and I really don't like drama) I can't help but feel a bit of disdain in regards to the way a supposedly LTS OS is being treated as if it's more of a PTS (part time) one, and that perhaps people (especially newcomers)  who aren't yet comfortable with switching over to a (said) experimental build of Ubuntu are not able to have access to (and here's the critical point) the most recent and **stable** version of one of the most widely used web browsers amongst this community. 

Every time I use tabbed browsing in Ubuntu now, TBP are broken, and it bugs the hell out of me. It's not like that in Windows, and I'm starting to resent that. I appreciate the step by step tabs on how to get FF 2 up and running, but I don't WANT to have to jump through hoops when the term LTS is constantly touted and in my face. 

Doug

---

### Post by Sef on 2006-12-29
Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

### Post by Sweet Spot on 2006-12-29
> **Sef said:**
> Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

This seems to allude the point I was trying to make though. Again, for someone such as myself with a bit of tech savvy, I can of course get through a self install when I have the time to do it, but where the problem lays is in the assumption that a newb will be able to, or will want to do it. 

So many people here are always on about how easy Ubuntu is, and how it is a great replacement for Win XP etc, and for the most part I'd agree. But if claims are going to be made like that, efforts to keep that reputation solid are absolutely necessary, and that has to include essential upgrades to the likes of major web browsers. 

I was just reading another thread which started I think back in May, which deals with North East members spreading the word about Ubuntu etc. I think that's a great idea, but with all the goals set in place, I also think it's a bit gratuitous/arrogant to take on such daunting tasks without the guarantee that even the most simple things are tended to, in order to make the experience of using Ubuntu for the FIRST TIME, (that IS the goal, to spread the word of Ubuntu to as many new users as possible, right ? After all, members of the Linux community in general, surely will have heard of it) an easy transition, and one that will further spread the word. 

I'm just speaking as someone who HAS recently migrated over from XP, so it's not like this is all out of my behind. I'm thinking like a fairly new Ubuntu user, who hasn't really booted to XP but once or twice (issues w/dvd shrink, which wound up being a bad DVD anyway) in the past 4 months. And although I CAN get things going myself, the plain and simple truth is that I'd rather have an automatic update do it for me. 

And that is important, because there are Win users whom are FAR more lazy than I am, and a lot of them are the target audience which you guys are trying to reach, I think. 

Doug

P.S. Monkey blog seems to be down at the moment.

---

### Post by kspringer on 2006-12-30
aysiu has a script that automates the installation process:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

(HTML is off. Don't see why but...? Copy paste will do it Unless HTML is actually on)

I used the script today, using aysiu's instructions, and it worked great.

My two cents.

---

### Post by travelerthe on 2007-01-02
I upgraded from Dapper to Edgy today.
According to Synaptic I have Firefox 2 installed but everytime I launch from the Applications menu or the panel I launches Firefox 1.5. 

How can I correct this?

---

### Post by Quillz on 2007-01-02
> **manutdfan2850 said:**
> so you are saying firefox 2.0 can not be installed on Dapper? 

that doesn't make sense.
It's very possible to install Firefox 2.0.0.1 and use it, which would be recognized by the command "firefox." And at the same time, you would prefer the bundled Firefox (1.5.0.8) by running the command "firefox.ubuntu"

---

### Post by geo_bio on 2007-01-02
I just got Firefox 2 on Drapper 6.06

Just choose your language from here:
[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

Save it to your desktop; _unzip it_, and there should be a file called "firefox" and "firefox-bin". FIRST: Try to doubleclick on "firefox", and it should run. If not, then doubleclick on "firefox-bin", and then "firefox" after it does whatever it does. It worked for me. I can't say thats the "proper" way to do it since I am a noob at installing things that dont come in the repositories, but I know it works.

---

### Post by Larry Roll on 2007-01-02
**What would be the virtues of upgrading to Firefox 2.0?  What does it do that FF 1.5 doesn't?  **

---

### Post by travelerthe on 2007-01-02
I want to take advantage of the changes to the tab system & the built in spell checker.

---

### Post by Frak on 2007-01-02
> **Larry Roll said:**
> **What would be the virtues of upgrading to Firefox 2.0?  What does it do that FF 1.5 doesn't?  **
On my end, more crashes, and the inability to download things, because the OK button is greyed out, other than that, new tab system and spell checker as stated above.

---

### Post by Frank Golden on 2007-01-02
> **Frak said:**
> On my end, more crashes, and the inability to download things, because the OK button is greyed out, other than that, new tab system and spell checker as stated above.
Hey everyone, The script mentioned at least 3 times in this thread (aiysu's) really works.
Give it a try. It even moves your plugins, addons and bookmarks over. Once installed,
to update use command gksudo firefox to open firefox. You will then see thst the update button is not greyed out. The above command opens firefox root. 

Not to belabor the point but doesn't LTS mean security updates?
I fail to see how Firefox has much to do with secutity.

---

### Post by Frak on 2007-01-02
LTS in means of **stability**.

EDIT
and yes aiysu's does work, it makes it more stable, and FF 2.0 is really good on Ubuntu, I was talking about Windows, just forgot to mention that little tid-bit, but its horrible on windows, I use opera instead.

---

### Post by Frank Golden on 2007-01-03
> **Frak said:**
> LTS in means of **stability**.

EDIT
and yes aiysu's does work, it makes it more stable, and FF 2.0 is really good on Ubuntu, I was talking about Windows, just forgot to mention that little tid-bit, but its horrible on windows, I use opera instead.
Sorry to hear that about Windows. FFox 2.0.0.1 works great for me in XP Pro.
I do however use the FirefoxPortable version created by John Haller. It was designed to run on a USB
memory stick and be used on any Windows machine. It does not alter the registry, and isn't really installed on any host machine. I install to the root of my C: drive and make a shortcut to the exe on the desktop. It is fully customizable (plugins, add ons and themes)
and runs great. Auto update works great also.  When I get everything setup I make a copy of the FirefoxPortable folder
and keep it safe in my documents. If my Firefox screws up I just copy the backup over it.
See below for more info 

[http://portableapps.com/](http://portableapps.com/)

Unfortunately, doesn't work in Linux.

---

### Post by Frak on 2007-01-03
> **Frank Golden said:**
> Unfortunately, doesn't work in Linux.

Unless your very clever... :-k

---

### Post by Frank Golden on 2007-01-03
> **Frak said:**
> Unless your very clever... :-k
Really. Do you know how to make it work in Ubuntu?:D

---

### Post by Frak on 2007-01-04
Make WINE port to a media drive, i.e. media/cdrom0/firefox, its still a directory, so WINE is still able to execute.

---

### Post by Frank Golden on 2007-01-04
> **Frak said:**
> Make WINE port to a media drive, i.e. media/cdrom0/firefox, its still a directory, so WINE is still able to execute.
I thought you might say use WINE. I'm a recovering alcoholic so I don't think I will
be going that route.:p :p . Seriously though, there are no Windows apps that I need to run in Ubuntu. If I need to run windows apps I run em from XP. Anyway it does sound like a solution for folks wanting to try
John Haller's portable apps on a Linux box. I'm content with the installed Ubuntu apps.
I do have a Cruzer Titanium setup with PortableAppsSuite to use on other Windoze PC's.
Works great.

---

