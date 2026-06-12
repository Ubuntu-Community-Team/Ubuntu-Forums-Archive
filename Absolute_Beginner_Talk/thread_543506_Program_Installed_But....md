---
title: "Program Installed But..."
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Shoot3r101 on 2007-09-05
Okay well I recently installed mono and I used a .bin file and the install went perfect. I restarted my computer and the mono menu item is still not there. I double clicked an icon that appeared on the desktop and it opened a folder and I double clicked the mono application but it just does nothing. By the way I did set permission.

BTW when I clicked the property's of the application it said the file type was: desktop configuration file

---

### Post by Shoot3r101 on 2007-09-05
seriously... Bump...

---

### Post by shearn89 on 2007-09-05
Hey - a desktop configuration file is just an icon for the desktop. It won't appear in the menu automatically unless you install it from Add/Remove applications. You can try pressing alt-f2, and typing "mono" to see if it runs.

P.S - you don't really need to bump a post if its only an hour old! have patience - most questions get answers....

---

### Post by Shoot3r101 on 2007-09-05
Okay I tried the run but nothing happened.

---

### Post by afonic on 2007-09-05
Install mono from the repositories.

sudo apt-get install mono

However I don't know if a menu icon is created, I think it just installs the mono compiler and stuff.

---

### Post by Shoot3r101 on 2007-09-06
Okay I did the apt-get and it installed it but still not in the menu? Can you guys teach me how to manually add it to the menu?

---

### Post by afonic on 2007-09-06
You want to add to the menu what?

I don't think Mono adds something in the menu, its the compiler and stuff like that, command line only. Are you looking for an dev interface?

---

### Post by bigboy_pdb on 2007-09-06
I think you should have a look at this page:
[http://www.mono-project.com/Introduction_to_developing_with_Mono](http://www.mono-project.com/Introduction_to_developing_with_Mono)

You'll also need to install the package "mono-mcs". You can do this by opening "Synaptic Package Manager" (System -> Administration -> Synaptic Package Manager). You can do a search for "mono-mcs". Right click on the package and select "Mark for Installation" and then click the "Apply" button.

"mono" runs the executables that you compile using "mcs". You can only use them in the command line (Applications -> Accessories -> Terminal).

---

