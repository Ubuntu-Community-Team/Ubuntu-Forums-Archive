---
title: "gdesklets problems"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-07-30
I like the gdekslets when they work, but some don't seem to.  

One of them is the weather desklet.  I have tried 4-5 different ones (from the vanilla install of gdesklets) and none of them can pull the info.  All of them have a part of the config that lists city and country.  So I enter my city and "US" or "USA" and it doesn't pull anything.  I can't find any instructions or anything else that can tell me what to do.

Also, their website at [www.gdesklets.org](www.gdesklets.org) seems to have been down for the last week or so.  

Does anyone have any information about a good support site, or does someone HERE use these things and know about configuring them?  I really like them and want to use them, but they don't seem to want to work.

Also, the RSS reader one won't pull any RSS feeds that I put in it.

---

### Post by flatwombat on 2007-07-30
Try this link: [http://gdesklets.zencomputer.ca/](http://gdesklets.zencomputer.ca/)  The one I'm using and that works is Goodweather.  What's happening on the other ones you've tried is that they were tuned to Yahoo Weather, which changed it's configuration and they haven't kept up.  

Here's a link for the info to set up Goodweather: [http://www.linspire.com/lindows_products_details.php?product_id=12909](http://www.linspire.com/lindows_products_details.php?product_id=12909)

---

### Post by kc5hwb on 2007-07-30
Thanks I will try that one.  I heard that the yahoo widget people wouldn't allow non-windows OS's to use them.  Apparently they are nazis or something  ;)

How about the RSS one, any ideas there?

---

### Post by kc5hwb on 2007-07-30
Also, I just downloaded this Good Weather desklet... how do I install it?  I use the Install Package option in the gdesklets app and it gives an error, saying the package is invalid.

---

### Post by flatwombat on 2007-07-30
Invalid?  I just installed it a few days ago on another distro and it's working fine (Mint).  Let's see if that one is the same as I've been using.... Yes, it's the first one; Goodweather.tar.gz ; simply download it into /home/username and then start up Gdesklets and choose File > Install Package and it should be fine.

---

### Post by erfahren on 2007-07-30
or you should just be able to open the gDesklets Manager and grag the GoodWeather.tar.gz into its little window.

There is another weather desklet I've just recently found on the internet. he used the Yahoo sensor but updated it. [http://www.technetra.com/writings/archive/2007/04/20/updated-weather-gdesklets](http://www.technetra.com/writings/archive/2007/04/20/updated-weather-gdesklets)

his you can just unpack the contents into your ~/.gdesklets directory.

---

### Post by kc5hwb on 2007-07-31
> **flatwombat said:**
> Invalid?  I just installed it a few days ago on another distro and it's working fine (Mint).  Let's see if that one is the same as I've been using.... Yes, it's the first one; Goodweather.tar.gz ; simply download it into /home/username and then start up Gdesklets and choose File > Install Package and it should be fine.

This worked fine.  I was trying to install after unzipping the tar.gz file.  I just loaded the zipped file and it installed fine.





How about the one called RSSgrab?  Or any of these other RSS ones, which one of those should I use?  I am getting errors on them saying that the file can't be found or that the file is invalid.

---

### Post by gpap1266 on 2007-08-02
Maybe you are behind proxy?
here is a solution [http://http://mail.opensolaris.org/pipermail/jds-review/2007-April/000867.html]("http://http://mail.opensolaris.org/pipermail/jds-review/2007-April/000867.html") 
Any help how to install it?

---

### Post by ramkumail on 2007-09-24
hi,
I was searching for this solution for a long time. thanks for the link.  I got the patch. I dont know how and where to apply it. I am new bee and googled for it but did not get enough info. all i can get is the command  patch does that but from which directory should i run it. there are two gdesklet directories. /home/.gdesklet and /usr/share/gdesklet. please take my hand and lead me out of this maze. I have not applied patch to any of the applications before. so please explain in a manner so that I can understand and other new bees will also benefit.

Thank you...

---

### Post by drmulot on 2007-09-24
Hello,
Once you have downloaded the GoodWeather desklet, open gdesklets ( right click ), select first option : Manage desklets.
This will open the desklets shell.
Click on file, then on : Install a packet
Select GoodWeather.tar.gz in the path where you downloaded it
It will then be installed automatically
It will be accessible from the 'uncategorized' category of desklets.

Have fun :)

---

### Post by ramkumail on 2007-09-25
Thanks drmulot for your time.
Sorry that i was not very clear on my problem. I have managed to install goodweather . I am behind a proxy. I think gdesklet donot support proxy. The above link([http://http://mail.opensolaris.org/p...il/000867.html](http://http://mail.opensolaris.org/p...il/000867.html) ) led me to a patch which will enable my gdesklets to connect through the proxy. I got a bin file from that link. Now i dont know what i should do with that bin file to enable my gdesklets to connect to weather updates through the proxy. can you help me to install that patch please.

---

### Post by ramkumail on 2007-09-26
some one help please...

---

### Post by ramkumail on 2007-09-28
I contacted **_Mr.Damien_** from SUN. Below is his solution to cross the proxy.


Ah, Chris Wang's proxy patch!
[http://cvs.opensolaris.org/source/xref/jds/spec-files/trunk/patches/gdesklets-07-proxy.dif](http://cvs.opensolaris.org/source/xref/jds/spec-files/trunk/patches/gdesklets-07-proxy.dif)
This patch modifies Downloader.py. This file seems to be installed to:
/usr/lib/gdesklets/shell/plugins/PackageInstaller/Downloader.py
You could try modifying the installed version of this file. You could do 
it manually or download the file and apply the patch:
$ cd /usr/lib/gdesklets
$ su
# patch -p1 < /path/to/gdesklets-07-proxy.diff
If it gives an error then it was not able to find the file and editing 
manually might be easier.
On my system the python script is compiled into Downloader.pyc and 
Downloader.pyo. These might need to be recreated, but I'm not sure how.

I was able to edit the file manually after reading this page. [http://www.cpqlinux.com/patch.html](http://www.cpqlinux.com/patch.html)
i think you can also save the text in the file as gdesklets-07-proxy.diff and use his commands. will keep posting after knowing how to recreate python script.

---

### Post by ramkumail on 2007-10-06
Hi folks,
 The proxy problem is fixed in the new beta 0.36 release. However i cannot compile it from source due to dependency problems which i cannot resolve. The full version will be out when final release of gutsy is out. hopefully If repositories of gutsy have a debian package for 0.36 things will be easier for all those suffering behind a proxy.:guitar:

---

