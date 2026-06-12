---
title: "OpenSUSE 64 bit"
date: 2012-10-13
forum: Any Other OS
---

### Post by Welly Wu on 2012-10-13
I downloaded OpenSUSE 12.2 64 bit Live GNOME ISO file and I burned it onto a blank CD-R disc. I rebooted my System76 Lemur Ultra Thin (lemu4) notebook PC and I booted off the disc. OpenSUSE 12.2 64 bit is compatible with my System76 Lemur Ultra Thin (lemu4). Everything works right out the box. There are no additional device drivers that I need to install to make my PC hardware work properly.

OpenSUSE is vastly different from Ubuntu. It is designed primarily for system administrators that require up to date but not bleeding edge software packages that prefer the YaST GUI to configure and setup their systems. Ubuntu still relies heavily on the terminal to do most of the heavy lifting especially when it comes to installing and configuring security tools. There are no paid software apps in the main OpenSUSE software repositories which is another major difference. You get your choice of GNOME or KDE when you download the DVD ISO and you can easily setup full-disk encryption using the YaST installation program. VPN protocols such as OpenVPN, CISCO IPSec, and PPTP are fully supported right out of the box. System hardening is done through YaST and it is granular although there are pre-configured settings based upon your organization's needs or if you are a single home workstation user.

[LEFT]OpenSUSE 12.2 64 bit is very nice. YaST alone makes it worthwhile if you are a systems administrator or if you like to tinker with your GNU/Linux distribution without having to resort to the terminal too often to get the job done. OpenSUSE 12.2 64 bit is considered to be the experimental and testing version of SUSE Linux Enterprise Desktop which you must purchase in order to install and update annually.

I chose to stick with Ubuntu because System76 offers official help and technical support for Ubuntu exclusively. I have a two year warranty and support contract with System76 for my Lemur Ultra Thin (lemu4) notebook PC. Ubuntu 12.10 64 bit is going to be released next Thursday on October 18th, 2012 so it pays for me to wait a couple of more days and to keep running Software Updater in the meantime. I like paid apps a lot and they extend the functionality and add features that are useful to me. In my mind, Ubuntu is certainly one of the largest GNU/Linux distributions in terms of the number of users and it offers the Ubuntu Software Center, Ubuntu One, Ubuntu Unity and it also has the largest software repository available. You can add PPAs quite easily and it is focused on the desktop user experience. Ubuntu is a large community and most of its users are quite friendly and they are willing to offer help and support right away.

However, OpenSUSE 64 bit would be my second choice if I had to use another GNU/Linux distribution. I could feel very comfortable using it and be able to focus on my work or task at hand without too many problems by switching to OpenSUSE 64 bit. I would recommend it to experienced GNU/Linux users looking for more control over their PCs and for those that are comfortable using the RPM system. For me, the Debian system is more familiar and I like using APT.

Highly recommended!
[/LEFT]

---

### Post by KiwiNZ on 2012-10-13
You seemed to have recommended so many distros then deleted them.

---

### Post by Welly Wu on 2012-10-13
I did not install OpenSUSE 64 bit. I just booted off the Live GNOME CD. The same is true for PC-BSD 9.1 RC2.

---

### Post by Rukiri on 2012-10-13
I would still consider opensuse for newbies mainly because it won't feel alien to former windows users and can pick it uip quite quickly.  I have no experience with yast so I am not reliable when it comes to it but yast really shines when it's used for a server environment. 

Sadly if the user is after control they're better off with a distro like Arch or Gentoo.  
I would probably recommend cinnarch ones some of the kinks are worked out as it does look promising.

---

### Post by inobe on 2012-10-13
This is a case of preference!

What if someone had more than one preference?

---

### Post by Welly Wu on 2012-10-14
After testing the OpenSUSE 12.2 64 bit Live GNOME CD-R, I decided to get rid of Ubuntu 12.10 64 bit Release Candidate and I installed OpenSUSE 12.2 64 bit bare metal on my System76 Lemur Ultra (lemu4). So far, almost everything works except for the SD Card slot. I am still learning how to add my Canon Pixma MX870 printer using the Internet Printing Protocol on my 802.11 G Wi-Fi private network, but everything else pretty much works right out of the box with no problems. GNOME 3.4.2.1 and GNOME Shell 3.4.2 do have a known bug with the screen saver lock function: entering the user's credentials does not unlock the screen saver and return the user back to his desktop. I disabled the locking screen saver function and I set it to automatically dim and eventually blank my screen after 5 minutes which is fine.

YaST is pretty thorough and it is a bit daunting for new OpenSUSE users because there are so many buttons and settings to wade through. It is certainly one of the most comprehensive systems administration tools that I have encountered in GNU/Linux. It will take me some time to learn how to use it properly.

OpenSUSE 12.2 64 bit ships with Linux kernel 3.4.11-2.16-desktop. I find this to be better than Ubuntu 12.04.1 64 bit LTS that ships with Linux kernel 3.2.0-31 generic because this older version locks up my System76 Lemur Ultra (lemu4) notebook PC randomly especially when more than half a dozen software applications are currently running. I found that upgrading to Linux kernel 3.3.6-030306 solved this problem, but I was no longer receiving any more updates to the Linux kernel by using this workaround solution so I was not impressed with this partial fix. Upgrading to Ubuntu 12.10 64 bit means that Linux kernel 3.5.0 shipped with it and kernel.org indicates that the Linux kernel 3.5.y is only expected to receive one more minor update and it will reach end of life status pretty soon. This was another bugaboo that presented an unacceptable solution to me.

OpenSUSE 12.2 64 bit was released on September 5th, 2012. It is not a cutting edge GNU/Linux distribution. It includes modern software packages and their respective versions, but it focuses on stability and a smooth user experience rather than including cutting or bleeding edge software. This was one of the problems that I experienced with Ubuntu 12.10 64 bit Release Candidate. It was a cutting edge distribution in which software randomly crashed frequently. The same is true with Ubuntu 12.04.1 64 bit LTS. Again, software crashed randomly. It distracted me from focusing on my digital work flow. Sometimes, crashes to Compiz meant that I had an unusable desktop environment as a result. I think that Canonical is so focused on making a profit off of Ubuntu that they are losing focus on the quality assurance and overall polish for Ubuntu in general. I also disliked the Ubuntu Unity desktop environment quite a bit. It is not highly configurable without adding PPAs and more software packages. I find it to be a rather inelegant solution that limits users' freedoms by constraining their digital work flows as that was my experience. I rarely used it at all.

GNOME 3.4.2 and GNOME Shell 3.4.2.1 are not my favorite desktop environment versions. I find it annoying to click between the Windows and Applications buttons to juggle my digital work flow. However, it is usable for the next several months and I can learn to live with it. I find GNOME to be more stable and usable than K Desktop Environment. Fewer stuff breaks or crashes in my experience. I know that this may not be everybody's experience.

You may be wondering why I switched from Ubuntu 12.10 64 bit Release Candidate to OpenSUSE 12.2 64 bit today. Part of the reason was it was a whimsical decision to try something different. The other part is more serious. I see the future direction in which Canonical is taking their Ubuntu brand and I do not agree with some of their choices. They are trying to market Ubuntu as a brand that can compete with Microsoft Windows and Apple Macintosh OS X to gain more market share and users worldwide. It is quickly becoming a commercial platform to generate additional revenues and profits for Canonical. I found out that I have to add and manage private keys to install and use paid software packages. I did not like any of these changes afoot, but I kept quiet for the most part. Ubuntu is still near and dear to my heart, but they are not my first choice for GNU/Linux purists especially for intermediate to advanced users like myself that are looking for more learning opportunities and challenges. The problem with going down the paid software and apps route is that you wind up with vendor lock in. I bought the Fluendo Multimedia Codec and DVD-Video player for Ubuntu and I can not use it in OpenSUSE 12.2 64 bit because I do not have access to my private key. I encountered a similar problem with PC hardware and software applications when I switched from Microsoft Windows 7 64 bit Ultimate Edition Service Pack 1 to Ubuntu GNU/Linux. I had to give away lots of expensive PC hardware that was designed for Windows 7 to my best friend and I could not easily convert my massive Apple iTunes library to FLAC format quickly enough. I learned my lessons the hard way. I am in search for a pure GNU/Linux experience that adheres closely to FLOSS.

I may return to Ubuntu in the future. It depends on the situation. For now, I think that I will learn how to use OpenSUSE 12.2 64 bit.

---

### Post by KiwiNZ on 2012-10-14
Instead of bouncing from one distro to another and giving away hardware(something that baffles me with some work I can't think of anything I have not been able to do something with) you should buy a cheap PC and use that as a test platform.

I also have my doubts if Linux(any Distro) is for you and you are better suited staying with Windows.

---

### Post by exploder on 2012-10-14
Ubuntu 12.10 does have some commercialism associated with it but they did provide an off switch for the Amazon shopping lens. I do not feel that going with a totally open source system is realistic, it takes too much away from having a good experience with multimedia playback. The length of support Ubuntu 12.04 offers is superior to what OpenSuse offers too.

Having paid applications available should I want them is also a plus for me. Canonical is a business and they are searching for ways to be profitable, right now the shopping lens is controversial but it is new and may develop into something very useful in the future. Ubuntu has been building it's own identity since the introduction of Unity, ideas take time to evolve and Unity has shown real promise. 

OpenSuse has always been hit and miss for me, one release will work very well and the next will not even boot up on my hardware. Ubuntu has had many releases that will not run well on my hardware too but recently they seem to have placed more emphases on quality. Ubuntu 12.04 runs well on all my NVidea based systems, 12.10 is working perfectly on my laptop with ATI discrete graphics. I can get 12.04 to run on the laptop but 12.10 is noticeably better where the graphics are concerned.

My top 3 distributions are Linux Mint, PCLinuxOS and Ubuntu. I have had very serious problems with my eyes and have had numerous eye surgeries as a result. Ubuntu with Unity just happens to be the easiest distro to see with it's defaults. My sight is alright right now but should something happen I want to be able to have some kind of chance at using my computers. Staying with a particular distribution has advantages when it comes to maintaining my systems and I have quite a few computers around here. 

PCLinuxOS KDE is my favorite rolling release period. PCLinuxOS in my opinion always has the best hardware support of any distribution I have ever used. When I had my last eye surgery I just could not see much of the text in KDE... Linux Mint was fairly manageable with poor vision but Ubuntu with Unity was the easiest for me at the time. I have my vision back now but I am probably looking at another operation next year to remove scar tissue from my retina.

OpenSuse does have a certain professionalism about it and the tools are good but PCLinuxOS offers better, easier tools in my opinion and the mylivecd feature is unbeatable. I like Linux Mint because Clem put the time and effort into Cinnamon because the community wanted to stay with a traditional desktop. Mint is hassle free too as far as codecs go and is a real time saver when it comes to setting up a system quickly.

After running Linux for so many years I have grown tired of going from one distro to another. Every new release of any distro always seems to have some sort of appeal to it but life is so much easier staying with the ones I know are going to work without spending all my time installing a new OS. Rolling releases and LTS releases are so much easier to deal with.

---

### Post by Welly Wu on 2012-10-14
The thing is that I get real work done better using Linux rather than Windows now. I spend less time waiting and there are fewer interruptions or distractions in Linux. I don't have a constant barrage of advertisements targeting me when I use the desktop in Linux either. Finally, Ubuntu and OpenSUSE are free to use so that helps me a lot. As it stands right now, it is going to be a real stretch for me to afford Windows 8 Pro 64 bit and Office 2013 Home Premium subscription. I don't like using out of date operating systems or software applications. That does not mean that I like cutting edge or bleeding edge software either. I think that OpenSUSE strikes the right balance better than Ubuntu.

Ubuntu is still a good GNU/Linux distribution. I may return to it in the future, but I wanted to try a different one for a while to see how I like it.

I was thinking about installing Red Hat Fedora 17 64 bit, but my experience is that it has poor support for proprietary hardware devices, device drivers, and firmware. So, I stayed away from Fedora.

I may decide to get a netbook as my PC for testing different operating systems and software applications. However, this is going to be difficult for me to afford in the next few months as I have bills to pay.

OpenSUSE 12.2 64 bit is pretty decent. So far, I have not gotten anything to crash or break yet. Most of the operating system and software packages work properly without any major problems.

I can tell you that OpenSUSE is slightly more difficult to learn how to use especially YaST. It requires more research and reading to learn how to get things to work which is a challenge for me, but it's okay.

I can't say that I recommend it to others yet. I am going to need more time evaluating it before I make my final decision.

---

### Post by KiwiNZ on 2012-10-14
If you cannot afford Windows 8 then don't buy it. The Windows 8 backend is almost the same as Windows 7 so in essence you are buying just a new front end with Win 8. An upgrade to Office 2013 is only required if you need the new features to do the tasks you need to do, if you are don't then you are purely paying for dormant features.

---

### Post by Welly Wu on 2012-10-14
I stopped using Microsoft Windows and Office. In fact, I stopped using Microsoft products and services altogether.

I added the GNOME 3.6 repository for OpenSUSE 12.2 64 bit andI am installing it now. I plan to install K Desktop Environment version 4.8.4.

I think that I need to reboot my System76 PC soon.

---

### Post by inobe on 2012-10-14
I have several systems, each with one or more Linux operating systems, one of which has Wheezy, another has Ubuntu, strictly testing purposes only.

The system i'm on now runs OpenSuSe 12.2, No testing going on here.

Ultimately, understanding why folks play with different Linux versions, It's all fun, never confuse one being better due to an individuals comments and suggestions and opinions.

Find what you like and use it, especially if it works the way you like it to, However if you follow opinions,
OpenSuSE is by far one of the smartest, sophisticated  distributions available, A wide range of customization features, easy settings up to expert settings located in YAST.

It really suits an export and the average novice, it's just the matter of navigating to the particular settings that are needed, and becoming familiar with them on how they work.

YAST beats editing text files, most distributions cannot compete when it comes to this.

I would stick with it, a fine polished masterpiece, Unless of course my opinion is meaningless!

Personally, I'm stuck between Wheezy & OpenSuSe:p

---

### Post by Welly Wu on 2012-10-14
OpenSUSE 12.2 64 bit is extremely stable and it is extremely fast and it has very high performance. I made some mistakes earlier which resulted in the fact that I had to re-install OpenSUSE 12.2 64 bit from scratch, but this second time today it took only 30 minutes to install, configure, setup, and use everything right out of the box again. I'm back to where I was earlier today except I don't have any problems. I have tried Ubuntu, Red Hat Fedora, and now OpenSUSE and I have to say that OpenSUSE is by far the most stable and the highest performer thus far. If you stick with the default software repositories, then nothing is going to break or crash.

I installed K Desktop Environment 4.8.4. It's quite nice and it's stable. I have no graphics corruption issues unlike in Ubuntu 12.10 64 bit Release Candidate with KDE 4.9.2.

I have not figured out where or how to install the device drivers for my SD card slot yet. I am going to do more research, but something tells me that I need to download the latest System76 device driver .DEB file and install it by hand. I am not exactly sure how to do that right now so I will leave this important task to another day. I also have not figured out how to add my Canon Pixma MX870 printer since it is connected on my Verizon FiOS 802.11 G Wi-Fi network at 192.168.1.7. I downloaded and I installed the proprietary Canon printer drivers, but I am having a problem adding the network printer. It's telling me that FirewallD is not started and I need to allow mdns, ipp, ipp-client, and samba-client. I am not sure how to do that. If someone can help, then I would appreciate it greatly.

---

### Post by Welly Wu on 2012-10-16
It seems that a new friend of mine on OpenSUSE forums is going to compile a Linux kernel module for my RealTek Semiconductor SD card reader and he will package it as a RPM file for me to download and install today or tomorrow. If it works, then I can test it with a SDHC 2 GB card to make sure it works. If all goes well, then I plan to purchase a SanDisk Extreme 128 GB SDXC UHS-1 card from Amazon early next week.

As for the network printer issue, I have a Canon Pixma MX870 connected to my Verizon FiOS Internet 802.11 G Wi-Fi private network and I can't get it to print documents. It keeps saying that the printer is unreachable.

I added the OpenSUSE Tumbleweed software repository. I updated and upgraded my entire OS and everything is super ultra stable and fast. It made a huge difference!

OpenSUSE Tumbleweed is much more stable, reliable, and faster than Ubuntu 12.04.1 64 bit LTS or 12.10 64 bit on my System76 Lemur Ultra Thin (lemu4) notebook PC. It is without any reservations or doubts in my opinion and experience. It's a terrific GNU/Linux distribution and I am glad that I made the switch.

---

### Post by Welly Wu on 2012-10-16
I got my Canon Pixma MX870 printer to work. It prints documents now. I simply had to put in the IP address and click detect more in YaST after I installed the Canon printer drivers for OpenSUSE 64 bit Tumbleweed.

Now, I am hoping that my new friend will help me to make my SD card reader work. I really want that 128 GB SDXC UHS-1 card.

---

### Post by Welly Wu on 2012-10-16
I got my SD card reader to work. I tested it with a Pro Max 2 GB SDHC card and it works.

My System76 Lemur Ultra Thin (lemu4) notebook PC is now fully compatible with OpenSuSE 12.2 64 bit with the Tumbleweed software repository.

I plan to get a SanDisk Extreme 128 GB SDXC UHS-1 card from Amazon early next week. I can't wait until I get it at home.

OpenSuSE 64 bit is wonderful. YaST alone makes it worth the switch from Ubuntu. It's unbelievably fast and the performance is just incredible! OpenSuSE is much much faster and much more stable and reliable than Ubuntu. It's a big difference.

I think that I will stick with OpenSuSE for a couple of months to see how I like it further. If I like it in a month from today, then I will stick with it.

---

### Post by gvirtue on 2012-10-18
Great work finding out how to get all of those bits of hardware working on a new distro. I have the same computer you do (Lemur Ultra) and I find it fantastic. 

Playing with different distros is a lot of fun. I have not used SuSE in quite some time, but I do remember it being one of the better distros out there. 

These days I prefer to do my distro hopping via VirtualBox. Not having to repartition and worry about losing data is just magical. It reminds me of the old days of VirtualPC on PowerPC Macs. Except that it isn't slower than frozen molasses. 

Every once in a while I toy with the idea of replacing Ubuntu with something more cutting edge like Fedora or Arch, but I quickly find myself going back to Ubuntu time and again.

I have always been a big fan of traditional Unix operating systems like FreeBSD and Solaris, but the lack of support for the Intel 6235 wifi chip in the Lemur rules them out completely. I know that someone is working on it in the FreeBSD camp but it looks like he has been at it for a bit with no progress updates. If and when that changes I will look into putting one on the hard drive next to Ubuntu.

The real reason I keep going back to Ubuntu and ultimately have stayed with it is because of the Mac principle. It just works. Sure Unity was a bit of a challenge at first but I have grown to enjoy it. I also have come to know and rely on the fact that Ubuntu tends not to break itself with updates and offers a tremendous amount of peace of mind for me with the LTS offering.

I really like the fact that with UbuntuOne I can be certain that I will not lose my latest manuscript, and that I will be able to purchase whatever weird Engima album I fancy next without having ten million different places to login.

In any case, I hope you have fun with OpenSuSE and I really hope you are writing down all of the steps you are taking to get your hardware working so others can experiment along with you.

Grant

---

### Post by AlexDudko on 2012-10-19
> **Welly Wu said:**
> 

OpenSuSE 64 bit is wonderful. YaST alone makes it worth the switch from Ubuntu. It's unbelievably fast and the performance is just incredible! OpenSuSE is much much faster and much more stable and reliable than Ubuntu. It's a big difference.


Could you give some examples? Point at some Ubuntu issues which make it less reliable and stable than OpenSUSE, please.
I've used both OpenSUSE and SLED (SUSE Linux Enterprise Desktop - a commercial distribution) and I prefer Ubuntu. The latter one (SLED) is a complete crap. Neither my mic nor webcam didn't work out of the box though the proper drivers were installed, I had to remove them and compile from source. There were also some issues with LibreOffice (disappearing Base menus, some special symbols not displayed, rightclick on selected text causing Writer's crash on some old files and many others) which are not present in Ubuntu. SELinux (I prefer it to Apparmor) is not implemented so that it could be usable.
YaST is a good application but it's rather a Windows way of doing administration tasks, for those who're used to standard Linux tools it's sometimes puzzling.

---

### Post by Welly Wu on 2012-10-20
Compiz crashes frequently in Ubuntu 12.04.1 64 bit LTS and 12.10 64 bit. Random software packages crash frequently as well. In OpenSuSE 64 bit Tumbleweed, nothing crashes or breaks. This is a apples to pears comparison here.

OpenSuSE 64 bit Tumbleweed is the most stable and reliable GNU/Linux distribution that I have ever tried on any PC thus far. It is also the fastest performing one that I have ever tried on any PC.

I am done with Ubuntu. I don't like the commercialized environment and I don't like the future direction that it's heading.

I plan to stick with OpenSuSE 64 bit Tumbleweed until March 2013. If everything goes according to plan, OpenSuSE 12.3 64 bit will be released at that time and I will be automatically upgraded to the latest stable release version at that time. When that day comes to pass, I will re-evaluate OpenSuSE 64 bit Tumbleweed and K Desktop Environment 4.9.x to see if it is meeting my future needs or not.

In the meantime, I have to configure SAMBA server and my SuSEfirewall2 to enable file sharing on my home network. Once that is done, I am done. There will be nothing left for me to do as I will have achieved a similar configuration with OpenSuSE 64 bit Tumbleweed compared to my previous Ubuntu 12.04.1 64 bit LTS installation. The key differences are stability, reliability, speed, and performance in favor of OpenSuSE.

OpenSuSE 64 bit Tumbleweed is different from SuSE Linux Enterprise Desktop or Server. I can't speak to the latter as I have no experience using the commercial version. Try OpenSuSE 12.2 64 bit in a Oracle VM Virtualbox guest virtual machine. I think that you will come to respect its power and performance along with praising its stability and reliability.

---

### Post by AlexDudko on 2012-10-20
> **Welly Wu said:**
> Compiz crashes frequently in Ubuntu 12.04.1 64 bit LTS and 12.10 64 bit. Random software packages crash frequently as well. In OpenSuSE 64 bit Tumbleweed, nothing crashes or breaks. This is a apples to pears comparison here.

OpenSuSE 64 bit Tumbleweed is the most stable and reliable GNU/Linux distribution that I have ever tried on any PC thus far. It is also the fastest performing one that I have ever tried on any PC.

I am done with Ubuntu. I don't like the commercialized environment and I don't like the future direction that it's heading.

I plan to stick with OpenSuSE 64 bit Tumbleweed until March 2013. If everything goes according to plan, OpenSuSE 12.3 64 bit will be released at that time and I will be automatically upgraded to the latest stable release version at that time. When that day comes to pass, I will re-evaluate OpenSuSE 64 bit Tumbleweed and K Desktop Environment 4.9.x to see if it is meeting my future needs or not.

In the meantime, I have to configure SAMBA server and my SuSEfirewall2 to enable file sharing on my home network. Once that is done, I am done. There will be nothing left for me to do as I will have achieved a similar configuration with OpenSuSE 64 bit Tumbleweed compared to my previous Ubuntu 12.04.1 64 bit LTS installation. The key differences are stability, reliability, speed, and performance in favor of OpenSuSE.

OpenSuSE 64 bit Tumbleweed is different from SuSE Linux Enterprise Desktop or Server. I can't speak to the latter as I have no experience using the commercial version. Try OpenSuSE 12.2 64 bit in a Oracle VM Virtualbox guest virtual machine. I think that you will come to respect its power and performance along with praising its stability and reliability.

Stop, stop, stop!!! You're NOT selling SUSE products, are you?
You write about OpenSUSE performance in every post.
If you could read and understand the text you'd never suggest me to try OpenSUSE in Virtualbox because you'd know from my previous post that I've got some experience of using both OpenSUSE and SLED and not in Virtualbox.
The majority of bugs happen systematically and you can provide enough information how to reproduce them. But if there are frequent crashes of random applications than maybe you are doing something wrong?

---

### Post by mips on 2012-10-20
> **AlexDudko said:**
> Stop, stop, stop!!! You're NOT selling SUSE products, are you?


He's got a new 'best' distro every two weeks and it's always better in some way, never backed up with any facts or subjectivity. Take it with a pinch of salt or just ignore.

---

### Post by Welly Wu on 2012-10-20
I don't know how to close this thread, but I am asking the administrators or the moderators to close this thread and lock it for me. Thank you.

---

### Post by sffvba[e0rt on 2012-10-20
*Thread **closed**.*


404

---

