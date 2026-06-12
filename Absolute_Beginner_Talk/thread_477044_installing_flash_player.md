---
title: "installing flash player"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by edat34 on 2007-06-17
I really need help bad with this. I have tried to install flash player and i still cant get it to work.

---

### Post by adityakavoor on 2007-06-17
Which architecture are u in .. i386 or amd64 ?

---

### Post by edat34 on 2007-06-17
i believe i386

---

### Post by edat34 on 2007-06-17
please, can someone help me?

---

### Post by bobplano on 2007-06-17
you may need to add some repositories but i think you can just run
```
sudo aptitude install flashplayer-nonfree
```

---

### Post by jimk0512 on 2007-06-17
Just checking, if you run Add/Remove Programs and search for Flash, you see that Macromedia Flash Player is already installed (box is checked), correct?

When you test flash player at the Adobe site, [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/), does the test for flash player say "Click here to download plugin", or "Installation complete"?

---

### Post by edat34 on 2007-06-17
home@home-desktop:~$ sudo aptitude install flashplayer-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "flashplayer-nonfree"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
home@home-desktop:~$ 
this is what i got when i typed the cmd.
yes the box is checked and when i went to the link you gave, it said installation complete for flash player. it asked me to dwn plun-in for shockwave player

---

### Post by steveneddy on 2007-06-18
Go to 

System --> Administration --> Synaptic Package Manager

Look at the very top tool bar and select Settings --> Repositories

A box launches and there a tabs. The tab on the left says "Ubuntu Software".

Check all boxes here 

Then click the Reload button.

and close the box and close Synaptic.

No do 

```
sudo aptitude install flashplayer-nonfree
```

in terminal and it will install it.

You could also, while Synaptic is open, look for flashplayer-nonfree and right click it, select Install. At the top there is a button with a check mark that says "Install". click it.

Easy....

---

### Post by edat34 on 2007-06-18
this is what i got when i typed cmd into the term; home@home-desktop:~$ sudo aptitude install flashplayer-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "flashplayer-nonfree"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
home@home-desktop:~$ 
i reinstalled flashplayer-nonfree and reloaded.

---

