---
title: "can't gain access to network-feisty fawn"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by destructo on 2007-04-27
Let me say hi and thanks if you can help.

Heres the deal.

I'm a newb, okay ive admitted it. Now that thats out of the way i will try and explain what happens.

I'm using Feisty Fawn 7.04 alternate Amd64.

When i go to get onto the network, >places>network. it comes up with a folder that has an icon which say Windows Network. 

This is what I want, however when i click on the icon nothing comes up the folder is empty. This is where the other computers that are shared should come up. My wife is running Ubuntu dapper drake 6.10 and she can see all 4 computers on the network and gets access to them all. 2 unfortunately are running windows and I'm trying to use my influential powers to convert these children using windows to change over to Linux. In the mean time i wish to access the network, sooo how do i do this? I wish to use samba. Is there a problem because this is a new release, are there bugs that need ironing out? anyways thanks for your help and responses.

I only installed feisty fawn yesterday and so far its great.

Thanks. :guitar:

---

### Post by Ubuntiac on 2007-04-27
Sounds to me like you need to add your computer to the same workgroup as everyone else.

1. I'd go onto you'r wife's computer and (if she'll let you ;) ) and go to network, >places>network

2.The name of that folder is the workgroup she's on (and seeing the other computers on)
Make sure that your computer is on the same workgroup by looking in smb.conf:

Assuming you're using Ubuntu, just open a terminal and type:
```

sudo gedit /etc/samba/smb.conf
```
(if you're in Kubuntu, replace gedit with kate)

3. Near the top of the file you'll see:

```

domain = workgroup
```

change where it says "workgroup" to whatever the name of the workgroup on your wife's computer was. If you want to be sure you can use the same command on her computer (the gedit one) to look at smb.conf on her computer and see what it says (eg workgroup = homenetwork)

4. When you're done, restart samba to make sure the new settings take effect by entering:
```

sudo /etc/init.d/samba restart
```

---

### Post by destructo on 2007-04-27
Well it turns out I'm a boon but i fixed the problem, i fiddled around a bit and solved it myself using one of the sticky articles about networking. 

After you have done something to the system you must remember to restart the computer ;)

Thanks.

---

### Post by destructo on 2007-04-27
got another one,

when the kids try and access my computer which is running feisty they get a password screen, how do i make it so they dont need to put a password in?

Thanks.

---

