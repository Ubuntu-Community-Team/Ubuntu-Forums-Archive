---
title: "Partitions, webserver and drivers oh my..."
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by Paul-Henri on 2005-10-03
Greetings all,
Firstly sorry for what is going to be a longish post but there is a bit I'd like to know and searching has just led to contradictory information or a lack of answers...
I've been dabbling with Linux for a couple of years now and, with Ubuntu, think I've found a distro I can finally settle down with and migrate (mostly) away from Windows XP.
I want to get this right from the get-go so what I'd like help with :
**1. Partition setup **: I know I will bork things up and may need to re-install every now and again (or for clean upgrades) so I want my personal information safe. Also I want to setup a webserver for web-page development and keep those pages safe. Just to complicate things I'll need to be able to access some files in both WinXP and Ubuntu. 
My thoughts on this is : /,home,www,swap partitions + a fat32 partition mutual area. This would all be on a 40Gb drive with WinXP residing on a 2nd 25Gb drive.
Can anyone suggest a better layout & space to allocate? What should I format my Linux partitions to? EXT3 I believe is the preferred format for Ubuntu.
**2. Webserver** : I'd like to have Apache, MySQL, PHP etc running so I can have a test server to design websites on. The [XAMPP]("http://www.apachefriends.org/en/index.html") package from Apache Friends looks like the easiest way to do this in one hit. The question of course is : is it?
**3. Drivers** : How do I change drivers in Ubuntu? It doesn't appear to be loading the correct drivers for my network card or sound card...
**4. Internet** : I can connect in Ubuntu (using a generic external 56k serial modem to Bigpond, an Australian ISP) but its SLOOOoooooooooow. I get less then half the download speed of a windows connection in Synaptic and it takes 10 minutes to load the Ubuntu website front page! I've tried various fixes suggested in this forum (disabling IPV6 etc) to no avail. This is using GnomePPP. This is a major stumbling block to moving to Ubuntu so a solution here is critical. It could be the modem, the ISP or the way I've set things up...
Thats the biggies for now - apologies again for the long post...
Thanks in advance :D

---

### Post by Victory on 2005-10-03
I myself an a newcomer to Linux so I can't help you with much. However I can give you some feedback about using XAMP. I've used the Windows version of XAMP and I have to say that yes it is a good webserver package. However XAMP is created for development use and not for production use, therefore it has less security features than say installing Apache, MySQL, PHP yourself. However if you follow the instructions provided for securing your server you should run fine with it.

---

### Post by Paul-Henri on 2005-10-03
Ahhh I didn't explain the webserver bit too well : I don't want a real webserver that others can access. It's only for my use so I don't have to pay for a host in order to do design work on.

---

### Post by Victory on 2005-10-03
Yes others can access the website via IP. If you're unsure I actually own my own dedicated server and can lend you some space and bandwidth. Contact me via PM if you're interested in free webhosting.

---

### Post by Paul-Henri on 2005-10-03
[QUOTE=Victory]Yes others can access the website via IP.[/QUOTE]

Hmmm best to do some security research then :)

---

### Post by Mustard on 2005-10-04
With regards to your connection issues,

1. Is your source.list using australian repositories or overseas ones?
2. Are you setup to use the correct proxy server address for Telstra, in your synaptic preferences?
3. Have you fiddled around with pppconfig much to try different protocols for connection?

I thought that you could actually set up apache as a local web server.  It certainly seems to be configured to allow that possibility.  Mind you, I've never got it to work very well.

---

### Post by Ampersand on 2005-10-04
[QUOTE=Paul-Henri]
**1. Partition setup **: I know I will bork things up and may need to re-install every now and again (or for clean upgrades) so I want my personal information safe. Also I want to setup a webserver for web-page development and keep those pages safe. Just to complicate things I'll need to be able to access some files in both WinXP and Ubuntu. 
My thoughts on this is : /,home,www,swap partitions + a fat32 partition mutual area. This would all be on a 40Gb drive with WinXP residing on a 2nd 25Gb drive.
Can anyone suggest a better layout & space to allocate? What should I format my Linux partitions to? EXT3 I believe is the preferred format for Ubuntu.
[/QUOTE]

I tend to use reiser for my linux partitions, I've not done any comparative tests personally. 

For the / directory, I've found a 7 or 8Gb partition to be plenty (for my purposes at least). The swap file should be approximately 1 1/2 times the amount of memory you have. The other partitions are up to you, depending on how much you want to put in them.

---

### Post by mvantol1 on 2008-03-11
I think Mustard is right with his last post, you should somehow be able to allow only 127.0.0.1 or a range of local pc's and denying all other accessors. If you should decide to install Apache, this could make things easier for you.

You could use these pages as a reference:

[http://www.easy-ubuntu-linux.com/apache-modules-ubuntu-configuration-2.html](http://www.easy-ubuntu-linux.com/apache-modules-ubuntu-configuration-2.html)
[http://httpd.apache.org/docs/2.0/howto/auth.html#whatotherneatstuffcanido](http://httpd.apache.org/docs/2.0/howto/auth.html#whatotherneatstuffcanido)

---

