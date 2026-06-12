---
title: "ubuntu minimal CD iso..."
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-12
Hello forum people,

uh....can anybody tell me how much data does the server install of ubuntu download?

if i download the minimal CD iso...10 megs..and start the the live web server install...how much will ubuntu then download while it installs?

500 megs?

i read somewhere that it onyl takes 15 minutes to do a server install? (maybe that meant from hard CD disc)

thanks

Vince.

---

### Post by LaRoza on 2008-04-12
For a server installation, it does take around 15 minutes.

The ISO is 499 MB. It doesn't download anything unless you tell it to.

There is no net install disk for Ubuntu that I am aware.

---

### Post by vinceUUUU on 2008-04-12
Hello

so you mean.....?

the live server install will take me to a command prompt in around 15 minutes....and does not actually install anything..... of the typical 500 meg ubuntu server CD?

then i must tell my machine what packages to install.....at the command prompt...

so in effect, it gets to that command prompt?  from what it finds on the Minimal iso file CD.....10 megs?

thanks

Vince.

---

### Post by LaRoza on 2008-04-12
> **vinceUUUU said:**
> Hello

so you mean.....?

the live server install will take me to a command prompt in around 15 minutes....and does not actually install anything..... of the typical 500 meg ubuntu server CD?

then i must tell my machine what packages to install.....at the command prompt...

so in effect, it gets to that command prompt?  from what it finds on the Minimal iso file CD.....10 megs?

thanks

Vince.

There is no minimal iso. For Ubuntu 7.10, there are three options (for x86 and x64). 

[list]
[*] Ubuntu Live install disk (desktop only)
[*] Ubuntu Server install disk (server only)
[*] Ubuntu Alternative disk
[/list]

They are all less than 700 MB (well, they can all fit on a cd), and the server install disk is 499 MB.

The live disk will run a live session and can be used to install the desktop version of Ubuntu.

The server disk will only install Ubuntu setup for a server.

The alternative disk doesn't run live, but can be used to setup a desktop (just like the live disk), a server (just like the server), or a command line system (a minimal install) and has a few other options.

The "text installer" is easy to use. It is not a command line, and has all the same general options as the live disk. It is easy to use. I use the alternative disk only for installing, because of it flexibility and speed.

I am not sure where this "10 mb" is coming from. A server installation doesn't need a GUI, and it doesn't have one. The desktop installation has the normal Ubuntu GUI. The base installation is just a command prompt, but it is easy to install the packages you want from there.

---

### Post by vinceUUUU on 2008-04-12
Hello

thanks for replying

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

this is the minimal ubuntu CD...(fiesty i think)

what i want to know is......when i boot this minimal ISO file up....i believe i must then type the word  "server"....and it installs a base ubuntu in around 15 minutes....using what it finds on the minimal ISO cd....

then i reboot into this base ubuntu....

at the command prompt, can i then tell it what other packages to download and install as and when i please?

thanks

Vince.

---

### Post by LaRoza on 2008-04-12
> **vinceUUUU said:**
> Hello

thanks for replying

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

this is the minimal ubuntu CD...(fiesty i think)

what i want to know is......when i boot this minimal ISO file up....i believe i must then type the word  "server"....and it installs a base ubuntu in around 15 minutes....using what it finds on the minimal ISO cd....

then i reboot into this base ubuntu....

at the command prompt, can i then tell it what other packages to download and install as and when i please?


Wow. I never knew of them...

I don't know exactly how that one works. I have done net installs with Debian, and there is almost nothing on the CD. The downloadind starts during the installation.

It probably doesn't install what it sees on the cd. If you install a server with it, it will download the server packages during the install.

After you install, the server is CLI only. You could install using apt-get and aptitude as usual.

Do you need a server?

---

### Post by LaRoza on 2008-04-12
I am using it now, so I can further answer questions.

---

### Post by LaRoza on 2008-04-12
It starts downloading the components very soon after selecting language and keyboard and configuring the network.

If you have network restrictions, this install method isn't going to help.

It has just enough on the cd to start the installation, but needs to download what it installs.

If you need a disk, whatever version, but cannot download it, PM me and I will mail what you want.

---

### Post by vinceUUUU on 2008-04-12
Hello

yes, i think you are right...

the downloading starts when it starts installing the server edition...

i don't think it gets right to a BASE command prompt type install....quikly or without downloading anything...

i beleive it goes ahead and starts a LIVE server install by downloading the packages...all 500 megs...

what i need is a tiny quik ubuntu BASE install...that gives me a command prompt...and has not downloaded anything in the meantime....

i don't think this minimal thing gives you a route to the final UBUNTU command prompt....until it has downloaded and installed the entire server edition....all 500 megs

what do you think?

Vince.

---

### Post by jken146 on 2008-04-12
You can use the minimal CD to install just the Ubuntu base system, which is quite small.  Less stuff is installed than in a standard server install.

---

### Post by vinceUUUU on 2008-04-12
Hello,

so how would i use that minimal CD then?

you say less stuff is installed if i do a BASE install..than a typical server install...

so what command do i type at the Minimal CD boot prompt?..........what command will do me a base ubuntu install and how much will it download?

also will it put somekind of package tool in?.....so i can use the command prompt to install further packages as and when i please?

thanks

Vince.

---

### Post by LaRoza on 2008-04-12
> **vinceUUUU said:**
> 

i don't think it gets right to a BASE command prompt type install....quikly or without downloading anything...

what i need is a tiny quik ubuntu BASE install...that gives me a command prompt...and has not downloaded anything in the meantime....

i don't think this minimal thing gives you a route to the final UBUNTU command prompt....until it has downloaded and installed the entire server edition....all 500 megs

what do you think?

Vince.

You can use the alternative disk to install a base system without downloading anything. However, the alternative disk is about the same size as the Live disk (it has the same packages and more).

Is there a reason you can't download the alternative disk? If you want it, I'll mail it to you. Faster than shipit.

> **jken146 said:**
> You can use the minimal CD to install just the Ubuntu base system, which is quite small.  Less stuff is installed than in a standard server install.

Yes, I use such a system on my iBook (see my blog). All CLI, just a few extra apps installed and it is flying.

---

### Post by vinceUUUU on 2008-04-12
Hello,

yes....not allowed much downloading here

but also the alternate CD hangs on install.....i used it one time...sometimes it installs, sometimes it fails to install....

just gonna read the latest posts here again

V.

---

### Post by LaRoza on 2008-04-12
> **vinceUUUU said:**
> Hello,

so how would i use that minimal CD then?

you say less stuff is installed if i do a BASE install..than a typical server install...

so what command do i type at the Minimal CD boot prompt?..........what command will do me a base ubuntu install and how much will it download?

also will it put somekind of package tool in?.....so i can use the command prompt to install further packages as and when i please?


You would have to have a fast network connection and be willing to wait for the downloads.

A server install is a server. It has a different kernel, and server packages (Apache2, MySQL, and other modules). It should not be used unless you want a server.

A base installation is a minimal install. It installs just enough to boot and run. It has no GUI and few tools beyond the standard Linux tools.

With a base install (using the alternative disk), you get the desktop kernel (actually, you choose which one you want), and the tools to install packages.

See my blog, that iBook is an example of this.

After the install, I edited my /etc/apt/sources.list to include the repositories I wanted (I used vim) and used aptitude to install what I wanted.

---

### Post by vinceUUUU on 2008-04-12
Hello

yes....so because the alternate CD failed....it was binned....

not got a copy of it

V.

---

### Post by LaRoza on 2008-04-12
> **vinceUUUU said:**
> Hello,

yes....not allowed much downloading here


You can PM me and I will mail them to you, or you can request a free disk from the Ubuntu site.

(I am faster)

I have many disks, so you can request anything you want from me (only free software)

---

### Post by vinceUUUU on 2008-04-12
Hello,

so if i have not got the alternate CD....i can't begin a base install anyhow..

also what is the answer about how much a base install downloads?

i have a fast web connection...

can't i do a base install from that minimal CD?

thanks 

Vince.

---

### Post by LaRoza on 2008-04-12
> **vinceUUUU said:**
> Hello,

so if i have not got the alternate CD....i can't begin a base install anyhow..

also what is the answer about how much a base install downloads?

i have a fast web connection...

can't i do a base install from that minimal CD?

thanks 

Vince.

I am not sure what you want. 

Perhaps you should explain what you want, and the restrictions you have.

A base installation is pretty light, but I do not know the exact size. I would *guess* around 200 MB.

---

### Post by vinceUUUU on 2008-04-12
Hello,

oh right...200 megs...that is still quite a lot for downloading...

i wanted it to be a real small ubuntu...tiny thing that justed booted a command prompt and allowed you to choose further packages as pleased....

i was thinking there would be something at around 50 megs that would do that BASE ubuntu install..not 200

what does it put in...to need 200 megs ....is that just the size a BASE install?

why would  a command prompt and package tool take 200 megs?

i ask this because recently i saw other linux distros that were GUI desktops and even came with tools aswell at under 10 megs in size.....Grey Cat linux....

there are also other GUI linux distros ....that fit on floppy discs...under 2 megs in size

thanks

Vince.

---

### Post by LaRoza on 2008-04-12
> **vinceUUUU said:**
> 
i wanted it to be a real small ubuntu...tiny thing that justed booted a command prompt and allowed you to choose further packages as pleased....

i was thinking there would be something at around 50 megs that would do that BASE ubuntu install..not 200

what does it put in...to need 200 megs ....is that just the size a BASE install?

why would  a command prompt and package tool take 200 megs?

i ask this because recently i saw other linux distros that were GUI desktops and even came with tools aswell at under 10 megs in size.....Grey Cat linux....

there are also other GUI linux distros ....that fit on floppy discs...under 2 megs in size


I don't really know the exact size.

The size is due to the way it is packaged and what is packages. Ubuntu isn't targetted to the same use as those ulta small distros.

Also, I think the kernel itself is 22 MB. Not sure though.

You can use one of those ultra light distros, or you can either download or request an Ubuntu disk.

You can always ask me...

---

