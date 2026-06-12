---
title: "Okay, Maybe I shouldn't have just gone ahead"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Athena's Owl on 2007-01-13
Hi.

I'm interested in learning linux, as I've just got all the hate for XP and there has to be a better way.

because I am pretty dependent on my desktop I have left it in the clutches of evil for now and am testing out xubuntu on an ancient compaq presario 1200. I know it'll be slow. I'll just use the lag time to take notes.

well first of all it didn't recognize my networking. I'm not too worried about that as it wasn't plugged into a network at the time, but I'll probably want to attend to that later.

once I finished the installation and it booted, I got these two messages: 

> SMBus controller not enabled! - upgrade BIOS or use force=1

via 686a 0000:00:07.4 base address not set - upgrade BIOS or use force_0xaddr

of course I compulsive wrote them down word for word. everything else checked out ok. 

I logged in as OEM, like it says, and it accepted my password...

and now it's waiting for me to do something. but what? WHAT? I'm positive it's something so basic, like typing win at the DOS prompt for 3.1, but I do not know what it is and I haven't the least idea how to google it. ](*,) 

I tried looking at the xubuntu site but I couldn't find a getting started tutorial or anything like that.  I will just take the answer from you, and gratefully, but I'd really, really love to have access to a manual, if someone could point me at it.

I'll keep trying google while I wait hopefully for a reply.

---

### Post by Iarwain ben-adar on 2007-01-13
Hi,
Welcome :wink:

How do you mean, it's waiting for you to do something?


Iarwain

---

### Post by Fluffy, the jolly sheep on 2007-01-13
> upgrade BIOS or use force=1

it's asking you to upgrade a piece of software (the [BIOS]("http://en.wikipedia.org/wiki/BIOS")) which is loaded on your motherboard. Probably the linux drivers of your motherboard only play nice with a newer version of the BIOS.

now the tricky part is to find these drivers. To find them you need to now the vendor and the type of your motherboard and search for a new bios version on the vendor's website. The type of your motherboard may be found in some manual that came with the computer, maybe somewhere on a bootup screen or else you can certainly find it somewhere on the motherboard itself. 

The force=1 thing is an option you can pass to linux kernel in grub to force some things to work, but I wouldn't recommend it as bad things might happen.

Good luck!

---

### Post by online14230 on 2007-01-13
Not sure how to reply, but heres a thought: Im thinking that youre at a prompt, as in win 3.11. Try "startx" and see what happens...

If you have the GUI started already, at the top of the screen are a few menu buttons: click on each and mess around with the very many programs available there....

please clarify: Do you have the GUI running already??? Im really curious...

---

### Post by jvc26 on 2007-01-13
When you logged in did you get to the root prompt? i.e. did it load a black screen like a dos install or did it load up the proper GUI? It looks like it may be demanding you to update the BIOS (as its so ancient) - how ancient is ancient? Anyway, hopefully we can get this sorted out for you :)
Il

---

### Post by shash_walia on 2007-01-13
you have to upgrade your bios most probably. you would have 2 do the following steps inorder 2 update your bios:

1. identify your motherboad make (intel, gigabyte, msi, foxxconn, whatever). since yours is a compaq then try and punch in the service tag which is given on your pc. if that doesnt work then your ll have to purchase a pair of screwdrivers and open up the system cabinet yourself and try 2 identify your motherboard. if that doesnt work then check the specs or box or sth..

if you still cant find it then msg me back

2. once you've got the brand name of your motherboard then you'll need to visit its website. and search the support and downloads for that paritcular motherboard model. from their you will get a list of options for important things 2 download. one of them would be the bios.

3. view the readme file as to see the different methods as to which you can download the file from. 

then update your bios accordingly

best of luck

---

### Post by chaplanger on 2007-01-13
You stated:
"tried looking at the xubuntu site but I couldn't find a getting started tutorial or anything like that. I will just take the answer from you, and gratefully, but I'd really, really love to have access to a manual, if someone could point me at it."
---------------------------------

Check out the documentation at this site to see if it will help you -- this is where Ubuntu keeps all of its manuals [https://help.ubuntu.com/](https://help.ubuntu.com/)

Notice the tabs at the top of the page for the various releases.  Then you can either download a PDF manual or simply view the HTML version in your browser.  Also the extracts from the Official Ubuntu Book and the Installation Guide can be quite helpful.  Hope this helps you.

---

### Post by Athena's Owl on 2007-01-13
> **Fluffy, the jolly sheep said:**
> it's asking you to upgrade a piece of software (the [BIOS]("http://en.wikipedia.org/wiki/BIOS")) which is loaded on your motherboard. Probably the linux drivers of your motherboard only play nice with a newer version of the BIOS.

agh, that's something I didn't think of.

> now the tricky part is to find these drivers. To find them you need to now the vendor and the type of your motherboard and search for a new bios version on the vendor's website. The type of your motherboard may be found in some manual that came with the computer, maybe somewhere on a bootup screen or else you can certainly find it somewhere on the motherboard itself. 

I still don't know precisely which motherboard I have in this thing. but I know that it is a Compaq Presario 1200 series, running an AMD K6-2 (isn't it CUTE?) processor.

I went around the HP site and they have a lovely way to upgrade your bios - so long as your computer has a working Windows installation on it. 

So I think what I will have to do is re-install Windows 2000 long enough to upgrade the BIOS, and then strip it off. I am in no hurry, it's not urgent, etc.

because I can't see any other way to upgrade the BIOS. if I had a way to just search through an actual list instead of this hardware detection thing... I'd be all right with that. I'd just put it on a floppy and do it that way.

> The force=1 thing is an option you can pass to linux kernel in grub to force some things to work, but I wouldn't recommend it as bad things might happen.

What sort of bad things are we talking, here?

Thanks for your answer!

---

### Post by Athena's Owl on 2007-01-13
> **online14230 said:**
> Not sure how to reply, but heres a thought: Im thinking that youre at a prompt, as in win 3.11. Try "startx" and see what happens...

yes, that's it, I'm at a prompt! it says root@Golem:~#

I tried startx and I got "bash: startx: command not found"

> If you have the GUI started already, at the top of the screen are a few menu buttons: click on each and mess around with the very many programs available there....

please clarify: Do you have the GUI running already??? Im really curious...

there is no gui for me. I'm in command-line land.

---

### Post by annda on 2007-01-13
many people report the message urging them to upgrade BIOS and then it doesn't change anything. so maybe you don't really need it either... can you still not launch X by typing startx?

oops, i was too slow.

---

### Post by ardchoille42 on 2007-01-13
> **Athena's Owl said:**
> Hi.

I'm interested in learning linux, as I've just got all the hate for XP and there has to be a better way.

because I am pretty dependent on my desktop I have left it in the clutches of evil for now and am testing out xubuntu on an ancient compaq presario 1200. I know it'll be slow. I'll just use the lag time to take notes.

If it's an oplder computer, you may be interested to know that you can install Ubuntu and then install a light desktop, like XFCE, or you can install just a window manager. There are a lot of light and fast window managers: Window Maker, Fluxbox, Openbox, Blackbox, IceWM, etc.

There is a nice listing of window managers here: [http://xwinman.org/](http://xwinman.org/)

I used Window Maker for years and it was nice and fast on my old HP computer. I also tried Fluxbox, which is nice and has a panel. I tried Blackbox, but it was too light for my tastes. I was even able to get openbox running as my default window manager in gnome - I wanted to be able to have the regular gnome menus in the desktop right-click menu and OB did that for me.

The wonderful thing about Linux is that you aren't limited to just one desktop/WM configuration, you can pick and choose what you like :)

---

### Post by Athena's Owl on 2007-01-13
okay, I tried starting it up again to see what happened, and I got this:

> Traceback (most recent call last):
  File "/usr/sbin/oem-config-dm", line 58, in ?
    sys.exit(dm.run(*sys.argv[3:]))
  File "/usr/sbin/oem-config-dm", line 44, in run
    os.kill(server.pid, signal.SIgTERM)
OSError: [Errno 3] No such process
Traceback (most recent call last):
  File "/usr/sbin/oem-config-dm", line 58, in ?
    sys.exit(dm.run(*sys.argv[3:]))
  File "/usr/sbin/oem-config-dm", line 44, in run
    os.kill(server.pid, signal.SIgTERM)
OSError: [Errno 3] No such process
ERROR: The OEM installer failed. Your system may not be useable yet. Please report this as a bug to your vendor.

To create a user so that you can use your new system normally, type:

    adduser USERNAME

... replacing USERNAME with the username you would like to use (your first name in lower case is normally a reasonable choice), and follow the prompts. If this succeeds, type 'exit' to reboot the system

bash: no job control in this shell
root@Golem:/#

so I tried this above instruction, rebooted, and it allowed me to login and now my prompt says 

> athena@Golem:~$

and i typed in startx, and got

> -bash: startx: command not found.


filled with sadness! is that really a bug up there?

will attempting to re-install the alternate xubuntu help? 

do I reinstall windows and get the BIOS upgrade and try again?

---

### Post by Tomosaur on 2007-01-13
Can you tell us the link you downloaded ubuntu form? It sounds like you downloaded the server edition, which doesn't come with a GUI :S

---

### Post by Athena's Owl on 2007-01-13
> **Tomosaur said:**
> Can you tell us the link you downloaded ubuntu form? It sounds like you downloaded the server edition, which doesn't come with a GUI :S

sure! I used the xubuntu 6.06.1 alternate, because it only required 64 mb of ram to install. I think that's all this wee little laptop has. I got it from this page: [http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/](http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/)

and the name of the file I downloaded is xubuntu-6.06.1-alternate-i386.iso

I also downloaded the desktop version, figuring I would use that on my desktop computer as it has 128meg of ram.

could it be that I did something wrong in the original installation?

---

### Post by Threbus5 on 2007-01-13
Hi Athena,

I agree with the discussion. You need not limit yourself to the server version or Xubuntu - just because it is supposed to be resource light. 

Try the normal Ubuntu (Edgy or Dapper). They seemed more friendly (to me) and run well on older machines. As long as the computer has at least 192 MB RAM for a CD install it should be ok.

Take care.


Hmmm, I see that you are indeed resource light and needed the alternate install. Welllll, let's think about this for a minute.

(1) I paid $17.00 and bought enough RAM to bring my 64 Mb desktop up to 192 so I could do a CD install.
(2) The alternate ought to work. You seem to have the proper file. Perhaps another download with a verification on the burn would yield better install results? 

Note:
If you do another install it's probably a good idea to choose to completely format the HD and install.

Good luck.

---

### Post by livinginx on 2007-01-13
> SMBus controller not enabled! - upgrade BIOS or use force=1

via 686a 0000:00:07.4 base address not set - upgrade BIOS or use force_0xaddr

When you put the CD in and boot it, on the menu with Check CD for Defects and Memory Test, there are some options across the bottom of the screen.

Try F6 (boot options) and then type force=1
Then press enter, not 100% sure if it will work, but it won't hurt to try.  Or try force_0xaddr

---

### Post by Athena's Owl on 2007-01-13
I have re-installed from the disk, and I now have gui!

i have no internet, though, which makes me quite sad. when I installed it, I didn't have anything hooked up to the internet (there are only so many ports into the router, alas.) did that matter? should I do it again, except connected?

---

### Post by %hMa@?b&lt;C on 2007-01-13
what is your internet service?
can you ping 64.233.187.99?

---

### Post by Athena's Owl on 2007-01-13
I can't ping that on the xubuntu system. I don't even have an IP...

and when I was installing it made a fuss about not being able to detect DCHP, if I recall that acronym correctly. That's why I wondered if I should do it over, but with the ethernet cable attached.

---

### Post by Albi on 2007-01-13
No, just do this:

sudo apt-get install dhcp3-server

---

### Post by MkfIbK7a on 2007-01-13
you may want to try
xinit 
this does the same as
startx
just a different command....

---

### Post by Athena's Owl on 2007-01-14
I tried sudo apt-get install dhcp3-server.

at the very end, I got:

invoke-rc.d: initscript dhcp3-server, action "start" failed

it noted during the installation that the packages were dated fo r 2006-05-05 231607048 seconds in the future. obviously my system clock is all wrong. could that have caused the problem?

if it is, how do I change my system clock time and date?

---

### Post by Dokatz on 2007-01-14
> **Athena's Owl said:**
> I tried sudo apt-get install dhcp3-server.

at the very end, I got:

invoke-rc.d: initscript dhcp3-server, action "start" failed

it noted during the installation that the packages were dated fo r 2006-05-05 231607048 seconds in the future. obviously my system clock is all wrong. could that have caused the problem?

if it is, how do I change my system clock time and date?

I've had tons of problems from incorrect date settings, You better take care of that for sure...Not 100% if it's causing the specific problem but being the master of causing problems; I'd say the less to go wrong the better.

-Word

---

### Post by Athena's Owl on 2007-01-14
Success!

I have a working install of xubuntu with gui and internet!

now I can get down to the fun of figuring out how it all works.

thanks, everyone!

---

### Post by Sef on 2007-01-14
> Success!

I have a working install of xubuntu with gui and internet!

Great to hear that.

> now I can get down to the fun of figuring out how it all works.

Please ask any question that you have.   We love questions here no matter how simple.

---

### Post by Mguel on 2007-03-13
Hi!

I'm just trying to install xubuntu on a Compaq Presario 1200-XL111 (also with AMD K6 and 64 ram).

I can't start the xubuntu live cd... it just get stuck on the process. I also get the two message errors of upgrading the BIOS, but it stuck in the same place even using the force=1 option. 

I haven't been able to find a BIOS to download at hp.com (or other) site.

I read that you used in some point the alternate cd. So I wanted to ask you if that was the way you finally manage to make it work? Using the alternate to install... 

And afterwards, how did you fixed the BIOS error messages as to be able to get to the GUI (have X running)? I didn't get it.

Thanks,
Mguel

> **Athena's Owl said:**
> Success!

I have a working install of xubuntu with gui and internet!

now I can get down to the fun of figuring out how it all works.

thanks, everyone!

---

### Post by mikeczap on 2007-12-02
> **Mguel said:**
> Hi!

I'm just trying to install xubuntu on a Compaq Presario 1200-XL111 (also with AMD K6 and 64 ram).

I can't start the xubuntu live cd... it just get stuck on the process. I also get the two message errors of upgrading the BIOS, but it stuck in the same place even using the force=1 option. 

I haven't been able to find a BIOS to download at hp.com (or other) site.

I read that you used in some point the alternate cd. So I wanted to ask you if that was the way you finally manage to make it work? Using the alternate to install... 

And afterwards, how did you fixed the BIOS error messages as to be able to get to the GUI (have X running)? I didn't get it.


Even though this is 8 months old, I stumbled across it because I, too, am playing with
Ubuntu on a Presario 1200 XL111.  This one has 128meg of RAM (or maybe more, since
I have a certain amount dedicated to the video) and a 6gig HD, along with a DVD/CD player.

For anyone trying to find BIOS upgrades at HP:  forget it.  Most of the Presarios are on
their ´no longer supported´ list, and I haven´t been able to find any other references
anywhere to another BIOS version.

I got it loaded finally with the Feisty Fawn Alternate Install disk back in April; the Normal
Ubuntu (not Xubuntu; I was brand new to Linux in general and Ubuntu in particular)
install CD would boot to a point but hang during the graphical portion of the install, but
the Alternate install took it.  One thing I have noticed, though, is that the CD-ROM seems
to be problematical:  once in a while, even if I have a bootable CD in it, and set the BIOS
to boot from CD, the computer ignores it and boots from the hard drive anyway.  And,
more often than not Ubuntu won´t read or auto-mount a data CD, but it always mounts
a DVD no problem.   I´m not sure if that´s a bug in 7.04 or a quirk of this hardware.

I do  recall that I did wipe the hard drive completely (with an old Win98 bootable floppy) of
the previous OS ( Win98 ) before doing the install, just as a matter of course.  Given the
relatively small hard drive size (6gig small?  Maron, how far we´ve come!) and older
CPU, I don´t think it will work as a dual-boot system effectively.

That said, at first the normal Ubuntu installation (with the GNOME desktop) would work.
Just.  Overall it was very slow.  Basic web browsing was ok, but OpenOffice would take
minutes to open, but once it was open seemed to work reasonably well, but I didn´t do too
much with it before I discovered that you could switch out your desktop manager, and based
on research on the web, I went with xfce.

What a difference!  It want from slow to slow-but-usable, and I have to say that as an
added bonus I really like Abisoft as a word processor over OpenOffice.  It may not have
quite as many features, but its pretty good.

Of course, all this Xwin hacking has reminded me that, back in my Unix system support
days, I loathed Xwindows because it seemed needlessly complex, but some of the
plumbing knowledge is coming back to me as I tinker on this.  I´m actually proud
that I figured out how to add the Gnome Network Manager applet to the menu bar,
which should make switching between wifi networks much easier (especially since
it allows you to properly configure WEP and WPA keys without tedious command lines),
but I guess years of MS Windows work has made me appreciate a graphical environment
(setting up Samba, for example, was an excercise in frustration until I got to the easy
part with the graphical printer set up).

This particular unit was one that was my mother´s, and I´d inherited it along with a Linksys
PCMCIA ethernet card and a Netgear WG511v2 PCMCIA WiFi card.  I specifically didn´t have
either inserted during installation, just to see how well it handled them.  To my pleasant
amazement, the Linksys card worked immediately, and it took quite a bit of massaging
to get the Netgear card working because of the lack of Linux-specific drivers, but I got
it done (kind of; I still learning, and as I said, figuring out how to get GNOME´s nm-applet
to run in xfce was a big help).

About the only complaint I have is the weird automounting behavior:  as I mentioned
above, data CD´s often won´t mount for love nor money.  But, though the machine will
automount USB thumb drives, I have noticed that if you try to copy large files to it, it
will often get kicked offline and be unmounted, and the only recourse is to remove &
reinsert it.  This seems to happen more often when using a GUI file tool, but is has also
happened from the plain command line, so it could something as simple as a too-long
file name (the drives in question are almost always VFAT´s, since I do a lot of sharing
to my Windows PC´s).  This also reminds me of one other age-related drawback to the
machine:  it only has 1 USB port, so a hub would be a necessity if you want to use a
large number of USB devices.

I haven´t been able to upgrade it to 7.10 yet, but that seems to be a general problem,
not one specific to this machine.  But, I´m very impressed by how well it works on a 7+
year-old computer, (once I´d identified the proper desktop manager), and given that I
have a bunch of old Pentium II and older PC´s in my basement that are completely
usable but underpowered for more modern commercial OS´es, I think I´ll be sticking
Ubuntu on them once I get around to setting up the rest of my home network.

A book report from:

MikeC

---

