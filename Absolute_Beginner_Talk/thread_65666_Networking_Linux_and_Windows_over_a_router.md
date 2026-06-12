---
title: "Networking Linux and Windows over a router"
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by hansoffate on 2005-09-14
This is a bit of a different question then the other post.  Sorry about it being very similar.  I was debating whether or not to post in that one but i ended up making my new thread.

Anyways, m question is, what is the easiest way to set up a network (file sharing mainly) with my windows box.  I basically just wnat to be able to transfer some important documents and music to my linux box and vice versa.  Which of the great tutorials should i follow to accomplish this.  I have read through them... but i wasn't sure if it would allow the windows and linux box to fileshare.

Thanks for your time and help
-Hans

---

### Post by xavierh on 2005-09-14
The siples way to do this is to set samba on the linux (ubutun box), share some folders, and make sure that on the dinwos machine you have an account that has the same username and password as the one you are using in ubuntu. also on the samba configuration you need to make sure that the the workgroup name is the same one that you use on the windows machine...

for example....

workgroup name: home

windows XP user: john
password: john

unbutu username: john
password: john

Try this and see if it works. DISCLAIMER: THIS IS A VERY SIMPLE SETUP THAT WILL HELP YOU ACCOMPLISH WHAT YOU REQUESTED. THIS IS IN NO WAY SECURE!!!

you can also check: [ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Nequeo on 2005-09-14
[QUOTE=xavierh]The siples way to do this is to set samba on the linux (ubutun box), share some folders, and make sure that on the dinwos machine you have an account that has the same username and password as the one you are using in ubuntu. also on the samba configuration you need to make sure that the the workgroup name is the same one that you use on the windows machine...

for example....

workgroup name: home

windows XP user: john
password: john

unbutu username: john
password: john

Try this and see if it works. DISCLAIMER: THIS IS A VERY SIMPLE SETUP THAT WILL HELP YOU ACCOMPLISH WHAT YOU REQUESTED. THIS IS IN NO WAY SECURE!!!

you can also check: [ubuntuguide.org](http://ubuntuguide.org)[/QUOTE]
 Like Xavierh said, 'samba' is definately the program you want. It's very powerful, and a little complicated to set up, but once you get it working right you'll be amazed at how well it does what you want. 

You said you'd read the guides, but weren't sure if they'd allow the machines to file-share? The Ubuntu Guide - Samba Edition -  ([http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver)) gives step by step instructions to set up file sharing between Windows and Linux. 

It's quite ..dense... however, and it's a 'do as we tell you' guide, rather than a 'this is how it works', guide. So if you have any questions about the instructions it gives, feel free to ask.

Cheers,

---

### Post by hansoffate on 2005-09-14
after typing
sudo apt-get install samba

i get this error
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

what should i do?  The first time i did it...power went out in the middle.  Well it just finished dlling it i believe.  What is wrong?

---

### Post by Nequeo on 2005-09-14
[QUOTE=hansoffate]after typing
sudo apt-get install samba

i get this error
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

what should i do?  The first time i did it...power went out in the middle.  Well it just finished dlling it i believe.  What is wrong?[/QUOTE]
 This may sound too simple, but try typing in
```

sudo dpkg --configure -a

```

The command-line is kinda like the Force. You can use it to manipulate the Universe around you (well, manipulate your computer, at least!), but you have to trust in it :)

---

### Post by hansoffate on 2005-09-14
I LOVE YOU GUYS!!!

This was painless.  I'm on my windows box right now and i can access the group.  This is awesome.  One last question... for this network question.  How do I navigate to the "workgroup computers" as windows calls it in Ubuntu.

:Edit: never mind i got it working.  Its under places incase some other newb like me needs help

---

### Post by hansoffate on 2005-09-14
I guess im wrong.  How do i find out what Ip address i have and change it to a specific one?  I want to do the same with the DNS as well?

---

### Post by Nequeo on 2005-09-14
[QUOTE=hansoffate]I guess im wrong.  How do i find out what Ip address i have and change it to a specific one?  I want to do the same with the DNS as well?[/QUOTE]
 In Ubuntu or in Windows XP?

---

### Post by hansoffate on 2005-09-14
Ubuntu.

---

### Post by Nequeo on 2005-09-14
[QUOTE=hansoffate]Ubuntu.[/QUOTE]
 On the menu:

System--->Administration--->Networking

DNS is controlled from the DNS tab, and you click on your network connection and select 'properties' to configure a static IP. 

It you just want to find out what the IP address for your machine is, type 'ip address' on the command prompt. And 'cat /etc/resolve.conf' to get your DNS settings.

Do you mind if I ask why you need static IP settings? It shouldn't be necessary to get file-sharing going with Samba.

---

### Post by hansoffate on 2005-09-14
Thanks.  It worked.  I got an off topic question.  What program plays mp3 and m4a.  I try playing them in xmms and rhythmbox and they dont work.  Do i need to dl the codecs?

---

### Post by Nequeo on 2005-09-14
Of course. :)

Many codecs, while free to download, are not 'open source' in the sense that they don't make the code publicly available. Thus, Ubuntu classifies them as 'multiverse' packages. This means you can install them yourself, if you want, but your actions are not condoned or supported by Canonical (the company behind Ubuntu).

May Linux distributions that do choose to let you play MP3s, Divx, DVDs, etc straight 'out of the box' are skirting very grey legal territory. The approach Ubuntu takes is good for two reasons. Firstly, it avoids any potential law-suits down the track, and secondly, it helps people realize there's more to MP3s than just music! 

If you go back to the Ubuntu guide I pasted a link to earlier, and search through it for 'media' and 'codecs', you'll find all the information you need to play anything you want. If you have any questions about that, though, it's probably better to start a completely new post. 

Cheers,

---

### Post by hansoffate on 2005-09-14
awesome thanks.   some of them seem to not be working. some of the codecs didn't install.  

when i try to open a .mp3 file with xmms iget this messege.  

Please check that:

your sound is configured properly (the ubuntu sounds are working)
you have the correct output plugin selected
no other program is blocking the soundcard

also which codec would allow me to open .m4a.

i believe its a lame codec but this is what happens when i try to get it
hans@hans:~$ sudo apt-get install lame
Reading package lists... Done
Building dependency tree... Done
Package lame is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lame has no installation candidate

---

### Post by Nequeo on 2005-09-15
Did you remember to add the Universe and Multiverse repositories? Follow the instructions in the guide about 'adding extra repositories' before you follow the rest of the instructions. There's usually a link to that bit of the guide at the beginning of every section.

Btw, are using Ubuntu 5.04?

---

### Post by hansoffate on 2005-09-15
no im using the new one... breezy badger i believe.  should i still follow it?

---

### Post by Nequeo on 2005-09-15
Hrm... Breezy Badger may give you some problems. The final release isn't due out until October, so you may run into a few bugs until then.

Moreover, the guide is only written for Hoary, so some of the stuff in the guide may work, and some may not.

Hrm... try this: Open up Synaptic and go to 'Settings' ---> 'Repositories'. Click 'add', then click on the 'Universe' and 'Multiverse' buttons, then click okay. Repeat that for 'Breezy Security Updates' and 'Breezy Updates'. Then press okay again.

It will ask you if you want to reload package info. Say yes.

Then close synaptic and go back to following the guide. Install as much as you can, and see how far you get.

I would also suggest installing 'beep-media-player' (the guide knows how!), which should work with MP3s at least.

---

### Post by hansoffate on 2005-09-15
k they all worked exept for the win32codecs.  The mp3 works now but the m4a doesn't work.  I think im just going to convert it or what not.

---

### Post by Nequeo on 2005-09-15
Aye, w32codecs is in Hoary extras...

I've never done much media converting, so I can't really help you from here-on... But I'm sure that after Breezy Final is released, it'll be there.

In the mean time, good luck, and let us know if you need any more help.

Cheers,

---

### Post by hansoffate on 2005-09-15
k thanks for all your help.

---

### Post by hansoffate on 2005-09-15
hehe, Another question.  I found a program that i want to install.  Its called peer guardian.  Its a .deb file what do i do?

---

