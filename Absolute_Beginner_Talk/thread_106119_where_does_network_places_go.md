---
title: "where does network places go?"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by shutupchuck on 2005-12-19
i've been searching on the wiki and on the forums for soem time now and all I want to know is :
Where does network places point to?
What I'm trying to do is go to the network places folder through the terminal and i cant find it under any of the root folders (var, lib, dev, media). I know this is a simple question but I'm a newbie so I'm allowed to ask it right? Thanks,
-Chuck

---

### Post by 23meg on 2005-12-19
Do you mean Places / Network Servers? It doesn't point to any particular location on your file system. What exactly are you trying to do by going into it in terminal?

---

### Post by shutupchuck on 2005-12-19
well I have a windows machine and a ubuntu machine right next to each other, and I can see the windows machine in the network servers folder when I'm using my ubuntu box. But when I log into the ubuntu machine remotely (using putty and ssh) I don't have the ubuntu screen in front of me, all I have is the terminal. I would like to be able to use the terminal in my ubuntu machine to access files on my windows machine.

---

### Post by 23meg on 2005-12-19
You need the smbclient command. Type ```
 man smbclient
``` for details.

---

### Post by shutupchuck on 2005-12-19
i hate to be annoying but there are more options than I'm used to in a command, are all of them necessary? like do I need to set buffer size, debug level, netbios name, username etc...? There's no way to do an ls of something to fing all of the connected computers?

---

