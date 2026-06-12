---
title: "In need of advice for a college/class project"
date: 2006-08-10
forum: Apple PPC Users
---

### Post by RKCole on 2006-08-10
Hello, everyone.

I will be starting Fall Quarter classes next month.  I am (excitedly) enrolled to take the college's second Linux class which will afterward give me the opportunity to take the Linux+ exam.

Our Computer Repair course has a lot of older computers.  The typical specs for these systems are as follows:

Intel Pentium III (or Celeron):  500MHz or greater
128MB+ RAM
Typical internal components such as Intel-based integrated graphics cards (we usually don't get anything outside of Intel or ATI), HDDS, etc.

I was asked to find a distribution of Linux that would possibly work on these platforms.  We are trying to start a program in which we would take donated computers (and the older computers at the college) and install a distro of Linux and basically set everything up for the end-users; we then intend on freely distributing these computers to students and others who are in need of a system.  Those of us in the Linux class (and those of us who have made it through the A+ Preparation courses) would then become the technical support base for the users of the computer systems.

I started using Ubuntu Dapper on June 1 of this year, and I love it.  I was just curious as to whether or not the Alternate installation for Dapper would be suitable for computers with these varying specs.

The college used to install Windows 98 on the computer systems, but many of us in the Linux class have shown the directors the power of the OS, and the fact that it is free helped out quite a bit as well.

So to sum this up:
1)  Would Dapper (Alternate installation) be a possible candidate for this project?

2)  Does anyone have any experience with the alternate installation on a computer with older specs (I am sure that it works great)?

3)  If it would not be a good candidate, what would be a good candidate for this project?

I greatly appreciate any help/advice/suggestions that any of you can provide.  I personally feel that this project will be a great help to many people, and I know that it is a good way for us to spread the word and experience of Linux to many people in our community.

Thanks again.

Take care.

---

### Post by VirtuAlex on 2006-08-10
For Gnome I'd suggest 256MB RAM and you'd be just fine. If you have less - go for Xubuntu.

---

### Post by chasisaac on 2006-08-11
this should work like a charm (depending on ram, I would also suggest that you instal and use various LINUX distro. 

Plus if you can. . . use a laptop. Much more diffcult to install 100%. Make sure you have externl video.

Depending on time and intrest I would also design a seciton that will install a program from source code. 

Better yet, recompile the kernal. Though for most applications this is a little on the archaic side.

---

### Post by RKCole on 2006-08-11
Thanks very much.

I downloaded the latest Xubuntu version last night.  I am going to get hold of an older system to use as my test machine so that I can get a feel for Xubuntu (I'm sure it won't take long as I am very familiar with Ubuntu).  I'm looking forward to getting this project started and supporting it.  Thanks for the help.  It is greatly appreciated.

One last thing...Is there any way to somewhat automate the installation of Xubuntu as we are expecting to have a lot of systems come through.  I've seen int eh past that some distros support installation scripts or kickstart files.  Is there any way to do this with Xubuntu?  If not it's alright.  I was just curious.

Thanks and take care.

---

### Post by VirtuAlex on 2006-08-11
Looks like you're in business:
> The alternate install CD allows you to perform certain specialist installations of Xubuntu. It provides for the following situations:

    * **creating pre-configured OEM systems;**
    * **setting up automated deployments;**
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM.

---

### Post by RKCole on 2006-08-12
Looks like everything's pretty well set.  Looking forward to getting this started.

Thanks for all of the help.

---

### Post by RKCole on 2006-08-14
Sorry guys...yet another situation has come to my attention.

I'm not sure how to go about this, but what (if possible) would be the best way to update the codecs (legally) for these systems?  The systems, when they will be worked on, will not be connected to the Internet, so we would not be able to use Automatix to install such things.  Is there a quick/somewhat simple workaround?


Thanks again for all of the help.

---

### Post by VirtuAlex on 2006-08-15
I'm not sure what do you mean under "legally" but before you've hired a lawyer you can download all needed debs and what not, and install them with a script using dpkg. Refer to [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by RKCole on 2006-08-15
Thanks.  I'll look into that.

Sorry for not specifying my meaning when I said "legally".  I'm still a bit new to Linux (so this will be a really good learning experience for me), and I was not sure if certain codecs were legal to install on Linux systems because of possible proprietary issues; I just want to make sure that everything is in order before the process begins.  I apologize for my ignorance.  I'm still learning. :) and I am getting a bit better.

What I was thinking of doing was creating a CD with the necessary items (such as codecs and OpenOffice, if it is not preinstalled on Xubuntu) and then maybe trying (if I have the skill to do this) write a script which will take care fo everything.

In any case I think that I'm off to a decent start.

Thanks for all of the help and input.

---

### Post by VirtuAlex on 2006-08-15
My logic would be like this: these old computers, they probably were holding an OEM Windows on them at some point in time. As new owner of these machines theoretically you also own a legal copy of Windows because it is OEM. Since you own a legal copy of Windows this way, you may use all appropriate codecs as you please. But I'm not a lawyer.
But my political position is that all information shold be free and should belong to people.

---

### Post by RKCole on 2006-08-15
I completely agree with you about the freedom fo information.  That's one of the key reasons why I have switched to Ubuntu...I use a screen magnifier for Windows which costs around $600...and I would be nearly incapable of using my PC without that product.  When I saw how the community for Ubuntu, and Linux in general, was working toward a more accessible operating system, that opened up a whole new world for me, and I am amazed at what I can get in this OS (Ubuntu) without worrying about having to pay an extreme price for accessibility...because on my income that's next to impossible...

I do apologize if I offended in the least with the legality thing...I just want to make sure that I am doing everyting correctly to the best of my ability.

Thanks again for all of your help and guidance.

---

### Post by VirtuAlex on 2006-08-15
> **RKCole said:**
> I do apologize if I offended in the least with the legality thing...
Cmon, you didn't offend nobody. Legality of using propriatry formats on linux is an open issue and we all have to deal with it one way or another.
By the way, check out compiz some time when you'll have machine with better video card. Its magnifying feature is magnificent ;) You'll like it.

---

### Post by RKCole on 2006-08-15
I know that this is off subject, but what kind of video card would I need for Compiz?  I've heard a lot about it.

---

### Post by VirtuAlex on 2006-08-15
nvidia cards are seemingly the best supported.
See [https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl") for more information.

---

### Post by GREGMACKENZIE on 2006-08-17
Hi I was doing a little digging into this subject myself since I have an older laptop. I had DSL recommended and found PuppyLinux which are designed for machines with small resources. [http://www.puppylinux.org/user/viewpage.php?page_id=1]("http://www.puppylinux.org/user/viewpage.php?page_id=1") and [http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/") Of the two PuppyLinux looks as though it might suit me. 

Greg
:-)

> **RKCole said:**
> The typical specs for these systems are as follows:

Intel Pentium III (or Celeron):  500MHz or greater
128MB+ RAM
Typical internal components such as Intel-based integrated graphics cards (we usually don't get anything outside of Intel or ATI), HDDS, etc.

I was asked to find a distribution of Linux that would possibly work on these platforms.

---

