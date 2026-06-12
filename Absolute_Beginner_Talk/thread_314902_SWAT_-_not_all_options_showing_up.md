---
title: "SWAT - not all options showing up"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by 99er on 2006-12-08
Hi there-
I was following the guide at [http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html]("http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html") and had no problems except when it came to configuring SAMBA with SWAT.  

I was confused because his directions told you to login to SWAT (no problem...) and then click on 'shares' to set up my shares.  Problem was, when I went to /shares, I didn't have any options for shares.  As a matter of fact, the only buttons at the top of my SWAT screen are home, status, view, and passwords.  I was suspicious that I was missing something, and then confirmed it after googling for a screenshot of someone elses SWAT screen.

I'm not sure what the problem is, although I suspect that it could be a problem with SAMBA, so SWAT won't show me the settings.

Any help anyone can provide would be appreciated.
Thanks.

---

### Post by lhtown on 2006-12-09
You might try going to system>administration>networking and clicking on the "General" tab. Enable the option that says "Scan for available services..."

I haven't tried exactly what you are doing, but I struggled for a day or so trying to set up networking and then finally ended up enabling this option and getting it to work with ftp instead of Samba.

You may have to reboot to get it to work.

---

### Post by Kjell on 2006-12-09
If you point your web browser to [http://localhost:901/](http://localhost:901/)

If you only get some "view only" icons on top, you're not in the admin mode.

When you log into swat you should use "root" as user, not your alias root
what you normaly use in Ubuntu.

If you are usure what you root password is, you can check/ or change it
System->Administration-> Users and groups , choose root and properties 

//Kj

---

