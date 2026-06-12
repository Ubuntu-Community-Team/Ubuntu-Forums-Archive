---
title: "ubuntu server help,answers please"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by satelight 7430 on 2007-09-18
hello to all
I help run a small buisness (7-10 workstations) ,its a peer to peer at the moment and were looking into 
a new server. the reason for this is cause windows allways seems to be faulty at the worst times. 
were running a simple file shareing program called wintac(software) and its what the data base is working with. back to the falty times,every night the software sends a copy of itseff offsight. if everyone has'nt signed off then it doesent back up.also when printing its like everything hang for a few short seconds,then goes.so when it buisy & work orders are being wrote constantly this is verry anoying!! we need to constantly run house keeping to keep the data base clean. so I suggested 
ubuntu server to be loaded , possibvly dual boot, so we could learn as we go vs a windows small buisness version. I have foud fiesty faun to be very frendly,so far(loaded it on2 machines) and now I'm looking into a server version. to make it simple all i need is a good os to handle a data base, each workstation will handle it own e mail & virus protection. any pointers would be great,advice is expected and wanted.thanks for everything.

---

### Post by Kilz on 2007-09-18
Linux servers (not just Ubuntu) in general make good database servers. But they do not have a desktop installed by default. Something people coming over from windows may want. You can install one with a few commands. The reason is that servers normaly want to use all resources to serve things. GUI desktops use lots and lots of resources. [You might want to read this page.]("https://help.ubuntu.com/community/Installation/LowMemorySystems") While it deals with low memory systems it gives good advice on desktops that dont use a lot of resources.

You could also install Gnome, KDE, or Xfce desktops,
sudo aptitude install ubuntu-desktop
or 
sudo aptitude install kubuntu-desktop
or
sudo aptitude install xubuntu-desktop

But if you want to go with all that bloat you might as well just install a desktop version to save headache.

---

