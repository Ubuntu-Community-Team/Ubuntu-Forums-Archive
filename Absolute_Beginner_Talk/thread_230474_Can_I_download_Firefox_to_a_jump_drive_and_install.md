---
title: "Can I download Firefox to a jump drive* and install it from there?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2006-08-06
* on another machine !!

Hi everybody,

I am in a very difficult spot and am looking for creative solutions. It appears that although I am able to connect to a network both through an ethernet connection and wirelessly, I cannot connect to the interweb. When I open firefox it just spins it's wheels until it times out. I have tried to solve this problem in a couple of different ways, but am hitting the wall each time. I have read the wireless config wikis, I have read the Ubuntu desktop guide, I have seacched the forums, and I have asked for help, and although several very kind folks have done their best, I am still jammed up.

Here is the thread that got me the closest:

[http://ubuntuforums.org/showthread.php?t=230124](http://ubuntuforums.org/showthread.php?t=230124)

What I am wondering now, is can it possibly be a problem with Firefox itself? The reason that I ask this is that I am certain that I am connecting to at least some of the servers that I am attempting to connect to. How? First, I am able to use the Evolution Mail client to send and receive mail. Second, I am able to ping site servers and get throughput with zero packet loss.

*Finally* I'll get to my question. Can I download the latest version of Firefox using my iBook (that does _not_ have Linux installed on it) and save it to a jump drive and then migrate it over to my ThinkPad and install it?

If I can't connect to the web, I can't use Synaptic to update my packages, or check anything, or basically do anything else. But if Firefox is all that is keeping me from being able to load web pages, then I would like to fix it or rule it out.

If someone has better ideas, I am all ears.

Oh yeah, I do not have a high speed connection at home, so I will have to wait until tomorrow to implement any suggestions.

A sincere TIA for any help solving this. I have been trying to figure it out for a couple of days, and am not getting very far.

Thanks again,

Kent

---

### Post by K.Mandla on 2006-08-06
Here's an idea for you. If you really want to download Firefox as a package, try Swiftfox, which is just an optimized version. You might even be able to get it directly with wget.

```
wget http://www.getswiftfox.com/builds/releases/swiftfox-1.5.0.6-pentium3.tar.bz2
```
Alternatively, you could navigate on another machine to [www.getswiftfox.com]("http://www.getswiftfox.com") and download the Pentium 3 package. 

Once you get it onto your machine (either directly or with a USB drive -- it's only about 8Mb), you can decompress it anywhere you like with ...

```
tar -xvf swiftfox* -C _________
```
The blank is the destination for the Swiftfox folder. Remember you'll need to prefix that command with sudo if you want to put it somewhere outside your home directory.

After that you can configure your desktop to use Swiftfox. In XFCE you can point the Preferred Applications settings to the swiftfox folder; I'm not sure how it would work in Gnome or KDE.

To be honest though, I don't know if it will help. If Firefox didn't work, Swiftfox might not either. If that's the case, maybe Opera or another browser will do the trick. Let's hope you don't have to drop back to links just to look at the 'Net!

Good luck!

---

### Post by aysiu on 2006-08-06
If you can use the repositories but not Firefox, try a different browser and see if that works.

```
sudo aptitude update && sudo aptitude install epiphany-browser
epiphany
``` If Epiphany works and Firefox doesn't, something's wrong with Firefox. If neither Epiphany nor Firefox works, then you might have some problem specific to web browsing (maybe an IPV6 thing?).

---

### Post by Carbonfish on 2006-08-06
> **aysiu said:**
> If you can use the repositories but not Firefox, try a different browser and see if that works.

Thank you both for your replys. Unfortunately Aysiu, I have not been able to connect to the repositories through the terminal. When I have tried to "sudo apt-get update" it tries to connect me to the repositories in Canada I think (which shouldn't matter I don't think) but it always times out. Trying to connect through Synaptic never works either. I realize that I am not being very descriptive. but since I don't have any connection where I am right now except dial-up (and I can't get ppp to even activate), I can't try to update and get the failure messages.

I know how busy you all are, but if you have a spare minute, the thread that I linked to in the first post in this thread shows most of the troubleshooting that I've done so far.

While I was hanging out between posts, and before I saw your replies, I downloaded firefox-1.5.0.6.tar.gz, but I could certainly use any other browser that you think might work better for me. I am yours to command. ;)  

I am very new at the command line (and as you may have gathered, at Linux in general), so if I were to try to install this thing, I might need a little hand-holding, or at the very least, a wiki to look at.  8-[ 

But I really appreciate your taking the time to respond. I will take any advice right up to wiping the drive and starting over, as I bought the ThinkPad with the sole intention of learning how to use OSS. That is why I didn't worry about trying to dual-boot or any of that. This is an immersion course in Ubuntu. But I have just jumped into the pool, so for the time being, I am still "dog-paddling."

Thanks again.

Kent

---

### Post by Jagot on 2006-08-06
The problem may be that the Canadian repositories are down at the moment - it happens occasionally.  You could try Opera.  Run this command from Terminal:

```
sudo gedit /etc/apt/sources.list
```

Then add this line to the end of that list:

```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

Now save that file and close it.

From Terminal again:

```
sudo aptitude update && sudo aptitude install opera
```

---

### Post by Carbonfish on 2006-08-06
Hi Jagot,

Can I do what you have suggested without being connected?
(I guess that I could just try and see what happens huh? :D :D )

Thanks,

Kent

---

### Post by Jagot on 2006-08-06
If I understand it you cannot download from the repo's you currently have which are Canadian - the repo for Opera is not Canadian, so it should be up at the moment.

Alternatively you can go to [http://www.opera.com/](http://www.opera.com/) - they have an Ubuntu specific .deb which you could download on another computer or something and transfer over to your Ubuntu computer to install.

---

### Post by Jagot on 2006-08-06
oops - double post

---

### Post by Carbonfish on 2006-08-06
No, I am sorry Jagot, I guess that I wasn't clear. I can't get connect at all on the machine that has Ubuntu on it. I am typing this on my iBook on a dial-up connection. I can't get dial-up to work at all on the ThinkPad (the machine that I am trying to get working), and therein lies the problem. 

I did what you suggested though, and it read the package lists, built the dependency tree, read the extended state info., initialized the package states, and built the tag database.

I then got:

Err http:archive.canonical.com dapper-commercial Release.gpg
   Temporary failure resolving 'archive.canonical.con'

and it goes through 4 other repositories with the same errors and failures, then,

Reading package list... Done
install: missing file operand after 'opera'
Try 'install --help' for more information.

So I guess that's that.

Thanks though. I'm still all ears!

Kent

---

### Post by Carbonfish on 2006-08-06
Okay, I got opera_9.01_20060728.6_shared_qt_en_i386.deb downloaded onto my jump-drive, and could migrate it right over to the ThinkPad. But I could use some hand-holding regarding installation. :oops: 

Since I'm still barely crawling where the Terminal is concerned, could someone point me in the right direction getting the .deb installed properly? It would be deeply appreciated.

I can't keep my eyes open any longer. If someone leaves install instructions here tonight, thanks. Otherwise, I'll bump this thread in the morning and take it from there. Back in eight or so hours.

Thanks,

Kent

---

### Post by Jagot on 2006-08-06
Providing you're using Dapper (6.06), which you appear to be, all you need to do is double click on the package and click 'install package'.

---

### Post by Carbonfish on 2006-08-06
> **Jagot said:**
> Providing you're using Dapper (6.06), which you appear to be, all you need to do is double click on the package and click 'install package'.
 Thank you Jagot,

I will ask what I'm sure is a silly question, but since I am the rankest form of n00b I will ask it anyway. Does that go for the .tar.gz package as well, or just the .deb package and can I just move these things onto the desktop and double-click them from there?

Well, I guess I can't really break anything... I'll just try it!

I'll zoom around and search the forums for how-to's regarding installing individual packages and try to move forward.

Thanks for all of your help and advice, and keep those cards and letters coming!

Kent

---

### Post by Jagot on 2006-08-06
That only goes for .debs - Ubuntu has a .deb installer.  You can have a look at this link with regards to installing pretty much anything, including .tar.gz packages:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Carbonfish on 2006-08-06
Jagot,

Thank you *very* much. I will follow the link you have provided and proceed from there. 

I hope that once I have an alternate browser installed I will be able to figure out whats going on with this frustrating network connectivity issue. 

I simply can't understand why I would be able to send and receive E-mail, and ping successfully with no packet loss, but no be able to load web pages. What's even more frustrating, is that the browser (so far Firefox) doesn't give me the usual "Firefox cannot find the server" message, it just acts like it's trying to load the page until it times out. And, it does this both with the ethernet connection (eth0) *and* the PCMCIA wireless card (eth1).

Weird.

Anyway, thanks again. I will open/install these packages and see where I am from there.

Kent

---

### Post by Carbonfish on 2006-08-06
Okay, another detour on the way to figuring this out. I tried to install Opera (the .deb package that I downloaded onto my thumb drive and moved over to my ThinkPad), but the GDebi installer says that there is an additional file to be installed. It says:

"To be installed libqt3-mt"

So I don't know how to proceed since I am still completely unable to get on-line. So I can't get to the repositories to load anything (or else I wouldn't have this issue), so can't imagine a way to find and get this additional file.

Any suggestions?

TIA,

Kent

---

### Post by Jagot on 2006-08-06
Right, this time try and install from Terminal instead.  Open a Terminal window and navigate to wherever the Opera .deb is.  So, if it is on the desktop type:

```
cd /home/carbonfish/desktop/
```

Then type:

```
sudo dpkg -i opera<tab key>
```

When I say tab key there, actually press the tab key after typing opera - it will fill in the rest of the filename so you don't have to.

Now it may thrown up the same error, but now do this:

```
sudo apt-get -f install
```

This should force it to install.

---

### Post by Carbonfish on 2006-08-06
Hi Jagot,

Well, I am not sure what I am doing wrong, but when I type

cd /home/carbonfish/desktop

the Termminal responds 

bash: cd: /home/carbonfish/desktop: No such file or directory

Sorry, but I have tried several times, making sure that I am missing nothing, and copying everything exactly. I can't copy and paste as I am on a different machine.

Kent

---

### Post by Jagot on 2006-08-06
The carbonfish part of that is whatever your username is- I just used your name here on the boards as an example - if it's something different then change that part to your actual username on your Ubuntu install.

---

### Post by Carbonfish on 2006-08-06
No, you are exactly right. My user name in Ubuntu is carbonfish. At the top of the Terminal window it says 

carbonfish@carbonfish-laptop: ~

?? Kent ??

---

### Post by Jagot on 2006-08-06
OK, sorry but I think the desktop part should be with a capital - my fault.  So should be:

```
cd /home/carbonfish/Desktop/
```

---

### Post by Carbonfish on 2006-08-06
Jagot,

I hope that I didn't just muddy the water with my last post. I am (as far as I know) carbonfish as far as Ubuntu is concerned. 

I am sorry for being thick about this, but I am unsure how to proceed. This is the first time I have had to change directories in the Terminal, but it seems like it should be fairly straightforward. I can't imagine what I might be getting wrong.

Kent

---

### Post by Carbonfish on 2006-08-06
Hi Jagot,

Okay the capital 'D' did the trick. I followed your algorithm right up to the <hit tab> part, and it did fill in the rest ot the pkg name, and I then hit enter. After which it read the database and unpacked opera. Then you were right, I got the same error that I got before, so I did the sudo apt-get -f install thing. I wish that I could copy and paste all the text that I got from there, but the bottom line is that it said that the following extra packages will be installed: libqt3-mt
0 upgraded, 1 newly installed, 0 to remove, and 0 not upgraded
Need to get 3151 kb of additional archives. 
After unpacking, 8933kb of additional disk space will be used. Do you want to continue?
I typed Y (by the way, does the terminal care if that is upper case?)

After that it tried to connect to the archive.ubuntu.com dapper/main libqt3-mt 3:3.3.6- lubuntu3

It could not connect. The connection timed out (as usual)

It then said:

E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing


That's it. Then it went back to a command prompt.

Kent

---

### Post by Carbonfish on 2006-08-06
Well Jagot,

Have I finally driven you over the edge?

KC

---

### Post by Jagot on 2006-08-06
Ok, it obviously can't get by without that dependency.  The only thing I can suggest now is to download that dependent file separately and install it first, then go through with trying to install Opera again.  You can download the file here:

[http://packages.ubuntu.com/dapper/libs/libqt3-mt](http://packages.ubuntu.com/dapper/libs/libqt3-mt)

---

### Post by Carbonfish on 2006-08-06
Hi again Jagot,

It looks like there are three packages for three different architectures that have the same name as the dependency that I need, but one is for MySQL, one is for ODBC, and one is for PostgreSQL. I am not sure which one to download. :confused: 

(Sorry about using the smiley, but I'm starting to feel a bit helpless.)

I'll keep putting one foot in front of the other if you will :>)

Oh yeah, I now have an alert icon up in my system tray telling me that an error occured, and to please run Package Manager from the right-click menu, or apt-get from the terminal to see  what is wrong. When I do that, a pop-up box (in Package Manager) says that I have 1 broken package on my system, and to use the broken filter to find it.

Kent

---

### Post by Jagot on 2006-08-06
The broken package is probably Opera.  If this all fails then it'll be easy to get rid of so don't worry for now.  Assuming you're using the 32bit x86 version of Ubuntu, then here is a direct link to the file you need to download:

[http://itanix.rutgers.edu/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.6-1ubuntu3_i386.deb](http://itanix.rutgers.edu/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.6-1ubuntu3_i386.deb)

I suggest you remove Opera first if it managed to install it:

```
sudo aptitude remove opera
```

Install this dependency, then go through the Opera install again.

---

### Post by Carbonfish on 2006-08-06
> **Jagot said:**
> The broken package is probably Opera.  If this all fails then it'll be easy to get rid of so don't worry for now.  Assuming you're using the 32bit x86 version of Ubuntu, then here is a direct link to the file you need to download:

[http://itanix.rutgers.edu/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.6-1ubuntu3_i386.deb](http://itanix.rutgers.edu/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.6-1ubuntu3_i386.deb)

I suggest you remove Opera first if it managed to install it:

```
sudo aptitude remove opera
```

Install this dependency, then go through the Opera install again.

Okay. Thanks again. I have removed opera (and the alert went away in my sys. tray) and I have downloaded the dependency to my jump drive. I will install the dependency first, then re-install opera. Should I install the dependency from the terminal in the same way that I did opera the first time, or can I use the installer in the GUI for the dependency?

Oh, and by the way, if you are ever in Portland, Oregon. I owe you the biggest steak that money can buy (unless you are vegetarian, then I'll let you pick the restaurant!). 

KC

---

### Post by Jagot on 2006-08-06
Haha, well, we don't even know if this is going to work yet - keeping fingers crossed anyway.

You should be able to install that file from the GUI.  Then you'll have to go back to the terminal to install Opera again.

It's nearly 1 o'clock in the morning here so I'm gonna have to go to bed.  Good luck and if there's anything else that somebody else can't answer overnight then I'll be back tomorrow no doubt.

---

### Post by Carbonfish on 2006-08-06
Jagot,

Thank you very much. I sincerely appreciate your help. Get some rest, and I hope you sleep well. One way or another I will post back to this thread to let you know how thing have gone.

Cheers.

Kent

---

### Post by Carbonfish on 2006-08-06
Well, it only took three hours, but Opera installed fine, and it turns out that it is not my browser that is the problem after all. Opera does exactly the same thing that Firefox does. That is, acts like it's loading a page, and then just sits there until it times out. 

Really frustrating!  ](*,) 

The thing that is killing me is, up in the little network monitor in the system tray, I can see the thing sending and receiving! If I go into the terminal, and ping *_anyplace.com_* it sure *looks* like there is throughput, and it says that X number of packets were sent and received with 0 packet loss. Also, as I mentioned in a previous post in this thread, I can send and receive mail through the Evolution Mail client, so I am connecting to something, I just can't connect to the interweb.

I am STUCK!

If anybody can think of anything for me to do, I will follow any and all suggestions. 

This is happening both with my PCMCIA wireless card (eth1), and when the machine is directly plugged in to an ethernet connection (eth0).

Maybe this is just a configuration problem, but the thing is starting to give me a nervous tick! :roll: 

I usually don't resort to this sort of pathos, but 
*HELP!*

Oh yeah, I've been in this coffee shop for over three hours now, and they are starting to give me "the look", so any suggestions will have to be implemented without a network connection to test, or tomorrow when I am again somewhere I can "plug in". 

TIA,

Kent

---

### Post by Carbonfish on 2006-08-07
Good morning,

I am have not resolved this problem, but I think that the title of this thread might mislead people, since I have actually solved the issue ( with much assistance from Jagot) of whether or not it is the browser. So if it's okay with everyone (moderators, helpful posters, etc.) I will start a new thread in the Absolute Beginners forum, but I haven't thought of an appropriately compelling title. :-k 

You'll know it when you see it (I hope! :D ).

Thanks, 

Kent aka Carbonfish

---

### Post by Carbonfish on 2006-08-07
Well, I am on-line on the ThinkPad using Ubuntu. I still don't have wireless capability, and I can't watch movies yet, or stream video, and I don't have alot of the plug-ins that I need to make stuff work, but I'm on the way and my little OSS experiment is not a "closed system" now that I can get to the repositories. So this is pretty great!

Now, if I can get some of this other stuff handled without the boss catching on that I am using work time and ethernet to get this updated, my life will be good. Thank goodness that I work in a library, and spend most of my time typing anyway!

I'll be asking lots of n00b questions, so please bear with me.

Kent

---

