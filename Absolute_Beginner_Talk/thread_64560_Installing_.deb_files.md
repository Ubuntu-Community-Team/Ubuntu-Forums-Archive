---
title: "Installing .deb files"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by Storm Rider on 2005-09-11
I must be blind, looked around and can't find a newbie explanation on how to install .deb packages.

Please give me step by step instructions or a link.

Thanks you.
PS: looking to install and run Cedega, F-Prot and QtFprot.

---

### Post by Kyral on 2005-09-11
sudo dpkg -i <package>

---

### Post by Storm Rider on 2005-09-11
Thanks for the quick reply Kyral :) 

So to break it down, use Natilus to open my home folder.  Right click the .deb file and choose "extract here".  Then open a terminal and > sudo dpkg -i <package>

Is that correct ?

---

### Post by aysiu on 2005-09-11
[QUOTE=Storm Rider]Thanks for the quick reply Kyral :) 

So to break it down, use Natilus to open my home folder.  Right click the .deb file and choose "extract here".  Then open a terminal and 

Is that correct ?[/QUOTE] No. You don't need to extract the .deb.

Let's say your .deb is called opera8.0.2.deb
Without doing anything else, you would go to the directory the .deb is on (let's say it's the desktop) by typing this:

cd Desktop

then install it by typing this

sudo dpkg -i opera8.0.2.deb

---

### Post by Storm Rider on 2005-09-11
Thank you !! :)

---

### Post by Storm Rider on 2005-09-11
Can you see anything I'm doing wrong here

[B]carlton@ubuntu:/home$ sudo dpkg -i fp-linux-ws.deb
Password:
dpkg: error processing fp-linux-ws.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fp-linux-ws.deb[/B]

---

### Post by ounn on 2005-09-11
Is that the real name of the .deb?

ounn

---

### Post by Galoot on 2005-09-11
It sounds like you might have a corrupt download. Try DLing **fp-linux-ws.deb** again.

*Edited to add:*
If that doesn't do it, maybe try downloading the [f-prot-installer](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=f-prot-installer) using the following command:```
sudo apt-get install f-prot-installer
```It should let you choose whether to use the file you've already downloaded or to get a new copy directly from the F-Prot FTP site.

---

### Post by aysiu on 2005-09-11
Or maybe you're not in the right directory?

---

### Post by sophtpaw on 2005-09-11
[QUOTE=aysiu]Or maybe you're not in the right directory?[/QUOTE]


yes, i still forget, and make that mistake. To be sure and this is a good thing to know, in command line when you cd desktop (for example) to be sure the download is there do 'ls' this lists everything in Desktop. I usually download things to '/home/conrad/downloads' confirm the package is there by doing 'ls' then go ahead with sudo dpkg - <package> Now you can even cut and paste the package from the ls. This is useful when you have a very long package name with lots of numbers dashes and underscores

hope that helps,

--
sophtpaw

---

### Post by Storm Rider on 2005-09-13
Created a download directory under /home/carlton and downloaded F-prot again.  

Now this is cool...there was dependency...perl-libwww which produced an error message. A moment later the update notification lit up with system updates for libwww and a couple other files.  Installed the updates and the next thing you know, the F-Prot install picked up and finished off.   \\:D/ 

Next job, get a gui for F-Prot.  I had been using QtFprot.  Is there a Gnome based front end?

Thank for your help folks :)

---

