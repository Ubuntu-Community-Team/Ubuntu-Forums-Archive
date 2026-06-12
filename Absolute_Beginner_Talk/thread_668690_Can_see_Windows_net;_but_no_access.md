---
title: "Can see Windows net; but no access"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by RBEmerson on 2008-01-15
I can access the Internet from this machine (IBM T21 running 7.10 loaded from the "alternate" 7.10 ISO image), as this note proves.  I can successfully update the system via the Internet.  But...

When I try to install a remote printer (I have one on a SuSE 10.0 system, one in a WinXP Media system), I can see and install the LJ-5P and Photosmart 7660 but can't print a test page to either printer.  A second WinXP machine can use either printer successfully (and has been doing so for, literally, the past couple of years).  

When attempting to browse the local network, I can see the local workgroup successfully but as soon as I try to browse it, I get an error.  

On the SuSE machine, I used smbpasswd to create a password entry for this machine (t21) and tried adding the username and password to the printer authentication process without success.  

The local workgroup (WXNET) works fine among two WinXP systems and a SuSE system but this system can only look into the local network as far as discovering the workgroup and then it's "party over".  What did I miss here?  :confused:

---

### Post by mikeyphi on 2008-01-16
Can you confirm that you've set up System/Administration?shared Folders? Specifically under the General Properties tab - enable "This computer is a wins server" 

The only other thought is - correct setting of permissions on the other systems to allow Ubuntu access?
If you can see the local workgroup but don't have access it would seem to indicate that you are not part of that workgroup - check under Systems/Administration/Network that you have entered the system name and workgroup name (under the general tab)

---

### Post by RBEmerson on 2008-01-16
Mikeyphi, thanks for your input.  I have progress of a sort...  :D

I followed the path to the shared files item and selected "WINS server", which started the process of installing Samba and NFS (might as well do both, although NFS isn't a big item on this particular net).  After adding (on t21) a username (note: both the username at the system level and for Samba [via smbpasswd -a]) for the WinXP Media machine (dv8330), dv8330 can see the t21  folder t21-share, after supplying a username and password,  Even though t21-share is *not* set to read-only, dv8330 cannot write to the share (access denied).  I haven't tried accessing t21-share from the SuSE machine, as its role (for this discussion) is strictly as a file and print server.  

This machine (t21) is still at the point of finding the name of the workgroup (wxnet) but is unable to see into the workgroup to at least find the two other machines' name (SuSE and WinXP), to say nothing of what's "on offer" from each of them. ](*,)

---

### Post by RBEmerson on 2008-01-17
Talking this problem over elsewhere, I was pointed to this discussion:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067) 


If I read the conversation correctly, samba, as it's supplied in 7.10 (Gutsy Gibbon) is effectively broken for anyone without the skill to tune, by hand, smb.conf correctly.  Kinda not the ubuntu way, methinks...  :confused:

---

