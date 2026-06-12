---
title: "Do I need to open port 80 in order to http with apache?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by neander on 2007-02-25
Ubunto 6.10, I have apache 2 installed and I believe my router is forwarding requests on port 80 to the ubuntu box nic. But I think I need to open port 80 with ubuntu? Is there a built in firewall? Apache is started but no response.

I've read about a program called firestarter but it seems to have vanished, supposed to be in add remove but it's not, sudo apt-get install firestarter fails to find, and synaptic fails to find.

Thanks

---

### Post by neander on 2007-02-25
Oooo it is in fact responding to http request, I was just testing with local ip not public, I guess that makes the difference?

Still curious about firestarter, what happened to it?

---

### Post by neander on 2007-02-25
It's available via synaptics if universal repository is enabled.

---

### Post by steve.horsley on 2007-02-25
I have a suspicion that the default Apache install is configured only to listen on 127.0.0.1 (localhost). I've not installed Apache myself, but I suggest you look for the config file and check the listening address.

P.S. by default, the firewall is not filtering. If you want to use it, I suggest you get a GUI front-end for it, like firestarter, because the actual firewall is command-line configured and rather complex. GUI apps that create the commands for you are much easier to understand.

---

