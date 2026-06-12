---
title: "Installing packages I download"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by JayDSee on 2006-09-13
I just insyalled Ubuntu and am trying to install flash 7. I'm using Firefox and was directed to dowload flash 7 from the Adobe website. I downloaded the package to my desktop and have bee trying to use add/remove Applkication and the Synaptic mackage manager as well. My questions are:

1) Does it matter to which location I dowload the package? If so, where should I have downloaded it to?

2) How do I get the Synaptic pkg mgr to find the flsh pck I downloaded?

3) I could not find this topic in the docu. It seems that the assumtion is made that all packages will be found in repository known by Synaptic pkg mgr.   I assume that this is not tru?  Where can I find docu to help me learn about dowloading and installed pkgs?  In Windows it was just a matter of downloading and double clicking to install. Is it not the case with Ubuntu?

Thanks in advance.

---

### Post by Scarlett on 2006-09-13
I wish I could help but I'm having the same issue.  I've collected quite a few howto's and helpful hints from this site but I'm really hoping someone could just tell me where I can find all the plug-ins in the Synaptic Package Manager.  I've heard Flash and maybe Java are in there but I can't find them and a search turns up nothing.  I'm sure it's a user error but I don't know enough to know what I'm doing wrong.

However, if you're impatient, here's a great tutorial on how to install anything:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Personally, I find the Terminal to be intimidating but if you're the adventurous sort, this a good place to start getting comfortable with it.  Instead of walking you through a particular task, it outlines a little of the theory behind it:
[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)

---

### Post by meng on 2006-09-13
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by bodhi.zazen on 2006-09-13
"Easy way"> Open synaptic.

Enable extra repositories (Multiverse).

Update

search for "flashplugin-nonfree"

Install.

From the command line:

Enable the repositories, in a terminal type ```
gksudo gedit /etc/apt/sources.list
```

Remove the hash marks (#) from in front of extra repositories.

save and exit.

now in a terminal:```
sudo apt-get update
sudo apt-get install aptitude
sudo aptitude install flashplugin-nonfree
sudo update-flashplugin
```

If you have troubble with sound, re-post.

---

