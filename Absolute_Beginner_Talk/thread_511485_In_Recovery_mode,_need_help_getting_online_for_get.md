---
title: "In Recovery mode, need help getting online for get-app"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by soulrider4ever on 2007-07-27
Hey,

I'm new to Ubuntu, but I absolutely LOVE IT...

However, I just setup a dual boot with my Dell E1505 and it has the X1400 ati gpu...I'm aware of the issue and how to fix it so my x.org works, however, when im in recovery mode, I'm not able to run the get-app update and get-app ATI drivers because it's not connecting me automatically to the internet..

I need to know what I need to type to get myself online so I can get these drivers so I can boot normal in GUI.

Thanks for helping out another noobie :)

Joe

---

### Post by nitro_n2o on 2007-07-27
it depends on  your interface 
sudo ifup <int> 

if you are connected to ethernet then ```
sudo ifup eth0
```
hope that helps

---

### Post by soulrider4ever on 2007-07-28
Thanks, worked like a charm!

Joe

---

### Post by Warmask on 2008-04-05
I am also trying to use apt-get in recovery mode and all I get is "Failed to fetch bla bla"

I tried "sudo ifup eth0"

but the output is 
```
sudo ifup eth0
Ignoring unkown interface eth0=eth0.
```
my ethernet connection is blinking, and if i boot w/ the live cd I can get on the internet just fine.
Can anyone tell me what is wrong, or if there is a different way of doing this?
I'm using 7.10

Thanks in advance!

---

