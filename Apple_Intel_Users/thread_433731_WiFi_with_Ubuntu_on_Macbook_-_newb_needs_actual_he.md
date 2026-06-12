---
title: "WiFi with Ubuntu on Macbook - newb needs actual help"
date: 2007-05-05
forum: Apple Intel Users
---

### Post by Lt_Data on 2007-05-05
So yeah, hopefully the title states it clearly. If not, I have a 2nd gen. macbook and wanted to put Ubuntu on it. I don't need to discuss the installation, as everything went well. However, I (and many others, it seems) have a problem with WiFi. The only difference is, I probably don't know what the hell I should do to approach the problem. I've tried the ndiswrapper way, and downloading an appropriate drive; here's what i was told to type in:

**Removing previous ndiswrapper:**

    *  Sudo aptitude remove -purge ndiswrapper-common ndiswrapper-utils*
               (I received a message that said "Aptitude: Invalid Option -- P" and didn't know where to continue from there)
      *Sudo rm -R/etc/ndiswrapper*
      * Sudo rm /etc/modprobe.d/ndiswrapper*

**Enter directory where I unzipped ndiswrapper:**

       *cd -/desktop/ndiswrapper-1.38/*

**Now finishing the ndiswrapper**

       *sudo aptitude install build-essential*
       *make uninstall* (repeat this step until it doesn't find anything)
       *make*
       *Sudo make install*

**Installing the Driver:**

       *sudo ndiswrapper -i NET5416.INF*

**Load ndiswrapper module:**

       *sudo modprobe ndiswrapper*

**Have it auto load at each boot:**

       *sudo ndiswrapper -m*

Yeah, so I am really begging for anyone out there, anyone at all to help me out and provide assistance that isn't AS esoteric as everything i've found. The above process didn't work, I kept getting syntax errors, and i don't even want to attempt the MADWiFi because I'm not completely sure what to do.

Thanks!

---

### Post by ronocdh on 2007-05-05
Well first off, I believe the **purge** modifier must be preceded by two hyphens, as opposed to just one. Thus the correct syntax would look like:```
sudo aptitude remove --purge ndiswrapper-common ndiswrapper-utils
```
Maybe that will help you. By and large, though, getting wireless up and running will be a bit of a chore. There is a solid post in here by widemos (maybe back a page or so now) that helped a lot of people get up on Madwifi. I think it was tailored for MBP C2D users, though.

---

### Post by Lt_Data on 2007-05-05
> **ronocdh said:**
> Well first off, I believe the **purge** modifier must be preceded by two hyphens, as opposed to just one. Thus the correct syntax would look like:```
sudo aptitude remove --purge ndiswrapper-common ndiswrapper-utils
```

 
That makes so much sense! :KS  Wow, I mean, the output I received even had "--P". I'm new to shell commands and such, but ouch, that kind of stings haha. Thanks for your help! I'm going to bite the bullet and attempt MADWiFi, I guess I see no reason not to. What's the point of loving technology if you're afraid of exploring through it. 

Peace

---

### Post by ronocdh on 2007-05-05
> **Lt_Data said:**
> That makes so much sense! :KS  Wow, I mean, the output I received even had "--P". I'm new to shell commands and such, but ouch, that kind of stings haha. Thanks for your help, I do hope the other person you mention posts here. If he/she doesn't do so in a few days I'll scour the forums for his/her posts for relevant info. I'm going to bite the bullet and attempt MADWiFi, I guess I see no reason not to. What's the point of loving technology if you're afraid of exploring through it. 

Peace
[Here]("http://ubuntuforums.org/showthread.php?t=429641&highlight=widemos") is the Madwifi post by widemos I mentioned. It links to a bug report, and as you can see by rifling through the thread, it has proved successful for many people; YMMV. Please post back with your results, though!

And don't worry about the bash thing, we've all been there. Another thing to keep in mind is that it's largely case-sensitive, for instance the famous example of ```
sudo gedit /etc/X11/xorg.conf
```This is used to edit your X server info, and in the beginning, everyone writes a lowercase X. ;)

---

### Post by Lt_Data on 2007-05-05
after the second command 

```

svn checkout ht-tp://svn.madwifi.org/branches/madwifi-hal-0.9.30.10 madwifi wget ht-tp://people.freebsd.org/~sam/ath_hal-20070428.tgz

```

I receive a message that says 

```

 The program 'svn' is currently not installed. You can install it by typing: **sudo apt-get install subversion**

Bash:svn: command not found

```

So I follow the instructions provided by the oh so powerful Terminal and typed in **sudo apt-get install subverion**. And when I did (and after entering my password) I received a message that said this:

```
 
Reading package lists... Done
Building dependency tree
Reading State information... Done
E: Couldn't find package subversion

```

And thus, you are up to date with my situation. I obviously didn't continue on with the code yet because I wanted help with this problem. If I **SHOULD** have carried on with the code then please let me know. 

I really appreciate any help, I must be doing something wrong since a majority of people have gotten it working this way. 

Peace

---

### Post by ronocdh on 2007-05-05
No, you are right to have stopped. Can you browse the web on this computer? If not, you don't have an internet connection! Make sure you are plugged into a DHCP-enabled ethernet connection and try again.

The svn check happens even before the computer attempts to connect to the internet, but even with subversion, you wouldn't be able to go through with the wgets.

---

### Post by Lt_Data on 2007-05-05
Damn, well thanks to Apple being oh so helpful, the macbooks don't come with the cables and Apples USB modem to connect to the ethernet and I'm pretty sure I don't have the cables. I'm almost ready to give up on having Ubuntu recognize my WiFi, I didn't know I needed to be connected to any sort of internet connection to have it recognize my WiFi. Are you certain that has to be done? I'm sure this shows the extent of my "newb-ery".

---

### Post by ronocdh on 2007-05-05
> **Lt_Data said:**
> Damn, well thanks to Apple being oh so helpful, the macbooks don't come with the cables and Apples USB modem to connect to the ethernet and I'm pretty sure I don't have the cables. I'm almost ready to give up on having Ubuntu recognize my WiFi, I didn't know I needed to be connected to any sort of internet connection to have it recognize my WiFi. Are you certain that has to be done? I'm sure this shows the extent of my "newb-ery".
The wireless chipset in your computer isn't well documented, meaning it is extremely difficult to write drivers for it. (Drivers will enable your OS, Ubuntu, to talk to and utilize the hardware.) The good people over at MadWiFi are hard at work getting support for the Atheros cards (which we have in our laptops from Apple), but it's not perfect yet. There are plenty of wireless posts on this forum, so read up at your leisure and get a feel for the current state of things.

DHCP-enabled ethernet will work out of the box. You can buy a cat5 (ethernet) cable at any electronic store for very cheap, and plug it into your router at home. Of course, you can always boot into OS X if wireless ethernet is a must before you have the problem solved.

---

### Post by Lt_Data on 2007-05-05
Yeah, Atheros really needs to cut that out. I mean, are they really that anti open-source that they refuse to release any bit of documentation that'd provide the slightest hint, instead of, in most cases, people having to reverse engineer it and do twice the work. I'll post updates on my progress, if possible, if I can't get it going I think I'm going to put my trust in the MADWiFi team and see if something stable comes out.

---

### Post by Lt_Data on 2007-05-10
Long story short, and to update my progress - I got rid of the partition and everything and took Ubuntu off of my mac. Instead I downloaded VMware  because i wanted to test that out. I installed Ubuntu as a VM ("virtual machine") on my mac this way it recognizes my wifi and I don't have to reboot to access my stuff via Mac OS X. It's a really sweet solution if you're looking for a quick fix or want to test out some new software. 

Check it out: [http://www.vmware.com](http://www.vmware.com)

the mac version you'd need is called VMware Fusion

---

### Post by benanzo on 2007-05-10
Good to hear you've got Ubuntu going anyway.

As to why Atheros doesn't help anyone develop drivers for their cards...

One argument I have heard is that it would be in violation of FCC regulations to publish specifications about radio devices so that someone could manipulate the frequency to do things that are illegal.  which is ridiculous.  they really just don't want to give away their "secrets."

---

