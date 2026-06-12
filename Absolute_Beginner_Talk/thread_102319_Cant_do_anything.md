---
title: "Cant do anything?"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by SpLaTt on 2005-12-11
ok, my friend gave me one of urs cds. 5.6 or something.

i installed it on an old comp, and just lately logged on. i downloaded/installed over 130 updates... and everything seem to be going right.

so im complety new to this, so one of my friends was helping me install an aim for linux. i unpacked it and everything. it made a usr folder on my desktop and it had a pic of a lock. he told be to take the files in the bin and lib, and put them in my local bin and lib.

this is where the proglem came in, i said i had no permission to do this, even tho i could use the root and it was my user folder, (and im the only account)

and later i found out i wasnt the owner or anything and i cant change options or do anything.


i dont know if u can fix this or what. so im thinking of downloading the ubuntu linux from the site. so it comes in a folder? but what do i do with the folder? or make it a cd or something? not sure what to do at all... (dont even know, do i need an image program or something to make it a cd??? im a windows user, do i need alot of help...lol)

---

### Post by peanut butter on 2005-12-11
the reason you cant change stuff in theese folders isbecause you are not root or a fake root.  Ubuntu uses sudo which makes you root i despise this so i just login as root. you canfind instructions [here http://ubuntuguide.org/#usersadministration]("http://ubuntuguide.org/#usersadministration") do the 1st and 3rd parts and then login to gdm as root

Warning do _***[I]not***[/I]_ do number 2

also you are _not_ the only account there are probably at least 10 they are just "hidden"

---

### Post by Zelut on 2005-12-11
Ok, I think I followed your question... 

Are you trying to install an IM client? (like messenger, AIM, etc?)  Unless you SPECIFICALLY need AIM for Linux you already have one installed.  Check out Applications > Internet > Gaim Instant Messenger and setup your AIM account.

As far as moving files to /bin /usr/bin, etc.. you really don't need to do that.  That is, technically, where executable files go but we've made things easier to deal with & you don't need to worry about that.

Get back to us with more questions.  I'm sure we can get this all figured out for you and you'll end up enjoyin' this quite a bit.

---

### Post by SpLaTt on 2005-12-11
ok, but should i upgrade my ubuntu? is there a way to do that without installing the newest over my old one?

---

### Post by GreenHawkIA on 2005-12-11
Unless you want to latest versions of all the software, it's probably not necessary.  Security updates for your distribution will be continued for another 6 months at least, and 5.04 (Warty Warthog) is a very solid and very good version.  I used it for a long time without any problems, and it did everything I wanted it to do.  If you do upgrade, be warned in advance it will require a large download - either just a fresh CD for install or the upgrade itself.  Instructions for an upgrade - if you want it - are [here.]("https://wiki.ubuntu.com/BreezyUpgradeNotes")

---

### Post by Zelut on 2005-12-11
What version are you running now?  If you have 5.10 you have the latest version, if you're running 5.04 I would suggest an update and, yes, this can be done without overwriting your current installation.  Check out the instructions here:

[http://www.ubuntuguide.org/#upgradingubuntu](http://www.ubuntuguide.org/#upgradingubuntu)

---

### Post by peanut butter on 2005-12-11
[QUOTE=GreenHawkIA]Unless you want to latest versions of all the software, it's probably not necessary.  Security updates for your distribution will be continued for another 6 months at least, and 5.04 (Warty Warthog) is a very solid and very good version.  I used it for a long time without any problems, and it did everything I wanted it to do.  If you do upgrade, be warned in advance it will require a large download - either just a fresh CD for install or the upgrade itself.  Instructions for an upgrade - if you want it - are [here.]("https://wiki.ubuntu.com/BreezyUpgradeNotes")[/QUOTE]
actually 5.04 was hoary and yes if you can you probably should upgrade to 5.10

---

### Post by aysiu on 2005-12-11
[QUOTE=GreenHawkIA]Unless you want to latest versions of all the software, it's probably not necessary.  Security updates for your distribution will be continued for another 6 months at least[/QUOTE] I thought it was eighteen months.

---

### Post by GreenHawkIA on 2005-12-11
I thought 18 months was with Breezy and the old ones were a year - but I wasn't sure so I posted 6 months at the minimum, just to not overinflate someone's hopes.  As for the Hoary/Warty things - oops.

---

### Post by SpLaTt on 2005-12-11
[http://www.ubuntuguide.org/#upgradingubuntu](http://www.ubuntuguide.org/#upgradingubuntu)

ok i went there, i typed in that first line in the root terminal and it says cannot create regular file, and no such file / dir. 

dont know what to do....


nvm, i ran it in the normal terminal, i dont get the difference

---

### Post by SpLaTt on 2005-12-11
how do you know if u have .10??? and i dont think it worked. can u explain to me how to get the zip file from the site onto the cd? ill just completely install it again.

---

### Post by Mustard on 2005-12-11
[QUOTE=SpLaTt]how do you know if u have .10??? and i dont think it worked. can u explain to me how to get the zip file from the site onto the cd? ill just completely install it again.[/QUOTE]

This command typed into terminal will tell you what version you have,

```
cat /etc/issue
```

Ironically to find the terminal program in the menus will tell you what version you have too, as in Hoary 5.04 the terminal menu choice is in Applications>>System tools, and in Breezy 5.10 its in Applications>>Accessories. :)

---

### Post by SpLaTt on 2005-12-11
ok i got .04/ and i dled the intel86 linux file. so now what do i do to it? how tp put it on the cd? it says its an image? do i need a program or something?

---

### Post by Mustard on 2005-12-11
[QUOTE=SpLaTt]ok i got .04/ and i dled the intel86 linux file. so now what do i do to it? how tp put it on the cd? it says its an image? do i need a program or something?[/QUOTE]

Its an ISO image, so it will be necessary to burn it onto a CD as an image using some type of CD burning software.

I'm sort of losing track of what operating system you are running on atm.  Do you still have 5.04 installed?  Are you doing this from a windows computer?

If you are still on 5.04 and doing all this from there, then I would suggest that you try an upgrade using the upgrade guide before you try a clean install from the a CD burnt with the new ISO you downloaded for 5.10.  If you are still on 5.04 and you want to get hold of some software to burn the ISO image to CD, the I would suggest you download and install something like gnomebaker using the synaptic package manager.  The problem with doing this is that its going to create a whole new set of questions, because you are going to have to enable extra repositories to do so, as gnomebaker is in what is called the 'universe repository' which is not enabled by default when you first install ubuntu.

Here is a link anyhow on how to enable extra repositories. 
[http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto](http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto)
Having done that succesfully you can then download and install gnomebaker and use that to burn a CD to 5.10 install disk.


If you can copy and paste the errors you receive when you try to follow the guide on upgrading in this thread then we can assist you further in the process.  The description of the error you gave earlier was a bit too vague to work out what the problem was.  When copying and pasting error messages it is helpful to include in that a copy of the command you ran that got the errors as sometimes the problem is in the syntax of the command you entered, rather than a problem with the way the system is set up.

I would mention also that if you are familiar with IRC, there is an IRC support channel for ubuntu.  You can find it at,
Channel:  #ubuntu
IRC server: irc.freenode.net

I'd highly recommend that you try IRC, as the number of questions you have is hard to answering in a forum thread without writing a whole novel each post. :)

As a side note, I think the earlier advice about logging in as root by default so you can access system files easier, is not something that I would recommend someone do.  A lot of these HOW TO's describing how you go about doing things are going to be assuming you are logged in as a normal user with superuser privileges and using sudo commands to work with system files.  By logging in as root, you are really moving into an area where you can wreck your system if you don't know what you are doing.  From the sounds of your posts so far, I would assume you have entered a pretty steep learning curve with regards to using a linux system.  It might be best if you stick with what is safe for now, rather than get too experimental.

---

### Post by SpLaTt on 2005-12-13
hmmm, i just found out that the computer im trying to run linux on has an old bios.... so the cd doesnt boot up. and i found that out after i inserted my windows cd, and wiped the harddrive... and my friend helped me make the floppy, (something aobut the file keeped getting damaged, so we did it thru the cmd prompt) but i dont see any option 2 boot from floppy, and then the cd. i looked at all the options on my bios,
dont know if this helps, but its an old compaq deskpro en series, in the 600s.

---

### Post by Zelut on 2005-12-13
I would suggest trying to update the BIOS first of all.  I recently had to do that with my web server--it didn't support HDD over 40G, nor did it boot from CD.  I found the motherboard model and found the BIOS update from the manufacturer site.

If you're willing to take the extra step to update the BIOS it might save you some headache in the future.

---

### Post by SpLaTt on 2005-12-13
but i dont have an os anymore :P

---

### Post by Zelut on 2005-12-13
You don't need an OS to update your BIOS.  You should be able to find the appropriate update using whatever connection you're using now, copy that to a floppy & update.

---

### Post by SpLaTt on 2005-12-14
hmm, ok i started the smart boot, there was alot of harddisks, one cd rom and a primary 1. when i hit enter on the cd rom i get
disk error! 0x0C

and i installed a windows os, and i can open and explore the cd from it... and i think its a disk reading error...

---

### Post by SpLaTt on 2005-12-14
and oh yeah, i downloaded irc and tried getting help. its pointless. they a just stop after a point. or just dont know. (tried getting help with above...)

ps. my bios cant be updated

---

### Post by SpLaTt on 2005-12-14
just made me anothe cd, verified it, all it good, still getiing the error msg. and this time i burnt the image onto the cd, not the seperate files..

---

### Post by Mustard on 2005-12-14
-edit-

Deleted previous questions as I was thinking of something else.

---

### Post by Mustard on 2005-12-14
[QUOTE=SpLaTt]and oh yeah, i downloaded irc and tried getting help. its pointless. they a just stop after a point. or just dont know. (tried getting help with above...)

ps. my bios cant be updated[/QUOTE]

How long did you try in IRC?

It really depends who is online and what time of the day it is as to whether someone will be around that can help with a given situation.

---

### Post by ajaustin on 2005-12-15
In your very first post you said:-

> ok, my friend gave me one of urs cds. 5.6 or something.

i installed it on an old comp, and just lately logged on. i downloaded/installed over 130 updates... and everything seem to be going right.

How did you manage to do the original install of 5.04 if your BIOS won't let you boot from CD?

Also, even if you cannot boot from the CD you can install Ubuntu using a boot floppy.  There is a file called install/sbm.bin on the install CDs for both 5.04 and 5.10 and full instructions on how to make the boot floppy at:-

[https://wiki.ubuntu.com/SmartBootManagerHowto?highlight=%28boot%29%7C%28smart%29%7C%28manager%29](https://wiki.ubuntu.com/SmartBootManagerHowto?highlight=%28boot%29%7C%28smart%29%7C%28manager%29)

But, I'm guessing, you must have made the Smart Boot floppy already as you mention it in another post.

Sounds to me like if you have burned the ISO properly you should be able to install 5.10 from the CD.

Tony

---

