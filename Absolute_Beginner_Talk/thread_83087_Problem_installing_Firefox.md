---
title: "Problem installing Firefox"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by BAD_ger on 2005-10-27
Hi Everyone, I am an absolute noob to Linux and UBUNTU. 
I have installed Breezy KUBUNTU. Everything went smoothly. Now I am trying to learn how to install more programs and my every effort has led to problems. 
In particular I would like to get some help installing Firefox.

I downloaded the Firefox installation file firefox-1.0.7.installer.tar.gz
then i did used the following commands trying to install it:

tar -xvzf firefox-1.0.7.installer.tar.gz
cd firefox-installer
./firefox-installer

the last command brings up the following error message

./firefox-installer-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory.

Could anyone please tell me where I can get this libstdc++.so.5?
Any help at all will be greatly appreciated.
Thanks in advance

---

### Post by rykel on 2005-10-27
hi,

are u using ubuntu breezy or hoary?

if hoary, the easiest linux installer for Firefox is its **autopackage**. Click [here]("http://www.autopackage.org/packages") to find and download it.

however, if u are using breezy with SCIM enabled, u will want to either remove SCIM for now (if u want to use the autopackage firefox alongside with SCIM) OR u just have to get the firefox deb thru' synaptic. go to *System/Administration/Synaptic* and search for "firefox".

hope tat helps!

---

### Post by Mustard on 2005-10-27
I would have thought firefox is installed already in Kubuntu.  I take it you want to have the 'latest version' for some reason?

I'm feeling lazy atm, or I would search for a HOW TO install the latest firefox in the forums. :)  (Just got out of bed)

Your problem has a familiar ring to it.  I am sure I have seen other posts about libstdc++.so.5.  If you're feeling more active than me, you can try searching the forum yourself.

With regards to the post above from rykel, I think Synaptic is called Kynaptic in KUBUNTU?  I am not sure.

---

### Post by towsonu2003 on 2005-10-27
[QUOTE=BAD_ger]Hi Everyone, I am an absolute noob to Linux and UBUNTU. 
I have installed Breezy KUBUNTU. Everything went smoothly. Now I am trying to learn how to install more programs and my every effort has led to problems. 
In particular I would like to get some help installing Firefox.

I downloaded the Firefox installation file firefox-1.0.7.installer.tar.gz
then i did used the following commands trying to install it:

tar -xvzf firefox-1.0.7.installer.tar.gz
cd firefox-installer
./firefox-installer

the last command brings up the following error message

./firefox-installer-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory.

Could anyone please tell me where I can get this libstdc++.so.5?
Any help at all will be greatly appreciated.
Thanks in advance[/QUOTE]

try not to use source codes, as you won't be able to auto update your software, a common problem with distros like slackware...

as a newbie, just use synaptic (System>Administration>Synaptic), though i'm not sure whether kubuntu uses synaptic or something similar. try doing a search for "package management" in wiki.ubuntu.org

PS. newbie myself...

PS2. The basic command is: 
sudo apt-get update
sudo apt-get install firefox

also, to search for packages to install,
apt-cache search keywprdtosearchhere

hope this will help.

---

### Post by Mustard on 2005-10-27
I would add that you can find assistance in IRC on the irc.freenode.net server in channel #kubuntu for things specific to KUBUNTU.  You will find a number of Kubuntu enthusiasts in there who will know more about the specifics of working with Kubuntu.

If Kubuntu is anything like my Ubuntu, then the x-chat irc client in the Application menu>Internet is already set up to join the irc.freenode.net server and will probably join the correct channel too.

---

### Post by erikpiper on 2005-10-27
It really should be installed I thought- NOTE it has an ugly blue globe as the icon, and you need to change the icon to a good one yourself. (Easy- look in the howto's section)

---

### Post by rykel on 2005-10-27
[QUOTE=Mustard]With regards to the post above from rykel, I think Synaptic is called Kynaptic in KUBUNTU?  I am not sure.[/QUOTE]

synaptic and kynaptic are 2 separate programs, altho' u can use either one in either ubuntu or kubuntu. they are inter-changeable, altho' synaptic does have more options iirc.   :cool: 

my suggestion is just to use the firefox autopackage installer... it is faster, more responsive and loads up quicker. and it is essentially the same thing as the zipped file u can download from mozilla.org, so it's also closer to the original.

remove the already installed firefox using synaptic/kynaptic if u need to! (doesn't hurt to keep it there too, if u need to use Yelp, epiphany or galeon)

ubuntu in future should support dual gecko engines! one for apps to depend on, the other for its firefox browser.

---

