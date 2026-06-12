---
title: "Ubuntu on a PC without Internet Connection"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2006-05-25
I was wondering if its worth it to install ubuntu on a pc without an internet connection becuase i cant install software through synaptic without an internet connection or can I?:confused: :confused: :confused: :confused: :confused:

---

### Post by IYY on 2006-05-25
It's possible to use CD repositories, or just install debs. But the way Ubuntu is set up right now, it might not be the best idea. Could be quite frustrating. Distributions like Fedora Core might be more suitable.

---

### Post by nanotube on 2006-05-25
or you could download and burn the entire repository contents onto a few dvds, from this site:
[http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en)
and then use the dvds.
but like IYY says, a net connection makes the experience so much nicer. :)

---

### Post by t[h]inker on 2006-05-25
Half year ago, I was in the same situation as you.
I had Breezy installation on my brothers computer (which is connected), but my own PC (in another city) was pernamently off-line. :(
So, I had to decide what I exactly need for my box (codecs, programs, etc...), then brought it my to my brother, borrow his net adapter card and install EVERYTHING what I needed.
As you may ques, it was pain, but it has been working realy good, much better than attemps to download the debs (packages), burn them on CD a try to install them with "dpkg -i foobar.deb"... ](*,) 
The problem was in package dependencies, of course.

So, these are *my* experiences: It's technically possible, but not so easy. Perfect solution is good neighbor with internet connection and one huge install-session for everything essencial ;)

---

### Post by youthforlinux on 2006-05-25
[QUOTE=nanotube]or you could download and burn the entire repository contents onto a few dvds, from this site:
[http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en)
and then use the dvds.
but like IYY says, a net connection makes the experience so much nicer. :)[/QUOTE]

how many cds would it take:confused: ](*,)

---

### Post by nanotube on 2006-05-25
[QUOTE=youthforlinux]how many cds would it take:confused: ](*,)[/QUOTE]

erhm... many. there are 3 dvds, each dvd is about 4.7 gigs... divide that by 0.7gig per cd, and you get about 20.1 cds. but at any rate, these will probably come as .iso, so you will have a hard time breaking these up.
if you have the disk space, you could just leave these dvd iso files on your harddrive, and mount them directly, without burning to cd. i think that would be better than trying to burn cds. .

---

### Post by hollywoodb on 2006-05-25
I disagree with "Ubuntu might not make the best choice" arguments... If you're happy with the default Ubuntu/Kubuntu/Xubuntu applications & games then the Ubuntu release cycle will suit you very well... You don't really have to worry about security updates and such being there's no internet connection.

However if you want to install a bunch of extra packages, then the options already mentioned are the way to go, despite the hassle.  In this case you might want to search for a distrubution with a sane release cycle that includes everything you want.

---

### Post by catlett on 2006-05-25
Ubuntu is big on having a one cd setup. This keeps the base system that they offer pretty basic. If your needs are basic then you are fine. But if you want or need to customise your system, you are going to have to  be imaginative (like the ideas posted)
Ubuntu's thing is 1 cd install the Just Works and anything else needed can be installed through online repositories.
FC5 is proobably the best for a non internet connection. The install has 5 cds. 2 do the install and the other 3 are  repositories on cd. If you pick a package it will prompt you to insert cd 4 and it will load the package from there. Ubuntu doesn't have an extra apps cd. You would have to make it yourself.

P.S. Nanotube,  kudos on your "beenie of the month"!

---

### Post by Mustard on 2006-05-25
[QUOTE=hollywoodb]You don't really have to worry about security updates and such being there's no internet connection.[/QUOTE]

That's not totally true, as at least one bug that came up with Breezy Badger is not going to be fixed without a security update ie the debconf bug that left the password plainly visible in the install log.   It's would be easy to fix by simply using a different password than the one used during the install, but nevertheless, some Breezy Badger people will be out there using Ubuntu who haven't done security updates, with this security flaw still sitting on there computer, just waiting for someone with the inclination and opportunity to exploit it.

The OP is using Dapper Drake though, so I suppose its not as relevant, but nevertheless, something could come up in the future. :)

-edit-

The same problem exists for using a vanilla copy of Windows, without an internet connection I suppose.

---

### Post by hollywoodb on 2006-05-25
[QUOTE=Mustard]That's not totally true, as at least one bug that came up with Breezy Badger is not going to be fixed without a security update ie the debconf bug that left the password plainly visible in the install log.   It's would be easy to fix by simply using a different password than the one used during the install, but nevertheless, some Breezy Badger people will be out there using Ubuntu who haven't done security updates, with this security flaw still sitting on there computer, just waiting for someone with the inclination and opportunity to exploit it.

The OP is using Dapper Drake though, so I suppose its not as relevant, but nevertheless, something could come up in the future. :)

-edit-

The same problem exists for using a vanilla copy of Windows, without an internet connection I suppose.[/QUOTE]

I was thinking more along the line of a single-user desktop with no outside connectivity... I guess in the case of a shared workstation the security updates would be of importance.

---

### Post by Mustard on 2006-05-25
[QUOTE=hollywoodb]I was thinking more along the line of a single-user desktop with no outside connectivity... I guess in the case of a shared workstation the security updates would be of importance.[/QUOTE]

On reflection I think I was being a bit pedantic. :)

---

### Post by nanotube on 2006-05-25
[QUOTE=catlett]
P.S. Nanotube,  kudos on your "beenie of the month"![/QUOTE]
:D

---

### Post by youthforlinux on 2006-05-26
[QUOTE=nanotube]erhm... many. there are 3 dvds, each dvd is about 4.7 gigs... divide that by 0.7gig per cd, and you get about 20.1 cds. but at any rate, these will probably come as .iso, so you will have a hard time breaking these up.
if you have the disk space, you could just leave these dvd iso files on your harddrive, and mount them directly, without burning to cd. i think that would be better than trying to burn cds. .[/QUOTE]

what about a usb drive?
could i copy the images to that????

---

### Post by nanotube on 2006-05-26
[QUOTE=youthforlinux]what about a usb drive?
could i copy the images to that????[/QUOTE]
sure, as long as it's big enough to store 15 gigs :)

---

### Post by youthforlinux on 2006-05-26
[QUOTE=nanotube]sure, as long as it's big enough to store 15 gigs :)[/QUOTE]
yeah its 300gb
how do i copy the images to it?

---

### Post by gr0kzer0 on 2006-05-26
When I installed Ubuntu on my computer I had no internet connection; I was in that situation for a couple of months.  If I wanted anything new, I used a Windows computer at the library, put the program or whatever on a CD-R, and took that home.

But I didn't need anything extra really - all I downloaded at the library was music files.

It's much better to be online, but it's certainly not mandatory.

---

### Post by youthforlinux on 2006-05-26
yeah i think i could do something like that too

---

### Post by nanotube on 2006-05-26
[QUOTE=youthforlinux]yeah its 300gb
how do i copy the images to it?[/QUOTE]
well, just download the ISO files (using bittorrent) from the site i gave you, either directly to the usb drive, or copy them over afterwards. you know, the iso's are just regular files. big, but regular. :)

then once you have them on there, use command 'mount' with the proper options, to mount the iso image files directly. (i forget the exact syntax, but search the forums, you will find it. it's something with "loop" in it...)

oh and a comment: you have a 300gb spare hd just sitting around, and you dont have internet?? i have internet but no 300gb hd. you wanna trade? hehe, j/k, i can't live without my internet. ;)

edit: ah, here is an easy way to mount iso: use the "nautilus script to mount iso files" from this page: [http://doc.gwos.org/index.php/Nautilus_Scripts](http://doc.gwos.org/index.php/Nautilus_Scripts)

---

