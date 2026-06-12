---
title: "Running Make"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Ephilei on 2006-07-07
I need to compile some drivers using a makefile. In a tutorial (here) I was told to just use the commmand "make" in the drivers' directory but BASH doesn't recognize the command. Is Make not included in Ubuntu by default? I'm nervous about straying fromt he tutorial because there are half a dozen different make files and I don't know which one is supposed to run. Thanks.

---

### Post by christhemonkey on 2006-07-07
You need to install a basic compiler thing.
```
sudo apt-get install build-essential 
```

Then it bash should recognise the make command.

---

### Post by Sonofmoog on 2006-07-07
> **christhemonkey said:**
> 
```
sudo apt-get install build-essential 
```

Great tip!  Thanks ..

---

