---
title: "install Apache, MySQL, PHP, and phpMyAdmin for offline use?"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Kandiman on 2007-03-01
hello, 

im currently a university student who has been asked to create a webpage with php code use.  however i have no access to the internet at home, so i have to do it all at uni, which, as i work during the day, means i only have limited time on the internet.

well. my tutor is aware that some people either are to scared to install linux or dont have internet access so has done the following (ill just post the email here as its alot easier than typing it all out, and it prob explains it better than me anyways:) 

[INDENT][INDENT][COLOR="Blue"]> Dear All,

I have finally, after many hours and many CD coasters, produced a customised version of Ubuntu 6.06 with Apache,
MySQL, PHP, and phpMyAdmin, and the CP1079 database, all pre-installed and running from the liveCD.

I call it "matt-you-buntu" :-)

So what, I hear you ask!

If you have a computer that you cannot or do not want to install Linux on, or one without an Internet connection,
yet want to use the Linux software we use at the University, you can now use matt-you-buntu without affecting
your computer in the slightest.

As long as you can boot a liveCD you can do all your CP1079 work on a computer without an Internet connection.

You will need a compatible memory stick or a CD writer or some method of saving files in between sessions.
As the CD runs the OS, not your hard disk, each time you reboot all changes to your files are reset,
so you need to copy to a stick, reboot, and copy back from the stick each time you turn on your machine.

Also, if you choose to install from this version, all the servers and files will be installed to your computer,
again, no Internet connection required (although one is preferred to install updates, etc.)

Downside...
There is a significant shortage of blank CDs at the moment, so you'll need to bring a blank CD to my office
for me to create a copy for you.  Alternatively, I have stored the CD image at
[http://www.scit.wlv.ac.uk/mag/matt-you-buntu.6.06.iso](http://www.scit.wlv.ac.uk/mag/matt-you-buntu.6.06.iso)
if you want to download and burn your own copies.

There is a ReadMeFirst.html file on the desktop of the liveCD to get you started.

Questions????

There is also an OPTIONAL support session for Linux/PHP today in MI214 at 3:30pm onwards.

Matthew[/COLOR][/INDENT][/INDENT]


but it will not install to my hard drive, and i cant use the live CD as i get the 640x400 resolution and it dont fit on my screen, so that means i have to edit the xorg.conf file.  however, I have to therefore install it.. well I tried to install it several times this morning, but for it to crash on the install while it checked my hda1 for files or something.. however I tried other versions of Linux distros I had and they worked.

so im wondering if (heres the question) if anyone can point me to some downloads where i can download [SIZE="4"]Apache, MySQL, PHP, and phpMyAdmin[/SIZE] so i can work offline, and do my uni work.  i tried to have a look at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) but theres alot there and i dont know which to use, like main/universe or stuff like that. 

i just need abit of info, or someone to point me in the right track so i can start to use linux. i currently have the normal 6.10 ubuntu installed, but no internet access...

i wait any reply, as im at uni at the moment for the next 4 hours, and if i can get it downloaded and burnt to a cd so i can do it tonight it would be awsome,... thanks,..

if you require any more info, please post it, and ill try my best to answer, but im not the cleverest bloke in the world so please bear with me... 

thanks again!

---

### Post by Ek0nomik on 2007-03-01
I have relatively new to Linux.  I still have my webserver installed on Windows.

[http://httpd.apache.org/download.cgi](http://httpd.apache.org/download.cgi)

[http://www.php.net/downloads.php](http://www.php.net/downloads.php)

[http://www.mysql.com/](http://www.mysql.com/)

Should be able to grab it all there... ;)

---

### Post by Kandiman on 2007-03-01
oh brill is that it?... i thought it was something complex... LOL :rolleyes: 

so can i just get this right please... if i go onto them url's and download the nessercary files onto a cd-r then go home and run them on my pc running ubuntu. then i should in theory be able to do html&php code and then view it on my pc at the same time..??  (im sorry if im not making sense,....)

i just wanna make sure im doing this all right... 

if thats the case your a legend!!! thanks cus thats all i really need to do, just so i can test my pages at home, then when im next in university, place all the relevent fiels on my public folder in linux.. cus at the moment im haveing to do a full 8 hour shift at work, then another 4 hours at uni, not including commuting on the bus and train,,,... 

deadlines in 4 weeks and im starting to stress, i know i can do it, but i need to have access offline to test my pages.. 

thanks again, (if this is incorrect or you have a alternative solution, please post, as if one dont work i can try the other, but hopefully this wil  do the trick!);) 

cheerz!

---

### Post by Ek0nomik on 2007-03-01
Well, I know **exactly** what you're trying to do.  Do it all locally, than simply upload it onto the University drive.  Firstly, I have never installed a LAMP (Linux, Apache, MySQL, PHP) webserver.  I have only done WAMP.  Installing Apache & PHP on Windows is CAKE.  That I can tell you for sure.  There are guides online that will show you how to do it in under 5 minutes.

Let me point out, if you are using PHP, you generally are going to store things in a database.  You're going to have to connect to that database, and programming that correctly locally won't be difficult.  But having to make sure you get your paths correct at the Uni could be more difficult.

What is the website exactly going to do?  Do you *actually* need PHP & MySQL?

You are probably going to want access to the internet if you haven't done PHP or MySQL before.  It can take a little learning (I truthfully don't know much at all, I have just been dabbling in it in my freetime).

---

### Post by Kandiman on 2007-03-01
yer you got it!

yer i have a database, basically i need to make a webpage where i can search for comics by a certain author or name, which has been pre created,.. 

i wernt to sure on which apache download to use, so i downloaded the unix and the windows one,... what im gonna do it downlaod as much as i can, burn it, and download tutorials and then try it home, if it dont work itll come back and have another look, but i think you know what i mean.

i also read something about LAMP, so i might try and google that and get a tutorial or something.. 

thanks man, if you were near wolves let me know, ill buy you a pint! :)

---

### Post by Synapse56 on 2007-03-01
> **Kandiman said:**
> 

so can i just get this right please... if i go onto them url's and download the nessercary files onto a cd-r then go home and run them on my pc running ubuntu. then i should in theory be able to do html&php code and then view it on my pc at the same time..??  (im sorry if im not making sense,....)

i just wanna make sure im doing this all right... 


Just to reassure you, yes you can write a php / html website and view it locally offline, I do it all the time with my laptop.

---

### Post by Kandiman on 2007-03-01
you both have given me the answer now, so you guys can tell me to go jump off a cliff if you want cus you both have been more than helpful, but i have one more question.....(s)... LOL.. sorry

right i went onto the apache website via the link above and i downloaded 

**Unix Source: httpd-2.2.4.tar.gz **    - for use on ubuntu
 [INDENT][INDENT]and[/INDENT][/INDENT]
**Win32 Source: httpd-2.2.4-win32-src.zip**    - for use on windows

so that should be okay?... (is it hard to install?..)

now im on the php website, and it says.. > We do not distribute UNIX/Linux binaries. Most Linux distributions come with PHP these days, so if you do not want to compile your own, go to your distribution's download site.  i dont know if ubuntu has one?.. where can i find that???...  

for the windows im downloading 

[B]Windows Binaries
PHP 5.2.1 zip package [9,545Kb] - 08 Feb 2007
md5: 682dd66fb03c7dd24c522f474e1b04b6 [/B]



now for the mysql 

im downloading **Linux (non RPM packages) downloads (platform notes) Linux (x86)**

and for windows **Windows downloads (platform notes)Windows (x86) ZIP/Setup.EXE**


are these the correct downloads i need to be using??.. and then whats myphpadmin and where can i get that?...

(really if your in wolves, im buying you a pint.. honest!):) :) :) :) :KS :KS 

thanks!

---

### Post by Ek0nomik on 2007-03-01
> **Kandiman said:**
> yer you got it!

yer i have a database, basically i need to make a webpage where i can search for comics by a certain author or name, which has been pre created,.. 

i wernt to sure on which apache download to use, so i downloaded the unix and the windows one,... what im gonna do it downlaod as much as i can, burn it, and download tutorials and then try it home, if it dont work itll come back and have another look, but i think you know what i mean.

i also read something about LAMP, so i might try and google that and get a tutorial or something.. 

thanks man, if you were near wolves let me know, ill buy you a pint! :)

Haha, a pint would be good.

I've been posting to you while in my Information Systems Design and Information System Programming lectures.  Boring as h/ll.

If the database is pre-created for you, it should be pretty easy than.  Just need to build the search and output.

Hope it works out for you!

---

### Post by indytim on 2007-03-01
I have a LAMP installation running on both my Linux box (Kubuntu V6.10) and Windows Win2k Pro.  If you have Linux up and running on your pc, suggest you install and configure with this how-to [LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP")

If you want to stay in a Window environment, this is what I've used for several years (features a Windows installer to install and setup Apache, PHP and MySQL w/ phpMyAdmin). 
[AppServ]("http://www.appservnetwork.com/") 

Both of these installations are development only (closed off to the outside world).  Might be a more workable approach than what you prof is suggesting (your programs stay resident on you pc).  Probably less futzing also as you will be running your LAMP installation at boot to your ops.

Hope this is of benefit.

IndyTim

---

### Post by Ek0nomik on 2007-03-01
> **Kandiman said:**
> you both have given me the answer now, so you guys can tell me to go jump off a cliff if you want cus you both have been more than helpful, but i have one more question.....(s)... LOL.. sorry

right i went onto the apache website via the link above and i downloaded 

**Unix Source: httpd-2.2.4.tar.gz **    - for use on ubuntu
 [INDENT][INDENT]and[/INDENT][/INDENT]
**Win32 Source: httpd-2.2.4-win32-src.zip**    - for use on windows

so that should be okay?... (is it hard to install?..)

now im on the php website, and it says..   i dont know if ubuntu has one?.. where can i find that???...  

for the windows im downloading 

[B]Windows Binaries
PHP 5.2.1 zip package [9,545Kb] - 08 Feb 2007
md5: 682dd66fb03c7dd24c522f474e1b04b6 [/B]



now for the mysql 

im downloading **Linux (non RPM packages) downloads (platform notes) Linux (x86)**

and for windows **Windows downloads (platform notes)Windows (x86) ZIP/Setup.EXE**


are these the correct downloads i need to be using??.. and then whats myphpadmin and where can i get that?...

(really if your in wolves, im buying you a pint.. honest!):) :) :) :) :KS :KS 

thanks!

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

---

### Post by Ek0nomik on 2007-03-01
Also, the discussion:  [http://www.ubuntuforums.org/showthread.php?t=368692&highlight=apache+php+mysql+setup](http://www.ubuntuforums.org/showthread.php?t=368692&highlight=apache+php+mysql+setup)

---

### Post by Kandiman on 2007-03-01
the second link i dont understand, the first link you posted, well that would mean i need to downlaod the server CD???.. and it also says you need a live inetrnet connection which i dont have?..

i downloaded appserve that indytim said, and the other things i posted, and i am aware that the appserve is windows only... 

errmm but how to LAMP at [https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP) down tell me what i need to download it just. i think the main thing is i get all the software and then ill have a go..

im hopeful now that it is possible and have learnt alot so far.. 

so all i need is apache and php and mysql downlaods so i can make/code/view offline... brilliant!!

im just googling everything,....

if you guys have the software or the links please post or email me at [email]y2kanda@gmail.com[/email]

ta!

---

### Post by Ek0nomik on 2007-03-01
I just gave you some links.  I didn't read all of the posts.  I just thought it may help a bit.

You can always continue searching the Ubuntu Forums.  "apache php mysql install" or something similair should give you some results.

As I said, if you were putting it on Windows, I'd be able to help more.  I haven't tried it on Linux yet.  Maybe I will next weekend...  :)

---

### Post by Kandiman on 2007-03-01
i think i know what im looking for now, so i think i should really have a go tonight and come back if i experiance any problems. 

im gonna try on windows and on linux, so if either work ill be a happy bunny, i just wanna use to learn how to use php, and test the code....

thanks once again...

---

### Post by webofunni on 2007-03-01
I think using xampp is good option thats come with everything preinstalled (gd, freetype mysql etc with php and apache ) also it had some smtp clients and ssl applications its can be downloaded from [apachefriends]("http://www.apachefriends.org/en/index.html") website

---

### Post by Kandiman on 2007-03-01
> **webofunni said:**
> I think using xampp is good option thats come with everything preinstalled (gd, freetype mysql etc with php and apache ) also it had some smtp clients and ssl applications its can be downloaded from [apachefriends]("http://www.apachefriends.org/en/index.html") website

wow! looks like thats the all in one,,.. im gonna try the lot lads and let you know what happens tommorra! cheers fella's!:guitar:

---

### Post by Ek0nomik on 2007-03-01
Using XAMPP you can have it done in no time.  It comes with Apache, PHP, MySQL, and Mercury Mail.  It also has phpmyadmin to administer your database.

---

