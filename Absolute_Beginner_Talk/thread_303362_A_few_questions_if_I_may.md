---
title: "A few questions if I may"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2006-11-20
For a long time I have been debating to switch to Ubuntu (currently running FC5)

After the last problems I've had trying to get vmware to work (as fedora runs an unsupported kernel) I'm seriously thinking into making the switch. Several of my friends also run on Unbuntu and tell me it's the dogs bolloxs!

However, there are a few things I want to know:

1) How difficult is it to install vmware? Do you have to re-build the kernel?
(Is the kernel in Ubuntu supported?)

2) What is your method of installing and uninstalling appz. Do you have anything like yum-extender? (something I swear by in FC). I want to be able to install an app and remove it as easily knowing everything has been removed.

3) Is there a installation guide (similar to [Stanton Finelsy notes]("http://www.stanton-finley.net/fedora_core_5_installation_notes.html")) that one can follow to get the most out of their box?

---

### Post by Circus-Killer on 2006-11-20
1) i have no idea

2) yes, from a comand-line we apt-get, and for those who like a gui there is synaptic package manager

3) the following guide should help you install most of what you would expect from a desktop OS: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by tribaal on 2006-11-20
Answers, in short:

1) Yes, extremely easy. You just need to install the kernel headers (a single copy/paste command line).

2) Ubuntu is based on Debian. We use the very efficient apt-get package management system. Installing stuff is only a matter of a couple of clicks.

3) Installation is pretty braindead, I don't really think there is such a thing as an install guide. Download a LiveCD, and boot it. The installation is pretty straightforward, and if you have installation questions you can sort them out while you install (since it's from a liveCD, you have net access while you install).

Hope this helps :)

- trib'

---

### Post by linuxbun on 2006-11-20
Wow, talk about support!! :D 

Many thanks for your prompt replies. Looks like i'll be formatting tonight then :mrgreen:

---

### Post by seshomaru samma on 2006-11-20
The equivilant of the Stanton guide in Ubuntu is [this ]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

---

### Post by anaconda on 2006-11-20
1. here is a quide of howto install VMWare server, which I followed without any problems.
[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto)
however VMWare player is? easier to install, because it is in the repositories.

2. I usually use synaptic package manager, but apt-get or aptitude are also quite easy. Of those 3 aptitude is the best in removing all packages(which were installed using aptitude) when you uninstall programs. Once you get all the needed repositories to your /etc/apt/sources.list you can install almost anything using any of these tree.

I have heard that one big reason for people to move to debian based distros from FC is that apt-get is much better than Yum.

---

### Post by linuxbun on 2006-11-20
Brilliant. 

Just one last night, is the latest version buggy? (FC's usally are when they first come out).

What am I best downloading, 6.10 or 6.06?

---

### Post by linuxbun on 2006-11-20
> **anaconda said:**
> 1. here is a quide of howto install VMWare server, which I followed without any problems.
[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto)
however VMWare player is? easier to install, because it is in the repositories.

2. I usually use synaptic package manager, but apt-get or aptitude are also quite easy. Of those 3 aptitude is the best in removing all packages(which were installed using aptitude) when you uninstall programs. Once you get all the needed repositories to your /etc/apt/sources.list you can install almost anything using any of these tree.

I have heard that one big reason for people to move to debian based distros from FC is that apt-get is much better than Yum.

Yup, i've read that too, also apt-get is a lot faster than yum. Vmplayer, hmm not sure. I had vmware desktop installed before. All I want to do is run 1 (possibly 2) operating systems by emulating them. Will vmplayer do that?

Cheers for the link, will check it out once installed :D

---

### Post by steve.horsley on 2006-11-20
I hvaen't seen any significant bugs in either. Edgy (6.10) feels a little faster and slicker to me.

One thing to watch for in Edgy though is that they replaced /bin/sh with a shell called **dash**, and although they claim it's "posix compliant", it seems to be breaking lots of people's scripts. As long as you know that, it's easy to fix things by re-linking sh back to bash instead (or edit the script). It's a bugger to work out what's wrong if you don't know they did it though.

---

### Post by linuxbun on 2006-11-20
> **steve.horsley said:**
> I hvaen't seen any significant bugs in either. Edgy (6.10) feels a little faster and slicker to me.

One thing to watch for in Edgy though is that they replaced /bin/sh with a shell called **dash**, and although they claim it's "posix compliant", it seems to be breaking lots of people's scripts. As long as you know that, it's easy to fix things by re-linking sh back to bash instead (or edit the script). It's a bugger to work out what's wrong if you don't know they did it though.

Cheers for that :D 

Just one other thing, I manage my backups by duplicity (locally and over ftp).

Man: [http://www.nongnu.org/duplicity/duplicity.1.html](http://www.nongnu.org/duplicity/duplicity.1.html)

As soon as I've made the switch can this be installed via your synaptic package manager? (is it in their repos?) I installed duplicity last time via yum extender. As my backups are encrypted, I need to be sure I can transfer them over again onto ubuntu.

---

### Post by anaconda on 2006-11-20
Yep..
duplicity is in the repos. (version 0.4.1-8ubuntu1)

The biggerst difference between VMWare server and Player is that with server you can make your own image files, but player can only use already made images.. 

I prefer 6.10, but its installer is a bit buggy.. really.. IT works best if you partition your hd before running the installer.

---

### Post by linuxbun on 2006-11-20
Brilliant!! :D 

Well player will do the trick for what I want then :D 

Thanks for the reply :D :KS :KS :KS

---

### Post by linuxbun on 2006-11-20
Omg, absolutely loving the change!


Just installed it. I'm surprised just how easy everything is. I have to at least spend an hour on fedora just to get the small things working, this kicks their arse! :mrgreen: 

Still busy setting it up the way I want and copying docs over.

Just a quick question about root. I went to do something that required a root password. I was unsure as I hadn't set a 'root password' so I just entered my usernames password. That worked.

On FC I had a user & root account. Do I still have this on here? Or am I signing on as root?! :confused: :eek: :eek: :eek:

---

### Post by achron on 2006-11-20
I'm new to Ubuntu as well, but if I recall correctly, the first ID created is like a virtual root id.  But in general, you aren't logging in with root powers automatically...  and you'll get prompted for the password whenever you do something "root-ish".

---

### Post by linuxbun on 2006-11-20
Ahh right, just checking, wouldn't want to be 'rooted' [-( :-D

---

### Post by anaconda on 2006-11-20
You can do as you wish.
If you are used to haveing root account you can enable it in ubuntu by giving root a password with: (if I remember correctly)
sudo passwd root

but the preferred way(the ubuntu way) is to use "sudo", and if you need to be root temporarily you can also use "sudo su"
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by CowzRule on 2006-11-20
If you installed Ubuntu Edgy Eft 6.10, here's a link that I found very useful:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

And welcome to Ubuntu :)

---

### Post by linuxbun on 2006-11-20
Brilliant. Cheers all :-D :-D

---

### Post by linuxbun on 2006-11-20
> **steve.horsley said:**
> I hvaen't seen any significant bugs in either. Edgy (6.10) feels a little faster and slicker to me.

One thing to watch for in Edgy though is that they replaced /bin/sh with a shell called **dash**, and although they claim it's "posix compliant", it seems to be breaking lots of people's scripts. As long as you know that, it's easy to fix things by re-linking sh back to bash instead (or edit the script). It's a bugger to work out what's wrong if you don't know they did it though.

It seems I've hit this already.. I've tried to configure it myself but I'm still a bit confused how ubuntu works with regards to this.

I installed i8kutils via packet manager (which is a fan controller for Dell laptops). When I try to run a fan, I get this error message:

-------------------------
can't open /proc/i8k: No such file or directory
can't open /proc/i8k: No such file or directory
    while executing
"exec /usr/bin/i8kfan {} 1"
    ("eval" body line 1)
    invoked from within
"eval $cmd"
    (procedure "i8kfan" line 12)
    invoked from within
"i8kfan {} $status($fan)"
    (procedure "toggle_fan" line 17)
    invoked from within
"toggle_fan right"
    invoked from within
".i8kmon.rfan invoke"
    ("uplevel" body line 1)
    invoked from within
"uplevel #0 [list $w invoke]"
    (procedure "tk::ButtonUp" line 22)
    invoked from within
"tk::ButtonUp .i8kmon.rfan"
    (command bound to event)
--------------------------------------

I've looked up: /proc/i8k and indeed it's not there. I can't figure out where they chucked this file either ](*,)

---

### Post by turbojugend_gr on 2006-11-20
Yup it is in the repo's (duplicity), so it's two clicks away for you ;). The version is 0.4.1 if it means anything to you.  btw make sure you follow these 2 guides when you are done, it's pretty much everything for you to start with. The first one is the official desktop guide whlile the seconds is the ubuntuguide.org one, pretty handy...

1.[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html)
2.[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Have fun m8, welcome to the Ubuntu community, we be seeing you I hope!

Cheers, TJ.

P.S.: Post asking everything here, no matter how silly you thing it is, NOONE will give you an RTFM here like the fedorians are said to do pretty often.

EDIT: oh haven't read all the post,never seen the second page there, sorry. It seems the guides are already suggested, so thumbs up from me too 'bout 'em.

---

### Post by linuxbun on 2006-11-20
> **turbojugend_gr said:**
> Yup it is in the repo's, so it's two clicks away for you ;). The version is 0.4.1 if it means anything to you.  btw make sure you follow these 2 guides when you are done, it's pretty much everything for you to start with. The first one is the official desktop guide whlile the seconds is the ubuntuguide.org one, pretty handy...

1.[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html)
2.[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Have fun m8, welcome to the Ubuntu community, we be seeing you I hope!

Cheers, TJ.

P.S.: Post asking everything here, no matter how silly you thing it is, NOONE will give you an RTFM here like the fedorians are said to do pretty often.

EDIT: oh haven't read all the post, seems the guides are already suggested, so thumbs up from me too 'bout 'em.

Yes the fedora forum was somewhat rude at times :rolleyes: :( Pleased to hear that ubuntu forums are different :D 

"In the repo's" :???: That's where I downloaded it from. I downloaded it via synaptic package manager :???: :???:

---

### Post by turbojugend_gr on 2006-11-20
M8 I haven't seen there where other pages, sorry I thought I was answering to the first page's last post, I edited my post but it seem I wasn't fast enough, sorry.

As for your issue, I would suggest searching this forums, as it is likely that another one had the same issue, so you will find how he solved it. It seems the repo's package is not up to the job. I can't help you more with this, but there is always another one that can ;).

---

### Post by linuxbun on 2006-11-21
Ok, thanks anyway :D

---

### Post by linuxbun on 2006-11-21
Found out what it was... once installed you had to: sudo modprobe i8k force=1

Works perfectly now, cheers!!! Absolutely lovin ubuntu, best os i've ever used, seriously :tongue: :grin: :grin: :grin: :grin: :grin:

---

