---
title: "home network"
date: 2007-04-13
forum: Apple PPC Users
---

### Post by heatrag on 2007-04-13
I want to connect to my Mac which shares the same router as my ubuntu machine. Documentation just gives me the following.
> To view computers on the network, open Places->Network Servers.
You may need to enter a username, password, and domain. You should obtain these from your network administrator.
is all that is in there is a windows network icon.
 Please could someone point me to some sort of tutorial that explains all in the simplest of methods please.

---

### Post by kugn on 2007-04-14
You need to enable Windows File Sharing on your Mac. You'd be able to do this at System Preferences>Sharing. This option allows you to share files in your Mac user's home folder. If there are multiple users on the Mac, you'd be prompted to choose which user's folder you want to share.

You should then be able to read the files following that documentation you've quoted.

If that doesn't work, you can try entering
smb://ip address of your mac
in the location bar of Nautilus/Konqueror.

Hope that helps.

---

### Post by heatrag on 2007-04-21
Thanks for the feedback. window ticked and no difference, smb://mac's ip address returns blank window. I have tried admin>networking>DNS and put the ip address in the search field, then gone to places>network servers and in the window with the windows-network icon there is another icon now of the mac's name in caps with -C at the end which when clicked opens another blank window. Then when on the mac , finder>network I get the same file name alias along with the servers alias, which when clicked gives me an alias of the main users account on the self same mac! I'm getting a bit lost here.

---

