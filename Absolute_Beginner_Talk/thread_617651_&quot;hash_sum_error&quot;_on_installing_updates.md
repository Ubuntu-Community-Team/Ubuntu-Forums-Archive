---
title: "&quot;hash sum error&quot; on installing updates"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2007-11-19
I just installed Gutsy on the desktop machine in my house. When I went to install automatic updates, all but three downloaded and installed properly. I checked around here on the forums, and stumbled on what looked like a solution; I tried it, and two of the three remaining updates came down fine. I still have an issue with one, and I'm wondering what I might do to resolve it.

When I hit "Install Updates," it looks like it's downloading fine, but just as it finishes, I get the following message:
```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22-14-generic_2.6.22.4-14.10_i386.deb
Hash Sum Mismatch
```

It gave me the same message with the two that I solved; in order to fix those, I went in and commented the "cdrom" line in my sources.list file. That hasn't seemed to work with the one remaining.

What shall I do?

---

### Post by doctorbighands on 2007-11-19
I tried to install Jokosher in the terminal just now, and I'm getting "hash sum mismatch" errors all over the place. Something tells me the CD I used to install Gutsy was corrupt in some way, and I should re-install. I'll try it now and see if it makes a difference.

In the meantime, if anyone has any other ideas or recommendations, please let me know!!

---

### Post by doctorbighands on 2007-11-19
Okay, now I'm lost.

I re-installed Gutsy. Before I did that, I did a checksum on the ISO, which was fine; I then checked the disc for errors using the installed utility on the live CD, and that was fine, too.

I went in and un-commented the relevant lines in my sources.list file, and ran a sudo apt-get update, and it didn't even finish that. There was a bunch of stuff about how "the compressed file may have become corrupted" or something. In addition, when I went to install the nvidia-glx driver with the Restricted Drivers update, I received another "hash sum mismatch" error.

What's going on?! I've installed Gutsy successfully on three machines before this one, and I've never seen this problem.


EDIT: I should note that Feisty was installed successfully on this machine prior to my upgrade attempt, and I never saw anything about a hash sum mismatch. If this is something to do with the nvidia driver, it wasn't an issue in Feisty.


SECOND EDIT: The apt-get update finished (finally), but I did still receive the aforementioned "compressed file corrupted" message. The exact message is as follows:```
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://us.archive.ubuntu.com gutsy/main Packages                           
  Sub-process bzip2 returned an error code (2)

```

---

### Post by doctorbighands on 2007-11-19
Now there's a new issue!!

I tried to go back into the terminal in an attempt to complete an update. I type in```
sudo apt-get update
```
and it returns the following message:```
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
```

?!?!

EDIT: A reboot solved this issue. Go figure. Everything else remains a problem, though!!

---

### Post by doctorbighands on 2007-11-19
Maybe this message will help, too. I try to enable the restricted nvidia driver, and this is what I get:```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/nvidia-glx_1.0.9639+2.6.22.4-14.10_i386.deb
  Hash Sum mismatch
```

---

### Post by doctorbighands on 2007-11-19
*bump*

Anyone?

---

### Post by doctorbighands on 2007-11-19
The more I fight with this issue, the more it seems to be a problem with the nvidia graphics card driver ("nvidia-glx"). I really don't know what do to about this.

---

### Post by doctorbighands on 2007-11-19
Have I stumped everyone on here? I find that hard to believe.

Please help if you can!

---

### Post by doctorbighands on 2007-11-19
*bump*

Still need help...

---

### Post by doctorbighands on 2007-11-19
*bump* again...

---

### Post by Partyboi2 on 2007-11-19
try using  aptitude instead of apt-get, 
```
sudo aptitude update
``````
sudo aptitude install nvidia-glx-new
```I read somewhere that this helped some people out that were getting the
Hash Sum mismatch error with apt while trying to install packages. 
(not sure if it is related)

---

### Post by doctorbighands on 2007-11-19
I tried two ways:```
sudo aptitude install nvidia-glx-new
```
and```
sudo aptitude install linux-restricted-modules-2.6.22-14-generic
```
and I still get a Hash Sum mismatch error each time.

*SIGH*

---

### Post by jbguev on 2007-11-20
I am getting the same error when trying to install the build-essential package using both synaptic and apt.  Any help would be greatly appreciated.

Jerry

---

### Post by jbguev on 2007-11-20
I disabled the CD-ROM for gutsy gibbon in the repositories and then retried downloading the build-essential package, and it worked just fine.  I still have no idea what is wrong with my install CD, since this is the third time I've installed Ubuntu from it.  Any explanations?????

Jerry

---

### Post by pikmaster on 2007-11-23
It seems the problem is related to apt and the way it handles the hashes. From what I have found, apt in version prior to 0.6.7 was working OK. Unfortunatelly, with upgrading to gutsy, apt version changed to 0.7.6

Some solution was to switch from local ubuntu repositories (like 
deb [http://**pl](http://**pl).**archive.ubuntu.com/ubuntu/) to the main one 
(deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)), but not all the packages are downloaded properly. 

In my case, there is no CDROM repositories in /etc/apt/sources.list, but the problem still exists.
Also, installing nvidia-glx-new didn't help (it is strange, that someone claimed it did, because the error lies elsewhere).

I also found that sometimes you are able to download the packages with *wget* and install them manualy by typing
  sudo dpkg -i *my.downloaded.package*.deb

I think this bug should be reported to apt maintainers, but I don't know how yet.


Pik Master

---

### Post by Partyboi2 on 2007-11-23
> **pikmaster said:**
> 
I think this bug should be reported to apt maintainers, but I don't know how yet.
Pik Master
If you believe you have a bug,
this will explain how to go about filing  a bug report
[http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)
:)

---

### Post by pikmaster on 2007-12-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/173932](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/173932) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				For all who may be interested - I created a launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/173932](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/173932)

---

### Post by hmus on 2008-01-13
exactly the same problem i have on my computer...what should be done?

---

