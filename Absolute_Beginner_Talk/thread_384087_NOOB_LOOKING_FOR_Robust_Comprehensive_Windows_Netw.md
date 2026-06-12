---
title: "NOOB LOOKING FOR: Robust Comprehensive Windows Networking APP"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by arang on 2007-03-14
hi guys, im new in this thing, the reason for which im writing this is simply because i decided to give Ubuntu a try, i just installed 6.10 and to my dismay i found out that ubuntu cant browse my LAN (it shows up to the name of the workgroup but doesnt go further than that, the same happened to me with 7.04).

Anyways, im starting to think that windows networking on Linux is flawed by design in the same way as audio support is flawed on it (yes i know im begging to be flamed), let me expand my idea. We all know that Windows XP and Vista are kind of easy (lets say dumb, yes i know they are limited with less choices yada yada yada), but the least thing i want is to be able to browse the net after installation, after given a user and password, i dont really see why there's NO app that centralize this, sure we got samba we can mount manually shares using the command line, sure we can (Supposedly cos i still cant do this on ubuntu after installation) browse the network but i wonder if there's any application that could manage this without all the mounting ,without having to edit the fstab everytime i want to "map" a drive, if there's a way to seamlessly integrate the apps (like g-streamer and others) to open data files over the net without having to mount them (yea something like /mnt/windows/share etc) there's no daemon that's able to abstract this from the whole machine making it believe that it's a local resource lets say something in another harddrive?, an app that lets me browse and map network shares without having to input user/pass all the time, and that allow fully all the operations possible in a file (things like cut and paste, play, open, extract or whatever its defined as it is in windows?). (Hope there's something that has a GUI Side not just command line to browse the net)

Am i asking for too much?, please guys refrain from pointing me to how-tos about samba, i'm looking for something that is made for blondes, yes i said it, something that even a 5 y.o. could do, cos seriously we cant expect that all the users just start editing config files, right?, there's something i can install, thats smart enough to find out the machines on the network and figure out the permissions and as i said previously, virtualize it to the (different heterogeneous) applications that i want to use?

Think about how Windows XP and after behave, i just install the thing put the user /pass and voila i have fully browsable , fully interactive, access to windows Shares, no command lines, no config files, no limitations (things like we cant do wins cos we are using dhcp and we dont have an static ip, or that the dhcp server doesnt always give us the same ip per mac) etc, i'm not asking for the moon just something that does the same no "but"s or 2nd handling, sure it's nice to have config files u can edit but keeping them optional instead of mandatory for full use could be nice.

Sorry if im not too clear about this and i know it's a tad nebulous but i tried to make it as clear as possible about what i was looking for.

As i said, point me to an app that does it all, (i wish the operative system did it all by itself a-la windows XP but i know thats asking for too much). 

Also dont forget that 99% of the times people have to deal with windows shares are to be able to do something GUI based (at least on the windows arena).

thanks guys
Frustrated user :mad: 
Arang

PD: please mention names of APPS with no shortcommings, no how-tos of samba thanks

---

### Post by orkim on 2007-03-14
I think you might be happier with the KDE desktop.  It is somewhat closer to Windows XP and it uses Konquorer just like Internet Explorer is used in XP.  I personally don't use it, but most people that I have installed Ubuntu for seem to enjoy it quite well.  There are network browsers and such which will allow you to access files without having to mount them.

I think, after reading your post, that this is most likely what you're looking for.  I would refer you to the Kubuntu site and suggest you check out the FAQ.  There is a quick "apt-get install kde" or similar line that you can run to "convert" your system to Kubuntu (add the KDE packages).

On the login screen you will need to select 'sessions' on the options panel and select KDE to log into KDE when you log out and back in.  You can set it to default if you prefer it over Gnome.

I hope that helps.  Good luck to you with KDE!

-orkim

---

### Post by maniacmusician on 2007-03-14
If you're going to use Kubuntu, I'd recommend a fresh install so Gnome packages don't mess with your KDE Menu. It's really the easiest way.

---

### Post by zorkerz on 2007-03-14
Im sorry im not entirely sure what you are looking for.  Are you simply trying to access your LAN to get shared files and printers, or are you trying to get onto the internet.  Or both.
Id start by looking here
LAN: places -> Network
Network Configuration (unless useing network manager) System->administration->network

I hope this helps but please write back and with some more info.  What errors are you getting what specifically have you tried and are you trying to do. I prolly won't be the right one to help you but...
best of luck

---

### Post by arang on 2007-03-14
sure sounds fine and dandy, but i think that somehow networking support should be in a level thats below the X, i mean, how's that our networking support depends on what window manager we choose?, so assuming what u said its true, i wouldnt have full windows networking support under XFCE? or something else?, i was asking if there's something that runs as a daemon (and no KDE LISA is nearly not an option), while keeping browsing capabilities under any  windows manager, i could be something ugly like those old X based apps of yore.

as an extra i prefer GNOME, thats just me. thanks.

something like this came into my mind

kernel--->"windows networking framework daemon"---> X based browsing/mounting/mapping app (any windows manager)
i know it sounds like asking for LISA but no LISA doesnt cut it. got anything else?

EDIT: This is all related to LAN, i know we can access internet without being able to access the windows networking file shares. (also this is not about NFS), and my main concern is that all apps know how to deal with files, but not all know how to deal with windows network shares, so u must mount the shares so those not windows networking enabled apps could access the files (i think xmms cant?) , so i reask there is nothing that could simply virtualize this thing at kernel level or in userspace in a daemon but exposing an API that can be programmed by someone so u can use a GUI based app to browse the net in the same way as we simply do in windows XP without having to deal with config files , fstab and comand lines?, also one thats event aware like if a share dissappears it just unmap /unmount or whatever with the share?.

---

### Post by orkim on 2007-03-14
Full networking support is still there.  It's just not as "pretty" as if you use KDE or similar.  Since you were referring to XP and how dumb/easy/etc it was, I was assuming that you wanted something pretty and easy to use.

You can accomplish the same networking tasks with any window manager though.  Doesn't matter.

-orkim

---

### Post by arang on 2007-03-14
> **orkim said:**
> Full networking support is still there.  It's just not as "pretty" as if you use KDE or similar.  Since you were referring to XP and how dumb/easy/etc it was, I was assuming that you wanted something pretty and easy to use.

You can accomplish the same networking tasks with any window manager though.  Doesn't matter.

-orkim

Yup i know Orkim u can use samba in command line in any window manager but as i said samba requires u to mount and unmount things, remember the old times with CD-ROMs u put them in the tray and u had to mount them and then unmount them to get the CD out of it when under windows it was just enough to push the button to get it out without the OS whining much?, i mean that kind of functionality. It's about functionality not being pretty or ugly but WITH GUI, i know some people love command lines, and its great and cool but if we have graphics capabilities in the computer and we can represent data in a better way thru those graphic capabilities why dont we use them to get things done faster and better, i remember the netware days when u could list the shares and they appeared in ur screen, but "browsing" a-la explorer style give us much better results.

---

### Post by orkim on 2007-03-14
Hrrm.  So, you're saying that you don't think it should depend on the window manger that you use as to whether you can browse network shares?  You're also saying that it doesn't matter if its ugly or pretty?  And what about a CD-ROM?  I'm not sure I get how that relates to browsing network shares.

If I follow what you are asking, and at this point I am really questioning whether I am or not, you are asking for a Windows XP like environment that is pretty and easy (enough for blondes, mind you) to use.  I'm pretty sure these are your exact words from the first post.

If this is the question, the answer is KDE.  It has all the front ends to tools to make your life easy and "respect the data" by making it easy to access.

I hope this answers your question.  Please post precise questions as they are much easier to answer.

-orkim

---

### Post by kinson on 2007-03-14
You could just use this:

```

This is the general format:
smb://[[[authdomain;]user@]host[: port][/share[/path][/name]]][?context]

```

No problem/complications for me. Or I just go to places->network (or something like that, I'm at work now), and my home windows pc's all show up. No problems whatsoever.

Cheers,
Kinson :)

---

### Post by arang on 2007-03-14
> **orkim said:**
> Hrrm.  So, you're saying that you don't think it should depend on the window manger that you use as to whether you can browse network shares?  You're also saying that it doesn't matter if its ugly or pretty?  And what about a CD-ROM?  I'm not sure I get how that relates to browsing network shares.

If I follow what you are asking, and at this point I am really questioning whether I am or not, you are asking for a Windows XP like environment that is pretty and easy (enough for blondes, mind you) to use.  I'm pretty sure these are your exact words from the first post.

If this is the question, the answer is KDE.  It has all the front ends to tools to make your life easy and "respect the data" by making it easy to access.

I hope this answers your question.  Please post precise questions as they are much easier to answer.

-orkim

what i tried to said with the CDROM metaphor is that the mount and unmount shouldnt be visible to the user, in the same way as it is invisible for the user under windows XP, now for the love of god stop hammering KDE on me, i wouldnt want this to become a KDE vs GNOME flame war please, what bothers me is that for example, right now GNOME is unable to browse my network, i see the workgroup but not the computers on them, i tried this in all the computers i have using the liveCD but all show the same problem, the same happens with feisty, also i think that most of the network browsers (not internet browsers ok?) go directly to broadcasts things on the line instead of communicating with a daemon and request it to check on it, the result is the same but a daemon could offer much more services like share and password caching and keep the "topology" in memory making things faster for example, it can also hide the whole mount and unmount ugly business from the user, in fact the user shouldnt have to modify his behavior treating networked files, compared to local files, (anyone remember NFS?) thats what im asking, i dont think that samba is the all be all of windows share networking, there isnt another group or tool or thing that does this in a better way?.

---

### Post by orkim on 2007-03-14
Samba can do everything that any Windows server can do.  Up to and including WINS support.  It is the de facto of the SMB type shares.

I think the mount/unmount debate is more of a personal preference.  But to each his own.

I'm not sure there was really a question to address other than if there was another tool besides Samba to do Windows shares.  I have read what you typed, but it seems to be more of a ramble than a direct question.

Hope that helps.

-orkim

---

### Post by ahyeop on 2007-03-15
Hi there.

I used Ubuntu 6.06LTS at my office PC on a MS WIndows network. To make my PC connected to the office network, I configure Shared Folder application in System -> Administration -> Shared Folder and then I can browse the office PC in the network using Network Server application on Places -> Network Server.

I think you have to give a credit to Ubuntu developers that makes it network browsing much more easier than using Fedora or RedHat. Although it was not as easy as WindowsXP but Ubuntu makes a browsing MS network experience much faster than Fedora. :guitar: 

Hope this help

---

### Post by rianquinn on 2007-03-21
I am looking for the same thing. For example, you cannot access a Windows Share unless you have password support enabled. You can only do this via the command line. GNOME Samba support is terrible. KDE does work well, except for the overhead of using KDE. Not to mention that most of the apps like OpenOffice and Firefox are not integrated well into KDE. No doubt though KDE is a better environment. 

I'd say this should be Ubuntu's top priority. I mean if I put in my Live CD and boot, I should be able to use a wizard (like Windows XP), answer a few questions and be able to access any windows share out there. 

I wonder if other distributions like OpenSUSE have this problem.

---

