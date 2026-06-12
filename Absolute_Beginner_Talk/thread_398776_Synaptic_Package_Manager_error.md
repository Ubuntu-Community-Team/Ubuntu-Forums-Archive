---
title: "Synaptic Package Manager error"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by gingin on 2007-04-01
Synaptic Package Manager error:
[B]
E: I wasn't able to locate a file for the peerguardnf package. This might mean you need to manually fix this package. (due to missing arch)
E: I wasn't able to locate a file for the peerguardnf package. This might mean you need to manually fix this package. (due to missing arch)[/B]

It came after I have manually removed peerguardian.
How to fix that?
Do I have to reinstall Synaptic?
Because it is a problem with that I cannot get updates add/remove in applications
refuses to work.

Thaks for help

---

### Post by Bachstelze on 2007-04-01
In a terminal :

```
sudo apt-get -f install
```

---

### Post by gingin on 2007-04-01
No god it doesn't help a case.Terminal kindly informs: 

 Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package peerguardnf needs to be reinstalled, but I can't find an archive for it.

Shall  we tray something else? Because I m totally dry of ideas.

---

### Post by Bachstelze on 2007-04-01
If I were you, I'd reinstall the package and then cleanly remove it.

---

### Post by gingin on 2007-04-01
Would you please guide me how I can remove Synaptic Package manually because add/remove doesn't work either.

---

### Post by Bachstelze on 2007-04-01
Synaptic has nothing to do with anything. Reinstall peerguardnf and then cleanly remove ir

---

### Post by gingin on 2007-04-01
I did that. The same effect and response from Synaptic.

---

### Post by Bachstelze on 2007-04-01
How do you remove it ?

---

### Post by gingin on 2007-04-01
I did manually, because I wasn't able used anything else .Synaptic was gone add/remove as well.
Thing gets even better at present reinstalling peerguardian Terminal soluts me with that:

gin@laptop:~$ sudo dpkg -i peerguardnf-1.5beta.i386.deb
Password:
dpkg: error processing peerguardnf-1.5beta.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 peerguardnf-1.5beta.i386.deb
gin@laptop:~$

---

### Post by Maestro23 on 2007-04-01
> **gingin said:**
> I did manually, because I wasn't able used anything else .Synaptic was gone add/remove as well.

What were your commands to remove it manually?

---

### Post by gingin on 2007-04-01
During installation was crated those files:
[http://doc.gwos.org/index.php/Peer_Guardian](http://doc.gwos.org/index.php/Peer_Guardian)  
And root directory witch I cannot remove from terminal 
/etc/peerguardian

Files was removed from the terminal with rm comand.

---

### Post by zvacet on 2007-04-01
```
 sudo apt-get remove --purge file_name 
```

---

### Post by Maestro23 on 2007-04-01
> **zvacet said:**
> ```
 sudo apt-get remove --purge file_name 
```

Beat me to it.

---

### Post by gingin on 2007-04-01
No effect this what I got:

gin@laptop:~$ sudo apt-get remove --purge peerguardian.sh 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package peerguardnf needs to be reinstalled, but I can't find an archive for it.
gin@laptop:~$ sudo apt-get remove --purge /etc/peerguardian
Reading package lists... Done
Building dependency tree... 0%
Building dependency tree       
Reading state information... Done
E: The package peerguardnf needs to be reinstalled, but I can't find an archive for it.
gin@laptop:~$ 

**E: The package peerguardnf needs to be reinstalled, but I can't find an archive for it.**
the same error again.

I think it is to ways out of this reinstall ubuntu or sympatick

---

### Post by Maestro23 on 2007-04-01
> **gingin said:**
> rm was used from terminal to remove /usr/local/bin/peerguardian.sh
and from pg file from /home directory
where is a folder in /etc/peerguardian witch I cannot remove for same unknown reasons.

Did you try 

> sudo (then your command)

Does it give any kind of error when you try and remove it?

---

### Post by gingin on 2007-04-01
Do you mean same thig like this:

sudo rm /etc/peerguardian 

I did an this is result:

rm: cannot remove `/etc/peerguardian': Is a directory

---

