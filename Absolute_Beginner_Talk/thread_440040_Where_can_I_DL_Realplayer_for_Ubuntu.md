---
title: "Where can I D/L Realplayer for Ubuntu?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by leefischer on 2007-05-11
I just installed Ubuntu two days ago.  I have some .rmvb files I want to view so i think i need to download a Realplayer that will work with Ubuntu.  Where can i get this from?   By the way, if something says it works under linux does that mean it works under Ubuntu too?    

Cheers  
Lee

---

### Post by starcraft.man on 2007-05-11
Ok, easy fix.

Please follow this [guide.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

Then, after you did the above, follow this [one.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28RealPlayer_10.29")

Make sure to do the alsa edit, some people get audio trouble otherwise. 

Very straightforward, any questions feel free to pop them in here :)

---

### Post by nanceconfer on 2007-05-11
~$ sudo aptitude install realplay
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package matching "realplay".  However, the following
packages contain "realplay" in their description:
  kmplayer-konq-plugins 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

________________________________

That's what I got when I pasted "sudo aptitude install realplay" into the terminal screen.

What do I do next? What did I miss? RealPlayer is not listed as an option under Applications -> Sound & Video.

I did go to the Software Sources screen and all the boxes were checked on the Ubuntu Software screen. I don't know if I was supposed to do something else there.

Thanks from a complete newbie.

Nance

---

### Post by Hendrixski on 2007-05-11
:-) if it works on linux, it works on Ubuntu, because Ubuntu is a Linux distribution, just like Red Hat, or SuSe, or Mandriva.  etc. etc.

Also, you don't need to type things into a terminal.  That's the **traditional** way of doing things in linux, doesn't mean you **have** to do it that way.  There's an easier way :) !!

click applications --> add-remove programs

It will bring up a list of EVERYTHING you could ever want to install.  Check out the multimedia stuff, and one of the options should be REALPLAYER.  just click on it, and hit the "APPLY" button and it will install for you.  It is really quite amazing.  and very fun.  soon, you'll be installing hundreds of programs just to try them out because you'll like it so much.

---

### Post by starcraft.man on 2007-05-11
You have to add extra repos manually, real isn't listed in the default repos. Please read first link I put :)

---

### Post by nanceconfer on 2007-05-11
Well, I have searched the choices under the Applications -> Add/Remove feature and have not found RealPlayer. It has been spiffy for other applications though.

So I have to manually add whatever a repo is.

But when I read the first link above, I am warned not to do anything that I don't understand and I sure don't understand anything beyond the first part telling me to check what I guess you are calling the defaults.

Is there some clear enough even for a complete newbie way to explain how to do whatever it is I have to do to install RealPlayer? What you have at the first link is no doubt clear to you, but it is Greek to me.

Thanks.

Nance

---

### Post by rich.bradshaw on 2007-05-11
Go to System/Admin/Software Sources,

you can add in what ever he told you there.

Then go back to add/remove and it will be there.

Repo (short for repositories) are large groups of pieces of software. By adding one, you are saying that you trust the owner and you trust what is in it. You shouldn't add a repo unless you are confident that this is OK, as if the software their has malware etc in it, then you won't realise.

Most are OK, but just realise what it means when you add one!

---

### Post by nanceconfer on 2007-05-11
OK now before I completely mess everything up --

I go to System -> Admin -> Software Sources.

Then I go to third-party software -- right??

And click Add.

And then I am asked to:

Enter the complete APT line of the repository that you want to add as source.

What is that?

Thanks.

Nance

---

### Post by e6626550w on 2007-05-11
> **leefischer said:**
> I just installed Ubuntu two days ago.  I have some .rmvb files I want to view so i think i need to download a Realplayer that will work with Ubuntu.  Where can i get this from?   By the way, if something says it works under linux does that mean it works under Ubuntu too?    

Cheers  
Lee

Go get automatix2 first. [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.3-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.3-7.04feisty_i386.deb)

I assume you are using Feisty. Clink on the link above and you'll see a odd looking icon on your desktop almost instantly. Then right click the icon and it should give you the option of opening the gismo with gbebi installer. If you don't have gdebi, then go to sys - adm and click on the synaptic package installer and do a search for gdebi and download and install it. I can't remember if it is included in the standard Ubuntu installation or not. 

Anyhow, the point is to get gdebi to install automatic2 for you. Automatic2 has realplayer and other goodies which aren't that easy to find especially if you are brand new to Linux. This is all off the top of my head,( other than the url which I looked up for you)  so if it doesn't work, shoot me. 

Incidentally, the Linux Realplayer isn't nearly as complete as the one for windows. VLC will also play MP3's too. You can get that via synaptic and I just noticed it is in automatix too.

With the Media Player Connectivity plugin for firefox, you can also watch MLB. TV with VLC even though they don't support Linux. After some one showed me how to do that I get rid of windows on my computer. 

eileen...

eileen...

eileen...

---

### Post by ridgerunner7 on 2007-05-12
Nance,
Yes you're right. In the APT repo line paste this:

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

However you will still need to add the repo's pgp key to apt by pasting this geeky thing on the command line:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

However, that will require you to know your superuser password.

---

### Post by nanceconfer on 2007-05-12
I pasted:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

on my Terminal page.  Put in my password. It said OK.

Then I pasted:

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

in the apt repo line. I reloaded as prompted. 

Then I went to c-span.org and tried again. I clicked on the Real option on C-Span2. I heard a snippet of audio but no video. I did see the Real logo on the C-Span screen. 

Suggestions?

Nance

---

### Post by jiminycricket on 2007-05-12
[https://help.ubuntu.com/community/Repositories/Ubuntu#head-b75a0c6c7e357640731529980d3f3ad3614b9a76](https://help.ubuntu.com/community/Repositories/Ubuntu#head-b75a0c6c7e357640731529980d3f3ad3614b9a76)

Realplayer is also in the canonical commercial repositories

---

### Post by enopepsoo on 2007-05-12
maybe I am a dumb ***, but I don't see realplayer in the plf repository

---

### Post by enopepsoo on 2007-05-13
I think that the only thing currently in the feisty commercial repos is vmware server.

---

### Post by trippinnik on 2007-05-13
how about realplay?  I haven't actually gotten it to work though...

---

### Post by akpower on 2007-06-06
I have installed Realplayer in Ubantu.
however, it is not executable.....

---

### Post by cjssmo on 2007-06-06
You can do this

sudo apt-get install gdebi

Then go to 

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Click on your Ubuntu version

Click open with Gdebi

click Application ->System Tools->automatix

Click on Media Players and Editors->RealPlayer

click start and your done

hope this helps someone

---

### Post by ugm6hr on 2007-06-06
My entry here:
[http://ubuntuforums.org/showthread.php?t=454622](http://ubuntuforums.org/showthread.php?t=454622)

Gives an eaiser Fiesty option for Realplayer installation (download, double-click, done with menu entry).

---

### Post by akpower on 2007-06-06
> **cjssmo said:**
> You can do this

sudo apt-get install gdebi

Then go to 

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Click on your Ubuntu version

Click open with Gdebi

click Application ->System Tools->automatix

Click on Media Players and Editors->RealPlayer

click start and your done

hope this helps someone
Thank you!

I still can't open realplayer in my ubantu......
that's wired.

---

