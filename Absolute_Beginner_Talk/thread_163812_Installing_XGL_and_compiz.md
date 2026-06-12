---
title: "Installing XGL and compiz"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by Majdaa on 2006-04-21
Hi, i just formatted my partition and installe dapper....i'm trying to get XGL and compiz to work with no success whatsoever, i've been asking in the IRC channel all day long. 

Anyway, here's what i think will help outline my problem:

My computer specs:
Intel pentium 4 2.8GHZ + HT
ATI Radeon 9200 128mb
1GB ram

I guess i should ask whether my computer can handle it in the first place...

i type in fglrx-control in the terminal, and get: fglrx-control: command not found

Then i figured the problem was with my driver...

I looked in synaptic and it seemed that i had my driver installed.....yet like i said...when i type fglrx in the terminal i get nothing....

I'm really confused and disoriented...i don't know where i'm headed...please note i'm an absolute beginner too...



Thanks for any help in advance

---

### Post by mostwanted on 2006-04-21
Find a tutorial on how to install radeon drivers (should be a howto somewhere). When you've got them working, look at the XGL/Compiz sticky thread in the Dapper forum.

Also, this doesn't belong in this forum, even if it's a newbie having the problems. Dapper is still only beta and XGL and Compiz aren't really traditional newbie stuff

---

### Post by lazyd2 on 2006-04-21
For ATI driver installation check this [_"page"_]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

As far as XGL, I followed [_"this"_]("http://www.tectonic.co.za/view.php?id=916") guide.

---

### Post by Majdaa on 2006-04-21
worked wonderfully, thank you very much.

My only remaining question is how to view all open windows together, and how to use the cube.
My understanding what that i switch the cube by changing the workspace, however, i only see one workspace in the plugin on the bottom right and it won't let me add a new workspace....


thanks for the help and sorry for the wrong section

EDIT: i found that in gconf-editor, zoom isn't even in apps>compiz>plugins. Cube is there but doesn't have system0>options...

---

