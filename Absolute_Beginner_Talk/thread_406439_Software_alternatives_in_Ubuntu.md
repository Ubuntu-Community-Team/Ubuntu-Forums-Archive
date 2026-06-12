---
title: "Software alternatives in Ubuntu"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by dello on 2007-04-10
Hi!

I've tested the BETA 7.04 and I must say I'm impressed. I've never used Linux before. Until I get used to Ubuntu, I'll probably use Windows too on another partition but may "goal" is to switch over only to Ubuntu as soon as possible. Until then I would appreciate some help. I've understood that (from surfing around this forum) I don't need firewall software, antivirus nore antispyware software.

**1.** Is there any RoboForm alternative for Ubuntu/Linux (Form filler/password reminder)? I REALLY need this kind of software to do my work. 

**2.** Is there any software for Ubuntu I can use to surf the Internet anonymously? I would appreciate another answer than "Tor", because I tried it for Windows and it was so slow so I consider it to be useless crap. In Windows I use Anonymizer Total Net Shield and it's SSH (proxy). I prefer SSH instead of SSL. It's faster and more secure.

**3.** I guess Ubuntu doesn't have a registry at all so this kind of software is unnecessary (cleaning and compacting the registry) in Ubuntu? I use Registry Mechanic in Windows. 

**4.** How do I erase files from my hard drive in Ubuntu **FOREVER**? In Windows, Evidence Eliminator is the best. Is there any alternative for this in Ubuntu? Another Windows example is Windows Washer. Thanks and have a great day! :)

---

### Post by rabid9797 on 2007-04-10
there are many alternatives for software in the linux world, some of them just harder to find than others, but a couple that come off the top of my head:

For Roboform: if you use mozilla firefox(i assume you do since its the default browser) there are many extensions for form fillers and password managers, as well as a couple in the repos
Firefox: [https://addons.mozilla.org/en-US/firefox/addon/4231](https://addons.mozilla.org/en-US/firefox/addon/4231)
[https://addons.mozilla.org/en-US/firefox/addon/1882](https://addons.mozilla.org/en-US/firefox/addon/1882)
[https://addons.mozilla.org/en-US/firefox/addon/3863](https://addons.mozilla.org/en-US/firefox/addon/3863) (passwords and forms)



as for anonymous surfing, there are plenty of proxy programs for ubuntu(im sure in the repos), but firefox has alternatives as well:
[https://addons.mozilla.org/en-US/firefox/addon/2217](https://addons.mozilla.org/en-US/firefox/addon/2217)
[https://addons.mozilla.org/en-US/firefox/addon/1415](https://addons.mozilla.org/en-US/firefox/addon/1415)


As for registry tweaks, thats one of the beauties of linux, everything is customizable and tweakable. if your looking for a quick fix to optimize ubuntu for your computer, there isn't one out there(that i know of, other member, correct me if im wrong). it just takes some good old fashion tweaking with gedit to get things perfect :)

im not currently in ubuntu, so, as you can see, i can't exactly say about the alternativ software for ubuntu, but im restarting back in a couple minues, and if you happen to get to my post before i can edit with other links, i hope there help :lolflag:

---

### Post by bobplano on 2007-04-10
i didn't think you needed an extension for formfillers in firefox. i thought you could just go to the options and put the information there(of course i don't acutally use this)

---

### Post by mdsmedia on 2007-04-10
> **bobplano said:**
> i didn't think you needed an extension for formfillers in firefox. i thought you could just go to the options and put the information there(of course i don't acutally use this)I was thinking the same thing.

Firefox has an inbuilt form filler, and it's so long since I actually thought about it that I'm not sure how to switch it on or off. It just works in Firefox for me.

Regarding firewalls, there is a firewall installed with Ubuntu by default (IPTables), but if you want to install a graphical frontend I installed Firestarter which is quite nice.

Anti-Virus is really only necessary if you're, say, receiving and then forwarding emails between Windows users. You might receive the email, be immune to any attached virus, on-send it to a friend who is not immune. I installed ClamAV for that purpose.

Anti-Spyware is not necessary (AFAIK) and in 1 1/2 years I certainly haven't seen any malware on my Ubuntu Linux.

---

### Post by dello on 2007-04-11
Thanks a lot but (correct me if I'm wrong) Firefox only fills the username, not the password for  that actual website I'm supposed to log in at, or? RoboForm uses "passcards" and they behave just like Firefox bookmarks. When I log in to RoboForm with my main password, I just click the passcard fot example to this forum and it logs me in automatically. In this way I only need one "superpassword" to remember for every website I need to log in at and everything is of course encrypted and therefor also protects me from keyloggers in Windows. Thanks! :)

---

### Post by mdsmedia on 2007-04-11
> **dello said:**
> Thanks a lot but (correct me if I'm wrong) Firefox only fills the username, not the password for  that actual website I'm supposed to log in at, or? RoboForm uses "passcards" and they behave just like Firefox bookmarks. When I log in to RoboForm with my main password, I just click the passcard fot example to this forum and it logs me in automatically. In this way I only need one "superpassword" to remember for every website I need to log in at and everything is of course encrypted and therefor also protects me from keyloggers in Windows. Thanks! :)When you first login to that site in Firefox it will (should) give you an option to save the login details, including password, for that site.

Next time you enter the login page it will (should) fill the username and password for you.

If you haven't yet logged into that site using Firefox, it asks if you want to save login details, "Now, Not Now, Or Never for this site" or words to that effect.

You can also have a super password to protect your password list in Firefox.

---

### Post by msak007 on 2007-04-11
> **dello said:**
> Hi!

I've tested the BETA 7.04 and I must say I'm impressed. I've never used Linux before. Until I get used to Ubuntu, I'll probably use Windows too on another partition but may "goal" is to switch over only to Ubuntu as soon as possible. Until then I would appreciate some help. I've understood that (from surfing around this forum) I don't need firewall software, antivirus nore antispyware software.

**1.** Is there any RoboForm alternative for Ubuntu/Linux (Form filler/password reminder)? I REALLY need this kind of software to do my work.

I struggled to find an alternative for the longest time, and every search I ever did never gave me any good solutions. Then I found the absolute best replacement if you use Firefox - an extension called PasswordMaker

[http://passwordmaker.org/](http://passwordmaker.org/)

It may seem a little complicated at first, but it's actually very easy to use and has some nice features. You can let it create a secure password for you based on the URL of the site, your username, the master password (to lock the passwords / settings), a hash system, specified characters to use, and password length. And you can have it autofill login forms once you enter your Master password. Also from a security standpoint, this is independent of the browser as all the settings and passwords are stored in a separate file, and you can have the Master password store in memory only, so if you close the browser and re-open it you enter it again to access your passwords. I actually prefer this to RoboForm now.

For a form filler, I also found a Firefox extension called ShopWiki:

[https://addons.mozilla.org/en-US/firefox/addon/4231](https://addons.mozilla.org/en-US/firefox/addon/4231)

You can add as many profiles as you want (different addresses, phone #s, emails, etc.), and when a form can be filled it's highlighted blue. If you click on it, it'll ask you if you want to fill the form in. If you want (optional), you can also store credit card information that can be locked using a password. If you're shopping online and want to fill a credit card form out, you enter your password first and then it'll fill it out.

Using those 2 extensions in conjunction with each other practically replaces RoboForm.

EDIT: I know many people are suggesting Firefox's built-in password manager and form filler, but I found them too simplistic and not highly configurable. One of the biggest drawbacks with the built-in password manager is that you can't store multiple logins / passwords for a single site.

---

### Post by o_fortuna on 2007-04-11
> **dello said:**
> 
**4.** How do I erase files from my hard drive in Ubuntu **FOREVER**? In Windows, Evidence Eliminator is the best. Is there any alternative for this in Ubuntu? Another Windows example is Windows Washer. Thanks and have a great day! :)

Hey! I know this one. The easiest way (for me) to delete files is to use the terminal (Applications-Accessories-Terminal) and do this:
```
shred -uz /directory/filename
```
If you want to be able to right-click a file and shred it, paste this into a blank file, save it, set it as executable (by right clicking, selecting properties, then Permissions, then check "Allow executing file as program) and copy it to ~/.gnome2/nautilus-scripts

```
#!/bin/bash

# Shreds the heck out of a file, deleting it forever and then overwriting it with zeros

cd $NAUTILUS_SCRIPT_CURRENT_URI
shred -uz $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
```

You can leave out the comment, of course ;) (but not the #!/bin/bash)

Of course, if you're not worried about the FBI looking through your hard drive, shift+delete will probably work just fine (that's just a normal delete which bypasses the Trash can). Shred's 25 overwrites (plus the extra zero overwrite) might be overkill.

One thing to do for any type of software you are looking for is to open up synaptic and searching the descriptions of packages. There are 18000+ packages in Ubuntu, so you can probably find what you need :)

---

### Post by dello on 2007-04-11
OK, thank you, everybody! That sure helped, but if someone knows how to surf anonymously in Ubuntu, except using "Tor", before I can check the repositories, that would be even greater. :)

---

