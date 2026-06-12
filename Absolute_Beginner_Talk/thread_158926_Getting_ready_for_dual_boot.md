---
title: "Getting ready for dual boot"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by jbmalone on 2006-04-11
I am getting ready to make a dual boot system of Dapper and Fedora Core 5, and I just have a couple of quick questions.

I have already backed up all of my data and I am going to format the drive and start over.

1.  What is the best way for me create a /home directory that both distros can share?  Is this possible?

2.  How much space should I allot for each operating system? (For the installation of each operating system, assuming they are sharing a /home partition.)

3.  How do I back up my Firefox bookmarks?

4.  What order should I install the operating systems?  Dapper then Fedora?  or Fedora then Dapper?

5.  How do I check the md5s on each disc to make sure that there are no errors?

Other than that, I think that I am ready to go.  

Thanks for all of the help.

---

### Post by aysiu on 2006-04-12
[QUOTE=jbmalone]
1.  What is the best way for me create a /home directory that both distros can share?  Is this possible?[/quote] It's possible, but I would advise against it, as each distro has its own way of doing configuration files.

> 
2.  How much space should I allot for each operating system? (For the installation of each operating system, assuming they are sharing a /home partition.) At least 3 GB... maybe as much as 8 GB, depending on how many programs you're planning to install.

> 
3.  How do I back up my Firefox bookmarks? Open up Firefox and go to Bookmarks > Manage Bookmarks > File > Export

> 
4.  What order should I install the operating systems?  Dapper then Fedora?  or Fedora then Dapper? Whichever one you want in charge of the boot menu should be installed last.

> 
5.  How do I check the md5s on each disc to make sure that there are no errors? [http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

P.S. With the types of questions you're asking, I don't know if you should be installing Dapper. It's probably better if you install Breezy.

---

### Post by Sef on 2006-04-12
> 1. What is the best way for me create a /home directory that both distros can share? Is this possible?

Yes it is possible.  During the partitioning, do a manual install.  See this excellent tutorial:  [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

> 2. How much space should I allot for each operating system? (For the installation of each operating system, assuming they are sharing a /home partition.)

How big is ur disk. and what do you plan on putting on it?  If it's movies and such, then I would allocate a lot more space.

> 3. How do I back up my Firefox bookmarks?

See this page:  [https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29]("https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29")

> 4. What order should I install the operating systems? Dapper then Fedora? or Fedora then Dapper?

It's your choice.

> 5. How do I check the md5s on each disc to make sure that there are no errors?

A) Use bittorrent instead.  It automatically checks the md5sum.

B) This is assuming you have saved the iso to your desktop.   Open a terminal > cd ~/Desktop > md5sum (name of package.)  The site should have an md5sum file on it open it up and the terminal and the site's md5sum should be the same.  If not, redownload.

---

### Post by jbmalone on 2006-04-12
Thanks you guys.  I already have another computer with Breezy on it, and I have another computer that I want to do this with.  So, if things don't work, I always have a back up plan. I knew the answers to a couple of these questions but I didn't know I did it the "right" way or not. If I have anymore questions, I'll post them up.

Thanks.

---

### Post by jbmalone on 2006-04-12
I have been trying to get all of the tutorials I need together before installing FC5, to try it out, but I can't find any.  Is there a Fedora site that is as comprehensive about how to install mp3 playback, Java, Flash, DVD playback, etc.?  If anyone knows of a site, that would be awesome.

Jacob

---

### Post by mrchrisblau on 2006-04-12
Having just come from an FC5 installation to ubuntu (yay!) I can say that FC5 tutorials are few and far between (at least from what i've seen). Good luck on that.

A lot of that basic media stuff (dvd, mp3, etc) that you're talking about *i think* comes standard with the fc5 install. I know dvd does. mp3 might be a challenge, I couldnt find a 64 bit mp3 player for my fc5 install. flash can easily be installed (assuming you have a 32 bit proc) from the macromedia website. I don't know about installing java.. never tried on fc5.

---

### Post by jbmalone on 2006-04-12
Well, I did just find these websites:

[http://stanton-finley.net/fedora_core_5_installation_notes.html#Installation](http://stanton-finley.net/fedora_core_5_installation_notes.html#Installation)

[http://home.gagme.com/greg/linux/fc5-tips.php#mp3](http://home.gagme.com/greg/linux/fc5-tips.php#mp3)

And it seems to have a lot of stuff that is common for a new user.

I think honestly, the best way to find out about a lot of the stuff is to follow some installation guides that tend to cover mp3, DVD, Flash, Java, etc.

---

