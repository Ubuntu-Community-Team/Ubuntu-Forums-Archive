---
title: "Switching from suse to ubuntu"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by lastredoubt on 2007-02-19
Hi,

I am currently running openSuse 10.1 on my toshiba satellite and am hoping to try out ubuntu 6.10 to see if it covers my needs a little better, or if i just like the feel of it more.  So, I have the torrent going and am going to burn the installation disc soon.  My concern is about my home directory.  If I am installing Ubuntu with the idea of getting rid of Suse, will the installation overwrite my personal files, such as music, pictures and documents, or is changing distros fairly seamless?  I am going to back up my documents, but pictures and music take up too much space for me to make it a viable option to back up.

Any recommendations or advice about this concern would be greatly appreciated,

thanks,
daniel

---

### Post by spoot on 2007-02-19
I think you'll be presented with a partitioning question somewhere at the beginning of the install process. If you pick the manual configuration, I think you can just tell the installer to use a certain existing partition as /home without formatting it.

That's at least how I remembered it, perhaps someone else could verify :)

---

### Post by hyper_ch on 2007-02-19
Yes, select "manual partitioning" or something similar. set then the right mounting point to your existing /home partition (in case you want to use it) and then select to NOT FORMAT it. Or you could create a second /home partition just for ubuntu, so your original one will be untouched...

---

### Post by Topsiho on 2007-02-19
The above solutions are correct :) but only work if /home sits in its own partition.
If not, the only option is to save all the files in your home directory (including the big ones) you want to keep AND to install the new version of Linux so that /home is installed in its own partition, which should be large enough to contain all your files AND have space enough for CD-ROM or DVD-ROM images you want to download in order to burn them. It should be larger still if you have more users. And then some more to be sure.

Welcome to Ubuntu, or Kubuntu and I hope (I mean I know) you like it tremendously. My experience is that installing new programs and updating is very much easier and faster than with other distro's (that is when I used them, for I switched to Ubuntu when it first came out, Oct. 2004 I believe. After that no Mandrake or Fedora or others for me :) ).

Topsiho

---

