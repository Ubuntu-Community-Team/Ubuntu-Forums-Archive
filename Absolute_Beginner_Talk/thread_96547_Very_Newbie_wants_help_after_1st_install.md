---
title: "Very Newbie wants help after 1st install"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by jeffinhedon on 2005-11-29
Hello 
I have just installed version 5.1 onto the second hard drive of my computer. All went well and I am pleased with the desktop view and am beginning to try and navigate around.
However its a bit frustrating when you try to do some action only to be told you dont have permission??.
I cant even access my floppy or the CD rom
I have the info to install the Speedtouch drivers but I cant get permission to do anything
Why cant all devices like floppy drives and cd-ron drives and also the drive where Windows be mounted at bootup so that at least I can actually work with them
For example how can I copy the required files into the home directory if I cant "see" the floppy to copy them from
I guess my understanding of Ubuntu linux is gong to be a long process:confused: :confused: 
Any basic help and advice will be very much appreciated 
and in the meantime I will browse the WWW and hopefully gather enough info to get me going :razz:

---

### Post by ertai on 2005-11-29
(I think you have Ubuntu 5.10 installed)

The linux architecture holds the preveliged action apart from the normal action. Then you want to do any preveliged things you'll need to put 'sudo' in front.

When I put a cd in my cdrom-drive it mounts automaticly. But when yours doesn't you can mount it by going to the terminal (Applications->helptools->Terminal) and then type 'sudo mount /media/cdrom/'. Then it will mount the cdrom. And when you're finished with the cdrom you type 'sudo umount /media/cdrom/' and then you can take the cdrom out of your pc.

The floppy is readable by typing in the terminal 'sudo mount /media/floppy' and dismount can be done by 'sudo umount /media/floppy'

---

### Post by Sutekh on 2005-11-29
Your user may not be in the required groups to have access to the CD-ROM and floppy.  Groups are basically a group of users that are allowed access, in your case, a particular device.

Can you open a terminal and type in groups <username>.  Here's what happens on my PC

```

user@ubuntu:~$ groups user
user: user adm dialout **cdrom floppy** audio dip video plugdev lpadmin scanner admin multimedia
user@ubuntu:~$

```

If your user isn't in these groups, you will need to add it to them. Simple!
Again in the terminal type
```

sudo adduser <username> <groupname>

```

Where username is your user name (!) and groupname is either cdrom or floppy.

That should allow you access to them (can't think why you weren't in the first place).  If you like post the output of **groups <username>** if you need more clarification.

---

### Post by Books on 2005-11-29
[QUOTE=jeffinhedon]
However its a bit frustrating when you try to do some action only to be told you dont have permission??.
Why cant all devices like floppy drives and cd-ron drives and also the drive where Windows be mounted at bootup so that at least I can actually work with them
I guess my understanding of Ubuntu linux is gong to be a long process:confused: :confused: 
[/QUOTE]

Dear jeffinhedon,

I feel your pain. I, too, just installed Kubuntu today. It's now 6:00 in the morning and I've been up all night wrestling with Kubuntu to try to get it to dial-up with a serial modem. I finally can "dial in" but am stuck on 9600 baud. The thread is [ can't dial-up - resolv.conf trouble]("http://www.ubuntuforums.org/showthread.php?p=528943").

The **good** news is that the people here have been wonderful! Several people have gone way out of their way to be helpful to me.

The discouraging thing is that at every turn it seems like there is some strange command. I didn't even know where the terminal was. Thing is, at least I knew what a terminal is in the first place - I use wget on Windows all the time. Most Windows users don't, *and don't want to know*. I know I'll get the hang of this eventually, but it should be more intuitive than this. Recognizing a hardware serial modem should be easy, instead I was missing a file (/etc/resolv.conf) after a basic install. Until Linux can autoconfigure for most hardware configurations, and be up and playing an MP3 and surfing an hour after putting in the CD... it isn't ready for average users. A person can be smart; people are dumb. If we want people to use Linux it has to be usable by dumb people.

Maybe that's a long night of discouragement talking... ask me again after I get some sleep. Oh well, I didn't learn Windows in a day, either. ;)

This is a good place to find help. Lots of good people.

Good luck!

Books

---

### Post by AndyCooll on 2005-11-29
At work at the moment, so can't see the exact details. However, under administration go to the "Users & Groups" setting. Highlight your logon name and check the properties. Under the "Advanced" section check what privileges you have. If "allow use of floppy disk" for instance isn't ticked, then tick it. This should solve most of your problems.

Of course, as has been hinted at above, certain functions will always require administrative privileges for which you will be asked for an administrative password, but more basic stuff like use of floppies, CD-ROM's etc should just work once you've done what I've said.

:cool:

---

### Post by Kyral on 2005-11-29
Points to his sig "Terminal For Beginners"

I have a section that explains the whole permissions thing :D

---

### Post by Brunellus on 2005-11-29
[QUOTE=Books]Dear jeffinhedon,

I feel your pain. I, too, just installed Kubuntu today. It's now 6:00 in the morning and I've been up all night wrestling with Kubuntu to try to get it to dial-up with a serial modem. I finally can "dial in" but am stuck on 9600 baud. The thread is [ can't dial-up - resolv.conf trouble]("http://www.ubuntuforums.org/showthread.php?p=528943").

The **good** news is that the people here have been wonderful! Several people have gone way out of their way to be helpful to me.

The discouraging thing is that at every turn it seems like there is some strange command. I didn't even know where the terminal was. Thing is, at least I knew what a terminal is in the first place - I use wget on Windows all the time. Most Windows users don't, *and don't want to know*. I know I'll get the hang of this eventually, but it should be more intuitive than this. Recognizing a hardware serial modem should be easy, instead I was missing a file (/etc/resolv.conf) after a basic install. Until Linux can autoconfigure for most hardware configurations, and be up and playing an MP3 and surfing an hour after putting in the CD... it isn't ready for average users. A person can be smart; people are dumb. If we want people to use Linux it has to be usable by dumb people.

Maybe that's a long night of discouragement talking... ask me again after I get some sleep. Oh well, I didn't learn Windows in a day, either. ;)

This is a good place to find help. Lots of good people.

Good luck!

Books[/QUOTE]
With respect, Ubuntu can and does autoconfigure for a great many--I can't say 'most,' because I have no idea what the upper bound is--hardware configurations, at least on x86 computers.  

you didn't have to learn any of this stuff for windows because your original equipment manufacturer did all of this for you in pre-installation.  If you bought from a particularly high-volume vendor, they already had a disk image with all the necessary configuration finished and simply dumped that image, byte-for-byte onto the hard drive.

Windows isn't that great to start off with either.  Nothing works without a driver, and often drivers for important devices--like graphics adaptors--are not included with plain old windows.  

I sympathize a lot with new users because the shock of dislocation can be acute, especially if you've only ever used a single operating system/environment.  The most important thing to remember is that things are very different in Linux.  

I usually tell people who are migrating from one OS to another to think of it like moving to a foreign city:  the first days are extremely disorenting.  You don't know where anything is.  You don't know how to ask the locals for directions.  You miss home.  You're numb with culture shock.  You want your mother.

After a while, you get used to things.  You figure out where the buses/trams/trains go, and when;  you pick up the language.  You acquire a taste for the food.  You can ask for and give directions.  You know the landmarks.

It's the same in Linux.

---

### Post by jeffinhedon on 2005-11-29
Thanks folks 
you have certainly given me lots to get on with
Watch this space:p :p

---

### Post by jeffinhedon on 2005-12-01
Well Folks 
I did say "Watch this space"
I have made a lot of progress since my last posting:p 
I have successfully setup my internet connection using the instructions given 
by b3nt . His Info sheet called 
The Linux Kernel Speedtouch Driver and Ubuntu proved invaluable here:p 
Now that I am connected I felt that I am really cooking with gas:p 
There is obviously a lot more to learn but if a silver surfer newbie like me can do it 
Then anyone can:rolleyes: 
I will continue to update these comments if anyone is interested.
Cheers and beers for now:cool:

---

