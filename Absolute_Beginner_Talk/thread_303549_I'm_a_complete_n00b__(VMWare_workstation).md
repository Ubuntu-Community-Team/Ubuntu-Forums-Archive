---
title: "I'm a complete n00b  (VMWare workstation)"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by Gamerunknown on 2006-11-20
I'm using Windows XP Home edition. I loaded Ubuntu from the ISO, because I wanted to try it out on a virtual machine, before booting it. I burnt it to disc, but that doesn't appear to work. 

When I run Ubuntu, in normal or safe graphics mode, it appears to run very slowly. When I try installing VMWare tools, it slows down entirely, and often, freezes my main computer. Is there any way to install VMWare tools before running the virtual machine, or any way to speed it up without doing so =\?

Any help much appreciated.

---

### Post by Gamerunknown on 2006-11-20
Oh, and I'm using Edgy, or 6.10 or whatever. >_>.

---

### Post by Gamerunknown on 2006-11-20
I can deal with the lag, but now, on firefox, it says "Server not found" for google.com >_>...

I haven't tried using the internet before on VMW.

---

### Post by stalker145 on 2006-11-20
Greetings.
> Is there any way to install VMWare tools before running the virtual machine
According to what I've seen, you have to actually have the VM installed and running to be able to install the VM tools. It goes in and loads 'something' to make everything work better.

> on firefox, it says "Server not found" for google.com >_>...
I personally use NAT'd networking with my VM's. In doing so, you give the VM its own IP on your network. The issue here is probably an incorrect network setup. You can shut down your VM and go to the properties. Change the type of networking from there.

> it appears to run very slowly
Remember that as with all OS's, you have to allocate RAM. Depending on the OS, you need to give more. I, personally, have 256MB allocated to my Win2k VM. If you don't have a bunch of RAM, it's all going to slow to a crawl.

Good luck. I don't know how much help this was, but it's worth a shot answering ;)

---

### Post by Gamerunknown on 2006-11-20
I tried installing VMWare Tools, but I've never actually seen anything happen at that time, except an executable with vmware as the prefix eat up like 95+ of the CPU.

>>>I personally use NAT'd networking with my VM's. In doing so, you give the VM its own IP on your network. The issue here is probably an incorrect network setup. You can shut down your VM and go to the properties. Change the type of networking from there.

I tried changing it, with the same result. I didn't shut it down first, though. I'll give it a shot now, thanks.

>>>Remember that as with all OS's, you have to allocate RAM. Depending on the OS, you need to give more. I, personally, have 256MB allocated to my Win2k VM. If you don't have a bunch of RAM, it's all going to slow to a crawl.

I thought that might have been the case =p. I've only got 160 down or something, and it shows up as static (not able to change that). Is that one of the things you can only change at the beginning?

>>>Good luck. I don't know how much help this was, but it's worth a shot answering

No, getting any answer is very encouraging =D

---

### Post by Gamerunknown on 2006-11-20
Hrmn, I tried reinstalling Ubuntu on the Virtual Machine, and it didn't mention allocating RAM. Must be based on my measly 512Mb =\

My computer properties gives an option though, where I can change the way stuff works, with Performance Options under Advanced Performance Settings.

---

### Post by stalker145 on 2006-11-20
> I tried installing VMWare Tools, but I've never actually seen anything happen at that time, except an executable with vmware as the prefix eat up like 95+ of the CPU
One of the things I noticed most recently with installing VM Tools was that the VM didn't 'grab' my cursor. Now, it may have been something that I changed and forgot about. 
With your VM eating your CPU like that, I would think that it's from not having enough RAM for the VM.

> Is that one of the things you can only change at the beginning?
From what I've seen, you should be able to change the amount of RAM allocated at any time. Just make sure to shut down the VM, change it, and restart.

All of the above (RAM, networking, and anything else) is just like installing new hardware into a real computer. Make sure to shut it down or it won't work. At least since this is software you don't have to worry about blowing up your rig ;)

---

### Post by Gamerunknown on 2006-11-20
Yeah, I totally forgot to shut it down first, xD. 

Told you I was a complete n00b =3. I'm posting from Ubuntu right now though, and I LOVE YOU! 

Roffles. Will stuff save normally on this VM now?

---

### Post by Gamerunknown on 2006-11-20
Ulp! Nothing handles .exe s? What is this madness o_0! =p

---

### Post by stalker145 on 2006-11-20
> **Gamerunknown said:**
> Ulp! Nothing handles .exe s? What is this madness o_0! =p

Ahh, yes, using Ubuntu as the VM. I'd forgotten that until I reread the thread. 
Things will save in the VM exactly the same as if it were a real load. You can also install any software you like into the VM. This is where you will need to install WINE or another sort of program to handle your .exe files as Linux does not natively support .exe. 
WINE should be available through the repositories, from the web site, or installable using Automatix. Just remember that the more things you run within the VM, the more your CPU/RAM usage will creep up.

I'm glad I could be of some help. Being new myself, I've been itching to contribute back to the community that's helped me muddle through the conversion :D

---

### Post by Gamerunknown on 2006-11-22
I wanted to say something the day before yesterday, but I totally forgot, and my sister had an exam today, so she was revising on the computer for most of yesterday =p.

What I found was that nothing was saved to my virtual machine, after starting it today =(. I had quite a few extensions to firefox and stuff, but it didn't work. I've found that it isn't so hard not to use exes, but it would have been easier to know at the start =p. I could download wine, but I'd feel like a traitor at the moment. Also, it may be gone the next time I look =o. 

I already allocated all the 8Gigs of storage too, and I'm not using any =(... 

Thanks for all your help so far though.

---

### Post by ewl1217 on 2006-11-22
Are you sure that you saved everything and shut down the virtual machine properly? Also, you should make sure that VMware is not set to revert to the previous state after shutting down.

---

### Post by Gamerunknown on 2006-11-22
I've never managed to shut down my virtual machine correctly, as it  takes up file history until it exceeds its limit (280Mbs) and completely freezes. At this point, I just restart. It never goes down, when I try closing processes, IIRC. 

Also, how do I open things? It said it can't open .bin files, and everything else I've tried to download just opened an archive, and never ran an installation wizard.

---

### Post by NiklasV on 2006-11-22
Installation wizards as you know them in windows are pretty rare in Linux.
Some applications use executable installers, the bin files you metion are probably installation wizards.
To run the bin files you need to make them executable, right-click the file, click properties, go to the permissions tab, and check "Allow execuing file as program"

Generally though, you would use the package manager to install software.
The package manager installs .deb files. If you double click a .deb package, GDebi will come up and ask if you wish to install it.
But mostly, packages are installed from the repositories. Go to Applications->Add/Remove for an easy to use package manager.
Just enter the name of the program you want, check the box, and click apply. The package manager will ask you for a password, just enter the one you logged in with.

---

### Post by Gamerunknown on 2006-11-22
Alright, thank you =D.

 Just to make things a little clearer, in case other users encounter the same problems: I think most of my problems were due to me booting from an ISO, because burning it to disc didn't seem to work. I didn't bother clicking install, as that made me lag the first time I did it, and I developed a pavlov response =p. Now, everything seems to be running a whole lot smoother...

(I just clicked disconnect device or something).

---

### Post by Gamerunknown on 2006-11-22
Also, just wondering, is it possible to export and import bookmarks, extensions and other settings from firefox? >_>

---

### Post by Gamerunknown on 2006-11-24
Oh snap, whenever I add a bridged connection (ethernet card), it doesn't work o_0

---

### Post by Gamerunknown on 2006-11-24
and by "it" I mean my internet connection.

---

