---
title: "Virtualization with VMWare, I must be in heaven"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by doctorberen on 2006-11-02
I was always afraid of virtualization but I wanted to get rid of my windows partition so badly so I finally tried it using [this]("http://ubuntuforums.org/showthread.php?t=183209&highlight=VMWARE") how-to.

It wasn't a very hard thing for a newbie to do and I just followed the steps outlined in the how-to. I really did not encounter any gotchas.

When I ran VMWare server console, it just asked me to insert my Windows XP disc and I installed Windows uneventfully.

Finally, I booted into Windows inside Edgy!

At first, I was dismayed when things were running so slow. So I went back to the How-To and installed something called VMWare Tools. And voila! After that, things started running as fast as they run natively.

I decided my Windows partition was a waste of space so I reformatted my hard drive and just used the extra space for a larger /home partition. 

Since then, I've never been such a happy camper with Linux. I am running all my windows stuff side by side with my Linux stuff and I don't have to reboot. And I'm not really noticing any performance differences with Windows. If there is, it is very minimal.

I'm just now amazed at how this changes everything. I mean I've read a lot of posts in the forum wishing they could use this or that application within Linux. Well now we can. And the best part of it is VMWare Server wasn't all that hard to set up.

I even think in a lot of situations, this may be a better option than running things in Wine. Because so far, I have yet to experience an error. Whereas with Wine, some of my programs are slow and prone to bugs.

I did read in the how-to that games may be a different story. And I still haven't tried memory extensive programs like Photoshop. And I'm sure there are situations when dual-booting will still be a better option.

But for me, I'm very happy with Windows XP running under VMWare and my suggestion for those who are thinking about taking the plunge (but are wary) is to take the plunge anyway!

---

### Post by doctorberen on 2006-11-02
Click [this]("http://picasaweb.google.com/chrisrayala/VMWare/photo#4992888779726716946") for a screen shot, if you are interested.

---

### Post by ajackson on 2006-11-02
Ah yes nothing quite beats that feeling you get when you get to reformat a partition containing Windows :D

---

### Post by Marsolin on 2006-11-02
I also find that virtualization is good for the opposite use. My laptop is a company one that runs Windows, but I'm able to run Kubuntu in VMware Player and still get my time with Linux in.

---

### Post by gn2 on 2006-11-03
Did you get sound to work in Virtual Windows, and if so how?

That's the bit I'm struggling with.....

---

### Post by compmodder26 on 2006-11-03
> **gn2 said:**
> Did you get sound to work in Virtual Windows, and if so how?

That's the bit I'm struggling with.....

In your the settings for the windows virtual machine, you need to add a sound device.

---

### Post by Bartender on 2006-11-03
Thanks for the encouraging post.  Been looking at VMW but scared of it.  What sort of horsepower recommended for an install that's fairly snappy?

---

### Post by compmodder26 on 2006-11-03
I've only tried used it on my laptop so I don't really have a comparison.

My laptop has a Core Duo processor running at 1.83 ghz, 1 gb RAM, and intel integrated graphics.  After installing VMWare tools in windows, it runs at near native speeds.  

The minimum recommended RAM allocation for the windows virtual machine is 256MB.  I allocated 352MB. Of course you want to leave enough RAM available for Ubuntu to still be functional.

---

### Post by darrenm on 2006-11-03
If you want to be really flash then have a look at the seamless RDP howto then you can use applications running in vmware windows running as normal applications in linux.

---

### Post by gn2 on 2006-11-03
> **compmodder26 said:**
> In your the settings for the windows virtual machine, you need to add a sound device.

I had a look in there, but couldn't find a way of doing so. Will have to have another look though.

Thanks for info :)

---

### Post by doctorberen on 2006-11-03
GN2,

Now that you mentioned it, I checked and it seems like I don't have sound as well.

I clicked the VM>Settings and I do see and **ADD** button but for some reason, it's grayed out. Suffice it to say I can not add sound for now. I'll try to look into it some more but do tell me if you were able to succeed with this.

I have a 2 year old notebook with 1GB of RAM and a 1.73GHz single core processor and windows is running almost as snappy as it would natively.

---

### Post by happy-and-lost on 2006-11-06
I've installed VMware and got my ATi card working (which means that I can finally run Neverwinter nights is Linux, yay!) all in the same day :D

One thing stands in the way of me removing my Windows partition... how do you access /home in XP running under VMware?

---

### Post by darrenm on 2006-11-06
Easy - apt-get install samba
As long as you have the same username / password in windows and linux then you will be able to access your /home/you directory after adding yourself to the encrypted password database using:
```
smbpasswd -a yourusername
```

---

### Post by funrider on 2006-11-06
> **doctorberen said:**
> GN2,

Now that you mentioned it, I checked and it seems like I don't have sound as well.

I clicked the VM>Settings and I do see and **ADD** button but for some reason, it's grayed out. Suffice it to say I can not add sound for now. I'll try to look into it some more but do tell me if you were able to succeed with this.

I have a 2 year old notebook with 1GB of RAM and a 1.73GHz single core processor and windows is running almost as snappy as it would natively.


I am running ubuntu VM from a winXP laptop by WMware and I am sound. I am not familiar with VMsever but I believe you can choose the sound device/card from the VM set up just like the way you choose the network card.

Good luck!

---

### Post by funrider on 2006-11-06
> **doctorberen said:**
> I was always afraid of virtualization but I wanted to get rid of my windows partition so badly so I finally tried it using [this]("http://ubuntuforums.org/showthread.php?t=183209&highlight=VMWARE") how-to.

It wasn't a very hard thing for a newbie to do and I just followed the steps outlined in the how-to. I really did not encounter any gotchas.

When I ran VMWare server console, it just asked me to insert my Windows XP disc and I installed Windows uneventfully.

Finally, I booted into Windows inside Edgy!

At first, I was dismayed when things were running so slow. So I went back to the How-To and installed something called VMWare Tools. And voila! After that, things started running as fast as they run natively.

I decided my Windows partition was a waste of space so I reformatted my hard drive and just used the extra space for a larger /home partition. 

Since then, I've never been such a happy camper with Linux. I am running all my windows stuff side by side with my Linux stuff and I don't have to reboot. And I'm not really noticing any performance differences with Windows. If there is, it is very minimal.

I'm just now amazed at how this changes everything. I mean I've read a lot of posts in the forum wishing they could use this or that application within Linux. Well now we can. And the best part of it is VMWare Server wasn't all that hard to set up.

I even think in a lot of situations, this may be a better option than running things in Wine. Because so far, I have yet to experience an error. Whereas with Wine, some of my programs are slow and prone to bugs.

I did read in the how-to that games may be a different story. And I still haven't tried memory extensive programs like Photoshop. And I'm sure there are situations when dual-booting will still be a better option.

But for me, I'm very happy with Windows XP running under VMWare and my suggestion for those who are thinking about taking the plunge (but are wary) is to take the plunge anyway!


one great advantage by using VM is that you can always refresh the XP from a source backup file, which means:

1. save money on antivirus/spyware softwares
2. no need to run stupid windows defragmentation
3. feel more confident to surf dirty website \\:D/ since you can refresh the XP in minutes
4. save money from cloning/backup program like nortons ghost
5. have ur XP run anywhere vmplayer is avaliable (it is so cool that you can now house an OS in a thumbdrive and work anywhere)

---

### Post by Lord Illidan on 2006-11-06
I don't think VMware is good for directX, opengl, though? Cos I'd like to run my games there.

---

