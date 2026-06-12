---
title: "Storage server"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Pyro_Killer on 2008-04-12
Hello people, I see that there are several theads about the suggest, but as I am so new to this subject, I do need some good answers, I do use an ordinary PC with a ordinary network card, and a Netgear 54 Mbps Wireless PCI adapter WG311v3. I do use windows XP and one MAC. What I want after I install ubuntu on the computer later tonight, is for it to go on the TV, and load and stream movies (wireless if possible) from the different computers ans store them there, because of storage issues. I have a lot of hard-drives with small space, as I am a student, and don't have a lot of cash. They are totaling at 600gb, and I want to make them all into one space to keep the stuff, and I want to lay a password on the wireless. Is this possible, and what programs do I need, please get many details, as my english is rusty.

---

### Post by hyper_ch on 2008-04-12
first, download the desktopcd and try to boot from that. That will show you if you may encounter problems with your hardware... video and wifi card can often be a problem...

if you have verified that you have compatible software then we can look further ;)

---

### Post by mlentink on 2008-04-12
Ehm...
Let me get this...

You want to turn the storage in both the XP box and the Mac into one big sotrage space and use that to store you captured video? Controlled from Ubuntu? That would at minimum mean a third box. But maybe I musunderstood.
May be we should do this one step at a time....

---

### Post by Pyro_Killer on 2008-04-12
No, I want to transfer the files from my mac and XP's to this server of mine. I also want to control the ubuntu unit from these other computers, and transfer files within it. The ubuntu will be the storage box, which is not installed because my download speed is low today.

I have already installed ubuntu on it before and know that everything works. The ubuntu will have its own box, and I have used ubuntu some times before and installed all kinds of stuff with alien, and without alien.

---

### Post by joshrobinson on 2008-04-12
i actually have an ubuntu fileserver, i do pretty much the same thing

i installed ubuntu 8.04 beta on it, then installed samba to set up a network that can be shared with my modified xbox(i use the xbox to read the files over samba, which is windows networking, and display them on my tv)

so install ubuntu, mount your hard-drives, setup samba, transfer your data

you will probably want to look up a few howto's, or as questions along the way

---

### Post by Pyro_Killer on 2008-04-12
Surtenly, I shall look at guides, but is it possible to get samba setup with a visual interface, instead of doing it through the terminal, because i have some difficulties with it, and is it possible to make a local wireless network without the internett, with the ubuntu as output point, with the network card, with a password?

---

### Post by joshrobinson on 2008-04-12
> **Pyro_Killer said:**
> Surtenly, I shall look at guides, but is it possible to get samba setup with a visual interface, instead of doing it through the terminal, because i have some difficulties with it, and is it possible to make a local wireless network without the internett, with the ubuntu as output point, with the network card, with a password?

yes samba can be setup with a GUI, you may have to edit the smb.conf file manually, but that isnt really that hard if a guide or someone points you in the right direction.

as far as setting up a wireless access point in ubuntu, im not sure. you dont have a wireless router running the internet?

---

### Post by Pyro_Killer on 2008-04-12
I do not have any internett exept for a mobile broadband(?) it goes over the 3g network, and I really wish I had ordinary internet access, but I don't. I still live at home, and I live with my dad, and it is impossible to get a cable out here. I will bring my server pc to my mom tomorrow, but only for some hours, so I need as much info now as possible, so that I am prepared.

Where is the smb.conf file? etc/apt or?

---

### Post by joshrobinson on 2008-04-12
```
sudo apt-get install samba
```
will install samba

```
sudo gedit /etc/samba/smb.conf
```
will let you edit smb.conf

read through the file, also look online for how to configure your smb.conf file
if when your over your moms, if you jump on these forums, someone will be around to help if you have questions.  but it would be best to ask them as you are trying to set it up

---

### Post by louieb on 2008-04-12
Just curious. The PC you plan to put Ubuntu on. What are the specs.
How much memory?
What type CPU? Speed?
How many hard drives? What size drives?
Did wireless work when you had Ubuntu on it before?

By letting us know what you have to work with. You will get better answers.  Lot of members here have a home network and will share what worked and did not work for them.

---

