---
title: "Ubuntu Server edition vs Windows home server"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by rgotten on 2008-02-23
I am new to all this, and as i mention earlier onn this forum, i am trying to buoild myself a small server for my office. Googleing I cam to discover Ubuntu server edition, and also researching have found that Windows home server edition runs for about $150. Even thoug Ubuntu is free, i would like to know why should i go with one of the two, and whcih one is more friendly, stable and easy to use for a small office server

Thanks

Rgotten:confused:

---

### Post by LeeDavis on 2008-02-23
If your using a server product at its most basic (maybe authentication and file sharing) I would go for Windows for ease of use and friendly (as far as setup goes).  Stability i would choose linux.  You also might want to consider life span too (Hardware & Software).  Typically with Microsoft products the newer the software the higher hardware reqs are.  Linux does not usually suffer this, thus, it mean saving some cash on Hardware.

---

### Post by freebeer on 2008-02-23
I don't have any experience with Windows home server, but I do have experience with other Windows servers (NT and 2003).  Windows tends to be more resource hungry than Ubuntu.  However, if you're more familiar with Windows, the learning curve of Ubuntu may be steeper than you're willing to go if you've got special requirements or considerations.

Ubuntu 7.10 comes with Samba (Windows sharing) already pre-installed and configured, I believe.  This may be perfectly adequate for your needs.  Since Ubuntu is free, you can alway give it a try to see if it meets your needs out-of-the-box (or with minimal adjustment).

My guess is that Windows home server is not going to be as robust as Ubuntu and that may be a consideration as your needs grow.  It's speculation on my part, but I suspect the Windows Home Server will have some key elements missing for a real server (depending on your needs) with the intent to force you to upgrade to a "real server edition".  That's what they did to XP Home edition with regards to joining domains.  #-o

---

### Post by rgotten on 2008-02-23
I am a docotor and would like to save all my pictures of patient, chart document into the server, have backups, and be able to remotly access it. I was planning to built the server with 2 500 gb hdd and a pentium 4. What do you think?

---

### Post by freebeer on 2008-02-23
What you describe is easily (depending on your comfort level with the OS) accomplished on Ubuntu.  And yes, remote access is available.

I *suspect* (but don't know) that Windows Home Server may not allow you remote access.  (Too insecure and possibly one of the vectors forcing you to "upgrade" that I spoke about earlier.)

---

### Post by rgotten on 2008-02-23
Do you think that a pentium 4 with 2 hard drive 500 gig each will do the work with ubuntu since is less resource hunbgry, or do you have any recomendation. I was trying to follow this recomnedation on building the server: [http://www.popularmechanics.com/technology/how_to/4247239.html](http://www.popularmechanics.com/technology/how_to/4247239.html)

Thanks

Rgotten

---

### Post by seventhc on 2008-02-23
One thing you should know.
Ubuntu server is command line only out of the box, but a desktop environment can easily be installed so you have a gui.

---

### Post by Daveski on 2008-02-23
> **rgotten said:**
> Do you think that a pentium 4 with 2 hard drive 500 gig each will do the work with ubuntu since is less resource hunbgry, or do you have any recomendation

Should work like a dream. how much RAM does this machine have? I have an Ubuntu server running on a PII with 256Mb and although it is certainly not fast, used as file and an email server it is just fine.

Also you do not NEED the server version of Ubuntu as you can install all the server components on the desktop version. I would recommend installing the standard desktop and adding server software of your choice (Apache, MySQL, Samba Server etc.)

---

### Post by JoshuaRL on 2008-02-23
Okay, if you want to do that you'll need the following:

* Secure (very important for you) remote file serve
* Secure firewall
* Secure OS
* Static IP address

That is probably much better and easier accomplished with Ubuntu.  And that link you have tells you how to set up the hardware for a server, not really the software.

If you decide to go with Ubuntu server, please realise that it doesn't come with a GUI out of the box.  We can help you set up and secure your system no problem, but you'll have to be willing to do a little work and learn a little.

But as far as servers go in the real world, probably 80-90% run on Linux because its so secure.

And, hopefully, welcome!

---

### Post by dasunst3r on 2008-02-23
When choosing, consider that Ubuntu Server is:
[list]
[*]Available at no cost -- not now, not ever (donations are appreciated, though)
[*]Adaptable to YOUR needs
[*]Requires less resources, which means that you can buy an older machine and it would still work well.  As a matter of fact, I have a server running Apache (HTTP server), MySQL (database), SSH, and FTP using only 128 MB RAM and not even touching the swap.
[/list]

For remote access, you will need to DMZ the server on the router and use something like ddclient.

---

### Post by Daveski on 2008-02-23
> **rgotten said:**
> Windows home server edition runs for about $150.

I have yet to hear any good feedback about Windows Home Server edition, although it hasn't been out for very long. If anyone here has some experience I would be interested in your opinions.

rgotten - remember this is an Ubuntu forum so I would expect most people will recommend Ubuntu as this is where their interest and experience lay. Also there are good reasons that most internet servers are Linux based.

---

### Post by JoshuaRL on 2008-02-23
I would suggest using Samba for fileserving in your circumstances.  Samba is easy once configured, and it is much more secure than FTP or other things.  There are a lot of resources for Samba configuration, but here's one from the help wiki:

[Setting up Samba](https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29)

---

### Post by rgotten on 2008-02-24
I have not decide yet, how much ram, but i am thinking about 2 gb

---

### Post by rgotten on 2008-02-24
Even though I am a doctor, I am pretty savvy on computers, but the linux enviroment as well as the ubuntu is new to me.  Is it hard to install a GUI, is it time consuming

Thanks

---

### Post by JoshuaRL on 2008-02-24
Not hard at all.  If you have the server edition installed you can just do one of the following:
```

sudo aptitude install ubuntu-desktop
sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-desktop

```
Ubuntu-desktop installs Gnome, kubuntu-desktop installs KDE, xubuntu-desktop installs XFCE.  You can look on Wikipedia to find out more.

I would suggest using Xubuntu, it's easy on system resources.

---

### Post by michaelzap on 2008-02-24
Why are you looking at a Pentium 4 CPU? Personally I only buy Core 2 Duo CPUs right now. There are some faster quad-core CPUs especially for server machines, but for most purposes I find the Core 2 Duo to be by far the best choice on the market now (relatively low price, hella fast, excellent software compatibility, uses very little electricity and doesn't overheat).

---

### Post by bodhi.zazen on 2008-02-24
If you are not familiar with Linux you need to be willing to learn, which may take a few months, or you should go with Windows.

A Linux server typically comes with no gui, and really one is not needed as you can do everything from the command line and with server usually you are manually editing config files.

The easiest command line editor for most new users is nano.

vim is very powerful, as is emacs, but these take some time to learn.

IMO the advantage of Linux is not cost, it is security.

The biggest downside you face is the time factor. With your profession I am sure your time is at a premium so if you have no experience with Linux you will need to factor in the time it will take you to learn Linux.

If you have a spare box (or partition), I suggest you install the Ubuntu Desktop and try your hand at basic networking. Can you get a samba server up and running ? How long did it take you ? Factor the time spent learning ubuntu into the cost.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Can your windows boxes connect to the Ubuntu server ?

That "little" exercise will give you a feel of what running a Linux server is all about.

Most people, myself included, find most, if not all, of the Windows experience they have is not transferable to Linux, the major exception would be networking experience.

---

### Post by rgotten on 2008-02-24
Thanks for all your reply and help, this looks very interesting. If you let me ask you the following:
I now this is time consuming, and that is why I am goin to do thi slowly. First by the components and build the server, then i cna play installing ubuntu and see how it works.

In reference to the server: if at the present moment alll my computers are windows xp base ( and for now they will stay that way), and i start saving the information from this computers into the server (which will be a linux base), will this comunication be fast? what happen in teh future if i decide to convert the server to a windows base system, will i be able to trnasfer the informationfrom teh server to a windows enviroment without any problem and withoutl loosing it organization??

Do i need a spare box, or just do the server and see how it works bedore starting for sure to save the chart information data in to the server??

Thanks a lot

---

### Post by rgotten on 2008-02-24
Thaks for your coments. At the present moment i have my computer network and the files are being save in each one of them, I am planning for the future and my idea was start to build the server, install a software and what i heard on some reviews, that ubuntu is the way to go, and i was planning to start learning/playing with it a little bit. If i install ubuntu on this server and then play on achieving the filw storage, backup and remote conecting while i learn. Do you think i will have a problem before i really use it for my whole office. will it intereact smoothly with my windows computers?

One more time thanks for your input and advise

---

### Post by Syndacate on 2008-02-24
I don't feel like reading all the posts here, so sorry if I'm regressing.

DEFINITELY - WITHOUT SECOND THOUGHT Ubuntu Server Edition.

No, I'm not some crazy linux fan, it's real simple.

I was using XP as a home server, now I'm not sure how much worse that is as a server than the windows server deal, but it's pretty bad.

From what I can tell the OS has MAJOR memory management issues.  I was hosting an FTP and HTTP server through there (I was only using it for storage at the time) and it was like bi-weekly thing that I had to connect a monitor 'n to restart it because it would die/bog out and would require a restart.  It was absolutely horrible as a server from my experience with it.

Now I use Ubuntu (regular) every day and I RARELY have to restart in general - none-the-less the fact that this is on my old server which I deemed a long time ago as "archaic, old, and EXTREMELY UNRELIABLE" - Now that Ubuntu is on it it seems to be 100% reliable, I've been using Ubuntu for the past ~9 weeks and with the exception of one X11 server crash, and me and my friend fighting for the mouse which jammed it up ;) I've never had a problem with it.  And of course since it's Ubuntu every jam problem I've had with it did NOT kill the computer, I just SSH'ed in via putty on my windows machine and restarted it remotely.

You have no idea how unstable my computer is and how stable Ubuntu made it.

I have a 3.0Ghz P4 processor, so right off the bat it runs hot, it's the nature of the processor, but mine runs...VERY hot, unnaturally hot, I've had overheating issues a few times even though there's like 10 fans (literally) in the case.  

It gets better than that, ie. none of my fan controllers work, all USB devices work on 1.0 even though they're all 2.0, my computer will not boot if my iPod is plugged in (ubuntu or windows), it will not recognize an external hard disk until 7m45s after it's plugged in in windows, 80% of the time when I boot it will not recognize a hard drive, so I have to keep rebooting until it finds one, then I have to use a PS2 keyboard because the USB isn't active at that point in the game so it won't detect the keyboard so I get the epic "No keyboard detected" message - but that's only if I can avoid the "Your CPU is undetected or has become unworkable, press F1 to continue" message.

So read that, realize that I PROMISE YOU I am NOT overemphasizing ANY of that - I have to go through when I restart my computer because of how unstable it is.  Sometimes it takes 30 minutes to hardboot my computer from dead off.

So now that you see how unstable my system is, I can tell you that since installing Ubuntu, I've restarted <10 times over the progression of the 9 weeks I've had it installed, and only like 2 or 3 were needed due to software installs, the rest were just like restarting it because I didn't know the hotkeys to restart the X11 GUI or stuff like that.  

For some reason my computer has a "shutdown memory" (yes, I coined the term) as if you shut it down from windows it won't have USB support at GRUB upon boot, so you have to use the PS2 keyboard to select my partition to boot (which is why I made sure default is Ubuntu for GRUB) and if I shut it down from Windows with an external hard drive still plugged in, it won't shut down at all.

I use windows almost daily though on my laptop to play games though.  I'm **NOT** downing windows in any way what-so-ever.

When it comes to server-needed-stability, GO UBUNTU.

PS:
Before you rant on me about how I have a "bad installation of windows" like that - it was installed, a put on a new wallpaper, it has an FTP and an HTTP server - that is it.  So it's not like a crap version of XP loaded with limewire downloads and the like.  It's a pretty clean install.

I promise you you will have less problems as a server if you use Ubuntu - and I rarely promise anything.

EDIT:
PS:  Let's not forget the cold, hard fact that Ubuntu is updated damn near daily and is free while Windows is updated bi-monthly (if that) and costs a ton for you to "rent" it (if you read the Windows user terms and license agreement you'll find out that you don't actually "own" a copy of windows, but more-so you're "renting the license" to use Windows - it's a joke).

Also, like I stated before but I don't think I stressed the importance of it:
**I AM NOT** a Linux Zealot - I do not think "linux, linux, and only linux", I just like the stability for a daily computer.  I also think windows does NOT suck, it all depends on the user, most users don't know Windows too well so they tend to have problems quickly, others have installations of Windows that have been working fine for years (ie. my laptop one +1 years w/ no problems).  Windows is a good system, but has its fair share of issues, as does any OS.  If you check the archives you can see the MASS number of posts I put in there about problems I've had with Ubuntu - but none are serious and none would matter if it was a server.  Ubuntu is a bit tricky to get fully functional for a daily, but once its setup the stability is super.  

Windows is great for what it is, but you know there's an issue when "recommended maintenance" for Windows entails a bi-anual reformat (yes, Microsoft recommends a reformat every 6 months).  Though I still remain (and both the Linux zealots and the mac fan boys can go to hell on this one) that Windows is the most versatile OS out there - why?  **Everything is made for it.**  Everything is originally made for windows, then apple makes their own proprietary stuff for their stuff, then somewhere in between some programming either A)  hacks the program and uses it to make a new version which is open sourced, or B)  programs from scratch something that works just like it.

The biggest boundary of Linux when coming from windows is everything is not originally made for it - it's "secondary" - and it's not proprietary.  You get past that, you're fine.

---

### Post by bodhi.zazen on 2008-02-24
I think once you adjust to Ubuntu you should have no problems at all.

The only problem may be trying to run windows software on Ubuntu, but you have not mentioned that.

---

### Post by seventhc on 2008-02-24
I would say Ubuntu will need a lot less reboots than windows. I used to know a site that shows the uptimes of different sites and what servers they were using. If I remember correctly FreeBSD usually had the most uptime, Windows was usually rebooted recently.
I can't remember the name of that site though and I'm trying to find it again.
It will give you a good idea about stability with different severs.
As for BSD, it isn't exactly user friendly, so I'm not recommending it. I'm just using the stats I remember.
Does anyone here know of the site I'm talking about?? If so please post the link. But I'll try to find it.

---

### Post by Syndacate on 2008-02-24
I'd also like to mention that Fidora is more of a server type linux OS.  Though I don't know anything about Ubuntu server edition so I can't tell you which is better.

---

### Post by rgotten on 2008-02-24
Well my idea is have my computers windows base and run windows programs, and then have all the information store in the server. Lets say i have a chart of a patient created in word for windows; the chart will be save into the server foilder; if i need to open it will i be able to see it on my windoows computer and opened from the server that is on linux (ubuntu) format, or will that be a whole process to oepn a file, the same question come if i conect remotly to the server and with my laptop which is windows xp and would like to open chart 1234 of pateitn peter perez which was created on word and safe in the server..Will this work smothly or not??

---

### Post by seventhc on 2008-02-24
OK, found it, you can find all sorts of different info here. here is one based on performance. 
the results are mixed between BSD and Linux with one mention of windows.
[http://news.netcraft.com/archives/performance.html](http://news.netcraft.com/archives/performance.html)
But windows scores pretty good in some of the other stats.
Note: They don't differentiate the different linux distros, so you won't see the name Ubuntu, only linux.

---

### Post by freebeer on 2008-02-24
> **rgotten said:**
> if i conect remotly to the server and with my laptop which is windows xp and would like to open chart 1234 of pateitn peter perez which was created on word and safe in the server..Will this work smothly or not??

Sure.  No problem (aside from configuring it properly, which is not a difficult task).

---

### Post by JoshuaRL on 2008-02-24
I agree with freebeer.  If you ever wanted to view the Word files on the server you might have minor issues because it's a word file, but if all it's doing is serving the files to other computers than you really shouldn't have any issues.

And for you, the stability and security of Ubuntu will be the biggest positive.  With the ease of use once configured a close second.

---

### Post by Daveski on 2008-02-24
> **rgotten said:**
> Well my idea is have my computers windows base and run windows programs, and then have all the information store in the server. Lets say i have a chart of a patient created in word for windows; the chart will be save into the server foilder; if i need to open it will i be able to see it on my windoows computer and opened from the server that is on linux (ubuntu) format, or will that be a whole process to oepn a file, the same question come if i conect remotly to the server and with my laptop which is windows xp and would like to open chart 1234 of pateitn peter perez which was created on word and safe in the server..Will this work smothly or not??

Sounds like you are going to use Windows desktop machines, and use the server as a network file store. If this is the case, then the data files will be fine being stored on a Linux server (you will be using something called Samba to allow the Windows machines to 'map' a network drive to the file store.).

The contents of the data files stored on your network server are irrelavent to the server, only the clients which connect and use it, so this will all work just fine. Many NAS (Network Attached Storage) devices are Linux based and Mac or Windows clients can happily use these as network data storage (see LaCie or Buffalo devices). You will be doing a similar thing with your Linux server.

You asked before about transferring to a Windows server, and will your data be safe? The answer is that you can copy this data to a Windows server without issue - or you could restore from your backups straight to a Windows server. If you are asking if the data will be safe if you install Windows 'over' the Linux installation, then you will need to know a little about the WAY Windows and Linux use local disks to store data.

Generally Windows (NT / 2K / XP / 2K3 / Vista) will use NTFS which is a proprietory file system, Linux will use ext2 or ext3 as a file system. Both can use FAT as a file system 'out of the box', but an NTFS driver can be installed to allow Linux to read / write to a Windows NTFS drive. I do not think Windows has an ext2 or ext3 driver, but someone may be able to shed more light on this. Basically so long as data is transfered over a network, then the underlying filing system is not an issue as the local OS deals with the transfer from Network protocol to file system protocol.

I hope I haven't confused things for you.

---

### Post by rgotten on 2008-02-24
All of you have being excelent in your help, and I really appreciate it. I believe that i am goint to build the machine and start with ubuntu and then swoly learn how to do things and hopefully guys like you will be around to help me. One last question for now, and since i am going to have all my patient information on this server: I was thinking to build a computer with a motherboard that Support RAID 1, and is my understanding that the 2 hard drive will be a mirror of each other, so if one fails, the other takes command. Should i install a 3rd hard drive for pure backups (just in case) or is the imaging pretty secure???/ Or should i back up to an external har drive????

Thanks

---

### Post by Daveski on 2008-02-24
> **rgotten said:**
> I was thinking to build a computer with a motherboard that Support RAID 1, and is my understanding that the 2 hard drive will be a mirror of each other, so if one fails, the other takes command. Should i install a 3rd hard drive for pure backups (just in case) or is the imaging pretty secure???/ Or should i back up to an external har drive????

Your understanding of RAID1 is correct. I would recommend backing up to an external drive, or even better have 2 external drives and swap them around regularly. The one that is not attached should be locked away somewhere - preferably away from the server or better still in another building to protect the data against a disaster such as a fire.

---

### Post by seventhc on 2008-02-24
couldn't hot swappable drives be used for back-ups?

---

### Post by seventhc on 2008-02-24
I worked for a place that did have critical data, and there way for safety was 
a daily backup
a weekly backup
a monthly back up
back ups got sent out to an off site storage facility
so they would have one backup we would have another copy of the back up and we basically had these people coming all the time dropping off and picking up the new.
Having back ups in 2 locations is a good idea, the chance of 2 places burning in disaster is extremely rare.
Your data seems critical, you might not a company that specializes in storage for you, but I would recommend at least 2-3 copies in at least 2 separate locations.
One could be your server I suppose and at least one in your home or some other place you deem safe.

---

### Post by rgotten on 2008-02-24
Do i have to do backups to the external hard drive and then swap them or can i have an exteranl hard drive at home and connect remotly with my laptop to the server and do a backup let say twice a week. loosing a few days of data is not terribel if there was a disaster, on the other hand if on hard drive fails on the system, i should still have the secon one workig. Or i should have a second basic computer in a diferent location doing backups coneting remotly to the server at nigth???what di you think

---

### Post by Daveski on 2008-02-24
Backing up remotely from a remote site is a great idea. You can usually just send the changed data so that each time the data transfer is fairly small.

---

### Post by dasunst3r on 2008-02-28
Oh, yeah... Ubuntu server won't corrupt your files: [http://www.betanews.com/article/Microsoft_struggles_to_fix_data_corruption_bug_in_Windows_Home_Server/1204145747](http://www.betanews.com/article/Microsoft_struggles_to_fix_data_corruption_bug_in_Windows_Home_Server/1204145747)

---

### Post by troutbum13 on 2008-02-28
I will offer my experience, I had a WHS server for about 6 months, I just switched to Ubuntu server 7.10 this week.

WHS:
pros
[LIST]
[*]Easy to set up and administer
[*]Shares and backups are VERY easy.
[*]The console idea is great for the average home users (this is an applet that installs on all the client machines that allows you log in and use a GUI to change shares, permission, and duplication)
[*]Pretty stable, I was running 24/7 and don't recall any crashes
[*]Easy to add storage
[*]built in websever with remote access to server and all windows PC's on the network
[/LIST]

cons
[LIST]
[*]SLOW...this may not be a problem for everyone but uploads to the server as low as 3-5MB/s over gigabit. If you are sending charts and snapshots this may not be a big deal, mine is a media server.
[*]Slow speeds are a result of the Drive Extender (DE) which copies files first to a storage drive and then recopies them to the JBOD shares. During what M$ calls duplication the system is dog slow.
[*]JBOD duplication...I think there are better ways of storing redundant data (RAID or LVM striping)
[*]$150 plus all the WPA junk
[*]Did I mention it is slow?
[/LIST]


As I said I moved to Ubuntu this week, I have been running linux as a desktop OS for a bit and decided to take the jump. It takes a lot more time to set up but is much more flexible. This is more a hobby for me so I don't mind the extra time/effort as I am learning a ton, but for a business?? I think linux better suits my needs and I would not go back to WHS. But WHS does a specific job abd does it OK :)

As a side note what could push ubuntu over the edge is a home edition of webmin. Webmin is great, but way too advanced for most home server users.  All you really need is User Access, Share Access, and Remote Access. If you could put something simple like that in front of ubuntu, LVM, RAID, samba, NFS, VNC, X11 and apache it would make set up and adoption so much easier.

---

### Post by Daveski on 2008-02-28
> **dasunst3r said:**
> Oh, yeah... Ubuntu server won't corrupt your files: [http://www.betanews.com/article/Microsoft_struggles_to_fix_data_corruption_bug_in_Windows_Home_Server/1204145747](http://www.betanews.com/article/Microsoft_struggles_to_fix_data_corruption_bug_in_Windows_Home_Server/1204145747)

Oh dear - the info from MS is a bit scant isn't it? Surely MS have LOADS of experience with mission critical data especially with something as core as network file storage - how come they dropped the ball with this one?

---

### Post by freebeer on 2008-02-28
My guess is that they deliberately hobbled the Home Server edition to keep people from using it at a cheaper enterprise server.  Note that the article claims the problem arises when a second drive exists.  I'm guessing that they figured that if you had enough storage requirements to require a second hard drive, you're really running a "real" server and therefore should cough up real bucks for one.  Not unlike ensuring that the XP Home can't join a domain, etc.

---

### Post by igknighted on 2008-02-28
> **Syndacate said:**
> I'd also like to mention that Fidora is more of a server type linux OS.  Though I don't know anything about Ubuntu server edition so I can't tell you which is better.

May I recommend for his project: Mandriva 2008!  Mandriva has a control panel to set this all up graphically, plus the Mandriva Directory Server makes file serving a breeze.  Much easier and more "newb friendly" than anything on Ubuntu right now.  Red Hat and Fedora (and CentOS) also have Fedora Directory Server, which is quite good (but a little more complex), and openSUSE has something, I forget what it is called, but it is pretty good as well i think.

---

### Post by TeslaTony on 2008-02-29
I believe that Windows Home server gives the option to run software remotely (i.e. install the software on the server, then run it on the computer of your choice instead of installing it on just one computer) if you have XP pro or Vista Business or Ultimate. Ubuntu won't be able to do that (at least not painlessly) for Windows-based software, which might be a consideration if you absolutely must have a particular program run that way.

Last I checked, Windows Home Server does offer remote logins to access files from outside the network. If you're storing data tat is at all sensitive, I'd be a little leery of the security that Microsoft has to offer.

---

### Post by SergioLopes on 2008-02-29
Sorry for bringging this up.

Currently i have a windows home server setup running with 5TB of storage using the drive extender feature (a total of 4 external hard drives), but i'm having too many problems with file transfer / streaming speed... 

I'm looking for an Linux alternative to try solve this isue.. but i realy need that "drive extender / span" feature... 

Any linux alternative ? 

PS: the main use of this server is to "stream" HD 720p and 1080p to a Hp Elite in the living room.

Thanks in advance.
Best regards

Sergio Lopes

---

### Post by 3rdalbum on 2008-02-29
Be aware with Windows Home Server: If you ever have to call Microsoft for support, they might refuse to help you if they know you're using their product outside a home environment.

My other comment is: I'm not sure you can even get Pentium 4 CPUs anymore, but I'd recommend against using them. They're great as a space heater, but not good in any other sense. A basic server can quite happily have a basic CPU, so I'd be looking at an AMD Sempron or a basic Core 2 Duo, tops.

---

### Post by JoshuaRL on 2008-02-29
> **SergioLopes said:**
> Sorry for bringging this up.

Currently i have a windows home server setup running with 5TB of storage using the drive extender feature (a total of 4 external hard drives), but i'm having too many problems with file transfer / streaming speed... 

I'm looking for an Linux alternative to try solve this isue.. but i realy need that "drive extender / span" feature... 

Any linux alternative ? 

PS: the main use of this server is to "stream" HD 720p and 1080p to a Hp Elite in the living room.

Thanks in advance.
Best regards

Sergio Lopes

Well, Ubuntu supports whatever your Motherboard can throw at it.  It won't be hobbled or restricted like WHS.  File transfer will be easy after you get it set up, and will be much faster from what I understand.

---

### Post by Daveski on 2008-02-29
> **freebeer said:**
> My guess is that they deliberately hobbled the Home Server edition to keep people from using it at a cheaper enterprise server.  Note that the article claims the problem arises when a second drive exists.  I'm guessing that they figured that if you had enough storage requirements to require a second hard drive, you're really running a "real" server and therefore should cough up real bucks for one.  Not unlike ensuring that the XP Home can't join a domain, etc.

Interesting theory - if a little 'conspiricy'. Surely Ms wouldn't stoop this low... ;-)

---

### Post by troutbum13 on 2008-02-29
> **SergioLopes said:**
> Sorry for bringging this up.

Currently i have a windows home server setup running with 5TB of storage using the drive extender feature (a total of 4 external hard drives), but i'm having too many problems with file transfer / streaming speed... 

I'm looking for an Linux alternative to try solve this isue.. but i realy need that "drive extender / span" feature... 

Any linux alternative ? 

PS: the main use of this server is to "stream" HD 720p and 1080p to a Hp Elite in the living room.

Thanks in advance.
Best regards

Sergio Lopes

That is what I use my server for as well. Look into LVM, it is CLI (AFAIK) but works great for adding and subtracting HDDs to a storage pool as your collection grows.

---

### Post by freebeer on 2008-02-29
> **Daveski said:**
> Interesting theory - if a little 'conspiricy'. Surely Ms wouldn't stoop this low... ;-)

Nah.. they'd never do such a thing.  The whole "can't log in to a domain in XP Home" is just my ineptitude.  Or Win2k claiming that an old hard drive I dropped into a new box is "unformatted", yet Ubuntu reads and writes to the drive just fine. ;)

---

### Post by archer75 on 2008-03-13
> **troutbum13 said:**
> That is what I use my server for as well. Look into LVM, it is CLI (AFAIK) but works great for adding and subtracting HDDs to a storage pool as your collection grows.

But what about redundency? I assume you could create two LVM "pools" and setup RAID 1 to mirror it but what if each pool ends up being a different size? What if you remove a drive from one of the mirrors, how does that affect the data on the other LVM pool?
What if you want a single pool of storage but don't want everything mirrored?

---

### Post by mestreofmestres on 2008-03-17
For the orignal poster, rgotten, believe me, you don't want to go with Windows Home Server. It's crap. Your remote access privilages are limited in that only one person can remote into it at a time (might as well be Windows XP/Vista for that matter). IF you went with a Windows solution, you need to go with Windows Server 2003 (or 2008 if your bold enough to try something brand new from Microsoft). As someone else posted, the learning curve coming to Linux isn't as steep as some people make it out to be, but if you've never opened command prompt in your life in Windows, then coming to Linux probably isn't the answer. It's definately more stable, but reality is, you have to use command line a lot even with a GUI installed. Even with Samba (the Windows File Sharing utility in Linux) every GUI utility I've used with it is pretty lame, I had to learn how to do it through konsole.

The choice is yours, but definately stay away from Home Server

---

### Post by mestreofmestres on 2008-03-17
> **freebeer said:**
> Nah.. they'd never do such a thing.  The whole "can't log in to a domain in XP Home" is just my ineptitude.  Or Win2k claiming that an old hard drive I dropped into a new box is "unformatted", yet Ubuntu reads and writes to the drive just fine. ;)

Don't forget, Windows 2000 won't read anything bigger than 128GB, so your hard drive is probably too big. Windows 2000 is 8 years old, anything that big wasn't even fathomed at that point.

Also XP Home is supposed to be a Home Edition platform, not too many people have Domain Controllers at home =)

I'm all about the approach of having everything in one version, but Microsoft like's to get money, what can I say

---

### Post by freebeer on 2008-03-17
> **mestreofmestres said:**
> Don't forget, Windows 2000 won't read anything bigger than 128GB, so your hard drive is probably too big. Windows 2000 is 8 years old, anything that big wasn't even fathomed at that point. 

That's not the problem... that particular drive was running Win2k before I upgraded the machine.  :D

> 
Also XP Home is supposed to be a Home Edition platform, not too many people have Domain Controllers at home =)


And why not?  :D  Seriously, though, I agree that most certainly wouldn't.  But I've run into situations where you want to join a domain, at least temporarily.  Microsoft had to deliberately disable (read: go out of its way) to do so.  It's like crippleware.

---

### Post by BlizzofOZ on 2008-03-18
Not sure if this has been mentioned, but WHS is having some data corruption problems.  I believe it happens when you add a drive to you've installed WHS and had it up and running.  Adding a new drive and then using apps that will write to files stored on the server causes corruption.  This includes some apps simply opening a mp3 file because they write info to the file.

Additionally, backups have also been reported corrutped.

This alone sent me to look at Ubuntu... Within a week I have it up and running with Samba file serving.

While I have command prompt experience, I don't how that someone with computer experience couldn't research get this OS running.

---

### Post by rgotten on 2008-03-28
All of you have being excellent on your comments and help, and after few weeks of thinking about this project I would like to summarize my ideas and get a consensus from all of your ideas so I can start it, let me say that I may ask some questions that might be out of this forum spectrum, but your help an orientation is very highly appreciated. As I mention at the beginning, I am a doctor and so far I have paper chart for my patients, and I am planning to do this project in about a year time and if it works after multiple testing, and being safe proof then I might move all my charts to this approved and safe project. I am going to express my project and at the same time ask question and would appreciate answer to them so I can make a start of this. 

My office has 3 computer + my laptop that run on windows xp professional, there are network thru a router (3 wired and my laptop wireless). My plan is as follow: I use word for windows with different templates to create the history and follow up evaluation of my patient. I use zoombrowser from cannon to save the images in a organize way (jpeg format). As you can see this is very primitive and this information is basically saved on my laptop and regularly safe into an external hard drive with Ghost. I would like to create a simple database where my front desk girl will place the name of the patient and chart number; this will have subfolder called for example: Medical record (where I will dictate on the word document template), Billing (where my secretary will scan and safe on pdf format payment from the insurance company, patient, etc), Photos (where I will safe the jpeg files), and other subfolder. (Help also on creating this database will be appreciated).

i.e John Smith 1111 	  ….Medical Record
				       Billing
				       Photos
				       Laboratories
				       Etc..

It is my believe after reviewing this forum and all your greatly appreciated comments that this is the step to follow:

	a) Build a computer: probably a duo core or sempro with 2 gb of ram, 500 wt of power, on raid 1 with 2 (500 gb) drives build on a chip case

	b) From this forum I heard about using xubuntu, kubuntu, etc, or even ubuntu desktop, and then add server software of my choice (Apache, MySQL, Samba server, etc) but also some of you feel very confident that I should use ubuntu server edition with LAMP. So I guess I have to install this (unless somebody has any other idea), and play with it, (I hope you guys will be there to help me on this.

	c) In my impression this server will be use for the following purpose (please correct me if I am wrong): all this files world, jpeg, pdf, etc) from any of my 4 windows xp computer will be save and also be access from these server. At the same time, being a raid 1 computer if one of the 500 gb hard drive fails, the other will start working as a mirror, also will have an external hard drive connected to one of the window xp computers from where a copy can be done from the server in a incremental way to have all the data of the server on a windows format external hard rive as a backup, and also be able to do a remote connection to the server on a weekly basis from my home windows computer and also do a remote backup in a incremental way. After I play with this and can safe some of the files from all this computer into the server, then I can safe bigger folders and see how this works to be access from the computers and also remotely access, and if after playing and this works, then work on creating the database…

	d) If anybody will guide me on how to build this database to be use on windows environment computer and safe the information on the ubuntu server and also be able to access this remotely from any computer I guess as a web page..Your help on this may be very highly appreciated.

One more time, I know I am asking many things and some of them may be out of the scope from Ubuntu forum, but on the same token, you guide has being excellent, as well as your help and instruction and your  orientation will be appreciated, I will follow steps and instructions of the most expert people…and in advance…..Thanks

rgotten

---

### Post by Daveski on 2008-03-29
> **rgotten said:**
> 
	c) In my impression this server will be use for the following purpose (please correct me if I am wrong): all this files world, jpeg, pdf, etc) from any of my 4 windows xp computer will be save and also be access from these server. At the same time, being a raid 1 computer if one of the 500 gb hard drive fails, the other will start working as a mirror, also will have an external hard drive connected to one of the window xp computers from where a copy can be done from the server in a incremental way to have all the data of the server on a windows format external hard rive as a backup, and also be able to do a remote connection to the server on a weekly basis from my home windows computer and also do a remote backup in a incremental way. After I play with this and can safe some of the files from all this computer into the server, then I can safe bigger folders and see how this works to be access from the computers and also remotely access, and if after playing and this works, then work on creating the database…


Sounds good. The Ubuntu server will initially be just a file server for Windows machines (running Samba to allow Windows machines to access the file shares over a LAN).

Your database is going to run on Windows machines, correct? I think you could write a MS Access database to do all that you require - are you at all familiar with Access? The Access database will be a shared file which can be hosted on the File server. Or you could have the database actually running on the Linux machine and have a web front end which can be accessed from the Windows machines (or any machine with a browser). This might be more complex to contruct.

---

### Post by rgotten on 2008-03-30
The database is going to be seen in windows machines, yes...Even though i have MS access on my computer i have never use it, if this is the route to go, where can i start learning about this, how easy it is to load images, remember also that i would like to be able to access the database remotly from any hospital as a web page, can this be done if the information is on ubuntu and i am accesing remotly from any computer in the hospital to check the information on one of my patients? will a database like you mention on linux hard to do..Thanks fro you ideas and comments. Also what about kuuntu xuvbuntu, etc, will it be more stabel to install ubuntu server and then a gui or you guys can help me with some of the scripts to write...I am planning to go today and buy the components of the computer to start building it up...Thanks

---

### Post by rgotten on 2008-04-04
I have built my server, it has a duo core on a nvidia 680isli motherboard with 2 gib of memory and 3 hard drive of 500 gb each, I am planning to do RAID 5. I am going to install Ubuntu server and then Kubuntu GUI (unlkess otherwise advise), How do i do the RAID 5 on Ubuntu server

Thanks

---

### Post by freebeer on 2008-04-09
Probably redundant, but it might benefit someone else reading through this thread.  I ran across this article on MS Home server: [linky]("http://www.eweek.com/c/a/Storage/Windows-Home-Server-Unbelievably-Bad-Storage/")

---

### Post by hyper_ch on 2008-04-09
> **rgotten said:**
> I would like to create a simple database where my front desk girl will place the name of the patient and chart number; this will have subfolder called for example: Medical record (where I will dictate on the word document template), Billing (where my secretary will scan and safe on pdf format payment from the insurance company, patient, etc), Photos (where I will safe the jpeg files), and other subfolder. (Help also on creating this database will be appreciated).

i.e John Smith 1111 	  ….Medical Record
				       Billing
				       Photos
				       Laboratories
				       Etc..

Have you considered using a CRM software? Maybe have a look at vtiger and sugarcrm. Both are free of charge (at least some versions). With those you should be able to manage your contacts, patient history (cases), billing, and more stuff... all you need is a browser (and of course a server...). As I'm thinking of becoming independant on my own I'm also currently evaluation different kind of software for that matter.

> **rgotten said:**
> 
a) Build a computer: probably a duo core or sempro with 2 gb of ram, 500 wt of power, on raid 1 with 2 (500 gb) drives build on a chip case
You won't need a powerful computer for that... what you descript up there is more than good ;)

> **rgotten said:**
> 
b) From this forum I heard about using xubuntu, kubuntu, etc, or even ubuntu desktop, and then add server software of my choice (Apache, MySQL, Samba server, etc) but also some of you feel very confident that I should use ubuntu server edition with LAMP. So I guess I have to install this (unless somebody has any other idea), and play with it, (I hope you guys will be there to help me on this.
I wouldn't go for any desktop and install a pure server. You need stability and security... the less stuff you install the better. a GUI is not needed at all. As I started with a linux server (before using it as desktop) I can recomend Debian a lot for server. It's just stable and runs and runs and runs and runs... the setting up will not be much different, only you don't ahve fancy graphics but linux servers are configure by their config files and it doesn't matter if you have a fancy looking text editor or a basic looking one.

---

### Post by rgotten on 2008-04-14
I have installed the server edition and have the option to install the extras: DNS server, LAMP, Mail Server, open SSH, postgreg SQL, print server, Samba files.
As i mention, I am new to this, Should i install all of them based of what i have said in the past and for the purpose i am building the server?

Thanks

Rgotten

---

### Post by hyper_ch on 2008-04-14
well, it depends what kind of software you want to run. The vtiger bin comes actually with (almost) all required stuff (apache, php, mysql) however a few additional things are needed... sugarcrm however comes only with the php files... for it you will be required to install apache, php, mysel...

---

### Post by Daveski on 2008-04-14
> **rgotten said:**
> I have installed the server edition and have the option to install the extras: DNS server, LAMP, Mail Server, open SSH, postgreg SQL, print server, Samba files.
As i mention, I am new to this, Should i install all of them based of what i have said in the past and for the purpose i am building the server?


The first component you need to get installed is Samba. The client files are already active on most Ubuntu distros, but you will need to install (and configure) the Samba daemon - this is the 'Microsoft File and Printer sharing' server component and will allow you to set up a shared location on your Ubuntu server which can be accessed by the Windows machines you have. There are some great How-tos on this forum for getting Samba to work.

---

### Post by rgotten on 2008-04-15
> **Daveski said:**
> Your understanding of RAID1 is correct. I would recommend backing up to an external drive, or even better have 2 external drives and swap them around regularly. The one that is not attached should be locked away somewhere - preferably away from the server or better still in another building to protect the data against a disaster such as a fire.

The motherboard raid did not work since it is a fake raid. I ended doing 3 500 gb har drive installed with software raid as follow: raid1 for boot (100 mb, each and each hard drive has the boot in it), raid 0 for swap 1gb, and raid5 for storage 989 gb. To do the backup, will this be a linux backup or will be  a windows backup?

---

### Post by rgotten on 2008-04-15
> **Daveski said:**
> The first component you need to get installed is Samba. The client files are already active on most Ubuntu distros, but you will need to install (and configure) the Samba daemon - this is the 'Microsoft File and Printer sharing' server component and will allow you to set up a shared location on your Ubuntu server which can be accessed by the Windows machines you have. There are some great How-tos on this forum for getting Samba to work.

Well i install everything on teh server option setup. One thing i left with no configuration during the installation was the " mail configuration" and I am having problems with the sudo command since it is asking for a password that i never setup. Reading and googling i found that this is because i did not perform the " mail configuration", and do not know how to configure it now.

Base on the above i have the following questions:

1) how to do the mail configuration or
2) reinstall completelly ubuntu server and just install some options (please advise on this, or is good to have everything install or if i need to install compnents after how you do this?) or
3) keep on playing for another 10 days and isntal version 8.04 (by the way, will ubuntu upgrade authomatically??when new version come out??)

Thanks

rgotten

---

### Post by chrisdugdale on 2008-04-15
I reckon that linux/unix runs a lot of the net for good reason. Not just because it's free. You can add a GUI to Ubuntu Server edition, or add LAMP (Apache2, mySQL5, php5, phpMyAdmin) to the Desktop edition of Ubuntu using Synaptic. It's fast and simple. I know there's a learning curve with any Linux distro, but the support on Ubuntu and much more accessible, more human, on Ubuntu than most. You may have a bit more time setting up, but OpenOrg.database can help you plan it out. I think you'll save time and money in security issues too. The help is much more accessible than for Windows in my opinion. My doctor friend hasn't turned back since moving to linux and I reckon you will too. It can do a lot more than just hold your picture project. I think you'll save thousands over a few years because of the stronger basics. Just my opinion, don't want to sound pushy. Chris

---

### Post by Daveski on 2008-04-15
> **rgotten said:**
> To do the backup, will this be a linux backup or will be  a windows backup?

If you just want to backup the data which is available for your Windows machines, then you can use a Windows machine to do the backups. You can also do the backups on the Linux machine if you prefer, and from here you can also backup the system and configuration.

---

### Post by Daveski on 2008-04-15
> **rgotten said:**
>  I am having problems with the sudo command since it is asking for a password that i never setup. Reading and googling i found that this is because i did not perform the " mail configuration", and do not know how to configure it now.

I am not sure what your problem is. When you use the sudo command, the password it requires is your normal user login password (so long as that user has the ability to run sudu - which by default it does).

From a terminal, if you want to run a command with full admin (root) access, then you simply preceed the command with sudo, and type your own password when requested. The command should run as root. e.g.

run **gedit **on its own and you are running with your user rights and will not be able to modify system files. Run **sudo gedit** and gedit runs as root and you are able to modify system files.

---

### Post by rgotten on 2008-04-16
> **JoshuaRL said:**
> Okay, if you want to do that you'll need the following:

* Secure (very important for you) remote file serve
* Secure firewall
* Secure OS
* Static IP address

That is probably much better and easier accomplished with Ubuntu.  And that link you have tells you how to set up the hardware for a server, not really the software.

If you decide to go with Ubuntu server, please realise that it doesn't come with a GUI out of the box.  We can help you set up and secure your system no problem, but you'll have to be willing to do a little work and learn a little.

But as far as servers go in the real world, probably 80-90% run on Linux because its so secure.

And, hopefully, welcome!

Thanks for your help,
I finally decided to istall ubuntu server, and on installation i had the option to install the extras, and i install all of them: DNS server, LAMP, Mail Server, open SSH, postgreg SQL, print server, Samba files.
As i mention, I am new to this, Should i install all of them based of what i have said in the past and for the purpose i am building the server? or should i reinstall and select only some options like LAMO, etc. 

Also when i did the installation one thing i left with no configuration during the installation was the " mail configuration" (i though i could do it later) and I am having problems with the sudo command since it is asking for a password that i never setup. Reading and googling i found that this is because i did not perform the " mail configuration", and do not know how to configure it now.

Base on the above i have the following questions:
1) What shold i have isntall with the ubuntu server, base on the above, 
2) how to do the mail configuration or
3) reinstall completelly ubuntu server and just install some options (please advise on this, or is good to have everything install or if i need to install some componets after, how you do this?) or
4) keep on playing for another 8 days and install server version 8.04 (by the way, will ubuntu upgrade authomatically??when new version come out??)

Thanks

---

### Post by rgotten on 2008-04-17
Thanks for your help, I am repeating part o my question form before but have not recive an answer that clarify my question.

I finally decided to istall ubuntu server, and on installation i had the option to install the extras, and i install all of them, thinking there were part of the package, which includes:  DNS server, LAMP, Mail Server, open SSH, postgreg SQL, print server, Samba files.
As i mention, I am new to this, Should i install all of them based of what i have said in the past in this forum and for the purpose i am building the server? or should i reinstall and select only some options like LAMP, etc. 

Also when i did the installation one thing i left with no configuration during the installation was the " mail configuration" (i though i could do it later) and I am having problems with the sudo command since it is asking for a password that i never setup. Reading and googling i found that this is because i did not perform the " mail configuration", and do not know how to configure it now.

Base on the above i have the following questions:
1) What shold i have install to beguin with in the ubuntu server, based on the above, 
2) how to do the mail configuration or so wound not have the problem with the sudo command password or
3) reinstall completelly ubuntu server and just install some options (please advise on this, or is good to have everything install or if i would like to install some componets after, how you do this?) or
4) keep on playing for another 7 days and install server version 8.04 , or if i keept it the way it is , will ubuntu upgrade authomatically, when new version come out??)

Thanks

---

### Post by Daveski on 2008-04-18
> **rgotten said:**
> Base on the above i have the following questions:
1) What shold i have install to beguin with in the ubuntu server, based on the above, 

I recommended the Desktop version, but if you have decided on the Server, that is fine. My suggestion is that you will only need the SAMBA server to allow XP machines to access the data stored here. I think that the DNS, mail, postgres SQL and printer servers are not useful yet for you, although SSH might be. LAMP will only be required if you want to set up a web based version of your database - but this is a BIG project.

> 2) how to do the mail configuration or so wound not have the problem with the sudo command password or

Are you still having problems with sudo? Have you understood my previous post with a quick explanation of what the sudo command is and how you use it? Is a mail important for this project?

> 3) reinstall completelly ubuntu server and just install some options (please advise on this, or is good to have everything install or if i would like to install some componets after, how you do this?) or
4) keep on playing for another 7 days and install server version 8.04 , or if i keept it the way it is , will ubuntu upgrade authomatically, when new version come out??)

There is no harm having everything installed so long as the machine has the resources like memory etc. To install the extra components later (or on the desktop version) you can use apt get from the terminal, or better still, Synaptic Package Manager from the GUI. Just search for the component you want and install or uninstall as you wish.

8.04 might be better or worse for you - the only way to really know is to install it. I would wait for the release to have been out for a while so that any probems get shaken out before you try to base a production system on this version. As for upgrading to 8.04, this is a bit hit and miss depending on how far beyond the 'normal' configuration your previous version has become. Some people have no problems upgrading, others find it breaks things they have installed (usually if they have added something outside of the 'supported' repositories). Your mileage may vary as they say.

---

### Post by rgotten on 2008-05-09
I have finish testing my software raid configuration and is working perfect. I did Radi 1 100 mb for boot, Raid 1 2 gb for swap, Raid 5 10 gb for the / (system), and Raid 5 (aprox: 980 Gb) for /home. (please let me know if this appears ok for you guys), then I have zero one of the hard drive (for testing) and it boot well in degrade mode, after i have rebuild the Raid without any problem. So now I am ready to continue with the server and this is what i need or questions i have:

I finally installed ubuntu server 8.04, from my understanding of what i needed after reading the threat i had to install the "LAMP" option and the "Samba" option. Which i had selected during my instalation of the server 8.04. NOW:

1) I need a easy way of configuring this ( i assume it was install simce i selecte it during the cd installation, can somebody give me some guidence on this.

2) If i would like to access this remotly from home or another computer, how can i do this (i have a router)??

3)How do i secure my server so nobody can access it from the outside

4) How do i do backups of the server??

Help will be apreciated

rgotten

---

### Post by rgotten on 2008-05-09
--------------------------------------------------------------------------------

I have finish testing my software raid configuration and is working perfect. I did Radi 1 100 mb for boot, Raid 1 2 gb for swap, Raid 5 10 gb for the / (system), and Raid 5 (aprox: 980 Gb) for /home. (please let me know if this appears ok for you guys), then I have zero one of the hard drive (for testing) and it boot well in degrade mode, after i have rebuild the Raid without any problem. So now I am ready to continue with the server and this is what i need or questions i have:

I finally installed ubuntu server 8.04, from my understanding of what i needed after reading the threat i had to install the "LAMP" option and the "Samba" option. Which i had selected during my instalation of the server 8.04. NOW:

1) I need a easy way of configuring this ( i assume it was install simce i selecte it during the cd installation, can somebody give me some guidence on this.

2) If i would like to access this remotly from home or another computer, how can i do this (i have a router)??

3)How do i secure my server so nobody can access it from the outside

4) How do i do backups of the server??

Help will be apreciated

rgotten

---

### Post by Gordy on 2008-05-09
SME Server is what I use and it works just great. It is stable as a rock...

CentOS based on Redhat Enterprise server.


You will like it I know..............

---

### Post by bodhi.zazen on 2008-05-09
> **rgotten said:**
> --------------------------------------------------------------------------------

I have finish testing my software raid configuration and is working perfect. I did Radi 1 100 mb for boot, Raid 1 2 gb for swap, Raid 5 10 gb for the / (system), and Raid 5 (aprox: 980 Gb) for /home. (please let me know if this appears ok for you guys), then I have zero one of the hard drive (for testing) and it boot well in degrade mode, after i have rebuild the Raid without any problem. So now I am ready to continue with the server and this is what i need or questions i have:

I finally installed ubuntu server 8.04, from my understanding of what i needed after reading the threat i had to install the "LAMP" option and the "Samba" option. Which i had selected during my instalation of the server 8.04. NOW:

1) I need a easy way of configuring this ( i assume it was install simce i selecte it during the cd installation, can somebody give me some guidence on this.

Configure what ? Samba ?

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

> 2) If i would like to access this remotly from home or another computer, how can i do this (i have a router)??

ssh is the way to go.

[uwiki]SSHHowto[/code]
[uwiki]AdvancedOpenSSH[/uwiki]

> 3)How do i secure my server so nobody can access it from the outside

I assume you mean other then your ssh connection ? 

Security is an ongoing process and involves configuring iptables and each server, for example see the advanced open ssh link I gave you.

> 4) How do i do backups of the server??

What part do you want to back up and do you want to bring your server off line to back up ?

I suggest you look at rsync, will back up data to another server.

See also : 

[http://ubuntuforums.org/showpost.php?&p=1628330&postcount=7](http://ubuntuforums.org/showpost.php?&p=1628330&postcount=7)

dd : [http://wiki.linuxquestions.org/wiki/Dd](http://wiki.linuxquestions.org/wiki/Dd)

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

[http://freshmeat.net/projects/g4l/](http://freshmeat.net/projects/g4l/)

---

### Post by rgotten on 2008-05-09
> **bodhi.zazen said:**
> Configure what ? Samba ?




Sorry about me being so newby and I am still learning. Well in this forum my conclusion was that i should install "LAMP" and "Samba", on the cd i8nstallation process I check mark the above two; Do i have to do anything else, or after installation the LAMP is installed and ready to use? 

If i do not have to do anything else with the "LAMP", it means i just have to configure "samba" ( i know that when the systems boots, one of the things that mention is "samba" on the booting process, so I will check your link

In reference to remote conection, I see that the version 8.04 has ssh or ebox, what is the difference and wchich is recomended

In reference to backup, how do i back data that will be save from my windows computers into the server ie: external hard drive conected to server

Thanks so much, and hope you understand one more time that this is completely new for me

rgotetn

---

### Post by Daveski on 2008-05-10
> **rgotten said:**
> Do i have to do anything else, or after installation the LAMP is installed and ready to use? 

That is Apache ready, but you do need to configure it if you want it to serve web pages. Again, Samba will need some config to set up a shared area, and to allow Windows machines (and users) to access it via a network.

> In reference to remote conection, I see that the version 8.04 has ssh or ebox, what is the difference and wchich is recomended

I think ebox is a web front-end to configure various services. I have not used this, but I have used Webmin (which I quite like) to configure the various components of my server:

[http://www.webmin.com/](http://www.webmin.com/)
[http://en.wikipedia.org/wiki/EBox](http://en.wikipedia.org/wiki/EBox)

ssh allows a (secure) remote connection to the command line - although you can run a graphics interface over it it you want. From this connection you can run commands as if you were sat at the machine. This can be very powerful.

> In reference to backup, how do i back data that will be save from my windows computers into the server ie: external hard drive conected to server


Yes, an external drive is a good idea - you can run a task to sync the data to this drive at a set time. Alternatively you can use a Windows machine to copy the data from the Samba share to a drive attached to the Windows machine. It is up to you what you backup and how.

---

### Post by rgotten on 2008-05-10
In your first part when you mention Apache and web pages is to access the files in a web format???

I sam assuming ssh webmin and ebox are for conecting and managing the server thru my office network from another computer, not having the monitor or keyborad attach to the server. Also

How do i connect from outside my office via the net, and also if i would like to make backups in a incremetal way from home, how can i do this. 
Basically my friend, were should i start now that the system is running..

Sorry, but you now i am newby and very hard trying to learn???

Thanks again

 rgotten

---

### Post by freebeer on 2008-05-11
Well, start with one thing at a time, then go from there.  I'm not clear on why you would need a LAMP stack, but let's leave that for now.

If this was my setup, I'd start with configuring Samba first.  Make sure that the Win boxes can see, read and write to the Linux box the way you want it to.  I would think that is your first priority.

Next would be your backup methods. Then remote access.

But that's me.  You might think otherwise.

---

### Post by Daveski on 2008-05-11
I agree with freebeer. Let's get your Samba system running first as this seems to be the most important part of this project.

I STRONGLY recommend getting some kind of admin tool like Webmin (or ebox?) to assist with the config of these services. If you were to use Webmin (for example) then you simply open 'Servers' and then 'Samba Windows File Sharing' and from this page create your share and allow access. An admin tool like this also means that you can easily do your admin tasks from any machine on the network which has a web browser (obviously you need a username and password to access the admin tool) - you could configure it so that you can do this remotely, but let's leave this for now.

Are you at all familiar with the Windows File and Printer Sharing system? Do you know (in the Windows world) how to set up a shared location and allow people to access this? In Linux / Samba the process is simiar.

When a Windows machine tries to access the shared location on the Linux server, do you want everyone to access using the same username/password or will you need different levels of access for different people / roles (i.e. the Administrator has read/write access, but ordinary users might only have read access). Perhaps the Windows machines will all access using 1 account, but when you do systems admin tasks (backups etc.) you might be accessing with another account.

This is important as the shared area must be secured so that a username and password are required to make a connection to it. Samba will require username/password pairs to grant access over the network.

---

### Post by rgotten on 2008-05-11
OK guys, i will follow your advise, i will start with SAMBA. How can i decide if i should go with webmin or ebox, (i see that ebox has some kind of RAID monitor feature and that will be nice), but evidently, i would like to use the easisest of use and with the requiere funtion.

In reference to if i am familiar with windows file and printer serving, i am a little bit, basis things, not a lot. Have done some file sharing in the past.

In reference to the read and write access, it depends. I need my staff to be able for example to scan and place on the server pdf files or jpg. I o  not want them to be able to delete them, when they can read only, can they save information into the server but not delete it, or how will this part be? (sorry if this was a dum question), so if what you were saying in the last part will be to have a restricted account for normal daily office staff work from any computer, and other account for admin work??

rgotten

---

### Post by rgotten on 2008-05-11
I will follow your and Daveski instructions, and steps, thanks

rgotten

---

### Post by linuxisfree on 2008-05-11
> **rgotten said:**
> I have not decide yet, how much ram, but i am thinking about 2 gb

Cool... You mentioned that your processor is Pentium 4, how fast is it, may i ask?
But, regardless, your specs would suit your needs quite well. Definitely go with Ubuntu

---

### Post by aluxgt on 2008-05-17
NTFS partition?
hi, thanks for all the information, i had read all the posts and i am traying to make the same file server.  

I have read this post: [http://howtoforge.com/ubuntu-home-fileserver](http://howtoforge.com/ubuntu-home-fileserver)
that is some kind of tutorial to get the same results, but the article point to the use of 2 HD, one for linux system and the 2nd. in NTFS formar to store the shared folders and files, that in order to read the HD with the NTFS partition in any windows based machine in case of any crash.

I have two question.  
1) what do you think about the mix: linux - NTFS that the article describes?

2) I have a 1TB WD green disk, may i have 2 partitions one wiht linux system an the other with NTFS partition and configure the samba to write the shared files and folders to that partition?

Please be kind :) i am very... very... very... newby too and i am trying to learn.
Thanks a lot for your help.
Best regards.

---

### Post by Daveski on 2008-05-18
> **aluxgt said:**
> 
I have read this post: [http://howtoforge.com/ubuntu-home-fileserver](http://howtoforge.com/ubuntu-home-fileserver)
that is some kind of tutorial to get the same results, but the article point to the use of 2 HD, one for linux system and the 2nd. in NTFS formar to store the shared folders and files, that in order to read the HD with the NTFS partition in any windows based machine in case of any crash.

Personally I don't see the need for an NTFS partition on the Linux machine unless it is a dual-boot with some version of Windows. Samba file sharing will work just fine (better?) on a Linux partition.

As for NTFS being able to be read on a Windows machine in the event of a crash, This is true but... Most of the decent disk recovery tools are live-boot Linux CD's anyway, and if you happen to have an Ubuntu disc to hand, then you can read / copy / transfer any data stored on a Linux (or NTFS) partition on any machine in which you can put the physical drive and boot from the Ubuntu CD.

---

