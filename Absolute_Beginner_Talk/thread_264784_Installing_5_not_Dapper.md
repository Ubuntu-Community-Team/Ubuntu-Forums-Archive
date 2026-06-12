---
title: "Installing 5 not Dapper"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by macthemaths on 2006-09-25
Hi,

I installed Dapper at the weekend and had connectivity problems (FFox worked after ipv6 fix but update and Automatix/EasyUbuntu wouldn't connect).

I loved the speed at which Ubuntu worked and was smitten with the GUI and theme but not having proper connection was bugging me.  So, back to Mandriva.

Then I found an Ubuntu 5 disc at home and am sitting here at work waiting to get back and try installing version five to see if it works better for me than Dapper.

Any thoughts on this as strategy for making Ubuntu my ditro of choice?  Will it work?

I'll post back later when I've given it a go.

Chris

---

### Post by Sef on 2006-09-25
> Then I found an Ubuntu 5 disc....Any thoughts on this as strategy for making Ubuntu my ditro of choice? Will it work?

Well, is it 5.04 (Hoary Hedgehog) or 5.10 (Breezy Badger)?

Support for both of them is ending soon: end of October for 5.04 and end of April for 5.10.  Thus after those dates, no more updates or security fixes. 

Did you try to post your problem with any error messages that popped up?

---

### Post by macthemaths on 2006-09-25
That's a shame.  I am typing this from my Breezy installation but I am still not able to get anything from Automatix or EasyUbuntu.  Everything gets connection time out problems.

I had to diable ipv6 in FFox to write this.  I will try again to disable ipv6 system wide, and then give EasyUbuntu another go.

I really hope it works.

Any ideas?  

I am connecting to Broadband via LAN and a router.

Thanks,

Chris

---

### Post by macthemaths on 2006-09-25
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

A message from Add Applications

Followed by this:

[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)
[http://www.getautomatix.com/apt/dists/breezy/Release.gpg](http://www.getautomatix.com/apt/dists/breezy/Release.gpg)

Then this:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://www.getautomatix.com](http://www.getautomatix.com) breezy/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by macthemaths on 2006-09-26
Well, the problem wasn't fixed and Automatix won't work from Mepis 6.

I still have a working internet connection and am typing this on a Mepis 6 install (was trying another distro to see if it would work).

I'd like to go back to Ubuntu Dapper but want to be able to run things like automatix and download packages.

Does anyone have any ideas please?

---

### Post by maaronB on 2006-09-26
Are you sure that you are using a upto date mirror when you download Automatix.  
Are you going to this website [http://www.getautomatix.com/](http://www.getautomatix.com/) 
and following these instrucions
```
 Automatic Automatix Installer (does not work on Mepis yet)

Open up terminal and paste the following lines one after the other (wait for each command to finish before you paste the next)

wget http://www.getautomatix.com/files/automatix-installer
chmod 755 ~/automatix-installer
./automatix-installer
```

If so then that is really strange, because I don't understand at all why a fresh install, with a working internet connection would have any problems.

---

### Post by maaronB on 2006-09-26
I am a little confused, is it just Automatix that won't install.  Or do you also have trouble when you use Apt/Aptitude/Synaptic/<whatever you prefear>.

Do you have the same type of trouble using the Mandriva Package installer.

---

### Post by kerry_s on 2006-09-26
I had a similar problem with a new /modem/router/wireless that my DSL sent me it turns out that the firewall settings were to high. I would check your router and see if it has a firewall and what it's set at. Try disabling it and updating if it works than you know you need to adjust it.

---

### Post by macthemaths on 2006-09-26
Thanks for replying.  I'm pretty sure that I correctly followed the instructions on the site.

I also tried it out in three distros.

In all of them I had to disable ipv6 to get FFox to work and I think that I successfully disabled ipv6 system-wide in Ubuntu but still no joy with EasyUbuntu or Automatix or the distro's update tools.

Thanks for your help.

---

### Post by macthemaths on 2006-09-26
I have disabled the firewall on my modem/router and it didn't have any positive results.

---

### Post by maaronB on 2006-09-26
From this site: [http://ubuntuforums.org/showthread.php?t=88639&page=2](http://ubuntuforums.org/showthread.php?t=88639&page=2)


Internet Stuff:

Do the following to remove IPv6 from your Ubuntu system, IPv6 can cause your internet connection to be slow, or, as in my case, not work at all!!

Type about:config no quotes into the location bar in Firefox (this may work in Opera?)

Then type ipv6 into the Filter field.

Double left click on the line that comes up to change it's boolean value to True

sudo gedit /etc/modprobe.d/aliases

Change this line: alias net-pf-10 ipv6

To this: #alias net-pf-10 ipv6

(# = commented out), Save & Exit

Now you can forget about ipv6, possibly for years.

Edit: From the same site

Ubuntu Tricky One!?

Everything was fine, except it was gradually dawning on me that there was a problem when trying to use Apt, or Synaptic; I couldn't! Everything else internet wise was great? So, I continued doing as much setting up as I could before inevitably having to face this problem, which I believe is due to my router & / or ISP?

I read wiki's & sticky's scanned the forums, & eventually found a beautiful solution

This page by python is gold, it would have taken me a year to solve this without outside help:

[http://www.ubuntuforums.org/showthre...nk+adsl+router](http://www.ubuntuforums.org/showthre...nk+adsl+router)

Synaptic & Apt, became fully functional after applying python's fix - just magic these forums.

---

### Post by macthemaths on 2006-09-26
This (sorting out the DNS files) seems to be doing the trick for me in Mepis.  I'll try swapping back to Dapper tomorrow.

Thank you so much,
You have made me happy - I knew that if I had patience the forum would come up trumps!

Chris

---

### Post by macthemaths on 2006-09-26
**OH YEAH!  And page rendering seems to be faster now - Thank you!**

---

