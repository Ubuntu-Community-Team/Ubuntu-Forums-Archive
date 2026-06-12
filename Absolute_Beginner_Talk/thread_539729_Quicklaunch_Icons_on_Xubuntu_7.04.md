---
title: "Quicklaunch Icons on Xubuntu 7.04"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by anmlcrckrs on 2007-08-31
Alrighty, I got Xubuntu up and running on my Portege 4010 and everything is running well. 

I've got WifiRadar up and running which is a great improvement over the standard network manager included with it, and I want to setup a launcher for wifiradar on my top panel.  

The main thing I don't know is the command that I need to put in the launcher properties to allow it to come up.  

I would also like to make one of these for gaim and am not sure where to find the command to input.  

Any help is greatly appreciated.

---

### Post by ericmitz on 2007-08-31
> **anmlcrckrs said:**
> Alrighty, I got Xubuntu up and running on my Portege 4010 and everything is running well. 

I've got WifiRadar up and running which is a great improvement over the standard network manager included with it, and I want to setup a launcher for wifiradar on my top panel.  

The main thing I don't know is the command that I need to put in the launcher properties to allow it to come up.  

I would also like to make one of these for gaim and am not sure where to find the command to input.  

Any help is greatly appreciated.

gaim should be 
```

/usr/bin/gaim

```

I dont have wifi-radar installed, but you can type:

```

which wifi-radar

```

into a terminal and it will tell you the path. In reality though, you probably dont need the full path anyway. you could more than likely just put 'gaim' and 'wifi-radar'

---

### Post by anmlcrckrs on 2007-08-31
Thanks!  Gaim works.

Got wifi-radar to work by using 

gksudo -S wifi-radar

Found it using the application finder and more info.

Thanks for the help!

---

