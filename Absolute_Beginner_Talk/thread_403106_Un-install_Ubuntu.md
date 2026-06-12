---
title: "Un-install Ubuntu"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by AnotherGoodIdea on 2007-04-06
I have some experience with Microsoft products. I also have many complaints against Microsoft and thats why I tried Ubuntu 6.06 and 6.10. Another good idea added to my growing list of good ideas.

I've found documentation to be my worst enemy in regards to Ubuntu installations. I carefully read the installation instructions and thought I understood what would happen. Installation didn't go as I expected. Ubuntu 6.06 was a very frustrating experience. Since I never got the Ethernet card setup I moved to 6.10. At the time I didn't realize just how much I didn't understand about the boot process. I did get Edgy installed and now have a dual boot system, default to XP Pro.

Dual boot wasn't what I was really looking for. I would have rather setup a new virtual machine. There is a problem with that approach also. I do believe it can be resolved but what is my time worth? I don't have 10 hours to give toward searching for why "gedit" is not asking for the password. From my hard drive installation, Edgy, I have been asked for the password in gedit.

As much as it pains me to say this, MSDN is much better at giving information I'm looking for. I say that with experience on-line and from the MSDN library installed on my hard drive.

What procedure can I follow to remove Edgy from my system? I need to get back to writing code.

Thanks

---

### Post by zvacet on 2007-04-06
All your problems can be solved.Why didn´t you came here before?I think you can delete Ubuntu by using it´s own live CD.when you came to partition step select Ubuntu partition and mark it for delete.After that you will see that partition as unlocated space.

---

### Post by confused57 on 2007-04-06
See this guide:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You might also want to burn a copy of the Super Grub Disk before trying to restore your mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Sorry it didn't work for you, maybe you can try again later on.

---

### Post by AnotherGoodIdea on 2007-04-06
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm) Good point. Since Edgy is 99% it is a valid back up to XP in an emergency. I'll leave it as is, hard drive space is not an issue.

Based on what I've read so far and started to see:
If the quality of documentation improves Microsoft is in big trouble. I'd love to see it happen. As for now, they have nothing to worry about. If you want to win a battle you need to be better than the next guy. It's not the system...its the documentation that will win the battle.

Thanks again!

---

### Post by ebozzz on 2007-04-06
> **AnotherGoodIdea said:**
> Based on what I've read so far and started to see:
If the quality of documentation improves Microsoft is in big trouble. I'd love to see it happen. As for now, they have nothing to worry about. If you want to win a battle you need to be better than the next guy. It's not the system...its the documentation that will win the battle.

No disrespect intended but I actually do not feel that documentation is as bad as you seem to think that it is. And, it is really not much different than windows in that respect. In fact it may be better because of the community support. also, the documentation that comes from Microsoft is nothing to rave over. 

My first introduction to Linux and Ubuntu was an installation that I successfully completed on an existing Windows system which created a dual-boot box. It was the easiest and fastest installation that I have ever performed. Maybe I was lucky or maybe it was Ubuntu that made my job so easy. Since that time I graduated to more complex Ubuntu installs where I manually partitioned the drives. I did have to read a little prior to feeling comfortable with that process but it was easy to find the resources that I needed.  

Check this out. I got a little bored last night so I decided to upgrade one of my machines to Feisty 7.04. After running one command in the terminal and making a few clicks, I had Feisty running smoothly with all of my data/settings retained. I felt so good after experimented with it that I decided this morning to update all of my other desktops to Feisty. The last of which is finishing up as I type this. :)        

Yes, sometimes I have had to work a little to get things going to way that I would like them to be. It certainly is rewarding to have accomplished most of the challenges that have confronted me. The information gained has been *extremely* helpful. I am doing everything that I was doing in Windows and more. The wealth of software applications that I have access to makes it possible for me to do more. I stream, watch movies, listen to CDs, burn discs, create music, edit photos, send/receive email, etc., etc......... The amazing thing is that I am able to do all of those things without much difficulty in getting the systems setup and a lot less research than I probably should have done.

---

### Post by pppetter on 2007-04-06
My guess is that you are really good at finding documentation for windows, and that this doesn't apply to ubuntu or linux. It takes a little bit of time to learn how to find the right information, and the same thing applies to windows. 

I'm sorry that ubuntu didn't live up to your expectations thou.

---

### Post by sirhalos on 2007-04-06
To remove Ubuntu from your desktop I would suggest using a GParted live CD to remove the partition or drive you have Ubuntu Linux installed onto. If you have the boot loader installed on the MBR (Master Boot Record) the easiest way I have found is using a Windows 98 floppy and typing fdisk /mbr that erases all MBR's from the hard drive.

---

### Post by ebozzz on 2007-04-06
> **sirhalos said:**
> TIf you have the boot loader installed on the MBR (Master Boot Record) the easiest way I have found is using a Windows 98 floppy and typing fdisk /mbr that erases all MBR's from the hard drive.

Wouldn't that be a problem if the existing XP Pro partition is going to be kept? :confused:

---

### Post by Lucifiel on 2007-04-06
My following comment might offend, so consider this a due warning! :D

I actually do agree that documentation for Ubuntu can be a problem because there are various guides with varying commands and some of these commands aren't really recommended because of stability and other issues. 

> For example: gksudo versus sudo 

And a couple of other examples I can't recall off-hand. 

A reason why documention for Ubuntu can be a bit messy and hard to find is well, because Ubuntu is still quite new. It was founded in 2003 and it does take some time for documentation to be developed and organised.

---

### Post by ebozzz on 2007-04-06
> **Lucifiel said:**
> My following comment might offend, so consider this a due warning! :D

I actually do agree that documentation for Ubuntu can be a problem because there are various guides with varying commands and some of these commands aren't really recommended because of stability and other issues. 

 

And a couple of other examples I can't recall off-hand. 

A reason why documention for Ubuntu can be a bit messy and hard to find is well, because Ubuntu is still quite new. It was founded in 2003 and it does take some time for documentation to be developed and organised.

Good point. What you just described can be a little confusing but I honestly have not found a lack of quality documentation for Ubuntu to be a problem. Using a combination of Ubuntu-specific books, The Official Ubuntu Docs site, Community Supported Docs and and the community itself, I have managed to find my way. How would it be different for a Windows user?

---

