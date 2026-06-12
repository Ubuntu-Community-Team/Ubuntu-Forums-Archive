---
title: "Unable to download"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by coolyog on 2007-09-07
im using ubuntu 7.04...and wen i clik on applications --> add/remove programs, to install beryl and mp3 codec i was nt able to do so..it downloaded some packages and in the ned gave the error, " Could not download all repository indexes".....but i successfully installed nvidia  7400 driver software by the same process....
can u plzz temme wht cud be the problem and wht is the soln?

---

### Post by meborc on 2007-09-07
you could try to run "sudo apt-get update" to update the indexes...

also it is wise to enable extra repositories in the synaptic [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

---

### Post by p_quarles on 2007-09-07
I've seen this before, and it's possible that you will need to fix a network setting. Run the command that meborc suggested, and post the output here.

---

### Post by coolyog on 2007-09-07
sir wen i tried the first command i got this message
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by meborc on 2007-09-07
hmm... do you have synaptic running? if so close it and run the command again...

synaptic is just a GUI for apt... so they both can't work at the same time

---

### Post by coolyog on 2007-09-07
yeah..now it says 

0%  connecting to in.archive.ubuntu.com   <ip add>.  [connecting to security.

---

### Post by coolyog on 2007-09-07
connection timed out

---

### Post by p_quarles on 2007-09-07
Is that it? Does it time out eventually?

Also, post the IP address. It's not yours, it's the one that APT is trying to connect to, and it can be a useful clue about what's wrong.

---

### Post by coolyog on 2007-09-07
91.189.89.6 is the ip of the server...

shd i go to preferences and change the server....change it to server of sum othr c ountry...will it help???

---

### Post by p_quarles on 2007-09-07
> **coolyog said:**
> 91.189.89.6 is the ip of the server...

shd i go to preferences and change the server....change it to server of sum othr c ountry...will it help???
Possibly. But try this first:
```
ping -c 5 91.189.89.6
```

---

### Post by coolyog on 2007-09-07
sir i tried that but no reply
100% packets lost

---

### Post by p_quarles on 2007-09-07
> **coolyog said:**
> sir i tried that but no reply
100% packets lost
Interesting. Now try this:
```
ping -c 5 www.google.com
```
By the way, is the computer having this problem the same one you are posting from?

---

### Post by coolyog on 2007-09-07
lol......100 % packets lost again.....
yes im using the same computer.....

---

### Post by p_quarles on 2007-09-07
> **coolyog said:**
> lol......100 % packets lost again.....
yes im using the same computer.....
Hmm. That's *really* strange. The test you just ran would usually indicate that you can't connect to the internet at all. So maybe your posts are in my imagination? :D

One thing you could try is this:
```
unset http_proxy
```
and then try running apt-get update again.

Meanwhile, I'm going to look into some other troubleshooting steps.

---

### Post by coolyog on 2007-09-07
ya i tried that..but still the same error...
btw i have started downloading frm the main server and itzz going on....but evrytime i get the error only in the end..dono whr this will work or not..i hope i dont get an error in the end...
btw wht is meant by repository?

---

### Post by p_quarles on 2007-09-07
Repository = the servers that host applications for download.

Could you post the results of these commands:
```
ifconfig -a
```
and
```
route
```

---

### Post by Paul133 on 2007-09-07
A repository is aserver that stores thousands of programs made for Ubuntu that you can download. There are lots of different repositories for different kinds of software. The main repository has all the free software, the universe has software under restrictive lienses, and the multiverse has software under questionable licenses.

To enable the others, open Synaptic, go to Settings -> Repositories. Under the tab Ubuntu Software, check all the boxes.

---

