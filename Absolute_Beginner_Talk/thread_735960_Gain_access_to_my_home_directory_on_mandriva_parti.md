---
title: "Gain access to my home directory on mandriva partition"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Jay I. on 2008-03-26
Hi people! I just installed ubuntu 7.10 but i'm already enjoying gnome feel and looks. I was working on Mandriva so far so the first thing i tried to do was to browse to my home directory on mandriva partition but i was told that i don't have enough rights. So my question is how to access my files using my ubuntu account. When i was installing ubuntu i was suggested to import my mandriva account into a new ubuntu one but i rejected the option. I really hope i will get some help here and now i'm gonna reboot to get back to mandriva...see you:p

---

### Post by TeoBigusGeekus on 2008-03-26
What if you try the terminal preceded by sudo?
i.e. sudo cd /media/Mandrivapartition/home

---

### Post by Jay I. on 2008-03-26
It helped though it's not what i really want. I got access to all my data but i want gui programs to be able to access it too. I tried to run Eclipse that's located on mandriva partition but when it requested path to the workspace i couldnt specify it caz the dialog for selecting workspace directory didn't allow me to browse anything in my home directory on mandriva partition. Ubuntu shows me that the home directory's owner and group is root and owner ID of /home/jay directory is 500 (i guess it's my mandriva user ID) when my ubuntu ID is 1000. So what can i do? change my user ID but how? If i'm not mistaken when i run Eclipse it runs with root priviledges so this is not the right way to acces my data. But anyway thanks for your help. As someone said it's one small step for man (for me), one giant leap for mankindO:) Any other ideas?

---

### Post by AdamWill on 2008-03-26
yes, you need to either change the UID on Ubuntu to 500, or on Mandriva to 1000. Either way, you would basically have to - as root - change the UID of your user (in Mandriva you can do this with userdrake, not sure about Ubuntu), then - still as root - go to /home and run "chown -r username.username username", to change all the files in your home directory to being owned by the new UID.

---

### Post by Jay I. on 2008-03-27
Yeah, this is the right way! Tanks a lot. Yesterday i reinstalled Ubuntu and imported my mandriva account settings but this didn't help though installer told me that i'd be able to access my documents. So what's the purpose of the option then? Maybe someone knows.
However the problem is solved. Thanks again.

---

