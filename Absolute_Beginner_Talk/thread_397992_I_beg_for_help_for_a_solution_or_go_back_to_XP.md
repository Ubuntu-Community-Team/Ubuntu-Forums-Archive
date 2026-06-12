---
title: "I beg for help for a solution or go back to XP"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by dnguyen527 on 2007-03-31
Hey,

So, I spent over 8 hours trying to figure out how install a belkin f5f6050 wireless network card. I just installed Ubuntu on a desktop I dont use, it took me forever just to realize the winrar file I download was THE ISO file. 

I dont know anything about command lines or kernals or anything else. It took me a couple hours just to figure out where the Terminal is. I got as far as setting up ndiswrapper after I found a site that spoon fed it to me. 

Anyway, I just need the USB network adapter that I have to work so I can get online. Thats ALL  I want.

If no one will help me with that, will some one PLEASE tell me how to uninstall Ubuntu and put Windows XP back on?

I got partially sick from staring at the computer with such fustration yesterday.

:confused:

---

### Post by dnguyen527 on 2007-03-31
This site almost looked like my savior -- [http://www.astahost.com/info.php/configuring-belkin-f5d6050-802-11b-usb-wifi-device-mandriva-2007-using-ndiswrapper_t14333.html](http://www.astahost.com/info.php/configuring-belkin-f5d6050-802-11b-usb-wifi-device-mandriva-2007-using-ndiswrapper_t14333.html)

but I cant figure out how to install Unshield X - I know its some kind of program called "Alien" on Ubuntu but I cant find it. I can't find or figure out how to install any urpmi or rpm program - I dont even know what that means. 

I have the drivers for it including those CAB files they talk about...

---

### Post by Maestro23 on 2007-03-31
Some links to help:

Installing software in Ubuntu:

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

*Read thru those links so you will start to understand how Ubuntu does things.  Then take one step at-a-time.

If you find the Ubuntu is not for you, you can always pop in your handy-dandy XP disc, let it boot and install Windows again.

Don't give up so soon, though. Good luck.

---

### Post by eljalill on 2007-03-31
You find the unshield program here:
[http://rpm.pbone.net/index.php3/stat/26/dist/17/size/233987/name/unshield-0.4-1mdk.src.rpm](http://rpm.pbone.net/index.php3/stat/26/dist/17/size/233987/name/unshield-0.4-1mdk.src.rpm)
rpm is just a file type, it's a little like .zip .
You have to download that file which it should through double clicking on the link on that webpage.

Also you have to install a program called alien, which you can do through synaptic, if you have an internet connection. (If not you can download the .tar.gz file from here:
[http://www.icewalkers.com/Linux/Software/57020/Alien.html](http://www.icewalkers.com/Linux/Software/57020/Alien.html)
Double click should open it, and thenit should be self explanatory how to install)

If you have more questions, please ask!

---

### Post by dnguyen527 on 2007-03-31
Hey, thanks I am trying it now. I have NO internet connection, I am downloading stuff on my Laptop to my usb flash drive and moving it to my desktop...

---

### Post by Maestro23 on 2007-03-31
> **dnguyen527 said:**
> Hey, thanks I am trying it now. I have NO internet connection, I am downloading stuff on my Laptop to my usb flash drive and moving it to my desktop...

Ouch.  In that case, you can also get Ubuntu software(packages) at the following:

Ubuntu Packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Good luck.

---

### Post by dnguyen527 on 2007-03-31
> **eljalill said:**
> You find the unshield program here:
[http://rpm.pbone.net/index.php3/stat/26/dist/17/size/233987/name/unshield-0.4-1mdk.src.rpm](http://rpm.pbone.net/index.php3/stat/26/dist/17/size/233987/name/unshield-0.4-1mdk.src.rpm)
rpm is just a file type, it's a little like .zip .
You have to download that file which it should through double clicking on the link on that webpage.

Also you have to install a program called alien, which you can do through synaptic, if you have an internet connection. (If not you can download the .tar.gz file from here:
[http://www.icewalkers.com/Linux/Software/57020/Alien.html](http://www.icewalkers.com/Linux/Software/57020/Alien.html)
Double click should open it, and thenit should be self explanatory how to install)

If you have more questions, please ask!

Hey, I downloaded both files. 

First one ssaid "Archive type not supported" 

2nd one: I put it on there and it opens like I unzipped it with a bunch of files. I found this last night too. I am clueless as to what the README is trying to tell me. I have no idea what all those files are. 

The post before you said to go to all those sites. I saw the first one last night, no real help because I cant get online on the computer. 2nd link looked good but it said I may need the internet which explains why when I did:

Sudo aptitude update
Sudo aptitiude install alien

It said there was no such file. 


AH internet on that computer would be so helpful.

---

### Post by Maestro23 on 2007-03-31
> **dnguyen527 said:**
> Hey, I downloaded both files. 

First one ssaid "Archive type not supported" 

2nd one: I put it on there and it opens like I unzipped it with a bunch of files. I found this last night too. I am clueless as to what the README is trying to tell me. I have no idea what all those files are. 

The post before you said to go to all those sites. I saw the first one last night, no real help because I cant get online on the computer. 2nd link looked good but it said I may need the internet which explains why when I did:

Sudo aptitude update
Sudo aptitiude install alien

It said there was no such file. 


AH internet on that computer would be so helpful.

To run that .rpm file, you will need alien.  Normally you would get it thru repo's, but in your case, use the packages link I posted.

---

### Post by eljalill on 2007-03-31
I know what you mean!
The thing is, that you need the second file /program to open the first file/program.
Just a second though....

---

### Post by dnguyen527 on 2007-03-31
> **Maestro23 said:**
> Ouch.  In that case, you can also get Ubuntu software(packages) at the following:

Ubuntu Packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Good luck.

Ok, so i searched for Alien and downloaded it for Edgy which is 6.10 right? The one you can currently download on this site? 

I got the file called alien_8.64_all.deb. I clicked on it and it says "Error: Dependency is not satisfiable: debhelper"

We are so close... I think.

---

### Post by eljalill on 2007-03-31
To install alien you need to open a terminal, and then navigate to the extracted Folder.
If it is on your Desktop then type cd /Desktop/alien .
In the same terminal you then make yourself to root :
sudo su (it will ask a password, use your own password)
then type perl MAKEFILE.PL
then make
then make install .
then exit, and you are a normal user again


This is the not so elegant way... deb packages are nicer. 
Does this work? Or do you have error messages?

---

### Post by Maestro23 on 2007-03-31
> **dnguyen527 said:**
> Ok, so i searched for Alien and downloaded it for Edgy which is 6.10 right? The one you can currently download on this site? 

I got the file called alien_8.64_all.deb. I clicked on it and it says "Error: Dependency is not satisfiable: debhelper"

We are so close... I think.

Yeah, its going to be rough for you without internet.  Everything has dependencies.  At that site, it will tell you exactly what other programs a package relies on.  You will need to download them as well.

---

### Post by eljalill on 2007-03-31
Hey, I just came across something else:
here: [http://rpm.rutgers.edu/repository/ubuntu/pool/universe/u/unshield/](http://rpm.rutgers.edu/repository/ubuntu/pool/universe/u/unshield/)
You can find a tar.gz of unshield.
Then you wouldn't need alien...

---

### Post by picpak on 2007-03-31
You wouldn't need alien, but then you'd need build-essential, and the programs build-essential depends on.

---

### Post by eljalill on 2007-03-31
I see... sorry this didn't help!

---

### Post by dnguyen527 on 2007-03-31
> **eljalill said:**
> To install alien you need to open a terminal, and then navigate to the extracted Folder.
If it is on your Desktop then type cd /Desktop/alien .
In the same terminal you then make yourself to root :
sudo su (it will ask a password, use your own password)
then type perl MAKEFILE.PL
then make
then make install .
then exit, and you are a normal user again


This is the not so elegant way... deb packages are nicer. 
Does this work? Or do you have error messages?

I tried cd/Desktop/alien and it said no such directory. I do have alien on my desktop.  

I also tried cd (space) /Desktop/alien

No luck. : (

---

### Post by Maestro23 on 2007-03-31
> **picpak said:**
> You wouldn't need alien, but then you'd need build-essential, and the programs build-essential depends on.

With him being a new user, I suggest he stays away from "compiling" from source for now.:)

---

### Post by picpak on 2007-03-31
Wait a sec, you missed the obvious thing on that page...the .debs.

Download these files:

[libunshield0_0.5-3_i386.deb](http://rpm.rutgers.edu/repository/ubuntu/pool/universe/u/unshield/libunshield0_0.5-3_i386.deb)
[unshield_0.5-3_i386.deb](http://rpm.rutgers.edu/repository/ubuntu/pool/universe/u/unshield/unshield_0.5-3_i386.deb)

And copy them to the computer you're using. Then run

```
sudo dpkg -i libunshield0_0.5-3_i386.deb unshield_0.5-3_i386.deb
```

and you should be on the road to success.

---

### Post by Maestro23 on 2007-03-31
> **dnguyen527 said:**
> I tried cd/Desktop/alien and it said no such directory. I do have alien on my desktop.  

I also tried cd (space) /Desktop/alien

No luck. : (

> cd /home/username/Desktop

then type

ls (shows you what is in that directory. Should see your file)


Your Desktop directory is under[COLOR="Red"] /home/username[/COLOR]

---

### Post by picpak on 2007-03-31
> **dnguyen527 said:**
> I tried cd/Desktop/alien and it said no such directory. I do have alien on my desktop.  

I also tried cd (space) /Desktop/alien

No luck. : (

The correct path is

```
cd Desktop/alien
```

To make it easier on you, just type **cd **, and then drag and drop the folder from the desktop into the terminal. It automatically gives you the folder path.

---

### Post by eljalill on 2007-03-31
And don't forget the [space] after cd . :)

---

### Post by picpak on 2007-03-31
The terminal should really open up a short little info page about these sorts of things when you first open it up...don't you agree?

---

### Post by dnguyen527 on 2007-03-31
Hey,

I am still here working on this. Now I have a lot to work with it. It may take me a minute.

While you guys were telling me this I was following a dependacy trail. 

So I downloaded Alien from that package page, which said I nedded Debhelper - downloaded - which told me I needed Html2text - downloaded which FINALLY installed. So I am working through the trail then going to what you guys just told me. 

I am getting excited haha

---

### Post by Maestro23 on 2007-03-31
> **dnguyen527 said:**
> Hey,

I am still here working on this. Now I have a lot to work with it. It may take me a minute.

While you guys were telling me this I was following a dependacy trail. 

So I downloaded Alien from that package page, which said I nedded Debhelper - downloaded - which told me I needed Html2text - downloaded which FINALLY installed. So I am working through the trail then going to what you guys just told me. 

I am getting excited haha

Hang in there, you will get it.  Just follow the bread crumbs.:)

---

### Post by dnguyen527 on 2007-03-31
> **picpak said:**
> Wait a sec, you missed the obvious thing on that page...the .debs.

Download these files:

[libunshield0_0.5-3_i386.deb](http://rpm.rutgers.edu/repository/ubuntu/pool/universe/u/unshield/libunshield0_0.5-3_i386.deb)
[unshield_0.5-3_i386.deb](http://rpm.rutgers.edu/repository/ubuntu/pool/universe/u/unshield/unshield_0.5-3_i386.deb)

And copy them to the computer you're using. Then run

```
sudo dpkg -i libunshield0_0.5-3_i386.deb unshield_0.5-3_i386.deb
```

and you should be on the road to success.

Ok so I copied those on to my USB flash drive and moved it to my desktop with Ubuntu and opened them to install the packages. Do I still need to do that code? 

Did that just install Unshield? Haha how clueless am I? - How do I know if its installed? 


I am still folllowing that stupid trail of files just incase.

---

### Post by JosephBear on 2007-03-31
i dont understand y he is having such a hard time i have a Belkin F5D6231-4 and it hard wired just fine just clicked firefox though i am a newbie can you tell me how to get in to terminal

---

### Post by dnguyen527 on 2007-03-31
> **JosephBear said:**
> i dont understand y he is having such a hard time i have a Belkin F5D6231-4 and it hard wired just fine just clicked firefox though i am a newbie can you tell me how to get in to terminal

Sweet man. Didnt work the same for me. 

SO, the trail ended and I was able to install package Alien_8.64_all.deb.

Still dont know if I actually installed it or not. I guess Ill go back to the drivers for the f5d6050 and see if I can unzip the CAB files now. 

I think these exact directions should be posted somewhere for newbies like me.

---

### Post by Maestro23 on 2007-03-31
> **dnguyen527 said:**
> Ok so I copied those on to my USB flash drive and moved it to my desktop with Ubuntu and opened them to install the packages. Do I still need to do that code? 

Did that just install Unshield? Haha how clueless am I? - How do I know if its installed? 


I am still folllowing that stupid trail of files just incase.


Yes.  Open terminal and type:

> cd /home/username/Dekstop (puts you at your Desktop)

ls (show you what is on your desktop, should see your files)

then run your dpkg commands.

How to Install software in Ubuntu (FYI): 

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by dnguyen527 on 2007-03-31
Then, use the “unshield X” command to extract the files from data1.cab, then from data1.hdr and from data2.cab.  

Those are part of the directions from [http://www.astahost.com/info.php/configuring-belkin-f5d6050-802-11b-usb-wifi-device-mandriva-2007-using-ndiswrapper_t14333.html](http://www.astahost.com/info.php/configuring-belkin-f5d6050-802-11b-usb-wifi-device-mandriva-2007-using-ndiswrapper_t14333.html)

- How do you actually use the "unshield X" command?

---

### Post by old coot on 2007-03-31
Ubuntu is a fine linux distro. I hope you don't give up on it, but if you do, at least try
PCLOS before going back to XP.  I have a little better luck getting online out of the
box with them. sometimes the reverse is true. I'm not recommending PCLOS over UBUNTU,
just over XP.

---

### Post by Maestro23 on 2007-03-31
> **dnguyen527 said:**
> Then, use the &#8220;unshield X&#8221; command to extract the files from data1.cab, then from data1.hdr and from data2.cab.  

Those are part of the directions from [http://www.astahost.com/info.php/configuring-belkin-f5d6050-802-11b-usb-wifi-device-mandriva-2007-using-ndiswrapper_t14333.html](http://www.astahost.com/info.php/configuring-belkin-f5d6050-802-11b-usb-wifi-device-mandriva-2007-using-ndiswrapper_t14333.html)

- How do you actually use the "unshield X" command?

.

---

### Post by dnguyen527 on 2007-03-31
Ok so I think Unshield is installed. How do i use it? I need to open these CAB files.

---

### Post by delilahjed44 on 2007-04-08
> **Maestro23 said:**
> Some links to help:

Installing software in Ubuntu:

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

*Read thru those links so you will start to understand how Ubuntu does things.  Then take one step at-a-time.

If you find the Ubuntu is not for you, you can always pop in your handy-dandy XP disc, let it boot and install Windows again.

Don't give up so soon, though. Good luck.

[COLOR="DarkRed"]Hey is this true? I have the handy dandy XP windows Pro actually over windows 2000 or me, cant remember.  Any way I have sought help in several forums including this one to help me install German Programs and have had no luck, also this does not include installing the mic, which I will need to have.  Otherwise I am sick to go back to windows, I have every media player, necessary libraries and Wine and I have had no luck with a set of 3 series of German cd's.  I cant seem to fine help either, though of dual boot, just left a note on asking for help with that.  But for now I need to know if this part is true about the XP disk? 

Thank you 
Sherri[/COLOR]

---

