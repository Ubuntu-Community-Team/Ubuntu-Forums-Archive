---
title: "can not install .deb files anymore"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by dynoweb on 2007-07-01
I get the .deb files just fine but when the package installer tries to install them it tells me that there is another synaptic running but there is not... I even tried to reboot but nothing different.
Can anyone help?

---

### Post by hackarre on 2007-07-01
A synaptic process would be: Synaptic, apt-get, aptitude and the upgrade manager, you just have to make sure that no one of these applications are running.

Did you reboot or you just closet x?

Try: dpkg -i "package.deb"

---

### Post by RomeReactor on 2007-07-01
Hi. If I'm not mistaken that's probably Update Manager running in the background; just give it a few minutes (10-15 after reboot) and try again.

---

### Post by ajmorris on 2007-07-01
> **dynoweb said:**
> I get the .deb files just fine but when the package installer tries to install them it tells me that there is another synaptic running but there is not... I even tried to reboot but nothing different.
Can anyone help?

Hi,
Please go into a terminal (menu >> Applications >> accessories >> Terminal)  and go into the directory of where your .deb file is (```
cd directory (desktop would be cd ~/Desktop)
```) 

then type ```
sudo dpkg -i your.deb
```

---

### Post by Raineer on 2007-07-01
> **RomeReactor said:**
> Hi. If I'm not mistaken that's probably Update Manager running in the background; just give it a few minutes (10-15 after reboot) and try again.

I would agree, try running "Update Manager" through the menus and seeing if there are packages sitting out there waiting to be installed. Maybe forcing a check and updating everything would get it out of the way.

---

### Post by dynoweb on 2007-07-01
> **Raineer said:**
> I would agree, try running "Update Manager" through the menus and seeing if there are packages sitting out there waiting to be installed. Maybe forcing a check and updating everything would get it out of the way.

it says the plarpebu package needs to be reinstalled.... how do i do that?

---

### Post by Raineer on 2007-07-01
From command line, 
**sudo apt-get install plarpebu --reinstall**

I would think Synaptic would do it for you, but maybe something is flagged wierd. That happens to mine occasionally as well.

---

### Post by dynoweb on 2007-07-01
> **Raineer said:**
> From command line, 
**sudo apt-get install plarpebu --reinstall**

I would think Synaptic would do it for you, but maybe something is flagged wierd. That happens to mine occasionally as well.

i tried that and this is what i got.

please view attachment.

---

### Post by RomeReactor on 2007-07-01
I did a search on Synaptic for **plarpebu** and got nothing; are you sure that's the package name? Do you have any extra repositories in your **/etc/apt/sources.list**?

---

### Post by Raineer on 2007-07-01
Sounds like it can't find the package anywhere.  A quick google search showed a repository [here]("http://repoubuntusoftware.info/").   I'd follow the first 2 steps under "Terminal Method 2" and then retry the reinstall command from earlier. I think it will pickup the package at that point.  

You might see a warning about not having a public key for the repository but that's not a show-stopper.

---

### Post by dynoweb on 2007-07-01
> **RomeReactor said:**
> I did a search on Synaptic for **plarpebu** and got nothing; are you sure that's the package name? Do you have any extra repositories in your **/etc/apt/sources.list**?

i have a screenshot of the error msg...

---

### Post by RomeReactor on 2007-07-01
It looks like that package comes from an external repository; I suggest you follow **Raineer**'s advice.

---

### Post by dynoweb on 2007-07-01
> **RomeReactor said:**
> It looks like that package comes from an external repository; I suggest you follow **Raineer**'s advice.

well it looked as if the repository stuff worked out just fine I am downloading new updates and installing perfectly..... thank you... if I have any questions later I will ask..

Thank you again

---

