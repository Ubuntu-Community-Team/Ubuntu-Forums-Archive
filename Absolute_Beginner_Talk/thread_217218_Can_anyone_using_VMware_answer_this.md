---
title: "Can anyone using VMware answer this?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Emceay on 2006-07-16
I have my actual windows volume mounted to a folder. I want to make files on my drive accessible to my virtual XP in VMware. I'm stumped, and without the ability to use my windows files, there was no point in emulating windows to begin with. Please help. Is there some way to view windows files that aren't within a .vmdk file? or is there someway to turn an external windows folder into a virtual one?

---

### Post by djsroknrol on 2006-07-16
Look here:

[http://ubuntuforums.org/showthread.php?t=183209&highlight=VMware](http://ubuntuforums.org/showthread.php?t=183209&highlight=VMware)

I think you'll find what you need there...my VM server **only** runs files thru my intranet. but I also started with a fresh MS install...

It is possible to make appliances of your own MS OS and have them run in your VMware, but  I've lost those links right now. Hopefully, someone has one to VMware and you could Google it.

---

### Post by djsroknrol on 2006-07-16
EDIT: Found it...:rolleyes: 

[http://www.vmts.net/selfp2v.htm]("http://vmts.net/selfp2v.htm")

---

### Post by scxtt on 2006-07-16
you can use a samba share on your host and "map network drive" it in your XP virtual machine ...

---

### Post by Emceay on 2006-07-16
That's mind-boggling.. I shared the drive using samba, but my virtual XP doesn't seem to want to connect to the network... Windows..
Ah well, these are some helpful links, I'll keep trying to sort it out. Thanks for the help

---

### Post by Emceay on 2006-07-16
On second thought, both of you said you were able to run drives off of the network in your VM.. How? I can't seem to detect my network in network places. Anything I could be missing off the top of your head?

---

### Post by scxtt on 2006-07-16
> **Emceay said:**
> That's mind-boggling.. I shared the drive using samba, but my virtual XP doesn't seem to want to connect to the network... Windows..
Ah well, these are some helpful links, I'll keep trying to sort it out. Thanks for the helpare you using "bridged" networking for your VM? -- you'll have to have it so your host and VM have separate IPs (my host is 192.168.1.100 and the XP VM is 192.168.1.102) ... and it's better to use the IP address of your host, instead of relying on samba browsing by workgroup ...

---

### Post by Thenotsowyzewun on 2006-07-16
Hi,

I think you're running Ubuntu as your Host OS, and Windows XP as your Guest OS (on top) via VMWare Player.
I'm doing the opposite, but hopefully I can help :).
Firstly in Ubuntu:

Go into System, Administration, Shared Folders, then click the folder you're sharing and click Properties, and tick Allow Browsing Folder.
Next click General Windows sharing settings. Change the Domain / Workgroup to MSHOME. This is the default Windows Workgroup.

Now press OK, OK, OK and then Applications, Accessories, Terminal.
Enter the command sudo mbpasswd followed by your username, e.g. ```
sudo smbpasswd ubuntu
```

It'll prompt you for a password to authorise sudo (superuser mode). Then it'll prompt you for your new samba password, twice (for confirmation).
Then type, exit, exit.

Now boot up your Windows XP virtual machine and tell it to restart.
Once it's started up again, click on My Computer, select My Network Places in the address bar. If you've got Common Tasks turned on in folder options they'll be an option on the left: View Workgroup Computers.
Otherwise you're be in Classic Mode, and the option you want is Entire Network in the main panel, followed by Microsoft Windows Network then MSHOME, then whatever your Ubuntu machine is called (probably Ubuntu).
You should be able to view your shared folders once you've done this.

If you can't, refer to the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=1259649&postcount=2") for disabling Digital Signing on all communications, and re-configuring Windows Firewall (although this shouldn't be necessary).

**Hope that helps :), tell us how you get on (and feel free to click those IM icons anytime - I'm online alot lately).**

If you require further assistance regarding VMWare Player, try the [VMWare Support Forums]("http://www.vmware.com/community/index.jspa") here, and if you require more general Linux Support try [Linux Questions]("http://www.linuxquestions.org").

---

### Post by djsroknrol on 2006-07-16
EDIT 2: I didn't have the exact link..the one I posted earlier is the main page. The link at the bottom of the page was the one I was trying to direct you to. **[Here]("http://www.vmts.net/article/selfp2v.htm")** it is.

---

