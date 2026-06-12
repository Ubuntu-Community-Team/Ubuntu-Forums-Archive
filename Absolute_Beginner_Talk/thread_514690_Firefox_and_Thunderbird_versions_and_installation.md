---
title: "Firefox and Thunderbird versions and installation"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Ellipsys on 2007-08-01
Hello all. I was  wondering about a few things regarding  firefox  and thunderbird on Kubuntu.  First of all, Firefox, which came with the OS as it was installed is up to 2.0.0.5. However, I notice that the auto-update is disabled. Is there a reason for this? As my windows box is using 2.0.0.6.

Next I went to install Thunderbird from the repository using Adept. However, I noticed that the repository has Thunderbird 1.5, not 2.0. Am I just missing it, or is 2.0 not available yet for some reason?

Taking note of this I went over to the mozilla website and downloaded Thunderbird 2.0.0.5.tar.gz.  Er... what do I do with it exactly? How do I install it?  If I do install it through this method, will I be able to update it with Adept, once 2.0 becomes available on the repository? Thanks.

---

### Post by aysiu on 2007-08-01
This link will explain why the updates are disabled and will give you the means to install the latest versions of Firefox and Thunderbird quickly:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)

---

### Post by Ellipsys on 2007-08-01
Ahhh now I understand.  So if I use the python script to install Thunderbird, and then it becomes added to the repository at a later time, will apt-get/adept "understand" and upgrade it like I had downloaded it natively?

---

### Post by aysiu on 2007-08-01
> **Ellipsys said:**
> Ahhh now I understand.  So if I use the python script to install Thunderbird, and then it becomes added to the repository at a later time, will apt-get/adept "understand" and upgrade it like I had downloaded it natively?
No.

If you use the python script to install Thunderbird, you're installing the .tar.gz straight from the Mozilla website. This installation is completely independent of the repository version maintained by *apt-get* / Adept. The package manager will continue to believe the latest version of Thunderbird is 1.5, even as you're using 2.0 that the script installed.

---

### Post by Ellipsys on 2007-08-01
Thanks for your quick reply again.  What about software from alternate repositories? For instance, Wine has instructions on their site to add Kubuntu's list of "OK" apt-get repositories, will it update from those "the same way" as from ubuntu's own?  Thanks.

---

### Post by aysiu on 2007-08-01
> **Ellipsys said:**
> Thanks for your quick reply again.  What about software from alternate repositories? For instance, Wine has instructions on their site to add Kubuntu's list of "OK" apt-get repositories, will it update from those "the same way" as from ubuntu's own?  Thanks.
Yes. If software is in the repositories, it'll update when the repositories themselves update the software.

The advantage of using the python script is that it allows you to use Thunderbird's built-in update feature that receives the updates straight from Mozilla instead of waiting for a new version of Thunderbird to appear in the repositories.

---

### Post by jdelcom on 2007-08-03
I followed the instructiones everywhere to install TB 2 and I lost the 1.5 program after changing the links :(
When I try to run in console (./thunderbird in the folder it is), I get this error:

./run-mozilla.sh: 424: ./thunderbird-bin: not found

What's happening? Why can't I run the new TB? I checked and run-mozilla.sh and thunderbird-bin are in that folder (in fact, I tar -z all that)

I'm running Ubuntu 7.04 64 Kernel 2.XXX-16 (just updated). Thanks in advance.

---

### Post by nanotube on 2007-08-05
> **jdelcom said:**
> I followed the instructiones everywhere to install TB 2 and I lost the 1.5 program after changing the links :(
When I try to run in console (./thunderbird in the folder it is), I get this error:

./run-mozilla.sh: 424: ./thunderbird-bin: not found

What's happening? Why can't I run the new TB? I checked and run-mozilla.sh and thunderbird-bin are in that folder (in fact, I tar -z all that)

I'm running Ubuntu 7.04 64 Kernel 2.XXX-16 (just updated). Thanks in advance.

well... the thunderbird tar.gz builds on the mozilla site are 32bit builds, they won't run on 64bit unless you put them in a 32bit chroot. so... either figure out how to do that (i run 32bit feisty, so have no clue, personally :) ), or use 32bit feisty instead, or find a 64bit build of thunderbird (i don't know where one would look for that, though...)

hope that helps... :)

---

### Post by nanotube on 2007-08-05
oh, and you /might/ find the following information helpful:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#.5BThunderbird.2C_Firefox.5D_What_you_need_to_run_Firefox_and_Thunderbird_on_64-bit_system](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#.5BThunderbird.2C_Firefox.5D_What_you_need_to_run_Firefox_and_Thunderbird_on_64-bit_system)

---

### Post by alienexplorers on 2007-08-06
I just downloaded the tar files for Thunderbird and Firefox from the mozilla site.  I ran tar unpack in my home directory for each program.  I then setup shortcuts for both and I had both new versions along with the older versions on Ubuntu.  This way if I have a problem with the newest versions of either program I have the old program to fall back on.

---

