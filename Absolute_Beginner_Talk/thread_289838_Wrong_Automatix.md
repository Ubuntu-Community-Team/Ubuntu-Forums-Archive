---
title: "Wrong Automatix"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Bartender on 2006-10-31
I did something moronic.  Followed the steps to install Edgy Automatix to a Dapper PC.  Now have the Automatix icon under System Tools, but it informs me that I have Auto for Edgy and won't proceed.  Problem is, since the whole package isn't installed, sudo remove doesn't remove it.  Synaptic doesn't see it either of course.
Help please!

---

### Post by Pjotr123 on 2006-10-31
Automatix itself is WRONG. Uses forced authorizations and can do ugly things to your system. Much better to skip this semi-virus and do a little legwork to complete your Ubuntu.

Sorry, the only solution I see for you is a clean reinstallation. And please, avoid Automatix.... If you really hate the legwork, then consider EasyUbuntu instead. That one doesn't do the harm that Automatix does, and is reversible.

Greeting, Pjotr.

---

### Post by gitano1 on 2006-10-31
I would agree with the clean reinstall. It sounds as though things are beyond normal repair. 
On the issue of Automatix, I installed Automatix2 under 6.06. It runs perfectly and enabled my install of the Nvidia drivers and other less readily available components. This is the site I used for the download:
[http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by angkor on 2006-10-31
> **Pjotr123 said:**
> Automatix itself is WRONG. 

Automatix isn't nearly as bad as you describe it to be. But that's another discussion entirely.

[quote=Bartender]it informs me that I have Auto for Edgy and won't proceed. Problem is, since the whole package isn't installed[/quote]


Did it do anything before it stopped proceeding, or does it just refuse to work? If it's the latter I don't see any reason why you would need a reinstall. What errors do you get when you try to uninstall automatix?

---

### Post by Bartender on 2006-10-31
I followed the steps (the Edgy not Dapper) at Automatix website.  The Automatix icon is there under System Tools.  If I click on it and follow the steps, it detects Dapper and says "This version is for Edgy only".  The only option is "OK".  I can't sudo remove.  It says Automatix not installed.  Synaptic does the same thing.  I tried following the correct steps for Dapper, hoping that it would remove the Edgy keys and put Dapper in its place, but it didn't change anything.  If I knew how/where to remove the intial bits of data that tell Auto what to do and where to go I could start over.

---

### Post by arnieboy on 2006-10-31
> **Bartender said:**
> I followed the steps (the Edgy not Dapper) at Automatix website.  The Automatix icon is there under System Tools.  If I click on it and follow the steps, it detects Dapper and says "This version is for Edgy only".  The only option is "OK".  I can't sudo remove.  It says Automatix not installed.  Synaptic does the same thing.  I tried following the correct steps for Dapper, hoping that it would remove the Edgy keys and put Dapper in its place, but it didn't change anything.  If I knew how/where to remove the intial bits of data that tell Auto what to do and where to go I could start over.
close automatix2.
now do 
```
sudo apt-get remove automatix2
```
now do 
```
sudo gedit /etc/apt/sources.list
```
and in the automatix source that you added to this file, change the word "**edgy**" to "**dapper**" (minus quotes)
save and close the file
now do 
```
sudo apt-get update
sudo apt-get install automatix2 
```

---

### Post by arnieboy on 2006-10-31
> **Pjotr123 said:**
> Sorry, the only solution I see for you is a clean reinstallation.
ROFL.. ignorance coupled with fanatical hatred can turn into something quite amusing.
as it stands (for the uninitiated) Automatix2 is one of the most advanced package managers of its times and it does not force anything. As for Easy Ubuntu, it does not work (is actually currently broken).. and is not even half as feature rich as AX2 (and by features I dont mean packages offered for installation).

---

### Post by bulldog on 2006-10-31
> **Pjotr123 said:**
> Automatix itself is WRONG. Uses forced authorizations and can do ugly things to your system. Much better to skip this semi-virus and do a little legwork to complete your Ubuntu.

Sorry, the only solution I see for you is a clean reinstallation. And please, avoid Automatix.... If you really hate the legwork, then consider EasyUbuntu instead. That one doesn't do the harm that Automatix does, and is reversible.

Greeting, Pjotr.

I have used automatix on several Dapper and Edgy installations and  never had any problem with it.
Think you're a little over reacting.

Want to say Thank You to the Automatix Team for the great application.

---

### Post by Bartender on 2006-10-31
Arnie, you DA MAN -
Automatix (the right one) doing its thing.  Thanks

---

### Post by Bartender on 2006-10-31
Is anyone else having trouble with the u.s. servers?  We tried thru Add/Remove, Synaptic, etc. to get some packages but no response.  Automatix was doing fine until it went to the u.s. servers and that was the end of progress.  
Wonder if all the Edgy downloads might be causing the trouble?  
Maybe should try late at night, or just wait a coupla weeks...the guy I was trying to help hasn't been able to get automatic updates for a few days now.  We hooked up my old PC and it got stuck too.

---

### Post by sKuarecircle on 2006-11-11
> **arnieboy said:**
> close automatix2.
now do 
```
sudo apt-get remove automatix2
```
now do 
```
sudo gedit /etc/apt/sources.list
```
and in the automatix source that you added to this file, change the word "**edgy**" to "**dapper**" (minus quotes)
save and close the file
now do 
```
sudo apt-get update
sudo apt-get install automatix2 
```

I had exactly the same problem, after reading the first couple of lines of this post i tought I was going to have to to a clean install! Luckiliy I read on and the above solution worked for me.

---

