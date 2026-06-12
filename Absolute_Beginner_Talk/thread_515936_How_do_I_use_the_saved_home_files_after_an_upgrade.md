---
title: "How do I use the saved /home files after an upgrade"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Ian-on-the-Trent on 2007-08-02
I'm in the process of upgrading from 6.06 to 7.04 via 6.10.  I followed the instructions/prompts and it involved a combination of files from a CD and from online sources.  Your basic upgrade or so I thought.

I've installed 6.10 but the original /home folders and /data folders were not mounted, in fact, I now have a new /home folder and different username.  I subsequently did manually mount two unmounted partitions (hda6, hda7) and lo and behold these were the missing folders.  To my issues/questions...

[LIST=1]
[*]How do I make the old /home folder active again?  This folder containers the files for 3 different users.
[*]Should I make any necessary changes before or after I upgrade to 7.04?
[*]I burned an image of the 7.04 Desktop disk. Should I just do a clean install using this then recover the old /home folders.
[/LIST]

If I sound a little scrambled...well, I am.

---

### Post by Inxsible on 2007-08-02
> **Ian-on-the-Trent said:**
> I'm in the process of upgrading from 6.06 to 7.04 via 6.10.  I followed the instructions/prompts and it involved a combination of files from a CD and from online sources.  Your basic upgrade or so I thought.

I've installed 6.10 but the original /home folders and /data folders were not mounted, in fact, I now have a new /home folder and different username.  I subsequently did manually mount two unmounted partitions (hda6, hda7) and lo and behold these were the missing folders.  To my issues/questions...
[LIST=1]
[*]How do I make the old /home folder active again?  This folder containers the files for 3 different users.
[*]Should I make any necessary changes before or after I upgrade to 7.04?
[*]I burned an image of the 7.04 Desktop disk. Should I just do a clean install using this then recover the old /home folders.[/LIST]
If I sound a little scrambled...well, I am.

If you are not gonna use/keep the 6.10, then simply do a fresh install of 7.04 in the same drive as where you have installed 6.10.

Make sure to select the /home folder during installation. If you dont select any, Ubuntu will create one for you under / (root). Make sure you are selecting the /home that you want to KEEP.(hda6 or hda7-- whichever is your /home)

Also note that Feisty denotes the drives as sda and not hda but don't worry everything should be the same.

---

### Post by Ian-on-the-Trent on 2007-08-07
> **Inxsible said:**
> If you are not gonna use/keep the 6.10, then simply do a fresh install of 7.04 in the same drive as where you have installed 6.10.

Make sure to select the /home folder during installation. If you dont select any, Ubuntu will create one for you under / (root). Make sure you are selecting the /home that you want to KEEP.(hda6 or hda7-- whichever is your /home)

Also note that Feisty denotes the drives as sda and not hda but don't worry everything should be the same.

Thanks for replying.

*(I'm replacing 6.10 with 7.04.)*

This is where I get confused. When I'm installing 7.04 I get the option to manually partition. If a make the partition hda6 /home and hda7 /data, will those partitions be reformatted and the files currently located there wiped out?

---

### Post by Inxsible on 2007-08-07
> **Ian-on-the-Trent said:**
> Thanks for replying.

*(I'm replacing 6.10 with 7.04.)*

This is where I get confused. When I'm installing 7.04 I get the option to manually partition. If a make the partition hda6 /home and hda7 /data, will those partitions be reformatted and the files currently located there wiped out?
If you mark them to be formatted, then yes.

You have to select the hda6 as /home and hda7 as /data... BUT DO NOT mark them to be formatted. In that event you should achieve what you want.

---

### Post by Ian-on-the-Trent on 2007-08-07
Okay, I'll give that a try,  Thanks.

---

### Post by Ian-on-the-Trent on 2007-08-07
I've started to install 7.04.

I've selected *manual partitioning *and I'm not at "Prepare for Partitioning". The partition created for my install of 6.10 is there and I can edit it to use the entire partition. I would assign the Mount Point as " / ". The swap space was assigned.

I can see the partitions hda6 & hda7. However, when I edit them, I cannot use the full size. Only the empty space is available.  I want to be able to access the accounts for the three different users of that PC.  

How do I go about this?  The HDD is already formated as EXT3.  Do I need to format the partition where the /root is going?  I won't reformat hda6/hda7.

---

