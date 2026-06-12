---
title: "Network"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-29
Hello!
There are two questions:
1-In windows I could type \\computer_name to access shared files on that computer. How should I access shared files on another computer (which has windows) from my ubuntu?
2-In windows command i could get a list of available computers by typing net view. How should I do that here?
Thank you.

---

### Post by Ex-windows on 2008-01-29
Have u tried going to Places>connect to server> search network? This should let you access all computers on the networks and any shared files. If you have the samba set up already. Hope I am understanding you correctly.

---

### Post by HereInOz on 2008-01-29
Firstly, you need to understand that Windows and Linux file systems are not the same, and do not behave the same.  It would have been nice if Microsoft wrote their operating system to be able to interact with other systems, but that is too much to ask, I am afraid.

Hence it fell to the Linux / Unix people to make their systems interoperable with Windows, and the software you use for that is called Samba.  You will need to install Samba on your machine to get full Windows file system interoperabilty.  Use Synaptic to search for Samba.  Install Samba (which will install a range of utilities) and also install smbfs.

Then, as Ex-windows says, go to Places > Connect to Server, select Windows Share in the drop box, then enter the Windows computer name or better still, the IP address, in the server box, enter the Share name and subfolder if desired, username, and use the Workgroup name for the Domain.  This should work, particularly if you enter the IP address rather than the computer name.

If you want to take things further try this:
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=samba&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=samba&titlesearch=Titles) 

It will give you some good tutorials on using and configuring Samba.  My favourite is option 5 - Setting up Samba
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Hope this helps a little.

---

### Post by Hoom@n on 2008-01-29
Thank you. I gonna test it.

---

### Post by Hoom@n on 2008-01-30
And sorry how can I see which programs are using network and what't their transfare rate? I mean something like system monitor but insted of process and ram i wanna have the network.
+++
There is no connect to server in my places. Please tell me again that how can I know which (windows)computers are on the network. (like "net view" in windows cmd)
Thank you.

---

### Post by Hoom@n on 2008-02-05
Hello again!
I found that I can go to: places->network->windows network->workgroup name and than see all the computers available on the network. Again I'm asking how can I see the list in terminal. As I said it's "net view" in cmd in windows.
1-There is a command in Winodws for this thing.
2-Linux can browse all the network computers.
1&2: there should be a command the see the network list in windiws. What's it?
Thanks,

---

### Post by Farley69 on 2008-02-05
Regarding your question about monitoring bandwidth, processes etc check out "Conky"  I just set it up yesterday works great, and there are some really good forums on setting up, and good examples of config files.

---

### Post by Hoom@n on 2008-02-05
What?!

---

