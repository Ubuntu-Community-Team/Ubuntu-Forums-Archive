---
title: "Sooo many questions, so little answers!  Here I am!"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by donsjuand on 2006-08-27
I have windows Xp and am considering installing Linux Ubuntu on a 2nd system.  Are drivers for hard disks easily available, as well as open source firewalls, spyware removal/malware removal, how are updates done?  What about msn messenger compatible apps?  DBasically I want to know how easy it is to have similar apps to windows apps...where's a good tutorial on installing and configuring hardware and software??  Please help!  I am a TOTAL nOOb to the linux world of open source and from far it's attractive... Thank you!

---

### Post by Jerome36 on 2006-08-27
You can search for updates manually, and they'll download and install on their own.  You can also be told that new updates are available, click the icon that appears, see what's available, and then pick what you want to update.  It's somewhat similar to automatic updates in Windows.

One of the programs that comes with Ubuntu, right "out of the box," is a program called GAIM.  It's a messenger, which handles not only MSN, but AOL, ICQ and Yahoo! IM.  The nice thing about that is you only have one contact window, and each messenger is split up inside of it.  Of course there are GAIM alternatives, but that's one that you have right off the bat.

It's pretty hard to not find a comparible program, in Linux, that is available on Windows.  Myth TV is a great program, similar to Windows Media Center.  GIMP is a decent paint program, similar to Paint Shop Pro or Photoshop (though in my personal opinion Photoshop is king).  Oppen Office (another set of software included with the initial Ubuntu install) is like Microsoft Office, and will even open Microsoft Office files!

As far as firewalls, spyware, and so on, I know there's anti-virus programs available.  Avast is one of them.  I know because I use it in Windows, but I don't use it in Linux.  The nice thing about Linux is it's a bit harder to have your system get infected with spyware and so on, simply because of how it operates.

Oh, installing software is really easy.  There's various ways to do it.  You can go to "Applications" and select "Add/Remove" to bring up an application which lets you select new programs.  They will download and install automatically.  You can also do it via the console, if you know the name of the software or package you want.  It'll download and install automatically.  Or you can download the files yourself, and manually compile and install them.

---

### Post by aysiu on 2006-08-27
> **donsjuand said:**
> 
Are drivers for hard disks easily available, Drivers for hardware are built into the kernel. Most of your stuff should be auto-detected. If they're not, they can be a pain to set up, but people on these forums will try to help you with that. A live CD is a great place to start, as you can preview the hardware detection without actually installing Ubuntu. > as well as open source firewalls, spyware removal/malware removal, Ubuntu defaults to not listening on any ports, and there's no rampant spyware/malware in Ubuntu, especially if you stick to the repositories. > how are updates done? You click the update button and enter your password. > What about msn messenger compatible apps? aMSN and GAIM > DBasically I want to know how easy it is to have similar apps to windows apps... Name the apps. > where's a good tutorial on installing and configuring hardware and software?? You shouldn't have to configure hardware unless there's a problem. For software, try [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) > Please help!  I am a TOTAL nOOb to the linux world of open source and from far it's attractive... Thank you! My best advice is to try the live CD and take things slowly. Don't install Ubuntu unless you know what you're doing. Always make backups of your important files.

To see what the installation process looks like, check out this page:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by bodhi.zazen on 2006-08-27
> **donsjuand said:**
> I have windows Xp and am considering installing Linux Ubuntu on a 2nd system.  Are drivers for hard disks easily available, as well as open source firewalls, spyware removal/malware removal, how are updates done?  What about msn messenger compatible apps?  DBasically I want to know how easy it is to have similar apps to windows apps...where's a good tutorial on installing and configuring hardware and software??  Please help!  I am a TOTAL nOOb to the linux world of open source and from far it's attractive... Thank you!
1. Drivers should be no problem.

2. Firewall is iptables. Installs and is secure at default. Several options for a GUI: guarddog, firestarter.

3. Linux has very limited, if any viruii/worms/spyware/maleware. There are antiviral programs, but these are mostly to protect your friends and family using Windows and not the Linux OS. If you keep your software up to date you will have adequate protection.

4. Instant messenger = GAIM. ? compatibility with msn, I use Yahoo.

5. Apps are similar. Start with open source apps available for Linux and windows on your windows box: Firefox, Thunderbird, and Open Office to start with. GAIM is also available for windows, runs better in Linux.

6. A new OS is "hostile" at first. Linux has a steep learning curve.

---

### Post by Jerome36 on 2006-08-27
> **aysiu said:**
> 
My best advice is to try the live CD and take things slowly. Don't install Ubuntu unless you know what you're doing. Always make backups of your important files.

Excellent advice.  I should have mentioned that as well.  If you haven't already done so get the Live CD and try Ubuntu, to see how you like it.  It'll run off your CD-Rom drive, and won't install anything onto your hard drive.  Eventually, should you decide to install Ubuntu, you can do it from the Live CD.

Also, like aysiu suggested, name some Windows Apps you're wondering about for Linux, and somebody can probably give you an answer.

---

### Post by autrui on 2006-08-27
> **donsjuand said:**
> I have windows Xp and am considering installing Linux Ubuntu on a 2nd system.  Are drivers for hard disks easily available, as well as open source firewalls, spyware removal/malware removal, how are updates done?  What about msn messenger compatible apps?  DBasically I want to know how easy it is to have similar apps to windows apps...where's a good tutorial on installing and configuring hardware and software??  Please help!  I am a TOTAL nOOb to the linux world of open source and from far it's attractive... Thank you!

i have some answers, but not all.  

drivers are available for pretty much everything, but, as can be expected, weird setups can be tetchy.  but it can all be dealt with.  

i dont know much about firewalls; i've been content with my router's firewall thus far.  spyware/malware/viruses are--and please someone correct me if i'm wrong--not really an issue in linux--not only is it unfashionable, but it's also a great deal safer for real reasons.  (ask about permissions and things like that.)  

updates can be done in a variety of ways; there's an update program that does a great job, but you can also do it with the synaptic package manager very easily.  and, i was surprised to learn, doing it from the command line (the "terminal") is really easy as well.  and when you do it that way, it really makes you feel like you know things! ;)

there are a couple of common chat programs: gaim and xchat.  they both reproduce all the major chats--aim, msn, irc, yahoo, etc, in one program.  i've been using gaim for a while now--i used it in windows long before i switched to ubuntu--it's great.  never used xchat, but i'm sure it's fine.  there's probably more than just those two, as well.

yes, every program you have in windows has something similar in linux.  except that they're usually more stable, and usually free!  

i installed ubuntu only a week ago, and i've been really happy.  im sure some gurus can give you a lot more insight, but, noob to noob, go for it.  you're going to back up everything you have to back up anyway, so why not just go for it!  you can always go back to windows if you hate it.

the downsides: you may have to learn things in order to get some things to work.  some things may take some tinkering.  a good portion of my first session was spent trying to learn how to mount a second hard drive i have that was formatted in NTFS, but now i can do it in a second.  and you will definitely have to learn things in order to optimize your system.  many things can be done with a familiar graphical user interface, but folks around these forums prefer to give instructions in command-line format, so you'll get into that quickly.  it's not hard, and folks are really helpful, and often happy to hold your hand as you go.

good luck, and i hope we see more of you!

autrui

::edit:: lol!  that's a lot of responses!

---

### Post by bodhi.zazen on 2006-08-27
I'll take one of whatever the cat is drinking.

---

### Post by jbag on 2006-08-27
> **donsjuand said:**
> I have windows Xp and am considering installing Linux Ubuntu on a 2nd system.  Are drivers for hard disks easily available, as well as open source firewalls, spyware removal/malware removal, how are updates done?  What about msn messenger compatible apps?  DBasically I want to know how easy it is to have similar apps to windows apps...where's a good tutorial on installing and configuring hardware and software??  Please help!  I am a TOTAL nOOb to the linux world of open source and from far it's attractive... Thank you!

I am also a Noob. Having only installed Ubuntu a couple of days ago. I ran Ubuntu for about 6 weeks off the live CD to see if I liked it or not. I did & ended up installing.

Ubuntu picked up every driver but 1 on my system. Actually when I go into the device manager it shows me that my scanner is there, it just doesn't want to work. Apps will not pick it up. I will try to figure it out myself 1st before I ask around.

From what I have seen over the last few weeks is that pretty much any apps that I used in Windows is available for Linux. They all work as well or close to the Windows apps. Open Office is fully compatible with M$ Office & just as easy to use.

I had a couple of issues when I 1st installed but both were quickly resolved through the community forums. These people are extremely courteous & very willing to share their knowledge with you. Their patience is overwhelming & do not treat you like an alien.

Internet access was automatic on my system. It picked up my NIC & Router & it picked up the ISP configuration. I can't say the same for Windows. I have already noticed that Ubuntu connects through Firefox quicker than it did with XP. I don't know if it will automatically pick up your ISP config.but it did mine.

Indeed try from the live CD for awhile & don't be afraid to install Ubuntu as help is right there when you need it. I am really glad I did.

Have fun

jbag

---

### Post by donsjuand on 2006-09-13
WOW You guys ROCK, thanks for the great answers, very helpful!!
Now if only these posts could convert into a .txt file, LOL.

Thnak you so much!

---

### Post by blx_286 on 2006-09-13
> **donsjuand said:**
> Now if only these posts could convert into a .txt file, LOL.

This is what I do and you may find it helpful. At the top of the thread choose "Thread Tools" and then choose "Show Printable Version". You can then save this page as html for future reference.

---

