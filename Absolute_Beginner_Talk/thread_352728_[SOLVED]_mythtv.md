---
title: "[SOLVED] mythtv"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-02-03
I have tried for several days to install mythtv. Loaded ubuntu from the cd no less than 12 times to make sure each attempt was a clean install. I have followed several guides. Each has it's own good parts but they all seem to be a little different. The closest I have got was where testing of the hardware worked. The hangup in over half the attempts came with myth not being able to do it's thing with mysql. Sometimes it seemed like the passwords were wrong or sql wouldn't let myth in. I tried by leaving the password blank but that didn't help. 

My question is... Does anyone know of a guide that is complete and detailed that an average person can follow with some success. One that is not outdated by upgrades throwing it a curve making it worthless. 

Thanks.  I'm in the process of reloading ubuntu now for another try. :)

---

### Post by phossal on 2007-02-03
Doesn't the Myth website have a giant installation .pdf? I vaguely remember downloading a pretty good document that included information on just about everything. The main page HTML doc: [http://www.mythtv.org/modules.php?name=MythInstall](http://www.mythtv.org/modules.php?name=MythInstall)

---

### Post by squrl on 2007-02-03
Yes they do but like some of the others it covers everything from red hat to black dog and is not very good as a guide.  I hunted for a reference to the drivers for hauppauge cards and haven't found it yet.  I know they have to be added to the mix at some point in the setup but ???

Thanks

---

### Post by NT4usB on 2007-02-03
Setting up MythTV was my first experience with Linux so I was learning as I went along.
When I installed 0.19 on 6.06 using Hyams guide, I started over many times...
Every time, something different went wrong.
When I finally got it, it was by doing the same things I did the many prior attempts.
After I got it working, I had to format and start over again because I screwed up the partitioning and had 200 GB I couldn't use.
The final install took ~3 hours from format to up and running... using the same guide, doing the same things.
I concluded that by doing it over and over again, I began to understand what was actually happening instead of just copying and pasting.
I also figured out I didn't need to follow the guides... just the basic steps to getting MythTV working. Don't move on until you have them completely sorted.
Get the Nvidia working with TV out.
Get the capture cards working.
Get lirc working.
Get Mysql working.
Then install MythTV...

So, stay after it. It does work.

ed: re, your question:
*My question is... Does anyone know of a guide that is complete and detailed that an average person can follow with some success. One that is not outdated by upgrades throwing it a curve making it worthless.*

The steps to making mysql work haven't changed... 
I think the biggest issue I had was permissions. I did things as root that should have been done as user. 
I did find that after having totally borked up mysql, I could completely uninstall and remove mysql and install it again without affecting the rest of the MythTV install.
After a while, I refused to start over from scratch. Instead, I resolved to sort out what was actually wrong. Removing that part of the install that didn't work if I needed to, and reinstalling just that portion. Linux is cool that way...

---

### Post by phossal on 2007-02-03
> **NT4usB said:**
> When I finally got it, it was by doing the same things I did the many prior attempts. ... The final install took ~3 hours from format to up and running... using the same guide, doing the same things.

I like Ubuntu, and rarely use Windows, but if those lines above are true, I'll never use MythTV or even attempt it, and I'll consider it a huge blemish on the face of Ubuntu. If you can follow the exact same steps and have a varying result, that's chaos. I certainly don't want anything on my computer that operates *that* way.

However, I'm sure a *better* understanding of the component software involved would take the lottery out of the installation. I agree that the OP should stick with it.

---

### Post by squrl on 2007-02-03
Thanks NT4  

I seem to hit snags when myth tries to connect to the database. Somehow the passwaords never work and myth can't get in.  Right now I have the firmware loaded and can do a test but got to a point it wanted a new file and then a script loaded and I messed up the whole thing again. 

Maybe someday.....

---

### Post by fenian on 2007-02-03
Starting from a clean install (make sure to install latest nvidia drivers and restricted formats) run these commands
> 
sudo apt-get install build-essential dialog apache2 mysql-server phpmyadmin gcc-3.4 libapache2-mod-php5
sudo apt-get install libapache2-mod-auth-mysql
sudo apt-get install dvdauthor mplayer
sudo apt-get install ntp ntp-simple 

then restart apache 

> sudo /etc/init.d/apache2 restart

then set the mysql password from the command line (replace whatever with the password you want to use.)

> mysqladmin -u root password whatever

open a web browser and type localhost in the address bar you should now be at page with two links apache2-default and phpmyadmin.Click the phpmyadmin link.You should now be at a login screen login as user root with the password you chose above.On the next page click the logout link.

Next setup ivtv following these instructions

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

Now we'll install the Mythtv packages 

> sudo apt-get install mythtv mythbrowser mythdvd mythgallery mythmusic mythnews mythvideo mythweather
sudo apt-get install mythweb mythtv-doc 

During this install process, you will be prompted for the MySQL password. For this, type in the password that you have in the phpmyadmin configuration step that you completed a couple of steps ago.

North American users: Create an account at [http://labs.zap2it.com](http://labs.zap2it.com).  This is where you will download TV listings from; and this is a free service.  What it will cost you is filling out a short (about ten question) questionnaire about every four months or so.  In the "Certificate Code" field, enter ZIYN-DQZO-SBUT.  Remember your username and password that you used to create an account here; we will need this later.

European users (thanks to Kenneth Nielsen for this contribution): you need to download and configure xmltv-util

   >  apt-get install xmltv-util
    tv_grab_dk --configure    (here, choose the proper tv_grab_* for your country)

Now we need to set a password for the mythtv user run

> sudo passwd mythtv

Next we need to edit the the /etc/group file run

> sudo gedit /etc/group

In the text editor that pops up find the line that begins with "admin" and add ,mythtv to it make sure the comma is there, it will look something like this

admin:x:114:fenian,mythtv

also find the lines with "plugdev" and "cdrom" and add ,mythtv to those as well.Scroll to the bottom and find the line that begins with mythtv add www-data to this line.Save and close.

Now we need to tweak some things for mythweb to work..

First look at your /etc/mythtv/mysql.txt. Take note of the information listed in it. You will have to update the username and password in /etc/mythtv/mythweb-htaccess.conf.


            > sudo gedit /etc/mythtv/mythweb-htaccess.conf

Look for these lines 
                      setenv db_server "localhost"
                      setenv db_name "mythconverg"
                      setenv db_login "mythtv"
                      setenv db_password "mythtv"
change the login to root and the password to your mysql password.

      The ownership isn't properly set on /usr/share/mythtv/mythweb/data and mythweb-htaccess.conf. Set them correctly by

           >  sudo chown www-data /usr/share/mythtv/mythweb/data/
            sudo chown mythtv.www-data /etc/mythtv/mythweb-htaccess.conf



Now log out and log back in with the username mythtv and the password you chose.

Setup mythtv with this command (don't use sudo)

> mythtv-setup

You can use this guide to help you through the mythtv setup screens

[https://help.ubuntu.com/community/MythTV_mythtvsetup](https://help.ubuntu.com/community/MythTV_mythtvsetup)

After you finish the setup run

> sudo /etc/cron.daily/mythtv-backend

It will take some time to load all the program guide info after it does restart the backend with

> sudo /etc/init.d/mythtv-backend restart

Then open the frontend with
> 
mythfrontend 
Hopefully you will now be able to use Myth.

I culled the info here from several different guides ...
[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)
[http://www.mythtv.org/wiki/index.php/Ubuntu_Installation_Guides](http://www.mythtv.org/wiki/index.php/Ubuntu_Installation_Guides)

---

### Post by squrl on 2007-02-03
Fantastic !!!!

Thanks Fenian,

I hope someone sees this and makes it where its easily found.
  

Thanks again

---

### Post by NT4usB on 2007-02-03
> **phossal said:**
> ... If you can follow the exact same steps and have a varying result, that's chaos...

Clearly, my point was lost on you so I'll expound.
If you're blindly following a guide, copying and pasting, and it doesn't work for you yet it's been proven to work, and has worked for others then don't blame the guide. Blame your lack of understanding of the processes (or inability to copy and paste correctly.*g*)
My point was, I screwed something up along the way and didn't know enough to recognize it or fix it before moving on so the installs failed. If the information in the guides was wrong, I should have **never** got it working by following them....

---

### Post by squrl on 2007-02-03
I have to agree with most of what you say NT4usb

A lot of this is being able to read between the lines. Some folks have a problem with that. I try to follow to the letter and when the writer leaves out a period it can mess things up.  Also lack of familiarity with Linux in general can be very confusing for some. 

From my experience as a retired engineer I know for a fact that if you give the same set of drawings to two different contractors you are going to get two different products. (sometimes with unimaginable differences :) )  

I appreciate all the help from those who contributed to my delinquency  Thanks again

---

### Post by phossal on 2007-02-03
> **NT4usB said:**
> Clearly, my point was lost on you...
I can relate to that statement. lol 

I was simply rubbing it in that, if the guide worked *ever*, it always worked. I think I understood the reality of the situation, even if you think I missed your point. The weak link in your installation attempts was *you.* I'm not sure why you would want to prompt me into stating the obvious so obviously. I constantly encourage the people I try to help - mainly with Java - to try and gain a deeper understanding of what they're doing. I certainly wouldn't disagree that understanding your system is a good thing.

---

### Post by squrl on 2007-02-03
LOL  this is almost funny if it wasn't so sad.

The first command in the list and it gets rejected 

Hell I'll buy a tivo

---

### Post by phossal on 2007-02-03
It failed on the command to grab build-essential? That's because you have repositories that aren't open, most likely. You need to enable virtually all of them. Typically, when I bite the bullet and jump in on a thread, I'm willing to actually *do* all of the steps at the same time. It helps me anticipate problems and verify that the method works. I have to be honest though: I sort of *want* MythTV, but it has such a horrible reputation for being a finicky install that I'm afraid to attempt it again.

---

### Post by squrl on 2007-02-03
Yup thats where it failed.  

I don't think this mythtv is a very good idea. If it's that fussy on install what is to be expected later about the time the wife would like to catch a particular program and it decided to fall apart. 

Maybe next year after it has been cleaned and polished a bit more I'll try again....Sometimes you get what you pay for.

---

### Post by phossal on 2007-02-03
No doubt. For *watching* TV, I'm quite satisfied with TVtime. After installing my TV card, I used:
```
sudo apt-get install tvtime
``` 
And it just *works*. I like hacking around with stuff, but I could easily spend *hours* setting up Myth, and I only *watch* TV for a total of an hour per week. It's hardly worth the investment. And, as you mentioned, if you're *serious* about capturing TV, there are many better ways like Tivo.

---

### Post by fenian on 2007-02-04
Go to System>Administration>SynapticPackageManager under the settings menu go to Repositories make sure they are all checked then click reload in the top left hand corner.Don't give up it's worth the effort and it works,really it does.

---

### Post by phossal on 2007-02-04
> **fenian said:**
> Don't give up it's worth the effort and it works,really it does.
lol They call it ***Myth***TV for a reason, don't they? I've *heard* it really works. ;)

---

### Post by squrl on 2007-02-04
LOL  I'll never know

---

### Post by nitebum on 2007-02-04
> **phossal said:**
> No doubt. For *watching* TV, I'm quite satisfied with TVtime. After installing my TV card, I used:
```
sudo apt-get install tvtime
``` 
And it just *works*. I like hacking around with stuff, but I could easily spend *hours* setting up Myth, and I only *watch* TV for a total of an hour per week. It's hardly worth the investment. And, as you mentioned, if you're *serious* about capturing TV, there are many better ways like Tivo.

Doesn't work with my Hauppauge 150. DAM. I thought I finally found an alternative to MythTV madness... Oh well - back to wasting more precious life force trying to get MythTV working
:roll:

---

### Post by punx45 on 2007-02-04
if you are having alot of trouble, and MythTV is the priority, (like you would take myth over ubuntu) then you should try MythDora, or KnoppMyth.   both are Distro installs designed to install mythTV at the same time.

I installed using MythDora on 'mythb0x' (hence the name). it was super easy.

if you would rather keep the Debian base (if you prefer apt)(more common things for support on these forums) then KnoppMyth would be good.

---

### Post by NT4usB on 2007-02-04
> **phossal said:**
> I can relate to that statement. lol 

I was simply rubbing it in that, if the guide worked *ever*, it always worked. I think I understood the reality of the situation, even if you think I missed your point. The weak link in your installation attempts was *you.* I'm not sure why you would want to prompt me into stating the obvious so obviously. I constantly encourage the people I try to help - mainly with Java - to try and gain a deeper understanding of what they're doing. I certainly wouldn't disagree that understanding your system is a good thing.

Believe me, it was very frustrating to get through the install, find that ivtv works this time, but now playback gets me a black screen!  ...format and try again.
Silly things... something simple as:
cd /etc/init.d/
and then trying to sudo gdm stop **is not** the same as 
sudo /etc/init.d/gdm stop

Best one was ivtv wouldn't work even though I did everything correct. Worked on it for hours. Finally said *F* it, shut down and went to bed. Next day, I fired it up and it worked! Turns out, you **must** cold boot to get the (v4.x) firmware to update. Many guides leave that part out.

> **squrl said:**
> LOL  this is almost funny if it wasn't so sad.

The first command in the list and it gets rejected 

Hell I'll buy a tivo

If you want something that works out of the box (such as it is) TiVo might be for you. The WAF (wife approval factor) might be higher. You probably won't even miss the features that make MythTV special like never seeing a commercial again... (I recorded the year end 'TV's funniest commercials' and no, it didn't skip them... just the real commercials in between)

> **phossal said:**
> ... Typically, when I bite the bullet and jump in on a thread, I'm willing to actually *do* all of the steps at the same time. It helps me anticipate problems and verify that the method works...
Very frustrating, following a thread, reading all the: *Thanks for the howto, works great!* posts and not being able to make it work myself. Went through it with the ATi card in another box. (maybe I should hold off on using Ubuntu until it's cleaned and polished a bit more..?)<d&r>

fwiw... I've enjoyed nearly flawless performance out of my MythTV box since I finished it last June. The backend has crashed twice since I put the box in the entertainment center. Other than that, it's 24/7. 
Only time it gets restarted is kernel stuff and to blow the dust out.
I've never been much of a TV watcher but it's nice to be able to see the shows I like, when I have time to watch them. 
Even better than MythTV is learning something new (Linux) and knowing that in only 10 years my MythTV box will be paid for by the $12.95 a month I saved on PVR rental form the cable company.<sfsf>

---

### Post by nitebum on 2007-02-04
> **punx45 said:**
> if you are having alot of trouble, and MythTV is the priority, (like you would take myth over ubuntu) then you should try MythDora, or KnoppMyth.   both are Distro installs designed to install mythTV at the same time.

I installed using MythDora on 'mythb0x' (hence the name). it was super easy.

if you would rather keep the Debian base (if you prefer apt)(more common things for support on these forums) then KnoppMyth would be good.

Thats some sound advice. I might try to free up some space for another install. Anyone know of an easy way to switch between the two installs (Ubuntu/MythDora)?

Would I have to reboot, or could I run MythDora inside of Ubuntu?

---

### Post by Titus A Duxass on 2007-02-04
NiteBum,
What problems are you having with the myth install?

I have used MythDora, before and it is a simple intall.
You will have to dual boot if you with to keep ubuntu.

I don't no about running MythDora inside ubuntu.

---

### Post by phossal on 2007-02-04
[edit] Forget it. lol

---

### Post by nitebum on 2007-02-04
I'm having problems with mysql. I've been trying for 3 days. I'm going to try MythDora b/c I'm new to Linux, and there are other things that I would rather be working on.

I just went through downgrading from AMD64 Ubuntu to 386 b/c it's just more useful right now. And that's what I need - Useful. 

But thanks for the help, and good luck to everyone else.

I'll report back if I have any luck with MythDora. Maybe I could run the MythFrontEnd from Ubuntu, who knows...

---

### Post by squrl on 2007-02-04
Well so much for the "mythDora crap.  Download, burn the dvd, load several times and end up with a mini version of ubuntu.   No tv.  Got a nice desktop screen.   Looks like a pissed off penquin.

---

### Post by Lem on 2007-02-04
This is a simple guide for running myth on a desktop ubuntu install.

It works (well it did for me).. I had to tweak /etc/modules to get my twinhan card working ([http://www.ubuntuforums.org/showthread.php?p=1739176#post1739176](http://www.ubuntuforums.org/showthread.php?p=1739176#post1739176))

but my hauppauge card was recognised no problems.

Better to run myth on a  thinned-down Ubuntu install (from server install ideally), but a combination of this guide and the ubuntu server install guide works very nicely with minimal effort!

---

### Post by squrl on 2007-02-04
Yup  thats a guide alright. I'd recognize it anywhere.  Looks just like the rest of them for mythtv.  I think they should rename it Notv

---

### Post by robgue on 2007-02-07
i followed the main guide [ here]("https://help.ubuntu.com/community/MythTV_Edgy_Frontend_Desktop") and am also getting mysql errors

---

### Post by robgue on 2007-02-08
well i started from scratch and followed your guide fenian with the exception of installing xserver, gdm and so on. It worked! Thanks. no more sql errors. now i just gotta set up my ati radeon properly and some other things like ir. thanks.:)

---

### Post by punx45 on 2007-02-08
> **nitebum said:**
> Thats some sound advice. I might try to free up some space for another install. Anyone know of an easy way to switch between the two installs (Ubuntu/MythDora)?

Would I have to reboot, or could I run MythDora inside of Ubuntu?

you would have to reboot, which would mean missed recordings. so-
better than that would be to go with KnoppMyth instead, and replace your current ubuntu install with it.   Its Debian (for the most part Ubuntu minus minor things), so you still have aptitude and most of the support here will actually be useful.   When you want to use the desktop, escape out of MythTV (the backend continues to run in the background) and use the computer.   then when you want to watch TV or recordings, hop back into mythfrontend.

I only went with mythdora over knoppmyth because i wanted to try out Fedora.

---

