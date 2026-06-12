---
title: "Mount a windows share from GUI"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Bigbird999 on 2007-10-30
Total Terminalphobe, I have spent hours trying to get  my windows shares mounted.  I get totally lost in the syntax and commands in Terminal.  Can I do this from the GUI in Gnome.  If not, can somebody please post the exact terminal commands i need to use.  I can see my windows box  via file browser as smb://erniepc/E  E is  200 GB hard drive shared as E,  It contains 3 folders  Video, Photos and Music  Each of these folders has many sub folders.

No mater what I try, I get a message saying that there is no such share.  It is making me crazy,  I an a total noob to Linux in mac os I just click on connect to server, can I do the same here?  What am I doing wrong????

BB

---

### Post by carlosjuero on 2007-10-30
Try using the IP address of the Windows box (i.e. smb://192.168.1.100/E) - I have had some issues with name resolution & SAMBA as well, the IP address always works though

---

### Post by MaximusTG on 2007-10-30
The command you need to enter is:

sudo mount -t smbfs //erniepc/E /folder/you/want/to/mount/to

You probably need to install the smbfs package first

So before the first command, enter:

sudo apt-get install smbfs

Should it still not work, try substituting 'erniepc'  with erniepc's IP address like the person above me suggested.

Good luck!

---

### Post by Repubhippy on 2007-10-30
I was able to mount an entire machine using the "Connect to Server" function (I think it is in the places menu.  That way there is a icon on my Ubuntu desktop that links to all the shares on my Vista box.  You just put in the name of the Server/PC and away you go.

---

### Post by meanburrito920 on 2007-10-30
are you using gutsy? because gutsy automatically recognizes windows partitions and has r/w capabilities to NTFS.

---

### Post by crazybilly on 2007-11-01
> **Repubhippy said:**
> I was able to mount an entire machine using the "Connect to Server" function (I think it is in the places menu.  That way there is a icon on my Ubuntu desktop that links to all the shares on my Vista box.  You just put in the name of the Server/PC and away you go.

The problem with this is that it still doesn't show up in 'save as' or 'open' dialogs.

I had to actually mount the share:

```
sudo smbmount //192.168.1.5/media /home/me/Desktop/server/ -o username=mymame,password=mypass,uid=1000,mask=000 
```

---

