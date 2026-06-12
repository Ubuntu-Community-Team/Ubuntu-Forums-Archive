---
title: "Looking for samba gui server/client"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by madmax69 on 2007-04-07
I'm am looking for a samba GUI that covers both the server and the client functions

it needs to be able to manage accounts for the server

and it needs to be able to manage the client to mount shares and set them up to mount on reboot 

all suggestions are welcome

Cheers

---

### Post by freebeer on 2007-04-07
Have you checked into swat?  It's in the respositories.

---

### Post by madmax69 on 2007-04-07
i have not been able to get it running the tuts for it are rather vague for a linux noob

---

### Post by OriginalGrumpyOldMan on 2007-04-07
Hi, You can try GSAMBAD, which is available from the Add/Remove Applications window.

Personally I haven't had much luck with it. Between it, the built-in "Shared Folders" admin tool and manually configuring the smb.conf file, there were too many conflicts, (incl. GSAMBAD not starting anymore) I resigned myself to editing the smb.conf by hand after looking at a couple of tutorials available here, and got everything working the way I wanted.

But maybe you'll find GSAMBAD to work out for you... it's free and if it doesn't work, just remove it.

---

### Post by Radon on 2007-04-07
Although a little off-topic, YaST does what you require very well.

---

### Post by madmax69 on 2007-04-07
> **OriginalGrumpyOldMan said:**
> Hi, You can try GSAMBAD, which is available from the Add/Remove Applications window.

Personally I haven't had much luck with it. Between it, the built-in "Shared Folders" admin tool and manually configuring the smb.conf file, there were too many conflicts, (incl. GSAMBAD not starting anymore) I resigned myself to editing the smb.conf by hand after looking at a couple of tutorials available here, and got everything working the way I wanted.

But maybe you'll find GSAMBAD to work out for you... it's free and if it doesn't work, just remove it.


GSAMBAD will not do the client functions i require like mount and unmount shares from other PC's

but as a server GUI it looks very nice

---

### Post by madmax69 on 2007-04-08
> **Radon said:**
> Although a little off-topic, YaST does what you require very well.

have you got a link for that it's not in the repository's

---

### Post by lukemack on 2007-04-08
If you mean GSAMBAD it should be available in add/remove programs. However, I never got it to work and it seems that has also been other people's experience.

---

### Post by madmax69 on 2007-04-08
> **lukemack said:**
> If you mean GSAMBAD it should be available in add/remove programs. However, I never got it to work and it seems that has also been other people's experience.

no it was YaST that i cna't  find.

i had a look at GSAMBAD and it look like it might do what i need for server wise but not client wise 
however i have not tryed it yet

---

### Post by theonlyrealperson on 2007-04-08
I've been fighting with Samba all weekend too. I eventually gave up and manually configured the smb.conf file and used the "shared folder" gui as well. That seems to be the best way to do it. You could try "Komba2", but I never had any luck with it. 

I though YaST was a package tool for .rpms, like Debian's "apt-get"? Maybe I'm thinking of YUM.

---

### Post by madmax69 on 2007-04-08
> **theonlyrealperson said:**
> I've been fighting with Samba all weekend too. I eventually gave up and manually configured the smb.conf file and used the "shared folder" gui as well. That seems to be the best way to do it. You could try "Komba2", but I never had any luck with it. 

I though YaST was a package tool for .rpms, like Debian's "apt-get"? Maybe I'm thinking of YUM.

funny you say that because i've been using koomb2 since lastnight and i've had to put it in my kde autostart folder to get it to mount stuff back on boot

but it's far from a system service and a bit buggy in detecting workgroups it's also not been worked on in 6 years  

it's anoying that many apps dont suport avahi or gnomeVFS and that this samba work around needs to be used

---

### Post by Nythain on 2007-04-08
have you checked out webmin... web based server administration of your pc... covers just about every popular linux server... all controlled through your web browser... pretty spiffy stuff

---

### Post by theonlyrealperson on 2007-04-09
> **Nythain said:**
> have you checked out webmin... web based server administration of your pc... covers just about every popular linux server... all controlled through your web browser... pretty spiffy stuff

Wow, that's pretty cool, I'm going to try this out.

Thanks!

---

### Post by madmax69 on 2007-04-09
just triedjust tried webmin my self and it's very nice indeed can kiss komba, config edit and command line good bye :D

---

### Post by igknighted on 2007-04-09
> **theonlyrealperson said:**
> I though YaST was a package tool for .rpms, like Debian's "apt-get"? Maybe I'm thinking of YUM.

Yast is a gui tool set that ships with Suse.  There is a tool included within Yast called Yast2 that handles package management like synaptic.  There is also a CLI version.  Yum is a command line RPM tool comparable to apt, but ships with red hat and Fedora only.

I think the person who suggested this mean that OP should try Suse out.  I would say the PCLOS or SAM would be better choices... they use Mandriva's Drake tools and there a great Samba gui included.

---

### Post by madmax69 on 2007-04-10
> **igknighted said:**
> Yast is a gui tool set that ships with Suse.  There is a tool included within Yast called Yast2 that handles package management like synaptic.  There is also a CLI version.  Yum is a command line RPM tool comparable to apt, but ships with red hat and Fedora only.

I think the person who suggested this mean that OP should try Suse out.  I would say the PCLOS or SAM would be better choices... they use Mandriva's Drake tools and there a great Samba gui included.

So what your saying is i need nuke my ubuntu OS to change to a totaly differnet linux distro just to get the GUI i'm after?

That is anoying. I was told ubuntu/kubuntu is the closest thing to windows that linux has ever been.  
I havent had to type command line since the 80's on my commodore 64. Linux sure snaped me down, face first, with that one. :P 

Well anyhow i've found Webmin which seems to be very powerful and desptie and even tho i'm been advised not to use it because it hase some security issues.

And the fact that ubuntu has decied not to support Webmin anymore without offering a soloution is absurd.

---

### Post by igknighted on 2007-04-10
> **madmax69 said:**
> So what your saying is i need nuke my ubuntu OS to change to a totaly differnet linux distro just to get the GUI i'm after?

That is anoying. I was told ubuntu/kubuntu is the closest thing to windows that linux has ever been.  
I havent had to type command line since the 80's on my commodore 64. Linux sure snaped me down, face first, with that one. :P 

Well anyhow i've found Webmin which seems to be very powerful and desptie and even tho i'm been advised not to use it because it hase some security issues.

And the fact that ubuntu has decied not to support Webmin anymore without offering a soloution is absurd.

I'm of the opinion (and I am not alone) that Ubuntu is not the best "new user" distro, just a really solid distro all around.  If you consider the CLI "old fashioned" then you may want to reconsider your choice of OS.  There are many GUI's to avoid CLI functions at times, but you will never fully experience linux without delving into the CLI.

Ubuntu is not designed in any way to be close to windows.  In fact, many of us use [ubuntu] linux because it is NOT like windows in most ways.  Linux strives to do things well.  The system is, in its own way, incredibly intuitive and fully featured.  If you want to learn a new system, we as a community would love to help, because we think it is the best there is.  However, if you just want a free/more secure windows, then you are going to find a lot of difficulty with linux, because it is certainly not that at all.  (Don't take me wrong, I want to help, I am just warning you that you may be in for more than you think here)

---

### Post by madmax69 on 2007-04-10
> **igknighted said:**
> I'm of the opinion (and I am not alone) that Ubuntu is not the best "new user" distro, just a really solid distro all around.  If you consider the CLI "old fashioned" then you may want to reconsider your choice of OS.  There are many GUI's to avoid CLI functions at times, but you will never fully experience linux without delving into the CLI.

Ubuntu is not designed in any way to be close to windows.  In fact, many of us use [ubuntu] linux because it is NOT like windows in most ways.  Linux strives to do things well.  The system is, in its own way, incredibly intuitive and fully featured.  If you want to learn a new system, we as a community would love to help, because we think it is the best there is.  However, if you just want a free/more secure windows, then you are going to find a lot of difficulty with linux, because it is certainly not that at all.  (Don't take me wrong, I want to help, I am just warning you that you may be in for more than you think here)

off topic a little but....
Don't get me wrong either Ubuntu is awesome in it's own wright and edgy is the only linux distro I've installed for longer than a week, or two for that matter! 
I ran all the way home to winXP when i tried redhat back in 2002

I just think that it's time linux grew up and away from the CLI. Time for it to come out of it's SHELL. (lol i made a funnie) Moving away will put a nice divide between the developers and the users.

Sure it's stable and all. But when microsoftXP power users like me finally realize that VISTA is not an Affordable option they are going to come running for linux :-) and with ubuntu being the most popular distro that leaves a masinve landing pad wide open 

If users can just be left alone to point and click and just have things work CLI free, Then it will leave the forums wide open for real suggestions and real development.

for example as an XP user the only thing i have to winge about on a forum is how crappy my broadband plan is :-)

---

### Post by igknighted on 2007-04-10
> **madmax69 said:**
> off topic a little but....
Don't get me wrong either Ubuntu is awesome in it's own wright and edgy is the only linux distro I've installed for longer than a week, or two for that matter! 
I ran all the way home to winXP when i tried redhat back in 2002

I just think that it's time linux grew up and away from the CLI. Time for it to come out of it's SHELL. (lol i made a funnie) Moving away will put a nice divide between the developers and the users.

Sure it's stable and all. But when microsoftXP power users like me finally realize that VISTA is not an Affordable option they are going to come running for linux :-) and with ubuntu being the most popular distro that leaves a masinve landing pad wide open 

If users can just be left alone to point and click and just have things work CLI free, Then it will leave the forums wide open for real suggestions and real development.

for example as an XP user the only thing i have to winge about on a forum is how crappy my broadband plan is :-)

I've really got to disagree here (and this topic is now severely off topic lol).  The CLI is not something linux is every going to grow out of.  It's too useful.  I install all my programs via CLI, its way easier that a GUI like synaptic.  I'm using Fedora right now, and I don't even have a package manager gui installed (tho many are available).  Once you learn how to do things on the CLI, they become much quicker than a GUI.  And you have the ultimate power over it.  I think the real question is, "when will windows and especially OSX users (who have a working bash on their system if they dug deep enough to find it) realize that they are missing out by completely ignoring the CLI".  Mac users have the terminal but don't know where it is.  I dug it up on a friends mac and she freaked because she though I was installing a virus.  Windows users are really hosed because the shell included with windows is worthless.  Sure the CLI isn't for everything, but it has valuable roles and is an integral part of computing, one that is ignored and cast off as "old fashioned" far too much.  It's not old, its just powerful, and you need to learn it to harness that power.

EDIT: a few examples:

Say I want to install flash.  I download flash from adobe in a tarball.  I can extract it with the GUI because thats a simple right click->extract.  Now, how do you install it without CLI?  Lets say you click the root file browser button, then you navigate around, and finally drag/drop.  Takes a while and is inefficient.  Do it with the CLI... ```
tar -xvz flash.tar.gz
cp /blah/blah/libflashplayer.so /usr/lib/mozilla/plugins/
```...done.  The CLI wins do to the its simplicity in the face of awkward GUIs.

Now, installing.  Synaptic and Adept are nice, but if I have a list of programs to install I need to open synatpic and wait for it, then do a search for each item to install and wait more, select them and wait while it checks deps, then wait as it installs.  In the CLI I can add the programs I want to a list and apt-get them in one step.  Piece of cake, one command.

Don't be so quick to dis on the CLI, its NOT a weakness of linux, but a strength.

---

### Post by madmax69 on 2007-04-10
> **igknighted said:**
> I've really got to disagree here (and this topic is now severely off topic lol).  The CLI is not something linux is every going to grow out of.  It's too useful.  I install all my programs via CLI, its way easier that a GUI like synaptic.  I'm using Fedora right now, and I don't even have a package manager gui installed (tho many are available).  Once you learn how to do things on the CLI, they become much quicker than a GUI.  And you have the ultimate power over it.  I think the real question is, "when will windows and especially OSX users (who have a working bash on their system if they dug deep enough to find it) realize that they are missing out by completely ignoring the CLI".  Mac users have the terminal but don't know where it is.  I dug it up on a friends mac and she freaked because she though I was installing a virus.  Windows users are really hosed because the shell included with windows is worthless.  Sure the CLI isn't for everything, but it has valuable roles and is an integral part of computing, one that is ignored and cast off as "old fashioned" far too much.  It's not old, its just powerful, and you need to learn it to harness that power.

to sum up my argument: 
Installing apps via CLI and editing config files to change the setting of an app or to get an app to work is not for PC "users" it's for developers, programers and sys admin. 

I'm lazy as are most PC "Users". we just want to poke around and click on buttons and have things work. 

lucky for me I'm old enought to have a CLI background  good ol` c64 basic and dos to give me a push to make use of linux. Others that have grown up on M$  will be "like CLI, what's that?"

edit*

to install a M$ app all you gotta do is leech exe to desk top doubble click and it's done oh you may need a key if you had to pay for it but who pays for apps these day LOL

no apti getti command to remember or anything just leech click and done

---

### Post by igknighted on 2007-04-10
> **madmax69 said:**
> to sum up my argument: 
Installing apps via CLI and editing config files to change the setting of an app or to get an app to work is not for PC "users" it's for developers, programers and sys admin. 

I'm lazy as are most PC "Users". we just want to poke around and click on buttons and have things work. 

lucky for me I'm old enought to have a CLI background  good ol` c64 basic and dos to give me a push to make use of linux. Others that have grown up on M$  will be "like CLI, what's that?"

Linux is a system for those who like to poke and prod.  If this generation is happy with their windows computing and doesn't want to change, who are we linux users to bend over backwards to lure them off.  If they want to look around, we are here to help, but what purpose would it serve the majority of linux users who love the CLI and are tinkerers to try to ditch it to attract a user base that doesn't really care what OS they use as long as they can check their email?  After all, were not making money on this... were building a system that we want to use for ourselves, not sell.

I would not call myself a developer, programmer or sys-admin (although I do know a little java from uni), I just like the power the CLI gives me.  And who says the CLI isn't for lazy users?  I use it because I get lazy.  Its easier lots of times.

In a crude attempt to bring this back on topic, you could certainly try PCLOS or SAM Linux on live CD and try to set up samba to see if it fits your needs.  What I was told when I was learning linux that really helped me as I was struggling to get Slackware to work was that there are hundreds/thousands of distros for a reason... if one was best the others would disappear.  The fact is there are lots of great distros.  You should try several before you settle in, and go with the one that fits your needs the best.  All of them are great choices.  If avoiding CLI is a priority for you, try Suse or SAM or PCLOS (I am helping to write documentation for SAM, I think its an awesome new distro... shameless plug lol).

---

### Post by madmax69 on 2007-04-10
> **igknighted said:**
> Linux is a system for those who like to poke and prod.  If this generation is happy with their windows computing and doesn't want to change, who are we linux users to bend over backwards to lure them off.  If they want to look around, we are here to help, but what purpose would it serve the majority of linux users who love the CLI and are tinkerers to try to ditch it to attract a user base that doesn't really care what OS they use as long as they can check their email?  After all, were not making money on this... were building a system that we want to use for ourselves, not sell.

I would not call myself a developer, programmer or sys-admin (although I do know a little java from uni), I just like the power the CLI gives me.  And who says the CLI isn't for lazy users?  I use it because I get lazy.  Its easier lots of times.

.

Yeah i guess i stil remember how to load c64 games: Load"*",8,1
man thats scary remembering that 20 years later

guess i'm just an old dog not wanting to learn new tricks

but i'll BASH away cause i like you guys and I still think that linux is on the edgy of a whole new world of point a click goodness :-)

---

### Post by igknighted on 2007-04-10
> **madmax69 said:**
> Yeah i guess i stil remember how to load c64 games: Load"*",8,1
man thats scary remembering that 20 years later

guess i'm just an old dog not wanting to learn new tricks

but i'll BASH away cause i like you guys and I still think that linux is on the edgy of a whole new world of point a click goodness :-)

I can't remember quite that far back, but I do remember launching all my games out of DOS from win 3.1... and I remember actually being sad when my next computer had windows 98 because I liked DOS better... sigh, I guess it was a sign :)

---

