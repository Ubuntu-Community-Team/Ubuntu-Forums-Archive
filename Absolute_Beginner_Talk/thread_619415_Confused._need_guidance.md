---
title: "Confused. need guidance"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by I_have_seen_the_light on 2007-11-21
I have a few PCs that i have acquired.  Now currently theya re running on fedora 7. NOw What I would like to do is to get one PC.  and install Ubuntu on it and use that PC to basically manage all the other PCs.  I installed Ubuntu server, but found out that it does not have a GUI so I went back to the Desktop version.  (which I am using now)

Now my questions would be:

1.  What is the main difference between the Ubuntu Server ed. and the Ubuntu Desktop ed.?
2.  What do I need to install to have this PC  (which has the Ubuntu desktop) to be able to administer and manage the other PCs on the network?
3.  do you have any good tutorial on this?  could you please share to me the link.

that's it for now.

Thanks

Homer

---

### Post by quinnten83 on 2007-11-21
I don't know much about the subject, but I do know, that you can install ubuntu server and then install the ubuntu desktop on top of the server to get a gui.
You should retain full server functionality as well as get a desktop. I don know how that works exactly.

i believe the code in terminal in the server would be
sudo apt-get install ubuntu-desktop

---

### Post by Inxsible on 2007-11-21
1) The server is customized, so that people can set up webservers etc easily. It doesn't have a GUI which is good on a server because you do not need all the heavy apps that you get in a normal desktop version. You can however, install a GUI on the server too.

2) To manage other machines, you can use VNC over SSH, or RDP over SSH or NXServer (FreeNX). You can also do it without SSH, but SSH is more secure.

3) Tutorials:

[Resumable VNC]("http://ubuntuforums.org/showthread.php?t=488207&highlight=FreeNX")

[FreeNX]("http://ubuntuforums.org/showthread.php?t=441496&highlight=FreeNX")

[VNC over SSH]("http://ubuntuforums.org/showthread.php?t=383053&highlight=FreeNX")

Remember you will need to install the servers on the Fedora machines and the client on your ubuntu machine

---

### Post by I_have_seen_the_light on 2007-11-21
thanks for the prompt reply.

Will try the tutorials once I get home.  I still haven one question though, Would it be possible for me to just add the programs needed so that i could have the server edition, rather than .  removing my current installation and then installing the server edition and them insalling the GUI?

thanks,

Homer

---

