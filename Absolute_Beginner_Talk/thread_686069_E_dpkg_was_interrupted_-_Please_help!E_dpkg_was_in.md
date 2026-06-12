---
title: "E: dpkg was interrupted - Please help!
E: dpkg was interrupted, you"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Georgie.Mathews on 2008-02-02
Hello I was busy installing slimserver via synaptic and it timed out when downloading the firmware. I rebooted and I cant use synaptic or command line apt-get as I get this error :
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


```

However running that command takes me back to the timed out part of the slimserver install which doesnt really help. 

Help will be appreciated :]:)

---

### Post by wormser on 2008-02-02
Did you run the command with sudo?

```
sudo dpkg --configure -a
```
```
sudo apt-get update
```

---

### Post by Rocket2DMn on 2008-02-02
What if you run
```
sudo dpkg --configure -a
```
The "sudo" is needed.

---

### Post by Georgie.Mathews on 2008-02-02
Yes I ran it with sudo. How do i kill the install, I dont want to install this particular package anymore.

---

### Post by Rocket2DMn on 2008-02-02
Hit CTRL+C while apt-get is running, then try
```
sudo dpkg --configure -a
sudo apt-get remove slimserver --purge
sudo apt-get clean
sudo apt-get update
```
where "slimserver" is the exact name of the package.

---

