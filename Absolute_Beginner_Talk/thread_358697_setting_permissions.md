---
title: "setting permissions"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2007-02-11
sorry lost here 

I used gpartion to decrease the size of the windows directory and give me a bigger file to write to ,,when using linux ( as I use it all the time ) 

but after getting the files showing on my computer .. I cant write to them as it says i dont have permission 

So off to the Wiki ..,,, tried lots of permiatation ..but it still comes back and says I dont have permission 

I tried  sudo su 

$# chmod 777 /media/filename

$#  chmod o+g+r+w+o /media/filename 

in the terminal it doesnt give me an error , but I still cant write to these folders

any Ideas,,,kindly recieved 

Stephen

also window stopped booting ,,but thats not a problem ...dont like the thing anyway 2

---

### Post by ashmew2 on 2007-02-11
I think this link might be of interest to u : [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)
Do get back here tho :D

---

### Post by Jussi Kukkonen on 2007-02-11
Which filesystem are we speaking about? Can you post the mount options you are using (defined in /etc/fstab usually)

Could you link to the instructions you've already tried?

---

