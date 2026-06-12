---
title: "networking and sharing ubuntu machines"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by clint1010 on 2006-11-25
Hi all,

I have had a look around, with little success. I am looking for a "How to" on networking two ubuntu machines together to share files. Could someone please point me to somewhere I could find more info, or a good How To?

Thanks
Clint

---

### Post by clint1010 on 2006-11-26
I am simply trying to set up a "small home office network" as I used to do in windows. I'm still searching, still no good. Everything is still a bit fuzzy. But I think I should use NFS? 

Any help at all would be great

---

### Post by steve.horsley on 2006-11-26
Between two Ubuntu machines, I guess that NFS would be the obvious chioce. I can't tell you how - I've never done it.

As an alternative, the easy way that I have used on the past is to install openssh-server on both machines and use SSH between them. This allows remote commands, like telnet does, but also allows FTP-like file access. You can connect to a machine using the nautulis file manager using the menu option Connect To Server..., and putting in the SSH username and password. If oushare files regularly though, an NFS mount would be the slicker way to go.

---

### Post by clint1010 on 2006-11-26
This would be perfect info for me, but obviously not so good

[https://wiki.ubuntu.com/HomeNetworking?highlight=%28networking%29#head-2189a46c6308159a8d3cedd92541932c8ab9092a](https://wiki.ubuntu.com/HomeNetworking?highlight=%28networking%29#head-2189a46c6308159a8d3cedd92541932c8ab9092a)

---

### Post by clint1010 on 2006-11-26
am trying to get NFS to work, no success yet. Anyone had experiance with NFS?

---

### Post by not_yet on 2006-11-26
perhaps I'm missing your point :-D 

but to share files just install Samba 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_share_folders_the_easy_way](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_share_folders_the_easy_way)

once thats done, setup some folders on each machine for sharing

right click on folder / share

then open the file browser, I use Nautilis

in the location bar enter the following

smb:// ip_of_the_machine_you want

eg:   smb://192.168.0.100

cheers

---

### Post by stimpsonjcat on 2006-11-26
here's the nfs howto: [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

### Post by clint1010 on 2006-12-02
simpsonjcat, thankyou very much. and thank you all, the mud has cleared. All working a treat with NFS. auto mount and all.

Cheers
:-D

---

