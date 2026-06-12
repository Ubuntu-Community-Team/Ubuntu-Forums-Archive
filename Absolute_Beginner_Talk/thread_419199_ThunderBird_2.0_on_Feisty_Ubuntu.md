---
title: "ThunderBird 2.0 on Feisty Ubuntu"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by unbreakable on 2007-04-22
these were launched the same day but feisty does not include thunderbird 2.0

So I went to the thunderbird site and downloaded it, unpacked it.. and now what???
lol

I dont know how to upgrade... I was able to run it, but from the folder on my desktop...
I am sure that, that is not the correct way.

So can anyone give me step by step instructions? (im a newbie.. does it show? lol)

thanks:popcorn:

---

### Post by lonce on 2007-04-22
When you download it, you will need to compile it and install it.

---

### Post by crimesaucer on 2007-04-22
I just installed Thunderbird 2.0 and it worked perfectly from using this guide:

[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

I only need to know how to change the path for the icon in my xubuntu's network menu. My XFCE menu doesn't list the --system-- icons in the Menu Editor. It was no problem changing my Mailwatch launcher and the icon I put in my menu in the top area where the separator is.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-27-6.png[/IMG]

---

### Post by phabulosa on 2007-04-25
Due to conflict with my SCIM input mathod, I need to roll back my thunderbird to 1.5

can anyone tells me how to do that?

thanks!

---

### Post by clevin on 2007-04-25
> **phabulosa said:**
> Due to conflict with my SCIM input mathod, I need to roll back my thunderbird to 1.5

can anyone tells me how to do that?

thanks!
edit the startup scripts of thunderbird (thunderbird and run-mozilla.sh), add one line in the beginning of the file (after the first line if it begins with #!/bin/sh):

> export GTK_IM_MODULE=xim

---

