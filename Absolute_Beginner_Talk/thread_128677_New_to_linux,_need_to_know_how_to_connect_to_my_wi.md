---
title: "New to linux, need to know how to connect to my windows network"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by BongoBob on 2006-02-12
I just made the jump from windows xp to ubuntu 5.10 and am learning many new things, but one thing I can't seem to find is how to connect this computer to the windows xp computer that's on the same network as this one. I know I need to use Samba, but I can't find a tutorial that is "noob friendly".

Does anyone know of a simple way to either explain how to do this to me or show me how to do this?

Thank you in advance to anyone that helps :)

---

### Post by alamba on 2006-02-12
[http://ubuntuguide.org/#installsamba](http://ubuntuguide.org/#installsamba)

Good luck!

---

### Post by sarum on 2006-02-12
Hi, I'm new to Linux and this forum and was about to ask this same question. But was unable to find how to start a new question. Can anyone help me on this please.
My question is not quite the same as Bongobob's. I have an XP machine running a printer(Hp3745) and a scanner(Canoscan). My Linux(Breezy) comp: sits next to the XP and is connected by cross over cabel and KVM(1 mouse, keyboard,& monitor).
I didn't think that I had Samba on the Linux. In a terminal I typed 'find samba', no reply but in search, there were plenty of entries, as there are also in (terminal) man & info:. But man & info(blessings on them both) are not as clear as the folk who reply to us newbies(young & old - I'm old).
Sarum (b:1935)

---

### Post by alamba on 2006-02-12
Hi Sarum,
You can launch a new thread by going to a specific forum (e.g. Desktop Support). You can do this by the Forum Jump box at the bottom of this page. 
Once in the forum click on the new thread box on the top left corner of the page.

Try "sudo /etc/init.d/samba restart". If it restarts then you have samba, or else download from the repositories by using system>>admin>>synaptic.

Akshay

---

### Post by sarum on 2006-02-12
Hi Alamba
Thankyou very much for your reply. I've made a note of both items and shall try them out this evening.
Thanks again Sarum.

---

