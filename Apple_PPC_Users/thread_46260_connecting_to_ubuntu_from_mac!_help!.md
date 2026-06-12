---
title: "connecting to ubuntu from mac! help!"
date: 2005-07-03
forum: Apple PPC Users
---

### Post by Digitallysick on 2005-07-03
Ive got a problem, my mac sees my Ubuntu pc but when i click on it in the network and click "connect" i get the spinning ball of death on my mac, do i have some settings wrong on my Ubuntu pc? any ideas?? its really important that i can transfer files between the 2

---

### Post by dkitty on 2005-07-04
I haven't tried it myself, but I hear that Samba is the way to go. Check [this thread](http://ubuntuforums.org/showthread.php?t=30243).

There's also a bit about [Samba in the Unofficial Ubuntu Starter Guide](http://ubuntuguide.org/#sambaserver). I'm reasonably sure that only covers the server bit of Samba and that there's also a client to install. I don't know much more of the specifics but I imagine a few searches of these forums would dig up plenty of information.

---

### Post by Digitallysick on 2005-07-04
i think samba is installed correctly?? i know its on the ubuntu box, i dont know about what i need on the laptop to connect?

---

### Post by ltmon on 2005-07-04
[QUOTE=Digitallysick]i think samba is installed correctly?? i know its on the ubuntu box, i dont know about what i need on the laptop to connect?[/QUOTE]

I wish I could help, but I have the same problem!  I haven't yet found the answer.

Anyone?

L.

---

### Post by crashtest on 2005-07-05
[QUOTE=ltmon]I wish I could help, but I have the same problem!  I haven't yet found the answer.

Anyone?

L.[/QUOTE]

If you run an ftp server on the Ubuntu machine, you can connect to it from the Mac.
In Finder, you click 'Go', then 'Connect to server'.  Enter the IP address, and connect.  Now the Ubuntu machine can be browsed thru Finder, and will actually show up as a mounted drive on the desktp.

---

### Post by Digitallysick on 2005-07-05
running an ftp on it sounds like a great idea, i think that would work the easiest, im going to try it out, thanks for the ideas!

---

### Post by ltmon on 2005-07-05
[QUOTE=crashtest]If you run an ftp server on the Ubuntu machine, you can connect to it from the Mac.
In Finder, you click 'Go', then 'Connect to server'.  Enter the IP address, and connect.  Now the Ubuntu machine can be browsed thru Finder, and will actually show up as a mounted drive on the desktp.[/QUOTE]

Yeah, this is probably easier than Samba and has all the functionality I need.

Cheers,

L.

---

### Post by Len on 2005-07-06
I also had the same problem with some installations (others not...). No doubt that OS X is the blame here. OS 7, 8 and 9 (with additional software) and Windows work very nice with the samba shares of Ubuntu. Didn't try this with OS X 10.4 yet, but with 10.3.9 this still was an issue, but not with every Ubuntu machine.

FTP shares are indeed an option, or something funny: if you enable "windows sharing" on OS X Ubuntu can connect to the OS X machine without problem. Weird...

---

