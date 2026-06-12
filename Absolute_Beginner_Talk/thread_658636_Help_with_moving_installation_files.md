---
title: "Help with moving installation files"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Godmatik on 2008-01-04
I have had ubuntu 7.10 on my PC for about a week now and so far I have been able to solve all my problems with the resources available on google and these boards. I have used the terminal to compile and install several programs and I've found all the necessary dependencies with synaptic. About an hour ago I downloaded a program called Dnuos to find bitrates and find out the audio quality of all the mp3 and flac files I have. Dnuos uses python to install, so I read the readme file and followed the instructions. I unpacked the tar.gz file. Opened up terminal and went to the directory where the unpacked files were (desktop). Next I typed sudo python2.5 setup.py install, according to the readme file "This will install Dnuos into your ``site-packages`` folder, and will add a

console script named ``dnuos`` (usually in ``/usr/bin/`` or

``/usr/local/bin/``)."

Dnous is installed and working fine now, except instead of installing it in the site-packages folder (which I don't even know where that folder is located) it dumped 3 folders on my desktop, which I guess it used for the installation directory. So now I have /Desktop/dnous, /Desktop/Build, and /Desktop/dnuos.egg-info where I do NOT want them.

My question, is there an easy way to move these files without ruining the program? Or if I can't do that how do I uninstall the program and reinstall it in the PROPER directory? I have no idea where the site-packages folder is supposed to be, my guess is /etc/python2.5/site-packages, but that directory doesn't exist. the Build folder on my desktop is locked so I cannot delete it, any help that anyone could render would be appreciated! :D

---

