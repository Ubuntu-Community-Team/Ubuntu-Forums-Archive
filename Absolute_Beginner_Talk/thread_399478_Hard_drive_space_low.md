---
title: "Hard drive space low"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Nxion on 2007-04-02
Hi,

Very noobish question. I run Edgy and I recently put VMware Server on my machine so I could run some VM's on my desktop. After I Installed it I relized that the harddrive that I set for it took up almost all my space. So I deleted the VM i created and I got rid of VMware Server.

The problem is that it still does not give me my free space back I had 60 gig free. before I installed VMware. Now even though its all gone I only have 23 gigs free space !. Is there a way to search for big files in Ubuntu ? Or clean up free space ?

Help please. :|

---

### Post by taurus on 2007-04-02
Did you also remember to remove ~/.vmware?

```
du -h ~
```

---

### Post by mikeyphi on 2007-04-02
> **Nxion said:**
> Hi,

Very noobish question. I run Edgy and I recently put VMware Server on my machine so I could run some VM's on my desktop. After I Installed it I relized that the harddrive that I set for it took up almost all my space. So I deleted the VM i created and I got rid of VMware Server.

The problem is that it still does not give me my free space back I had 60 gig free. before I installed VMware. Now even though its all gone I only have 23 gigs free space !. Is there a way to search for big files in Ubuntu ? Or clean up free space ?

Help please. :|

I'll (humbly) echo what Taurus said..I initially installed VMplayer and had problems then tried to install VMserver but couldn't until I had found and removed all files previously created for VMplayer!!

---

### Post by Nxion on 2007-04-02
> **taurus said:**
> Did you also remember to remove ~/.vmware?

```
du -h ~
```


Meh..

I think you hit it on the head lol. I totally spaced the /.vmware folder. I remembered to remove the /vmware folder but forgot about the /.vmware one. Thanks ! I will try it when I can get to my laptop.


:) :)  Thanks Taurus !!!!! :) :) 

(>'.')>   <('.'<)

---

### Post by Nxion on 2007-04-03
I have my hard drive space back ! WOO !

I ran the command you told me about and it showed that all that space was being used by root. so I looked and what I did was forgot to empty the trash in root :(

Man do I feel dumb :(

Oh well at least I have my space back WOO HOO !

Thanks taurus and mikeyphi for the help !

---

