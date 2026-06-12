---
title: "Completely Brand New"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by insyted on 2007-01-23
Hello,

I plan to use Ubuntu on my computer.
I have never used Linux before, so I have absolutely no experience with this.

I'm using an Intel 64-bit Celeron D processor.
Asus Graphics card with Nvidia 6200TCLE GPU.

Will Ubuntu be able to support this?
My video card has support for dual monitors.
Would I be able to do this on Ubuntu?

Does Ubuntu use a special client to download and install Ubuntu software from the internet location(warehouse)?

Can anybody give me a website listing all Ubuntu applications?
Can Ubuntu run other Linux apps?
How does the OS take advantage of the 64-bit technology in my system? What particular applications take advantage of 64bit technology?

What antivirus and antispyware applications are available?

Thank You.

---

### Post by tronica on 2007-01-23
ubuntu will support your setup just fine. it will work with dual monitor but you need the nvidia driver installed i recommend this guide to get you going,

[http://ubuntuguide.org]("http://ubuntuguide.org")

as far as 64-bit its the way of the future, however lots of apps don't work on it yet. but thats up to you. there are ways around that

---

### Post by insyted on 2007-01-23
Thanks. That guide has great infomration.

I still wasn't sure about the software thing.
I guess Ubuntu uses a client to access the internet to download and install software.
Can it install any Linux software that I can find in many places online? What are the limitations?
Is there anything that will allow me to chat on AIM/Yahoo Messanger/MS Messanger?

---

### Post by teitunge on 2007-01-23
You could install most of the software you want to. Ubuntu uses synaptic and aptitude to install software. Synaptic is the gui one, and aptitude is the textbased.

To use aptitude, which I prefer, I would advice you to add some repos., and you will find a howto at ubuntuguide.org.

To answer the question about AIM and msn, you have a program called GAIM which allows you to access any of those. For MSN I personally prefer Kopete, but it`s your choice :)

---

### Post by carverj on 2007-01-23
> Does Ubuntu use a special client to download and install Ubuntu software from the internet location(warehouse)?

Can anybody give me a website listing all Ubuntu applications?
Can Ubuntu run other Linux apps?
How does the OS take advantage of the 64-bit technology in my system? What particular applications take advantage of 64bit technology?

What antivirus and antispyware applications are available?

Learning to use the terminal is the go with Linux. Takes time, patience and trial and error, but boy is it worth it in the long run.
Follow the instructions in the [www.ubuntuguide.org](www.ubuntuguide.org) to update repositories and then synaptic is the GUI for installing/removing Ubuntu and Linux software.
AVClam is the antivirus app. of the moment and antispyware may not be necessary. Could be wrong there, never even thought about spyware and Linux!! It rocks.
Good luck and get stuck in.

> I still wasn't sure about the software thing.
I guess Ubuntu uses a client to access the internet to download and install software.
Can it install any Linux software that I can find in many places online? What are the limitations?
Is there anything that will allow me to chat on AIM/Yahoo Messanger/MS Messanger?

Yes, Linux was originally designed with Unix technology. Very network/internet friendly functionality.
Synaptic is found in the System > Administration menu. You can not only install/remove software, you could also enable your repositories there. These are the libraries of available open source apps.
> Can it install any Linux software that I can find in many places online? What are the limitations?
What synaptic? Yes, as long as you have your repo's enabled and connecting. From time to time you'll have connectivity issues with repo's and so you may visit [www.sourceforge.org](www.sourceforge.org) for the app. or do a search and install the software manually.

---

### Post by teitunge on 2007-01-23
> **carverj said:**
> AVClam is the antivirus app. of the moment and antispyware may not be necessary. Could be wrong there, never even thought about spyware and Linux!! 

Hehe, after I changed from windows to ubuntu for about three months ago I have totally forgot about viruses and spyware..

---

### Post by igknighted on 2007-01-23
> **insyted said:**
> Thanks. That guide has great infomration.

I still wasn't sure about the software thing.
I guess Ubuntu uses a client to access the internet to download and install software.
Can it install any Linux software that I can find in many places online? What are the limitations?
Is there anything that will allow me to chat on AIM/Yahoo Messanger/MS Messanger?

There are many clients for those services, most popular are Gaim (handles all of those) and Kopete (also handles them all I believe).  You certainly can get software all over the internet, but I would always scan the Repositories first.  It is safer to install from there (all packages are signed).  There is no universal .exe type installer however.  Like .zip and .rar and .ace you need different programs to unpack/install these various packages.

As for 64 bit, if this is something you are really interested in, I would steer you away from Ubuntu or Debian based distro's in general.  They do not interact well with the 64 bit environment.  Try an RPM based distro such as OpenSuse or even a source based distro like Sabayon (based on Gentoo, but very user friendly) if you really want to explore 64 bit.  There arent many programs that don't run at 64 bit, but some notable ones are flashplayer and Opera.

There are a few anti-virus programs for linux, but at this point all they really do is scan for windows viruses so you don't pass them along to your friends (in other words they aren't needed) and anti-adware programs are not needed.  There is a firewall, also not really needed, but it is installed by default.  You can control it through the terminal or download a nice GUI frontend called 'firestarter'.

Your hardware looks like it is well supported.  If you have wireless it might be an issue, or some other obscure hardware, but nothing you listed looks like it should have any issues.

Good Luck!

---

### Post by IYY on 2007-01-24
> Will Ubuntu be able to support this?

The safest thing is to run the LiveCD and check for yourself. No installation required. However, from your description of the machine, it sounds like everything should be fine.

> My video card has support for dual monitors.
Would I be able to do this on Ubuntu?

Yes, but the configuration can be a bit trickier than in Windows. The new nVidia drivers do have a graphical way to configure it, but it's still not very intuitive.

> Does Ubuntu use a special client to download and install Ubuntu software from the internet location(warehouse)?

If you mean the Ubuntu repositories, then you can use the program Synaptic (installed by default). 

> Can anybody give me a website listing all Ubuntu applications?

I don't know of a list, but from my memory, here's what's installed by default:

Firefox, a web browser.
Gimp, an image editor like photoshop.
Gaim, an instant messenger that supports popular protocols like MSN, Yahoo and AIM
Open Office, includes a word processor, presentation and spreadsheet software. Compatible with Microsoft Office.
Evolution, an e-mail client like outlook.
A media player
Various configuration and system management utilities.
All sorts of little apps like calculator, text editor, terminal, basic games, a document reader, etc.

> Can Ubuntu run other Linux apps?

Sometimes. Certain programs work on all Linux distributions with a single binary (games like Quake, for example). Other programs can be installed with utilities like Alient (converts RedHat's RPMs to Ubuntu's Debs).

Moreover, most Linux apps come in source-code format, so you can always compile it for any distribution. The repositories also have a very large selection of such software.

Commercial Linux software is always designed to run on all distributions.

> How does the OS take advantage of the 64-bit technology in my system? What particular applications take advantage of 64bit technology?

If you install the 64 bit edition, the OS will take full use of the 64-bit technology. Not all applications will, however. I'm not sure about the details, since I'm still in 32-bit land. :p

> What antivirus and antispyware applications are available?

You certainly don't need antispyware since no spyware application has ever been made for Linux. There are no Linux viruses in the wild either, but there is an antivirus you can download. It's generally used to scan files you plan to distribute to Windows users. The default security configuration is good, so you don't need a firewall either.

---

