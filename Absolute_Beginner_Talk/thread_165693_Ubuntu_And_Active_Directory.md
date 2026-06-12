---
title: "Ubuntu And Active Directory"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by tstrowd on 2006-04-25
](*,) 
Has anybody had a problem adding Ubuntu as a client to Win2000 domain?
I've tried adding the client to AD using a procedure like this
[http://www.ubuntuforums.org/archive/index.php/t-91510.html](http://www.ubuntuforums.org/archive/index.php/t-91510.html)
But at the point of this: net ads join -U [email]domainadminuser@DOMAIN.INTE[/email]RNAL
I get a error message "Failed to open /var/lib/samba/secrets.tdb"

On a Win XP client i can see in Network Neighborhood the Ubuntu computer in  workgroup "LAB" and i can access it. 
Is there any troubleshooting guides out there with ACTIVE Directory integration?
Thanks

---

### Post by mjm115 on 2006-04-25
[QUOTE=tstrowd]](*,) 
Has anybody had a problem adding Ubuntu as a client to Win2000 domain?
I've tried adding the client to AD using a procedure like this
[http://www.ubuntuforums.org/archive/index.php/t-91510.html](http://www.ubuntuforums.org/archive/index.php/t-91510.html)
But at the point of this: net ads join -U [email]domainadminuser@DOMAIN.INTE[/email]RNAL
I get a error message "Failed to open /var/lib/samba/secrets.tdb"

On a Win XP client i can see in Network Neighborhood the Ubuntu computer in  workgroup "LAB" and i can access it. 
Is there any troubleshooting guides out there with ACTIVE Directory integration?
Thanks[/QUOTE]

Have you tried the steps located [here]("https://wiki.ubuntu.com/ActiveDirectoryHowto").

---

### Post by tstrowd on 2006-04-26
I will try this site. Thanks. But i've noticed the response i get from Ubuntu is different from what the instructions says. For instance..right after this:

Try if you can receive a kerberos ticket: 

    # kinit user
    Password for [email]user@EXAMPLE.COM[/email]: ...
I get "Server  was expecting a different response" or something like this.
I know i'm typing in the correct password. Now what?

---

### Post by uteck on 2006-04-26
This may not be too helpful, but I am playing with the latest beta version of Suse10.1 and it joined the 2003 AD domain at work with no fuss during the install.  I can even use it to authenticate the login with GDM.  Now I just need to get Office and Exploder installed and I can start testing to see if it can replace a MS box.
(It has to be Office as the macros from Excel don't work in OO.o, and the web based app we use is IE only.)

---

### Post by Nequeo on 2006-04-26
[QUOTE=uteck]This may not be too helpful, but I am playing with the latest beta version of Suse10.1 and it joined the 2003 AD domain at work with no fuss during the install.  I can even use it to authenticate the login with GDM.  Now I just need to get Office and Exploder installed and I can start testing to see if it can replace a MS box.
(It has to be Office as the macros from Excel don't work in OO.o, and the web based app we use is IE only.)[/QUOTE]

I successfully managed to get an Ubuntu 5.10 PC joined to a Windows 2003 domain. Haven't tried Windows 2000 - but I do [this book]("http://www.oreilly.com/catalog/linuxwinworld/") at home. I won't have access to it until the weekend. But if you've still having problems in a couple of days I'll try and distill what it says about joining AD domains. There was a whole chapter on it. It didn't work exactly for Windows Server 2003, but it was close enough that I could Google up the missing gaps. Would probably be just peachy for 2000.

---

### Post by tstrowd on 2006-04-27
>>>This may not be too helpful, but I am playing with the latest beta version of >>>Suse10.1 and it joined the 2003 AD domain at work with no fuss during the install.
Don't you have to buy this? If not where can i get it?

---

### Post by tstrowd on 2006-05-17
Well i've tried for over a week now to get Ubuntu to ATHENTICATE to active directory.
Seems like Ubuntu is good for the home user/stand alone PC, but won't make it in an Active Directory environment. I will try Fedora next because it seems more tailored to a Domain environment.

---

### Post by jecos on 2006-05-18
[QUOTE=tstrowd]Well i've tried for over a week now to get Ubuntu to ATHENTICATE to active directory.
Seems like Ubuntu is good for the home user/stand alone PC, but won't make it in an Active Directory environment. I will try Fedora next because it seems more tailored to a Domain environment.[/QUOTE]

Skip fedora, [www.opensuse.org](www.opensuse.org) and download.

---

