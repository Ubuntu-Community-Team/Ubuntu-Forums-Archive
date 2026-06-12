---
title: "Obuse OS to me"
date: 2005-06-17
forum: Absolute Beginner Talk
---

### Post by tittiger on 2005-06-17
Having trouble with the live version. Simple things like wrting to my NTFS (i believe) drive. SU to root (I have no idea what password was set) can't play mpegs or figure out how to DL the necessary codecs. All setting are always lost.
There does not seem to be any good helpf resources. (which is why I am here)
Also the default configuration is about useless in a lot of respects.

Any and all help appreciated!
Joe

---

### Post by desdinova on 2005-06-17
1) Don't use su - use sudo - for the live cd root is disabled - use your own password for sudo

2)NTFS writing is problematic at best in Linux - Blame MS for not releasing the specs.

---

### Post by tittiger on 2005-06-17
THanks :-(


Tried sudo and I get no where. Returned a lot of (to me :non senseical syntax hints)

If a disk is FAT wil it automatically mount as a RW volume?

---

### Post by Kyral on 2005-06-17
You don't use sudo the way you use su.

sudo is more like what happens when you type su -c <command> Its su for only a command. So you have to type sudo <command>.

---

### Post by desdinova on 2005-06-17
[http://www.icon.co.za/~psheer/book/index.html.gz]("http://www.icon.co.za/%7Epsheer/book/index.html.gz")

A handy little book all about linux, readable on line!

---

### Post by desdinova on 2005-06-17
Can you explain more about your issues with the Live CD - its difficult to make recommendations unless you include more info. I've only been on Ubuntu about a week after several years on MDK/Suse and I've found it the best distro so far.

---

### Post by desdinova on 2005-06-17
[QUOTE=tittiger]Having trouble with the live version. Simple things like wrting to my NTFS (i believe) drive. SU to root (I have no idea what password was set) can't play mpegs or figure out how to DL the necessary codecs. All setting are always lost.
There does not seem to be any good helpf resources. (which is why I am here)
Also the default configuration is about useless in a lot of respects.

Any and all help appreciated!
Joe[/QUOTE]

As the live cd is only meant to be a taster, you can't really add to it - to get the full desktop experience - you need to install it

---

### Post by tread on 2005-06-17
For codecs and a lot of helpful information visit [http://ubuntuguide.org](http://ubuntuguide.org) .

Welcome, you'll soon find this board is a really helpful place :)

---

### Post by tittiger on 2005-06-17
Thanks all. I have never gotten so much support so quickly.  

I will admit that I am brain damaged when it comes to Unix flavors the learning curve is just too steep as compared to the 5 or 6 other OS's that I have used, MAC, OS2, BEOS.....

I do like the new Knoppix distribution becuase even though it is live I can at least write data to my hard drive. UBUNTU however seems close to useless unless you can write data to a drive!!!

I think I will build a HD with Ubuntu this week end and see how it goes. Can I use the live version to do an install?  If not that means that I will have to doe a complete WinDOze build to get the Ubuntu ISO.
Thanks
Joe

---

### Post by tread on 2005-06-17
Unless you have the live dvd, you cannot. You need either the install cd or live dvd. Stick around, Ubuntu is the friendliest distro around.

---

### Post by desdinova on 2005-06-17
[QUOTE=tittiger]Thanks all. I have never gotten so much support so quickly.  

I will admit that I am brain damaged when it comes to Unix flavors the learning curve is just too steep as compared to the 5 or 6 other OS's that I have used, MAC, OS2, BEOS.....

I do like the new Knoppix distribution becuase even though it is live I can at least write data to my hard drive. UBUNTU however seems close to useless unless you can write data to a drive!!!

I think I will build a HD with Ubuntu this week end and see how it goes. Can I use the live version to do an install? If not that means that I will have to doe a complete WinDOze build to get the Ubuntu ISO.
Thanks
Joe[/QUOTE]

If you can use OS/2 and Beos you can learn Linux - it takes a little time and/or patience. Use that RUTE link I added and read up a little - its pretty generic Linux info.

The curve isn't steep at all,just different. And the BeOS shell (command line) was POSIX - i.e related very closely to the Bash shell.

---

### Post by desdinova on 2005-06-17
[http://www.linux-tutorial.info/](http://www.linux-tutorial.info/)
[www.linuxcommand.com](www.linuxcommand.com)
[www.linuxhomenetworking.com](www.linuxhomenetworking.com)

---

### Post by fastluck on 2005-06-17
If you want permanent root access (I hate typing sudo all the time), type this:

sudo su -

After you enter your password, you'll be root.  Then type this:

passwd

and enter your password.

Fastluck

---

### Post by tittiger on 2005-06-17
FYI
just discovered that in the live version there is a root terminal icon.
Seems that since you never set up a PW for root this is a convenient way to SU to root.....

Joe

---

