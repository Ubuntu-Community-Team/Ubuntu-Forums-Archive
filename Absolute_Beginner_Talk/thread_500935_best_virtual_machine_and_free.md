---
title: "best virtual machine and free"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by simons-photography on 2007-07-14
I'm thinking of running ubuntu on a virtual machine to test it out what is the best one and one that is free ?

---

### Post by macogw on 2007-07-14
virtualbox. it's free (both gratis and libre), and it's faster than VMWare

---

### Post by starcraft.man on 2007-07-14
> **simons-photography said:**
> I'm thinking of running ubuntu on a virtual machine to test it out what is the best one and one that is free ?

Hi there, welcome to Ubuntu. I see your new :).

As for Virtual machines, the best free fully functioning one is [Virtual Box]("http://www.virtualbox.org/") (it's only real limitation is it only supports x86/32 bit OS at this time). 

My advice to you would be tor read through my blue link to understand installing in Ubuntu, then at the right times Linux Command (when I link to it) and finally when you get all that I'd direct you to add the repositories for Virtual Box to get it installed.  You can of course use the binaries but you'll be thankful for using the repos later, it makes management much easier. Oh and both the repositories and binaries are in the download section of course.

---

### Post by simons-photography on 2007-07-14
well i lost my password or user name so had to reregiaster i did try ubuntu a while ago but gave up but i'll give feisty fawn a go, my modem is my cell phone and because i hacked the phone to change provider it will only connect to the internet via a program supplied with the phone so unless I can pass the internet connection thru windows to ubuntu i'm screwed really,

i want to install ubuntu in its 64 bit version so how does that effect the virtual machine ?

---

### Post by starcraft.man on 2007-07-14
> **simons-photography said:**
> well i lost my password or user name so had to reregiaster i did try ubuntu a while ago but gave up but i'll give feisty fawn a go, my modem is my cell phone and because i hacked the phone to change provider it will only connect to the internet via a program supplied with the phone so unless I can pass the internet connection thru windows to ubuntu i'm screwed really,

i want to install ubuntu in its 64 bit version so how does that effect the virtual machine ?

VBox doesn't support 64 bit versions of anything (host or guest, yet). In a VM you won't see much if any performance boost from that though so just stick to regular 32 bit for Virtual Box. I assume your Windows version is 32 right? Not that many people I know have moved yet to 64...

As for the phone modem, I can't help there. My advice would be to get a regular DSL line. Doesn't that cell data plan cost a fortune if your using it as your main computer access? I mean downloading, torrenting or anything else intensive must eat up your bandwidth... unless your doing something shady with it (i.e. your hacking).

---

### Post by macogw on 2007-07-14
youd have to use vmware or qemu then, i think.  actually, idk if qemu does 64bit either

---

### Post by oilchangeguy on 2007-07-14
> **simons-photography said:**
> I'm thinking of running ubuntu on a virtual machine to test it out what is the best one and one that is free ?

why not just run it from the live cd? you can test it that way with out having to install it on the computer, until you're ready.

---

### Post by starcraft.man on 2007-07-14
> **oilchangeguy said:**
> why not just run it from the live cd? you can test it that way with out having to install it on the computer, until you're ready.

I think his main reason for dropping it in a VM is cuz he can't get his internet otherwise, due to his special phone set up/software. I still think there must be a cheap DSL provider near ya that could give ya a better deal, most data plans I know cost way too much.

---

### Post by oilchangeguy on 2007-07-14
> **starcraft.man said:**
> I think his main reason for dropping it in a VM is cuz he can't get his internet otherwise, due to his special phone set up/software. I still think there must be a cheap DSL provider near ya that could give ya a better deal, most data plans I know cost way too much.

ok, next question. using this strange connection method with windows, how many years is it going to take to create a usable ubuntu cd? i totally agree, the user needs to obtain a decent internet connection. and most phone, and cable companies now have entry level packages available. with pricing at or near dial up levels.

---

### Post by dewdman42 on 2007-07-14
Is VirtualBox better than VMPlayer and VirtualPC2007, both also free?

I have been using VMPlayer with a prebuilt Kubunutu 7.04 distribution, it was completely painless to get running, no install!  And its working just great.  But I'm curious how VMWare compares to VirtualBox?

---

### Post by starcraft.man on 2007-07-14
> **dewdman42 said:**
> Is VirtualBox better than VMPlayer and VirtualPC2007, both also free?

I have been using VMPlayer with a prebuilt Kubunutu 7.04 distribution, it was completely painless to get running, no install!  And its working just great.  But I'm curious how VMWare compares to VirtualBox?

Virtual PC is bottom of the barrel, please don't even try and compare them. I've used two different versions of that program and both were horrible and slow. On a decent system you probably won't notice much difference in speed between them (VMware and Virtual Box). However, I have heard of people "feeling" it to be faster with VBox, it makes sense to me that it's lighter but I don't know if it's actual speed or subjective.

Oh and if your worried about installing, Virtual Box reads VMDK files that VMware uses. You can install it and open up the image, if you like it I believe you can even overwrite the additionals from VMware, though don't take my word on that I always do a clean install from a CD when working with VMs. Virtual Box certainly has more features than VMplayer, and even server I believe. It's kinda between server and workstation of the VMware line I suppose.

---

### Post by Warpnow on 2007-07-14
The free version of Vmware and Vbox are about the same. If you have the crazy cash to drop on the paid version of vmware its better. 

That said, most people here will swear til the end of the earth vbox is unconestedly better because is free like linux, and they're biased like that, which is the stupidest thing I've ever heard of.

---

### Post by starcraft.man on 2007-07-14
> **Warpnow said:**
> The free version of Vmware and Vbox are about the same. If you have the crazy cash to drop on the paid version of vmware its better. 

That said, most people here will swear til the end of the earth vbox is unconestedly better because is free like linux, and they're biased like that, which is the stupidest thing I've ever heard of.

Biased? Uh, I don't think so. I've both used server (long time ago) and gotten my hands on Workstation. I now use VBox for all my VM work that's 32 bit (my new workstation is 64 so I went back to my VMware for a while). Virtual Box isn't just free, it's also partly open source which is a big plus for many of us who favour projects which are FLOSS. I don't think supporting and promoting open source projects is stupid...

---

### Post by AndyCooll on 2007-07-14
I agree with warpnow, those who tell you VirtualBox is much better than VMware are looking through rose-tinted glasses. I've used them both and both are excellent.

I personally prefer VirtualBox as it is an excellent product and free as in "freedom". Vmware is also an excellent product however and more mature, however it is only free as in "beer". 

In the end the choice is yours, and whichever you choose you won't go wrong.

:cool:

---

