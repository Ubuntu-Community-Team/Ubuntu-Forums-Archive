---
title: "Ibook G4 7.04 help with connecting to wi-fi"
date: 2007-04-25
forum: Apple PPC Users
---

### Post by cbdaqb on 2007-04-25
ok ive got ubuntu running fine and i have heard u need like a code for getting airport extreme to work on it what is this code or how do i make it work?

---

### Post by stmiller on 2007-04-25
Please use the search function. This question seems to be asked almost every hour....

---

### Post by cbdaqb on 2007-04-25
cant find it i need a link

---

### Post by stmiller on 2007-04-25
[http://ubuntuforums.org/search.php?searchid=18861433](http://ubuntuforums.org/search.php?searchid=18861433)

---

### Post by ewout klimbie on 2007-04-26
> **cbdaqb said:**
> cant find it i **need** a link
No, you would **like** a link. This is a community forum, not paid tech support!

Now to answer your question:
In order for these steps to work you'll need to use your wired networkor dailup internet connection.
[LIST=1]
[*]go to System -> Administration -> Synaptic Package manager
[*]Press search
[*]search for bcm43xx-fwcutter
[*]mark package for installation
[*]search for wifi-radar
[*]mark package for installation
[*]click apply
[*]Wizzard should ask you if it should grab and install firmware, say yes.
[*]unplug ethernet or modem
[*]reboot
[*]enjoy wifi!
[/LIST]

For me network manager doesn't work so I disabled it and use wifi-radar, if network manager works for you that is the preferred tool (it integrates better with ubuntu).

if it doesn't work there are more detailed tutorials, such as [this]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear") one.

---

### Post by cbdaqb on 2007-04-26
ok thanks a lot thats all i needed

---

### Post by xfile087 on 2007-05-01
I've been wanting to get the net working under Ubuntu on my iBook for ages and I installed 7.04 on hoping i'd finally be able to and I was a bit disapointed that it never (not Ubuntus fault, I know) but with your instructions, which were so simple, it I have now have fully working wi-fi on my old iBook so just wanted to say thanks!!!

---

