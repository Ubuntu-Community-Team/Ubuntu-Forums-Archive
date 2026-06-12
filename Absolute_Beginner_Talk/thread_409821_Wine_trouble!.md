---
title: "Wine trouble!"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Squeak2 on 2007-04-15
OK. I downloaded wine 9.35 from wineHQ and I extracted on ubuntu, now what do I do? I tried the sudo apt-get install wine but it says that it doesnt exist. Many thanks.

---

### Post by slickidiotfan on 2007-04-15
Go to Synaptic Package Manager<Settings<Repositories make sure everyone of the first 4 boxes are checked (especially universe). Close out and click Reload on the console. Next click search and put in "wine". Two files must show up, both wine and wine-dev, mark the open box next to the names and click Mark for Installation for both wine and wine dev. Next click apply. It should be good - try putting in "sudo apt-get install wine" in the terminal, it should say 

```
sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

There you go.

---

### Post by psycosmyth on 2007-04-15
Oh, I thought you had a drinking issue:D 

Is there an installer file? It will be included with some extracted apps. I haven't used that method yet. If you find the file you can rclick on the extracted folder and open it in terminal, then type ./wine-installer. I could be wrong here since I haven't seen it but we'll keep this going in case someone has a positive answer.

---

