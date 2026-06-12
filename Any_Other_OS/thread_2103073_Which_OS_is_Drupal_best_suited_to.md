---
title: "Which OS is Drupal best suited to"
date: 2013-01-09
forum: Any Other OS
---

### Post by tech291083 on 2013-01-09
Dear Friends,

I know the basic PHP, MySQL, HTML, CSS and JavaScript all self-taught. Now I want to learn Drupal CMS so that I can develop small sites for a very small company of my own and learn something useful in my free time. 


I have some books with me on PHP, MySQL etc. I have also purchased a couple of books on Drupal 7 as well. My worry is after having read a couple of books on Drupal 7, I am still not able to decide as to which OS of the below 3 I should install Drupal 7 in. I would also use MySQL and PHP with Drupal by default as you know.

I have the following OS with me now all of them on separate pcs.

Win 7 Home Basic 32 bit
Ubuntu 12.04 LTS 32 bit
Fedora 16 32 bit (will soon install Fedora 18 32 bit)

I do not want to learn Drupal with some ready-made software stack as it looks daunting to me namely XAMPP, 

Please guide me. Thanks a lot.

---

### Post by Cheesemill on 2013-01-09
I would go with which ever OS you are most comfortable with as you can get the same set up using any of them.

For me this would be Ubuntu Server running on a VM.
You can install Ubuntu Server and then just run one command to install the other parts of the LAMP stack (Apache, PHP and MySQL)...
```
sudo apt-get install lamp-server^
```After this you can just follow the instructions for installing your CMS and you're ready to go.
I can have a new web-server with a CMS installed up and running in under 15 minutes using Ubuntu Server.

One thing I would say is that if this is your first experience using a CMS, I would probably go for Wordpress and/or Joomla instead. Drupal has more features and is more flexible but the downside of this is that it takes longer to get results. Using a different CMS first will teach you the basics far quicker than jumping straight in with Drupal.

---

### Post by lykwydchykyn on 2013-01-09
I've installed Drupal on Debian stable, Ubuntu LTS, and Suse 10.x, and it's pretty neutral with regard to Linux distribution.

Never tried it on Windows, but IMO Apache, PHP, and MySQL are best suited to Linux.  Trivial to install without using a pre-rolled stack like XAMPP.

---

### Post by tgalati4 on 2013-01-09
Ubuntu 12.04.  You will get security updates for 5 years, which is important for a web server.  

I like tasksel for installing the LAMP stack.

Checkout [http://bitnami.org](http://bitnami.org) for installing services as "stacks".  Although I prefer installing the services natively on the operating system.

---

### Post by Version Dependency on 2013-01-10
I've used Drupal on Debian, Ubuntu LTS, and CentOS servers.  It's pretty much the same regardless of distro though.  Choose the OS you are most comfortable with.

---

### Post by tech291083 on 2013-01-12
> **Cheesemill said:**
> I would go with which ever OS you are most comfortable with as you can get the same set up using any of them.

 
I am comfotable with all of them as I have used them in the past. I am no expert but a bit better than the average user that is for sure. So I would love to try Drupal on one OS that is the easiest for me to manage. So I need other users' opinion like yourself.
 
 
 
>  
You can install Ubuntu Server and then just run one command to install the other parts of the LAMP stack (Apache, PHP and MySQL)...
```
sudo apt-get install lamp-server^
```

 
 
I already have one hard disk with Ubuntu 12.04 LTS 32 bit installed on it. Should I use this OS/distro for my Drupal install or download Ubuntu Server distro as mentioned here on this page?
 
 
[http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)
 
it says > Ubuntu Server 12.10 64-bit version under the download button and I am not sure if there is a 32-bit version available. I am ok with this 64-bit version if required for Drupal. It is not an issue with me.
 
One more thing is that I generally use KTorrent to download distros using torrents due to the slow internet connection that I have. So I searched and found this page for torrents, but I can't see a torrent for Ubuntu 12.10 Server 64 bit distro for a PC (Intel x86) computer, if I understand the naming of the torrent correctly. I am using Intel Dual Core E5700 cpu, although it is capable of running 64 bit applications, I want to download the 64 bit distro only. This will the 1st time that I am gonna use a 64 bit Linux distro of any kind.
 
> 
[ubuntu-12.10-desktop-amd64.iso.torrent]("http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-amd64.iso.torrent")
[ubuntu-12.10-desktop-i386.iso.torrent]("http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.iso.torrent")
[ubuntu-12.10-server-amd64.iso.torrent]("http://releases.ubuntu.com/12.10/ubuntu-12.10-server-amd64.iso.torrent")
[ubuntu-12.10-server-i386.iso.torrent]("http://releases.ubuntu.com/12.10/ubuntu-12.10-server-i386.iso.torrent")

 
 
 
> 
After this you can just follow the instructions for installing your CMS and you're ready to go.

 
Ok, but can you please suggest me some good links to tutorials on the net so that it easy a bit easier for me to do?
 
> 
One thing I would say is that if this is your first experience using a CMS, I would probably go for Wordpress and/or Joomla instead. Drupal has more features and is more flexible but the downside of this is that it takes longer to get results. Using a different CMS first will teach you the basics far quicker than jumping straight in with Drupal.
 
I agree with you 100%, but Drupal is more popular these days if I am correct. I need to learn to use it any way for future use. 
 
Thanks a lot for the response you have given to me. Please feel free to suggest whatever you find is appropriate for me.

---

### Post by tech291083 on 2013-01-12
> **lykwydchykyn said:**
> 
Never tried it on Windows, but IMO Apache, PHP, and MySQL are best suited to Linux. Trivial to install without using a pre-rolled stack like XAMPP.
 
Yes, I am of the same opinion open source/Linux is best when it comes to other open source technologies like PHP and MySQL. Thanks.

---

### Post by tech291083 on 2013-01-12
Ok,
 
I have found this page, which lists all the editions for the Ubuntu 12.10 OS. As I scroll down this page, I see that there is no link for a 64 bit edition compatible with Intel PC (Mine is Intel Dual Core E5700 cpu, capable of running 64 bit applications), so I guess I will have to use the 32 bit edition only. Thanks.
 
 
> [ubuntu-12.10-server-i386.iso]("http://releases.ubuntu.com/12.10/ubuntu-12.10-server-i386.iso") 17-Oct-2012 17:29 672M Server install image for PC (Intel x86) computers (standard download)
[ubuntu-12.10-server-i386.iso.torrent]("http://releases.ubuntu.com/12.10/ubuntu-12.10-server-i386.iso.torrent") 18-Oct-2012 14:27 27K Server install image for PC (Intel x86) computers ([BitTorrent]("https://help.ubuntu.com/community/BitTorrent") download)
[ubuntu-12.10-server-i386.iso.zsync]("http://releases.ubuntu.com/12.10/ubuntu-12.10-server-i386.iso.zsync") 18-Oct-2012 14:27 1.3M Server install image for PC (Intel x86) computers ([zsync]("http://zsync.moria.org.uk/") metafile)
[ubuntu-12.10-server-i386.jigdo]("http://releases.ubuntu.com/12.10/ubuntu-12.10-server-i386.jigdo") 18-Oct-2012 14:27 118K Server install image for PC (Intel x86) computers ([jigdo]("http://atterer.org/jigdo/") download)
[ubuntu-12.10-server-i386.list]("http://releases.ubuntu.com/12.10/ubuntu-12.10-server-i386.list") 17-Oct-2012 17:29 83K Server install image for PC (Intel x86) computers (file listing)
[ubuntu-12.10-server-i386.metalink]("http://releases.ubuntu.com/12.10/ubuntu-12.10-server-i386.metalink") 18-Oct-2012 14:43 31K Ubuntu 12.10 (Quantal Quetzal)
[ubuntu-12.10-server-i386.template]("http://releases.ubuntu.com/12.10/ubuntu-12.10-server-i386.template") 17-Oct-2012 17:29 51M Server install image for PC (Intel x86) computers ([jigdo]("http://atterer.org/jigdo/") template)
[ubuntu-12.10-wubi-amd64.manifest]("http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.manifest") 17-Oct-2012 09:34 44K Ubuntu 12.10 (Quantal Quetzal)
[ubuntu-12.10-wubi-amd64.tar.xz]("http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz") 17-Oct-2012 09:58 536M Ubuntu 12.10 (Quantal Quetzal)


---

### Post by tech291083 on 2013-01-12
[http://releases.ubuntu.com/12.10/ ]("http://releases.ubuntu.com/12.10/")

---

### Post by Cheesemill on 2013-01-12
> **tech291083 said:**
> So I would love to try Drupal on one OS that is the easiest for me to manage. So I need other users' opinion like yourself.
I would suggest Ubuntu Server, there are plenty of good tutorials around that take you through the steps needed to install LAMP and then Drupal.
 
 > I already have one hard disk with Ubuntu 12.04 LTS 32 bit installed on it. Should I use this OS/distro for my Drupal install or download Ubuntu Server distro as mentioned here on this page?I do all of my learning and development on VM's as this method has several advantages. As Ubuntu Server is command line only and doesn't have a GUI, by running it in a VM you can be looking at guides and forums at the same time your server is running. You can also take regular snapshots of your server so that if you break something you can easily roll back to an earlier version. By having your server as a VM you are keeping it separate from the rest of you system. If you want to reinstall you can without affecting your day to day OS. Also you can reinstall your main OS without losing your server, as VM's are just a couple of files on your disk you can copy them and back them up just like any other file.
 
 
> it says  under the download button and I am not sure if there is a 32-bit version available. I am ok with this 64-bit version if required for Drupal. It is not an issue with me.
 
One more thing is that I generally use KTorrent to download distros using torrents due to the slow internet connection that I have. So I searched and found this page for torrents, but I can't see a torrent for Ubuntu 12.10 Server 64 bit distro. I am using Intel Dual Core  E5700 cpu, although it is capable of running 64 bit applications, I want to download the 64 bit distro only.I would recommend using the 64-bit version of Ubuntu Server 12.04 instead.
12.04 is an [LTS]("https://wiki.ubuntu.com/LTS") (Long Term Support) release, meaning it is more stable than 12.10 as well 
 as having a much longer support period (until 2017). LTS releases are recommended for servers unless you *have* to have the latest versions of software (you don't).

Torrents are available for all Ubuntu releases on the official site...
[http://releases.ubuntu.com](http://releases.ubuntu.com)
[http://releases.ubuntu.com/precise/ubuntu-12.04.1-server-amd64.iso.torrent](http://releases.ubuntu.com/precise/ubuntu-12.04.1-server-amd64.iso.torrent)
 
> I agree with you 100%, but Drupal is more popular these days if I am correct. I need to learn to use it any way for future use.
At the end of the day it's your choice.
I wouldn't say that Drupal is more popular, it just allows you to create more complicated sites. I use Drupal on projects only when it is the best solution, but if a site can be created with Joomla or Wordpress I will use one of those instead, as it will be much quicker to develop as well as having simpler code.

Just play around with Joomla for a couple of weeks first and then move onto Drupal if you want to. With Drupal it will take a while to get your first site running, but you can be up and running with other CMS's in a couple of hours. You will learn far quicker by starting with the basics instead of jumping straight in at the deep end.

---

### Post by tech291083 on 2013-01-12
> **Cheesemill said:**
>  
 
I would recommend using the 64-bit version of Ubuntu Server 12.04 instead.
12.04 is an [LTS]("https://wiki.ubuntu.com/LTS") (Long Term Support) release, meaning it is more stable than 12.10 as well 
as having a much longer support period (until 2017). LTS releases are recommended for servers unless you *have* to have the latest versions of software (you don't).

 
I agree with you and I would love to use the 64-bit version of Ubuntu Server 12.04, but as I can seen on the page below, there is no 64-bit version available for an Intel cpu. All of my pcs have Intel processors and no AMD at all.
 
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)
 
Thanks a lot for the woderful reply you have given to me, appreciated.

---

### Post by Cheesemill on 2013-01-12
The amd64 version is for AMD and Intel CPU's.

It's named this way because AMD first developed the instruction set that all modern 64-bit CPU's now use.

amd64 is the name of an architecture, it has nothing to do with who makes your CPU.

---

### Post by tech291083 on 2013-01-13
> **Cheesemill said:**
> The amd64 version is for AMD and Intel CPU's.

It's named this way because AMD first developed the instruction set that all modern 64-bit CPU's now use.

amd64 is the name of an architecture, it has nothing to do with who makes your CPU.

Thanks a lot for clarifying the whole idea behind the naming of a link for 64-bit version. I vaguely remember a friend of mine telling me the same thing as you have. But I never got to download a 64-bit version thinking it might trouble my the then pc with only 2 GB DDR3 RAM, but now I have 4 GB DDR3 RAM. So despite the slow connection I am going to download 64-bit versions of both servers ie Ubuntu 12.04 LTS (for long term support) and 12.10 for the latest features. 

Thanks a lot for your help, appreciated.

---

