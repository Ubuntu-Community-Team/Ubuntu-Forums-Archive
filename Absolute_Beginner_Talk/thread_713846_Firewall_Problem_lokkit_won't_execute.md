---
title: "Firewall Problem: lokkit won't execute"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Alethinon61 on 2008-03-03
Hi folks,

Andrew and Paul Hudson, in their book "Ubuntu 7.10 Linux Unleashed", say that to set up a firewall in Ubuntu one should,

Quote:
"Start the lokkit command from a console or terminal window.  You must run this command as root...:

$ sudo "/usr/sbin/lokkit"
End Quote

I typed that commend in a terminal and the system didn't recognize it.  I tried it with and without the quotation marks, with and without the dollar sign (I noticed there already is a dollar sign, so this may not need to be typed), and nothing worked.

Any ideas?

Thanks,
~Sean

---

### Post by kpkeerthi on 2008-03-03
Try these to locate if it is actually available in your system.
Open a terminal and type these in sequence:
1.```
sudo updatedb
```
2.```
locate lokkit
```

Does it print something?

---

### Post by Alethinon61 on 2008-03-04
> **kpkeerthi said:**
> Try these to locate if it is actually available in your system.
Open a terminal and type these in sequence:
1.```
sudo updatedb
```
2.```
locate lokkit
```

Does it print something?

I tried your suggestion but nothing happened.  I opened a terminal, typed "sudo updatedb" (but without the quotation marks), then pressed enter.  I was asked for my password, which I entered, then pressed enter.  All I got was this:

kazubuntur@kazubuntur-desktop:~$ 

So what do I do now?  Does this mean that I don't have the program available and have to go get it somewhere?

Thanks,
~Sean

---

### Post by kpkeerthi on 2008-03-04
> So what do I do now?
I gave you two commands. Did you run the second one also?

---

### Post by jan quark on 2008-03-04
I would suggest using the applications iptables and fwbuilder as described in this excellent guide:
[LIST]
[*][https://help.ubuntu.com/community/DynamicFirewall?highlight=%28firewall%29](https://help.ubuntu.com/community/DynamicFirewall?highlight=%28firewall%29)
[/LIST]

---

### Post by kpkeerthi on 2008-03-04
Anyway...
I'm not using neither have I used these but found them available in gutsy repositories

[http://packages.ubuntu.com/gutsy/lokkit](http://packages.ubuntu.com/gutsy/lokkit)
[http://packages.ubuntu.com/gutsy/gnome-lokkit](http://packages.ubuntu.com/gutsy/gnome-lokkit)

You need to enable universe and multiverse repositories from System -> Admin -> Software Sources and  run from terminal below commands to install these
```
sudo aptitude install lokkit
```

If you also need the GUI,
```
sudo aptitude install gnome-lokkit
```

Good luck.

---

### Post by Alethinon61 on 2008-03-04
> **kpkeerthi said:**
> Anyway...
I'm not using neither have I used these but found them available in gutsy repositories

[http://packages.ubuntu.com/gutsy/lokkit](http://packages.ubuntu.com/gutsy/lokkit)
[http://packages.ubuntu.com/gutsy/gnome-lokkit](http://packages.ubuntu.com/gutsy/gnome-lokkit)

You need to enable universe and multiverse repositories from System -> Admin -> Software Sources and  run from terminal below commands to install these
```
sudo aptitude install lokkit
```

If you also need the GUI,
```
sudo aptitude install gnome-lokkit
```

Good luck.

Thank you, that worked.  I was only able to install and access the non-GUI version, but it was very simple to use.  I'm not sure why the GUI version wouldn't install, but I'm not partial to one over the other.

~Sean

---

### Post by Alethinon61 on 2008-03-04
> **jan quark said:**
> I would suggest using the applications iptables and fwbuilder as described in this excellent guide:
[LIST]
[*][https://help.ubuntu.com/community/DynamicFirewall?highlight=%28firewall%29](https://help.ubuntu.com/community/DynamicFirewall?highlight=%28firewall%29)
[/LIST]

Thanks for the suggestion. I'll check out the info you referenced.

~Sean

---

