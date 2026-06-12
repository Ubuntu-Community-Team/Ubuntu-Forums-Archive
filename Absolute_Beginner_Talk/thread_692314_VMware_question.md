---
title: "VMware question"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-02-09
well i have windows Vista and ubuntu on dual boot and i have vmware on ubuntu with XP on it sooo my question is

Can i reach my music file or photo file on my VMware on ubuntu that are on my other partition ?

---

### Post by tribaal on 2008-02-09
I'm not sure i understand your question properly, but you can definately reach any file in a virtual machine.

You should treat it exactly like if your virtual machine was another computer on the same network: make a shared folder in your VM and access it from ubuntu like a network folder (in nautilus, type "smb://<your VM's ip address>" in the location bar.

Hope this helps :)

- Trib'

---

### Post by articwolf939 on 2008-02-09
well like i have music on my vista OS that i want to acess from VMware on ubuntu is it possible so i dont have to redownload it on VM

---

### Post by tribaal on 2008-02-09
Ah well ok I read it the wrong way the first time :)

So your files are on the physical hard drive on your Vista partition, and you want to access them from your XP virtual machine?

There are two main options here:

1. Mount the files with Ubuntu, and then serve them to your VM (and possibly other computers if you like) like a network share.
2. Mount a partition as a virtual hard disk. I'm not sure this is possible with the free VMware server, but it is possible to do it with VMware Workstation (which is the one I use).

Depending on what is more convenient to you, we'll get in the specifics... It's a little late here :)

- trib'

---

### Post by articwolf939 on 2008-02-09
well i have the free version so ill try Number 1 :)

---

### Post by tribaal on 2008-02-09
Hum to mount a windows partition in ubuntu, I suggest you refer to[ this well-written article]("http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/").

Then you'll need to share your files from Ubuntu with "Samba", a program that makes Ubuntu shares accessible from Windows. Again, here is [a nicely done tutorial]("http://www.linuxlove.org/2007/11/30/sharing-ubuntu-directories-over-local-network-with-samba/").

You'll find that you'll be able to access all your files from Ubuntu, maybe mounting them in your XP VM will not be necessary?

Don't hesitate to post back if you have questions.

- trib'

---

### Post by articwolf939 on 2008-02-09
ok ive done what both sites say and when i go on my vista partitiion i cant acess my ubuntu  i looked up my ubuntu IP from IPchicken is that the right IP adress? and is there anything else i have to do like enable file sharing on ubuntu or anything? cos i cant find the file i set up to share to windows either where do i find that at?

---

### Post by dcstar on 2008-02-10
> **articwolf939 said:**
> ok ive done what both sites say and when i go on my vista partitiion i cant acess my ubuntu  i looked up my ubuntu IP from IPchicken is that the right IP adress? and is there anything else i have to do like enable file sharing on ubuntu or anything? cos i cant find the file i set up to share to windows either where do i find that at?

You should make up your mind, you originally wanted to access your Windows partition from your Ubuntu VM (and were given instructions to do this), not the other way around.

---

