---
title: "Problem installing VWware 5.0 Tools in ubunto 5.10"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by peterm on 2006-04-04
Hi list.

Having succeeded in getting ubuntu to install as a guest on VMware 5.0 I am trying to now install VMWare Tools. Following the screed to extract the tools from the .tar.gz file into the correct directory works and I can see a file vmware-install.pl
Using the recommended command line :-
sudo ./vmware-install.pl 
produces an error message :-
command not found

I cannot get a response on the vmware list so need to ask :-
what is the significance of the error message. I'm linux illiterate and this is my attempt to get a system up and running to learn a little more.
Any practical suggestions welcome.

peter
Peter

---

### Post by Stealth on 2006-04-04
Try doing this first:
```
chmod +x vmware-install.pl
```
and then the "./vmware-install.pl" command

---

### Post by trent dillman on 2006-04-04
Applications > Accessories > Terminal

```

cd /media/cdrom
sudo ./vmware-install.pl

```

---

### Post by peterm on 2006-04-04
Thanks

initial attempt failed with permissions so I tried
sudo chmod +x vmware-install.pl
and it worked.

Thanks.
Now I have another problem in that vmware-tools needs different vmhgfs modules, whatever they are. During the initial install VMware lists a dozen or so ditros but ubuntu is not among them so I selected other-lunux. 
It might be a case of going back on the VMware list now and seeing if there is an update which supports ubunto 5.0 on VMware 5.0.
Thanks.
peter

---

