---
title: "Samba install in 7.10"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by maghemi on 2007-10-20
Hi,

I'm a completely fresh linux user. So i really have little idea what i'm up to. Anyway the main reason for me putting linux on is to set up a few shared things on my network. One of which being centralized storage. This is where i come unstuck. I can't seem to work out this samba thing. First up i tried to do it by right clicking on a folder and selecting 'Share folder' it prompted me to install NFS and SMB. But didn't actually do it. It just kept asking me to install it. So i tried to do it with sudo apt and i got this message.

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  smbclient samba-common
E: Package samba has no installation candidate[/I]

So i've been reading all these guides on how to setup samba, But most of them assume that the apt install works or you already have it on. But as you can see I can't even get that far. I'd appreciate any direction as to how i can fix this problem.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-20
hello 

```
sudo apt-get install samba
```

should work but .... 

you should try the gui way  gui means by clicking on stuff with you mouse.

so System>Administration>Synaptic Package Manager

Then i would make shure you have univers restricted and multivers checked so 

select Settings > Software Sources and then check all of them
Close that window
Now click Search and type samba press return 
and wait for it
ok
So now you should just scroll down to samba and check the box and then apply and follow the menus 
if this dosent work check your internet connection

O tell me how it goes

---

### Post by maghemi on 2007-10-20
Ahhh.. Fantastic. Thanks for that. 
I'd searched in there before, But I didn't know there were more than one source, of which i didn't have selected, so samba never turned up in the search. It's downloading now to install at last :)

---

