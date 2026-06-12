---
title: "Newbie Networking Problems"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by ccangia on 2007-12-25
Hello;

    I have read all of the networking posts. No help. I have also read everything else I can find. Still no help.
    I am new to linux and ubuntu. I am using 7.10 on an old Dell P3. Everything seems to work fine. 
    I am on a home network with an Intel Imac. and a dual boot Vista/XPsp2 machines.
    Unbuntu can see the Mac and I can access it. However it cant see windows at all in either XP or Vista. The Mac can not see ubuntu and Windows can not see ubuntu. 
    As far as I know I have done all of the standard things, samba is installed. I checked smb.conf and the workgroup is workgroup which is correct. I made sure all of the items listed were public=yes and also yes for read and write. I connect through a belkin router. 
    Can anyone tell me what I am missing?

TIA

Charlie

---

### Post by Guruprasad on 2007-12-25
Hi Charlie

Once my Windows PC couldnot see Ubuntu where as Ubuntu could see Windows on network. I went through a pdf help file on samba website and changed some settings in configuration file. Later it worked. unfortunately now I dont remember what settings I changed. U can try looking at the help on samba website.

---

### Post by angelsguitar on 2007-12-25
> **ccangia said:**
> Hello;

    I have read all of the networking posts. No help. I have also read everything else I can find. Still no help.
    I am new to linux and ubuntu. I am using 7.10 on an old Dell P3. Everything seems to work fine. 
    I am on a home network with an Intel Imac. and a dual boot Vista/XPsp2 machines.
    Unbuntu can see the Mac and I can access it. However it cant see windows at all in either XP or Vista. The Mac can not see ubuntu and Windows can not see ubuntu. 
    As far as I know I have done all of the standard things, samba is installed. I checked smb.conf and the workgroup is workgroup which is correct. I made sure all of the items listed were public=yes and also yes for read and write. I connect through a belkin router. 
    Can anyone tell me what I am missing?

TIA

Charlie

On a terminal, try this:

```
sudo smbpasswd -a *username*
```

Change *username* for the name you use to login into Ubuntu.  You will be asked for your sudo password (just type your login password) then you will be asked for a password to use with the shared folders (choose the one you want or leave blank and press Enter for no password).
That should solve it.  Remember to specify which folders you want to shared, otherwise you will be able to see the computers in the network but not able to access any folder.
Hope this helps!:)

---

### Post by JurB on 2007-12-25
[LEFT]Have you shared a folder? 

[/LEFT]

---

### Post by angelsguitar on 2007-12-25
Yes, I have a home network and have shared folders between Windows and Ubuntu.

---

### Post by JurB on 2007-12-25
Do the Xp and Vista machines have a software firewall running?
Is the shared folder on the Ubuntu machine in your /home folder?

---

### Post by angelsguitar on 2007-12-25
> **JurB said:**
> Do the Xp and Vista machines have a software firewall running?

I don't use Vista, but on XP I have the firewall that comes with it running.  No problems at all as of today.

> **JurB said:**
> Is the shared folder on the Ubuntu machine in your /home folder?

Yes.

---

### Post by ccangia on 2007-12-25
Hi;

     Thanks for the smbpasswd trick. It worked for the Mac.  I can now network back and forth with the Mac. However I still can't open XP or Vista from Ubuntu and neither sees the Ubuntu shares I created. By the way I am not using a firewall in Ubuntu and only the Windows firewall on XP and Vista.
    I mostly use the Mac anyway but there is a principal to be upheld so I want it to work with WIndows too.

Thanks again;

Charlie

---

### Post by angelsguitar on 2007-12-25
> **ccangia said:**
> Hi;

     Thanks for the smbpasswd trick. It worked for the Mac.  I can now network back and forth with the Mac. However I still can't open XP or Vista from Ubuntu and neither sees the Ubuntu shares I created. By the way I am not using a firewall in Ubuntu and only the Windows firewall on XP and Vista.
    I mostly use the Mac anyway but there is a principal to be upheld so I want it to work with WIndows too.

Thanks again;

Charlie

Mmm...I'm almost running out of ideas right now.  Only thing I can suggest is trying the ip address method described in the Ubuntu documentation (the question mark icon on the top panel in the Ubuntu Desktop), section 6.3.2.  You can find it here too:
[https://help.ubuntu.com/7.10/internet/C/networking-shares.html]("https://help.ubuntu.com/7.10/internet/C/networking-shares.html")
The smbpasswd trick is described there too (that's where I got it from!)
Hope this helps.

---

### Post by rkd on 2007-12-25
Have you tried turning off the firewall on the Windows box temporarily to see whether it is causing the difficulty?

---

