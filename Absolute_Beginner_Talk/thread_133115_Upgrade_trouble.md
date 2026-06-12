---
title: "Upgrade trouble"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by Iesos on 2006-02-19
I tried to ask this question in the Upgrade section of this forum, but noone would help. So here it comes again:

I can't upgrade (not trough synaptic or apt-get in the terminal)!
I have identified the problem to be something about ubuntu-docs and kubuntu-docs (yes, I do have both KDE and Gnome). It would be OK if they didn't mess up all other upgrades too. I have to select all upgrades manually in synaptic to get it to work (rather painfull). This is the total printout when running #apt-get upgrade:

> 
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  skype wine
The following packages will be upgraded:
  kubuntu-docs linux-image-2.6.12-10-386 ubuntu-docs
3 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/30.4MB of archives.
After unpacking 14.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_SE:en",
        LC_ALL = (unset),
        LANG = "sv_SE"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

Preconfiguring packages ...
(Reading database ... 189339 files and directories currently installed.)
Removing kubuntu-docs ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_SE:en",
        LC_ALL = (unset),
        LANG = "sv_SE"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Removing `diversion of /usr/share/ubuntu-artwork/home/index.html to /usr/share/ubuntu-artwork/home/index-ubuntu.html by kubuntu-docs'
dpkg-divert: rename involves overwriting `/usr/share/ubuntu-artwork/home/index.html' with
  different file `/usr/share/ubuntu-artwork/home/index-ubuntu.html', not alloweddpkg: error processing kubuntu-docs (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kubuntu-docs
E: Sub-process /usr/bin/dpkg returned an error code (1)

(I can't remove the ubuntu/kubuntu docs either.)

If noone got a clue, could some one help me with the

> perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_SE:en",
        LC_ALL = (unset),
        LANG = "sv_SE"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

warnings? I think it is something with my lang. settings (obviously). I write LaTeX documents in swedish sometimes and need to use å, ä and ö in an easy way, so i think I need that setting. I just want to get rid of the warning. (A friend helped me set it up.)

Great thanks in advance!

---

### Post by nalmeth on 2006-02-19
I have the same problem with the kubuntu and ubuntu docs. Using the gnome-update-manager, i can get around these and install any other available upgrades, simply by unselecting the misbehavers when prompted.

I have been meaning to sort this out, because it is annoying, as I like to do things in the terminal. Try apt-get remove the names of the packages. Or look into removing the .deb that are sitting there --> something to do with apt-get remove cache _program_ or something. Not entirely sure. 

If you don't get this figured out tonight, I will give a go at it. Between you and me we'll get this sorted out. Your not alone here.

BTW, I don't have any languages set up besides english, so I don't believe that is the source of the problem

EDIT:
> (I can't remove the ubuntu/kubuntu docs either.)

missed that part...

---

