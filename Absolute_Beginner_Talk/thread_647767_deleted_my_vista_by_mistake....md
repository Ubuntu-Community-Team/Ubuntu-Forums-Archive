---
title: "deleted my vista by mistake..."
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by shucks on 2007-12-22
I deleted Vista by mistake on my laptop while trying to split Linux with Vista..I'm going to assume I can't get it back although I have the cd-key.

So anyways, just assume I'm very bad with computers, especially linux. 

How do I get sound, flash, and java and everything I need. (ex: for using youtube, adobe documents)
When I install programs like bit torrent, where do they go?
How do I see how much free space I have on my hard drive, and other specs like how much memory the currrent running programs are using?

I thought there was a way to download some bundle that allows me to play mp3s, view flash, dvds, etc all that codec stuff. As of now I can't even insert a dvd and play it or listen to an mp3.

---

### Post by kellemes on 2007-12-22
> **shucks said:**
> I deleted Vista by mistake on my laptop while trying to split Linux with Vista..I'm going to assume I can't get it back although I have the cd-key.

So anyways, just assume I'm very bad with computers, especially linux. How do I get sound, flash, and java and everything I need  for linux?

Are you sure Vista is gone?
Have you seen the output of "sudo fdisk -l" ? Is there some NTFS-partition visible?

---

### Post by kool_kat_os on 2007-12-22
on flash just look for it on the adobe site.  for java you can download it also at the sun microsystems site.

---

### Post by kellemes on 2007-12-22
> **kool_kat_os said:**
> on flash just look for it on the adobe site.  for java you can download it also at the sun microsystems site.

Better follow the Ubuntu-way..
[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")
[https://help.ubuntu.com/community/RestrictedFormats/Flash]("https://help.ubuntu.com/community/RestrictedFormats/Flash")

---

### Post by kool_kat_os on 2007-12-22
that works too...

---

### Post by shareMenaPeace on 2007-12-22
Hi,

with GUTSY i had no need to install anything extra so far ... always somethign pops up and ask me ... to make this happen make sure to enable from

MENU TAB (top panel)

Administration -> Software Sources 

enter your password and than enable (check) from Thris Party Software the 2 repositorys there...

Than use 

Admnstration .> Update Manager 
and update

Than after this is done for all things you need use

Adminstration .> Synaptic Package Manager
Load it to install stuff and enter what you ene dinto the search box ..than mark what you want.

Later for themeing ubuntu you could use also
you might start with 
getautomatix.com

and

ubuntu-tweak.com


also later for themeing thsi is nice
[http://gnome-look.org/](http://gnome-look.org/)


Cheers

---

### Post by kool_kat_os on 2007-12-22
I guess my way is a little bit harder...(again)

---

### Post by Ub1476 on 2007-12-22
Install all codecs, flash java whatever:

Open add/remove, search for "ubuntu-restricted-extras" and install it.

Ubuntu wont play encrypted DVDs by default, so take a look [here]("http://geekybits.blogspot.com/2007/10/playing-encrypted-dvds-in-ubuntu-710.html") for a simply howto.

System>Administration>System Monitor to show running programs/CPU/memory..

You can also see disk space here.

Applications ends up in Programs>Select whatever menu. In the filesystem they usually are in /usr/lib.

There are also [Screenlets]("http://www.screenlets.org/index.php/Home") if you liked Vista's gadgets.

If you like to have some Visual Effects, open System>Preferences>Appearance>Visual Effects. Select whatever you want to. If it works alright, open add/remove and install "Advanced Desktop Effects". Now you can select "custom" in Visual Effects and have some more fun:)

Please post any issues you should encounter. We're here to help!

---

### Post by kool_kat_os on 2007-12-22
Ub1476, how do you make ur avatar?

---

### Post by Ub1476 on 2007-12-22
[Downloaded it.]("http://tux.crystalxp.net/")

---

### Post by jken146 on 2007-12-22
> **shucks said:**
> How do I get sound, flash, and java and everything I need. (ex: for using youtube, adobe documents)
Sound -- should just work.  If not, please post back with more details about your problem.
Flash, Java, some codecs -- ubuntu-restricted-extras is the package you want.
PDFs -- evince document viewer is already installed.

> When I install programs like bit torrent, where do they go?
The executable files for most probrams go in /usr/bin, but other things go in other places.  You probably won't ever have to look in /usr/bin or /usr/lib.
 
> How do I see how much free space I have on my hard drive, and other specs like how much memory the currrent running programs are using?
System Monitor (in the System menu) does all those things I think.


For DVD playing, you can enable the Medibuntu repository ([www.medibuntu.org](www.medibuntu.org)) and install the package libdvdcss2.

---

### Post by markharding557 on 2007-12-22
> **shucks said:**
> I deleted Vista by mistake on my laptop while trying to split Linux with Vista..I'm going to assume I can't get it back although I have the cd-key.

So anyways, just assume I'm very bad with computers, especially linux. 

How do I get sound, flash, and java and everything I need. (ex: for using youtube, adobe documents)
When I install programs like bit torrent, where do they go?
How do I see how much free space I have on my hard drive, and other specs like how much memory the currrent running programs are using?

I thought there was a way to download some bundle that allows me to play mp3s, view flash, dvds, etc all that codec stuff. As of now I can't even insert a dvd and play it or listen to an mp3.

ubuntu-restricted-extras should sort you out 
you need to add the medibuntu.org repositorys in order to play commercial dvd and wmp files
and don't ever install that nasty vista again it restricts and controles what you do

---

### Post by markharding557 on 2007-12-22
here is a link for mediabuntu[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by shucks on 2007-12-22
whats [sudo] password? and why can't I click on quick reply?

I just installed EasyUbuntu, but I can't find it?

---

### Post by ch_123 on 2007-12-22
The password for Sudo is the same as your user password.

---

### Post by shucks on 2007-12-22
yea thats what I figured but it wouldnt work..it was asking for it on the terminal thing. But anyway, I installed easyubuntu so that I could play mp3's and stuff like that but they still don't work.

---

### Post by Orfintain on 2007-12-23
I accidentally deleted my entire hard drive by mistake , there really needs to be some kind of check  to see if you have enough space before installation begins.

I got half way though installing on a partion that was too small and I was left with two non working OSes and had to format the drive ....

---

### Post by shucks on 2007-12-23
ok so I got sound, flash, and dvd to work. But while I was trying to get java to work through the synaptic manager, I messed it up pretty bad. Now when I try to use the synaptic manager I get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

when I ran that on terminal I got this error:

sam@sam-laptop:~$ sudo dpkg --configure -a
[sudo] password for sam:
Setting up sun-java5-doc (1.5.0-13-0ubuntu1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation. You will need to go download one of the
archives:

jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download. The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

I downloaded sun-java 6 and put it in the tmp folder in root, but didn't help.

---

