---
title: "installing nvidia-glx restricted drives without internet access..."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by stil on 2007-06-28
I've just installed on an old system of mine and everything seems to be going fine (wasn't expecting that!, woop!) I want to access 3d acceleration on my gf4ti4200, so I used 
> apt-get install nvidia-glx

That was actually an educated guess on my part (learning slowly)

Turns out I need to download some specifics

nvidia-glx 1.0.8762+2.6.15.11-3

linux-restricted-moduules - 2.6-151nvidia-glx_1.0.8762+2.6.15.11-3_i386.deb

Looks alien to me! :confused: I should have written down the net address that went with the message, but now I dont have access to that machine and I need to make the most of my time while I have net access.

Firstly, where can I get these? My googlefu is failling me. Secondly, how do I go about installing the restricted drivers without 'apt-get install'

thanks

---

### Post by Seisen on 2007-06-28
you can find linux-restricted-modules  and the nvidia-glx here, just do  a search for the exact one.

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
then you can just put them on a cd or a usk key to transfer them to your computer.

---

### Post by stil on 2007-06-28
Great. Where do they go once I have them?

---

### Post by Seisen on 2007-06-28
Once you have them on your computer you need to put this in the terminal.

```
sudo dpkg -i nameoffile.deb
```
do this for both files.

---

### Post by stil on 2007-06-28
hmm, I can only find one .deb file

[this is the correct version?](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia-glx&searchon=names&subword=1&version=dapper&release=all)

---

### Post by Seisen on 2007-06-28
The first one is the one that you need and you couldn't find the  other package?

---

### Post by stil on 2007-06-28
I searched for nvidia-glx a few times and that is what came up. Is it right in front of me? :D It's almost 5am and I probably shouldn't be trying to deal with this kind of thing at this hour #-o

---

### Post by Seisen on 2007-06-28
Here is the link to dowload the one you need

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.15%2Fnvidia-glx_1.0.8776%2B2.6.15.12-28.1_i386.deb&md5sum=68eca5375d924bb485fafec25d9504c6&arch=i386&type=security]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.15%2Fnvidia-glx_1.0.8776%2B2.6.15.12-28.1_i386.deb&md5sum=68eca5375d924bb485fafec25d9504c6&arch=i386&type=security")

---

### Post by stil on 2007-06-29
Thanks, Seisen. Hopefully I'll report back here tonight with some success :)

---

### Post by stil on 2007-06-29
Ok, apparently these aren't the right ones. I get a version mistmatch between the .deb files and the nvidia kernel? (kernel of some sort) :|

I downloaded those files above because 1.0.8762 was listed under the same link as 1.0.8776, but it's a no-goer because the install demands 1.0.8762~

Odd that the version should be listed but not included/available. What am I doing wrong here?

btw i'm using ubuntu6.06 lt

---

### Post by stil on 2007-06-30
Right, I found the 8762 file on another site. Appears as though I only needed the one .deb file.

After dpkg and nvidia-glx-config enable I had to edit the xorg.conf and change the driver from nv to nvidia, and now it all seems to be working fine! woop!

---

