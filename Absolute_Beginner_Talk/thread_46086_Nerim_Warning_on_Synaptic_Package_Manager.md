---
title: "Nerim Warning on Synaptic Package Manager"
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by Weta on 2005-07-03
Hello

The following warning appears when I open Synaptic Package Manager:  "W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)"

I found some references to Nerim problems on other Ubuntuforums, but I couldn't understand the suggested advice.  Hence this post on the Beginner forum..

Using File manager, I see that I have eight "ubuntu-backports" files and two "ftp:nerim.net" files.  The nerim files are:  

ftp:nerim.net_debian-marillat.dists_testing_Release
ftp:nerim.net_debian-marillat.dists_testing_Release.gpg

It seemed to me that the previous forum advice was that the nerim files aren't  required by most users.  Is someone able to tell me whether I should therefore delete the two nerim files to address the warning?  Or should I keep the files, and do something different (e.g. try to install a "key"), or do nothing and hope this warning will be resolved when the next update is released?   

Thank you

Weta

---

### Post by Xian on 2005-07-03
[QUOTE=Weta]The following warning appears when I open Synaptic Package Manager: "W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)"[/QUOTE]
You generally get this warning message when there are repo entries in the sources.list file that have not been placed into the Apt cache, which is just to say that 'apt-get update' has not be run recently.

---

### Post by ceti on 2005-07-03
[QUOTE=Weta]Hello

Is someone able to tell me whether I should therefore delete the two nerim files to address the warning? Or should I keep the files, and do something different (e.g. try to install a "key"), or do nothing and hope this warning will be resolved when the next update is released? 

Thank you

Weta[/QUOTE]

Actually, you better get rid of them. Please read this, first (if you haven't yet):

[http://www.ubuntuforums.org/showpost.php?p=194471&postcount=5](http://www.ubuntuforums.org/showpost.php?p=194471&postcount=5)

Then click here:. [How to add extra repositories?]("http://ubuntuguide.org/#extrarepositories"), which is the first question on the Repositories section of the Unofficial Guide, to build your sources.list only with the default repos.

Cheers

---

### Post by Weta on 2005-07-04
Thank you for each reply.  

It looks like I need to learn how to use the command line.  A bit intimidating, but I will give it a try.  

Weta

---

### Post by aysiu on 2005-07-04
[QUOTE=Xian]You generally get this warning message when there are repo entries in the sources.list file that have not been placed into the Apt cache, which is just to say that 'apt-get update' has not be run recently.[/QUOTE] The Synaptic Package Manager equivalent of *apt-get update* is just hitting the "Reload" button. I wouldn't delete the nerim repository necessarily. It doesn't do any harm. Sure, if you still get that error message after hitting "Reload" or typing *apt-get update*, you can get rid of it.

The command-line is super easy if you follow the steps (it's just cutting and pasting). If it seems a bit much for you, Mepis is a great distro that can do all of this via GUI (including adding extra repositories).

---

### Post by Weta on 2005-07-04
Hello Again

I couldn't resist having a go at using the command line.  The original text wasn't quite the same as on the Ubuntu Guide, but I just deleted two "extra" lines and added two missing ones.  As aysiu said - it's just cutting and pasting.  

Synaptic nows runs without the warning.  Problem fixed!  Thanks again for the advice (and encouragement).

---

