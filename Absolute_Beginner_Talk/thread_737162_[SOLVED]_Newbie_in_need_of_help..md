---
title: "[SOLVED] Newbie in need of help."
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Not so Superdave on 2008-03-27
New user here. Been windows used till now. So everything, every term is all brand new. I can already see how much better it is on this side of smartness, 

Trying to get the screenlets but have been having some issues/ errors. I had a friend install linux and he's been trying to help me do other things as we go. Much help would be appreciated. In very simple terms lol. Trust me. At this point I'm lost. I guess I first need to figure out how to post the errors. ```
Err http://hendrik.kaju.pri.ee gutsy/screenlets Packages
  404 Not Found
Fetched 6897B in 2s (2306B/s)
Failed to fetch http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
W: GPG error: http://hendrik.kaju.pri.ee gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.



```

This is after running the sudo apt-get update

---

### Post by tstack77 on 2008-03-27
[http://www.getdeb.net/release.php?id=2309](http://www.getdeb.net/release.php?id=2309)

getdeb has been a VERY valuable site in my few months with ubuntu. Welcome aboad!

(.deb packages are the easiest install method...just open and install!)

EDIT: sorry, didn't realize that you already had screenlets installed. for me, I just download the packages from gnome-look ([HERE]("http://www.gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=6700")) and install using the screenlets program. Hope this helps>

---

### Post by northern lights on 2008-03-27
Have you done what the error message suggests? i.e. did you run ```
sudo apt-get update
``` after you added the repository to your sources.list?

---

### Post by markekeller on 2008-03-27
And a little more information might be useful.  Are the above errors coming up when you're trying to install Ubuntu?  Or after you run a command in the terminal?  Or are they output from the Synaptic Package Manager?

---

### Post by Not so Superdave on 2008-03-27
Sorry, this is after running sudo apt-get update

---

### Post by northern lights on 2008-03-27
Crap. Then, have you tried tstack's link? If not, download the .deb from there (watch out to get the right version - i386 or x64, depending on your comp) and choose "open with GDebi package installer". Should also prove rather easy.

---

### Post by Not so Superdave on 2008-03-27
Well, I was hoping to do it this way. I'll look into that option a little later. I'm wanting to learn more about how it all works and the commands used to make it all happen. Is there a good book for the basics that explains the commands and some errors you might receive? Also how often do things change with the different versions? 

Thanks for the replies and thanks in advance for the future ones.

---

### Post by bilal.17 on 2008-03-27
the repository you entered is not working cuz the link is not working i think

there is a new one but i cant seem find it right now

---

