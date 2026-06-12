---
title: "how do i modify source.list"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by hwe001 on 2006-04-26
i need to install FLTK but i couldn't find it from Synaptic. Read from other posts that I need to modify source.list (uncomment a few lines). but system reminds me that i don't have permission to modify the file, can anyone tell me how this can be done?

---

### Post by jazzmuzik on 2006-04-26
You can add repositories from Synaptic.

Look at Settings, Repositories, Add, Custom

---

### Post by professor_chaos on 2006-04-26
Synaptic is one way. But you should get familiar with the commandline method.

First pick and editor. To start we will use a graphical editor called "gedit"
Second, you need "permisson" of root to edit this file. Root is the administrative account on your system. For this we use the command "sudo".
Third, we need a terminal to do this.

Ok, now that you understand that, open a terminal window from Applications->Accessories->Terminal. Next type 
```
sudo gedit /etc/apt/sources.list
```

now you can edit the file with administrative privilages and then when your done, type
 ```
sudo apt-get update
```
this find updates from the repository you just added and now your free to install with synaptic.

---

### Post by az on 2006-04-26
[QUOTE=professor_chaos]Synaptic is one way. But you should get familiar with the commandline method.
[/QUOTE]

No.  You shouldn't have to use the command line if you don't want to.  The command line is great, but it's not for everybody.

---

### Post by gingermark on 2006-04-26
In this case however, editing the file manually does allow you to add proper comments for each repository you might add, which using Synaptic doesn't I think. You can add comments easily enough with Adept though.

And please note the file is source**s**.list. Anyone trying professor_chaos's instructions would have little problem there....

---

### Post by Danny Boy on 2006-04-26
EDITED: Removed link.. just realized it was for Hoary.

---

### Post by manicka on 2006-04-26
aysiu has a nice how-to for sources [here]("http://www.psychocats.net/ubuntu/sources")

---

### Post by gingermark on 2006-04-26
[QUOTE=Danny Boy]hwe, 

  I'm not sure what repositories you need but a good list and walk through is [here]("http://www.ubuntuguide.org/#extrarepositories").[/QUOTE]
NO

I'm sorry, but that is a bad list to give a newbie as it is for Hoary, and I would suggest the OP is using Breezy or maybe even Dapper.

If anyone is interested in extra repositories check out my sig - but be careful using unofficial repositories.

---

