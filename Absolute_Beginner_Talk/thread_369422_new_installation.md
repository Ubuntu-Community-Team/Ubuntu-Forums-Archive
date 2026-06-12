---
title: "new installation"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by amod on 2007-02-24
guys  i hav just installed the 6.10v of ubuntu so i am a noob....i am preety darn excited....now i hav 2 HDDs..on one is windows while on the other theres ubuntu...and i installed them in such a way dat i can get into da particular os only if i boot from a particular Hdd...so how do i go about adding windows to the linux boot loader..i supp dat grub??????
nowi wanna mount the drives of the other Hdd onto ubuntu...would like to know how i go abt doing that??????
i use the cyber roam client to access the net...i hav downloaded something called linc daemon...4m da advice i got the last time i posted on this forum...so i would like to know how do i go abt configuring my net?????
last but not da least....Do i need a antivirus for linux????if yes is AVAST! gud...coz i use it on xp and i am pretty satisfied with it....

Guys plz help me out...so that by tomorow i don't hav to see windows ne more on my desktop..coz as soon as i get da hang of linux...i'll gladly giv da boot to windows....

---

### Post by nereid on 2007-02-24
Please, could you speak in plain english next time? There are also users on this board whose mother tongue ain't english. Thanks.

Ubuntu should have added Windows automatically to GRUB. Please be so kind and post a little bit more information about your harddisk settings (where do you have installed Windows and where Ubuntu, maybe post the content of the /etc/fstab file or something like that).

What is the cyber roam client? No, you don't need an antivirus application for Linux. There aren't many virii for Linux around and most of the time the problem happens to be between keyboard and chair.

---

### Post by srinu85 on 2007-02-24
i have two hard disks in one i have widows xp now i waned to install ubuntu in another hard disk i have tried also but its getting init has disabled for 5 min n it is continuing the same message can anyone tell what is the problem and please help me out in installing ubunutu

---

### Post by amod on 2007-02-25
1. i already had windows on one hard drive....i got another drive yesterday ...so i disconnected my hard drive which had windows  and connected te new one and installed ubuntu in it so there wa no chance that Grub woud have added windows....
so i want to add windows to the Grub loader...how do i do that????

2. now i want to mount the old hard drive which had windows in it , so that i can view the files on ubuntu....

3. i downloaded alien after going through some of the threars here...i tried installing it and the installer gives me the error that 'the package is not satisfatory' something like that...

4.' Cyber roam client 24 online' is a dialer i use to access the internet. As i hav writen above i downloaded linc-daemon again after going through your forums but i cannot install it because its in .rpm format. and also how to configure it i would like to know????
i have tried to post in plain english.Plz help me out.

---

### Post by amod on 2007-02-25
guys i am an aboslute noobie. I have already installed ubuntu. i have a geforce fx 5200 128mb gfx card but while running the diagnostics of cedega it shows me that my system doen't have a 3d accelerator sumting.Will i be needing to download the drivers for my graphics card???

---

### Post by Maestro23 on 2007-02-25
> **amod said:**
> guys i am an aboslute noobie. I have already installed ubuntu. i have a geforce fx 5200 128mb gfx card but while running the diagnostics of cedega it shows me that my system doen't have a 3d accelerator sumting.Will i be needing to download the drivers for my graphics card???

Open a terminal and type:

 > glxinfo | grep direct

If it comes back: "Direct Rendering: Yes" then you are good to go for 3D.

---

### Post by amod on 2007-02-25
how do i mount the drives of my other Hard drive????

---

### Post by overdrank on 2007-02-25
> **amod said:**
> how do i mount the drives of my other Hard drive????

This thread might help. [http://www.ubuntuforums.org/showthread.php?t=369435&highlight=how+to+install+grub](http://www.ubuntuforums.org/showthread.php?t=369435&highlight=how+to+install+grub)

---

### Post by nereid on 2007-02-25
> **amod said:**
> 
3. i downloaded alien after going through some of the threars here...i tried installing it and the installer gives me the error that 'the package is not satisfatory' something like that...


Which means that the rpm is maybe damaged.

> **amod said:**
> 
4.' Cyber roam client 24 online' is a dialer i use to access the internet. As i hav writen above i downloaded linc-daemon again after going through your forums but i cannot install it because its in .rpm format. and also how to configure it i would like to know????
i have tried to post in plain english.Plz help me out.

How do you connect to the internet? Via DSL or through any other kind? Do you sit behind a router?

---

### Post by amod on 2007-02-25
no DSL bro.Theres a server in my locality which is the link between my computer and the ISP. Thats all the Information i can provide because quite frankly i myself don't know.

---

### Post by amod on 2007-02-25
guys i wanted to ask you that i saved a few webpages on my hard drive which ofcourse were in html file format.i did this from windows. But when i boot into linux, whenever i open those web pages they don't open as webpages even in the firefox browser. All i see is the programming language like the one we get when we open a web page in a note pad.  i apologize for my English.

---

### Post by amod on 2007-02-25
thanxs a million!!!!

---

### Post by nereid on 2007-02-25
So you're sitting behind a modem which goes into same plug like the telefone? This means you need a dial up application, if my memory serves my right, *vwdial* should do the job. Something like this should be installed by default with Ubuntu.

**EDIT:**
Concerning your downloaded webpages, just open Firefox and then point the location to file:///home/yourname/filename.html. This should display the page in the right way (make sure the the suffix is htm or html).

---

### Post by amod on 2007-02-25
nopes...there is no telephone ofr modem involved....i connect to the server via my onboard lan card.i have a fixed ip address...i just need a dialer...if poosible can i send you the software so that you can have a look and tell me what is to be done????

---

### Post by nereid on 2007-02-25
Sorry for my lack of understanding but you've got a LAN card in your PC which is connected to a splitter which is then connected to what? Where does the LAN cable goes into? You're sure, that you've got no DHCP server running which will automatically asign your PC an IP address (which could be static or dynamic)?

---

### Post by amod on 2007-02-25
the lan card goes into hub which is connected to a server which is connected to the ISP.
one more thing... i would like to know the tested  link from where i can download alien to convert .rpm into .deb...i downloaded it from the link posted that is [http://www.howtoforge.com/converting...deb_with_alien](http://www.howtoforge.com/converting...deb_with_alien)
 but when i try to install it, it gives me all the information about the software nut ells me that the package conent is not satisfactory. Plz help me out...

---

### Post by amod on 2007-02-25
is there any way i can send you my internet dialer so that you will be better equiped to resolve my problem because i have read so much good about linux and when i am so handicapped, i really get frustrated...

---

### Post by nereid on 2007-02-25
So the server connects to the internet. How does it do it? Is it your gateway? You need a ppp program to dial into the web which should already be installed on your default Ubuntu installation. Sending me your internet dialer wouldn't help me at all. I'm still trying to understand your network layout (PC->hub->server->internet, as far as I've understood you).

**EDIT:**
I've just searched the web a little bit and I think this is what you want: [GNOME PPP or PPPoE](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Dialup_PPP_Client_.28GNOME_PPP.29). Depending on your connection to the internet. If you use an old modem with the telephone line or ISDN line then use PPP. If you have broadband internet access (various flavours of DSL) than you need to use PPPoE.

---

### Post by amod on 2007-02-25
i configured my ethernet card. ran the pppoeconf application and filled in the usrename and password as i was asked for it...then in the terminal window i ran the command or rather my brother 's_spiff' ran it...but i still canot connect to the net....and you got the network layout right...My gateway and Dns Server is the same...if that info can help

---

### Post by amod on 2007-02-25
Cyberoam Client for Linux does not come in a executable format like in Windows. But as a zipped file (called a tar ball).

You need to download the client tarball. Put it in a folder.

The Client is available temporarily from this address

[http://www.mhowlinux.org/pub/CyberoamLinuxClient.tar.gz](http://www.mhowlinux.org/pub/CyberoamLinuxClient.tar.gz)

And goto the console or shell (command prompt). Change directory to that folder and unzip the file by giving command

$ tar -zxvf CyberoamLinuxClient.tar.gz

After you unzip it enter the new directory created for Cyberoam Client by the unzipper(tar) and run the Cyberoam Client

$ ./crclient -s


enter the necessary parameters for you isp
and

to login

enter

$ ./crclient -u <username>


Remember you need to be super user to do all this in ubuntu

to become super user
enter

$ su
Password:<enter the root password>

The Cyberoam Client is also attached to this post



Just found a more detailed escription

[http://mm.ilug-bom.org.in/pipermail/linuxers/Week-of-Mon-20020408/004615.html](http://mm.ilug-bom.org.in/pipermail/linuxers/Week-of-Mon-20020408/004615.html)



i gogled and got this info....thats all  can do....by the way am also using windows and hence can be online...

---

### Post by nereid on 2007-02-26
If you've got the software already, what is your problem? Doesn't it run or what is your problem?

I think you don't understand what I mean with your network layout. You've got a PC running Ubuntu. Your network cable goes from this PC into the hub. Another PC, your server, is also connected to the hub. So how do you connect to the rest of the world? Via WLAN or do you plug a cable from the hub into the wall or does you server have two LAN ports? My problem still is, that you can't tell me how you are connected to the rest of the world (with cable beeing V.90 56k modem, a flavor of DSL, T1 or T3).

I've again searched the web and found [linc](http://linc.sourceforge.net). Another Cyberroam comform client for Linux.

---

### Post by amod on 2007-02-26
a'rit ...see i got a pc at home which has ubuntu.Now my Pc is connected to a hub i don't know where,which is connected to a server i dunno where that is too but i know the person who owns the server because i pay him every month for the internet access.That person is the middle man so to speak who provides the internet access of the ISp in my locality.When i asked him for a dialer for linux he asks me "Linux?????Whats that?????"His server is connected to the Isp.Thats how i connect to the internet.There are other users who connect the same way....i can see their computers in "My Network Places' but none of them are on linux.So the server provides the lan connection to which my computer is connected. Thats all i know.

Ican't cofugure nmirc so that i can ask people in india using the same ISP for internet access on linux...Could u help me out there???i made a server called freenode then what do i do????

---

### Post by nereid on 2007-02-27
Setting IRC up is very easy. You've got to know the server where you want to connect to and enter the things in the applications, really self explaining. Join your prefered channel and up and away. Haven't you searched the web for *cyberroam client linux*?

---

### Post by amod on 2007-02-27
i did search for it...but hey don't provide one....then i searched for it on this forum so there was a thread on this and from there i got the link to this software....anywayz plz tell me a link from where i can download a .rpm convertor to .deb (like alien but i can't install it)and the procedure to install it...then i can install linc and see wether i can have internet access on ubuntu....and plz tell me when are you online (GMT i.e) so that i can converse with u faster and efficiently...

---

### Post by nereid on 2007-02-28
I don't know any other rpm to deb converter than alien, sorry. When I'm online? Can't say, totally erratic. How is it with IRC? Did you find a channel? I'm sure these people could help you way more than I.

---

### Post by amod on 2007-02-28
it uses the port 6667...it just doens't connect to any server even when i have internet access...Don't know way to do...newayz can u give me a tested link for alien and the procedure as to how to install it

---

### Post by Maestro23 on 2007-02-28
> **amod said:**
> it uses the port 6667...it just doens't connect to any server even when i have internet access...Don't know way to do...newayz can u give me a tested link for alien and the procedure as to how to install it

Ubuntu packages: [http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/)

Select your distro then search alien.  Download the package.  It's a .deb so:

> sudo dpkg -i alien_8.64_all.deb

---

### Post by amod on 2007-03-01
i downloaded all for edgy eft...but when i try to install it, the application gives me a error that 'package dependency is not satisfactory'...What should i do???? Extract it in the filesystem drive and then write the QUOTE above in the terminal....is that wat is supposed to be dun???? Another thing is that how much space is to be allotted for swap...i hav 256 mb of Ram and ubuntu runs just fine but i simply can't just do anything on it other than play games...although i hav allotted 1gb for SWAP...Is it enough or do i need to allot more????

---

### Post by amod on 2007-03-02
Guys plz help me out

---

### Post by Maestro23 on 2007-03-02
> **amod said:**
> Guys plz help me out

Your swap size is fine.  As for the alien dependencies.  Go back the Ubuntu packages site and look up the alien package.  It will tell you all the packages it depends on.  They will have a red circle by them.

To see if your system has them, you can run a search thru Synaptic. If you don't have them, they must be downloaded as well.

Good luck.

---

### Post by amod on 2007-03-02
but i downloaded all...which is an option at the end of the page....so i hav to download them individually as well...cool..Will do it..

---

### Post by amod on 2007-03-02
What do i do with the .tar.gz files

---

### Post by amod on 2007-03-02
Is there any way in which i can get all of those files including the dependencies downloaded at once...if yes then how do i install them

---

### Post by Maestro23 on 2007-03-02
> **amod said:**
> What do i do with the .tar.gz files

What files are .tar.gz?  Those are source files and must be compiled.  A whole headache in itself especially not having access to the repositories.  You are going to run into a lot of dependency errors there as well.

To install from source, you first need a package called "build-essential".

---

### Post by amod on 2007-03-02
i'll surely be needing a tutorial on this....coz i don't know wat i hav downloaded and wat i have not...is there any way i can download the dependencies and repositories  and tar.gz all in one zip file or somekind of a installatin file..

---

