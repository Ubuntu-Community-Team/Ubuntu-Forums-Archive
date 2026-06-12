---
title: "Synaptic just kinda... Pops..."
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Raavea on 2006-09-29
Um, I'm not sure how to describe this.

 Earlier today it was working fine - I used it to install WINE from the repos.

 I just went to open it. It asked for me password, which I entered, began loading the synaptic package manager itself, and then the whole thing vanished. No error message.

 Now, whenever I go to open it, it doesn't ask the password and opens to the bare window (no content) and then vanishes again.

 I might note that I just installed the 0.10 murrina debian, and am about to go find a newer one to see if that helps.


 What's that sudo apt-get thing you can do via the command line..? dist-upgrade or something..? :S It's late here. Technically early.



 EDIT: Okies, so I still have no idea what the issue was. Even put the synaptic openy command thinger into a terminal window to try and catch an error message, but nothing.

 A website told me to sudo apt-get update, upgrade, dist-upgrade, and it's all working now.

 I wonder what caused this...

---

### Post by morphodone on 2006-09-29
hmm, you could try

```
gksudo synaptic
```

and see if there is any error messages

otherwise

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install *packagename*
```

---

### Post by bulldog on 2006-09-29
```
sudo aptitude update
sudo aptitude dist-upgrade 
```

---

